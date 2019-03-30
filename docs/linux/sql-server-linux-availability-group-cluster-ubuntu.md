---
title: SQL Server 가용성 그룹에 대 한 Ubuntu 클러스터 구성
titleSuffix: SQL Server
description: Ubuntu에 대 한 가용성 그룹 클러스터를 만드는 방법을 알아보고합니다
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.date: 04/30/2018
ms.topic: conceptual
ms.prod: sql
ms.custom: sql-linux, seodec18
ms.technology: linux
ms.assetid: dd0d6fb9-df0a-41b9-9f22-9b558b2b2233
ms.openlocfilehash: b174f21cc0fa15404587f63019b5bcda2eb72534
ms.sourcegitcommit: 706f3a89fdb98e84569973f35a3032f324a92771
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/29/2019
ms.locfileid: "58658107"
---
# <a name="configure-ubuntu-cluster-and-availability-group-resource"></a>Ubuntu 클러스터 및 가용성 그룹 리소스 구성

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

이 문서에서는 Ubuntu에서 3 노드 클러스터를 만들고 이전에 만든된 가용성 그룹에 클러스터 리소스로 추가 하는 방법을 설명 합니다. 고가용성을 위해 Linux에서 가용성 그룹을 필요한 3 개의 노드가-참조 [가용성 그룹 구성에 대 한 높은 가용성 및 데이터 보호](sql-server-linux-availability-group-ha.md)합니다.

> [!NOTE] 
> 이 시점에서 Linux의 Pacemaker 사용 하 여 SQL Server의 통합은 Windows에 WSFC를 사용 하 여으로 결합 없습니다. sql에서 클러스터의 현재 상태에 대 한 지식이 없는, 모든 오케스트레이션에서는 외부가 되며 서비스는 독립 실행형 인스턴스로 Pacemaker에 의해 제어 됩니다. 또한 가상 네트워크 이름은 WSFC 관련, Pacemaker에 동일한 동등한 옵션이 없습니다. Always On 동적 관리 뷰 클러스터 정보를 쿼리 하는 빈 행을 반환 합니다. 장애 조치 후 투명 하 게 연결에 사용 하려면 수신기를 만들 수 있습니다 하지만 (다음 섹션에서 설명)으로 가상 IP 리소스를 만드는 데 사용 된 IP를 사용 하 여 DNS 서버에서 수신기 이름의 수동으로 등록 해야 합니다.

다음 섹션에서는 장애 조치 클러스터 솔루션을 설정 하는 단계를 안내 합니다. 

## <a name="roadmap"></a>로드맵

고가용성을 위해 Linux 서버에서 가용성 그룹을 만드는 단계는 Windows Server 장애 조치 클러스터에 대 한 단계와 다릅니다. 다음과 같은 단계를 간략히 설명 합니다. 

1. [SQL Server 클러스터 노드에서 구성](sql-server-linux-setup.md)합니다.

2. [가용성 그룹을 만들](sql-server-linux-availability-group-configure-ha.md)합니다. 

3. Pacemaker와 같은 클러스터 리소스 관리자를 구성 합니다. 이러한 지침은이 문서에 있습니다.
   
   클러스터 리소스 관리자를 구성 하는 방법은 특정 Linux 배포에 따라 달라 집니다. 

   >[!IMPORTANT]
   >프로덕션 환경에 같은 고가용성에 대 한 STONITH는 펜싱 에이전트가 필요합니다. 이 문서의 데모는 펜싱 에이전트를 사용 하지 마세요. 데모 테스트 및 유효성 검사에만 됩니다. 
   
   >Linux 클러스터는 클러스터를 알려진된 상태로 반환할 펜싱을 사용 합니다. 펜스를 구성 하는 방법은 배포 및 환경에 따라 달라 집니다. 이때 펜싱 일부 클라우드 환경에서는 제공 되지 않습니다. 참조 [RHEL 높은 가용성 클러스터-가상화 플랫폼에 대 한 지원 정책을](https://access.redhat.com/articles/29440) 자세한 내용은 합니다.

5.  [가용성 그룹에 클러스터 리소스로 추가](sql-server-linux-availability-group-cluster-ubuntu.md#create-availability-group-resource)합니다. 

## <a name="install-and-configure-pacemaker-on-each-cluster-node"></a>설치 하 고 각 클러스터 노드에서 Pacemaker 구성

1. 모든 노드에서 방화벽 포트를 엽니다. Pacemaker 고가용성 서비스, SQL Server 인스턴스 및 가용성 그룹 끝점에 대 한 포트를 엽니다. SQL Server를 실행 하는 서버에 대 한 기본 TCP 포트는 1433입니다.  

   ```bash
   sudo ufw allow 2224/tcp
   sudo ufw allow 3121/tcp
   sudo ufw allow 21064/tcp
   sudo ufw allow 5405/udp
        
   sudo ufw allow 1433/tcp # Replace with TDS endpoint
   sudo ufw allow 5022/tcp # Replace with DATA_MIRRORING endpoint
        
   sudo ufw reload
   ```
   
   또는 방화벽을 비활성화할 수 있습니다.
        
   ```bash
   sudo ufw disable
   ```

1. Pacemaker 패키지를 설치 합니다. 모든 노드에서 다음 명령을 실행 합니다.

   ```bash
   sudo apt-get install pacemaker pcs fence-agents resource-agents
   ```

2. Pacemaker 및 Corosync 패키지를 설치할 때 생성된 기본 사용자의 암호를 설정합니다. 모든 노드에서 같은 암호를 사용합니다. 

   ```bash
   sudo passwd hacluster
   ```

## <a name="enable-and-start-pcsd-service-and-pacemaker"></a>사용 및 pcsd 서비스 및 Pacemaker를 시작 합니다.

다음 명령을 사용 하도록 설정 하 고 pcsd 서비스 및 pacemaker를 시작 합니다. 모든 노드에서 실행 합니다. 이 노드를를 다시 부팅 한 후 클러스터에 다시 조인할 수 있습니다. 

```bash
sudo systemctl enable pcsd
sudo systemctl start pcsd
sudo systemctl enable pacemaker
```
>[!NOTE]
>Enable pacemaker 명령 'pacemaker 기본 시작 중단 없는 runlevels를 포함 합니다.' 오류가 발생 하 여 완료 될 수 있습니다. 이 무시 해도 됩니다 클러스터 구성을 계속 진행할 수 있습니다. 

## <a name="create-the-cluster"></a>클러스터 만들기

1. 모든 노드에서 모든 기존 클러스터 구성을 제거 합니다. 

   동시에 pacemaker, corosync 및 pc를 설치 하 고 서비스의 모든 3이 실행을 시작 하는 실행 중인 'sudo apt-get install pc'.  Corosync를 시작 템플릿을 생성 합니다. ' / etc/cluster/corosync.conf' 파일입니다.  이 파일을 성공 하는 다음 단계에 존재 하지 않음-pacemaker를 중지 하려면이 문제를 해결 하므로 / corosync 삭제 하 고 ' / etc/cluster/corosync.conf', 한 다음 다음 단계를 성공적으로 완료 합니다. 동일한 작업을 수행 'pcs cluster 제거' 및로 사용 하 여 시간 초기 클러스터 설치 단계입니다.
   
   다음 명령은 기존 클러스터 구성 파일을 제거 하 고 모든 클러스터 서비스를 중지 합니다. 이 클러스터를 영구적으로 제거합니다. 사전 프로덕션 환경에서 첫 번째 단계로 실행 합니다. 참고 pacemaker 서비스 및 다시 사용 하도록 설정 하는 요구는 'pcs cluster 삭제' 사용할 수 없습니다. 모든 노드에서 다음 명령을 실행합니다.
   
   >[!WARNING]
   >이 명령은 기존 클러스터 리소스를 제거합니다.

   ```bash
   sudo pcs cluster destroy 
   sudo systemctl enable pacemaker
   ```

1. 클러스터를 만듭니다. 

   >[!WARNING]
   >클러스터링 공급 업체 조사를 시작 하는 알려진된 문제로 인해 클러스터 ('pc 클러스터 시작') 다음 오류로 인해 실패 합니다. 클러스터 설치 명령을 실행할 때 만들어진는 무엇이 /etc/corosync/corosync.conf에 구성 된 로그 파일 때문입니다. 이 문제를 해결 하려면 로그 파일을 변경 합니다. /var/log/corosync/corosync.log 합니다. 또는 /var/log/cluster/corosync.log 파일을 만들 수 있습니다.
 
   ```Error
   Job for corosync.service failed because the control process exited with error code. 
   See "systemctl status corosync.service" and "journalctl -xe" for details.
   ```
  
다음 명령은 3 개 노드 클러스터를 만듭니다. 스크립트를 실행하기 전에 `< ... >` 사이의 값을 바꿉니다. 주 노드에서 다음 명령을 실행 합니다. 

   ```bash
   sudo pcs cluster auth <node1> <node2> <node3> -u hacluster -p <password for hacluster>
   sudo pcs cluster setup --name <clusterName> <node1> <node2...> <node3>
   sudo pcs cluster start --all
   sudo pcs cluster enable --all
   ```
   
   >[!NOTE]
   >이전에 같은 노드에서 클러스터를 구성한 경우 'pcs cluster setup'을 실행할 때 '--force' 옵션을 사용해야 합니다. 이 방법은 'pcs cluster destroy'를 실행하는 것과 같고 'sudo systemctl enable pacemaker'를 사용하여 Pacemaker 서비스를 다시 사용하도록 설정해야 합니다.


## <a name="configure-fencing-stonith"></a>펜싱 (STONITH) 구성

Pacemaker 클러스터 공급 업체는 STONITH를 사용 하도록 설정 및 지원 되는 클러스터 설치를 구성 하는 펜싱 장치에 필요 합니다. Cluster resource manager는 노드 또는 노드 리소스의 상태를 확인할 수 없습니다, 하는 경우 펜스를 알려진된 상태로 클러스터를 다시 표시 하려면 사용 됩니다. 리소스 수준 펜싱 주로 리소스를 구성 하 여 가동 중지 시에도 없는 데이터 손상이 있는지 확인 합니다. 리소스 수준 펜싱을 사용할 수 있습니다 예를 들어, 오래 된 경우 처럼 노드에서 디스크를 표시 하려면 (복제 된 블록 장치 Distributed) DRBD를 사용 하 여 통신 링크 중단 합니다. 노드 수준 펜싱 노드 리소스 실행 되지 않도록 보장 합니다. 노드를 다시 설정 하 여 이렇게 하 고는 Pacemaker 구현의 STONITH (약자인 "헤드에 있는 다른 노드가 특이") 이라고 합니다. 키를 누릅니다. 무정전 전원 공급 장치 또는 관리를 서버에 대 한 카드 인터페이스 예를 들어, pacemaker 다양 한 펜스 장치를 지원 합니다. 자세한 내용은 [처음부터 Pacemaker 클러스터](https://clusterlabs.org/pacemaker/doc/en-US/Pacemaker/1.1/html/Clusters_from_Scratch/) 고 [펜싱 및 Stonith](https://clusterlabs.org/doc/crm_fencing.html) 

구성 펜싱 노드 수준 환경에 따라 크게 달라 집니다, 있으므로 (구성할 수 있습니다 나중)이이 자습서에 대 한 비활성화 했습니다. 주 노드에서 다음 스크립트를 실행 합니다. 

```bash
sudo pcs property set stonith-enabled=false
```

>[!IMPORTANT]
>STONITH를 사용 하지 않도록 설정 하는 것은 테스트 목적에 대해서만 합니다. 프로덕션 환경에서 Pacemaker를 사용 하려는 경우 환경에 따라 STONITH 구현 계획을 계속 사용 합니다. 참고가 시점에 모든 클라우드 환경 (Azure 포함) 또는 Hyper-v에 대 한 펜스 에이전트가 없습니다. 검사가 클러스터 공급 업체는 이러한 환경에서 실행 중인 프로덕션 클러스터에 대 한 지원을 제공 하지 않습니다. 

## <a name="set-cluster-property-cluster-recheck-interval"></a>클러스터 속성 클러스터-다시 확인-간격 설정

`cluster-recheck-interval` 리소스 매개 변수, 제약 조건 또는 다른 클러스터 옵션에 대 한 변경 내용에 대 한 클러스터 확인 하는 폴링 간격을 나타냅니다. 클러스터를 연결 된 간격으로 복제본을 다시 시작 하려고 복제본이 다운 되 면 합니다 `failure-timeout` 값 및 `cluster-recheck-interval` 값입니다. 예를 들어 경우 `failure-timeout` 60 초로 설정 됩니다 및 `cluster-recheck-interval` 설정 120 초 이내 60 초 보다 큰 간격을 120 초로 다시 시작 시도 됩니다. 오류 제한 60s와 클러스터-다시 확인-간격은 60 초 보다 큰 값으로 설정 하는 것이 좋습니다. 클러스터 다시 확인 간격을 작은 값으로 설정 하는 것은 좋지 않습니다.

속성 값을 업데이트 하려면 `2 minutes` 실행:

```bash
sudo pcs property set cluster-recheck-interval=2min
```

> [!IMPORTANT] 
> Pacemaker 클러스터에서 관리 하는 가용성 그룹 리소스가 이미 있는 경우에 최신 사용 가능한 Pacemaker 패키지 1.1.18-11.el7를 사용 하는 모든 분산 발생 경우 설정을 시작 실패-는-치명적이 지 클러스터에 대 한 동작 변경 참고 해당 값은 false입니다. 이 변경에 장애 조치 워크플로 적용 합니다. 주 복제본 중단이 발생 하는 경우 클러스터는 사용 가능한 보조 복제본 중 하나에 장애 조치 해야 합니다. 대신 사용자 클러스터 유지 실패 한 주 복제본을 시작 하는 것을 알 수 있습니다. 해당 기본 되지 온라인 상태가 되 면 (때문에 영구 작동 중단)를 클러스터 하지 장애 조치 다른 사용 가능한 보조 복제본으로 합니다. 이러한 변경으로 인해 시작 실패-는-치명적이 지 설정 하려면 이전에 권장 되는 구성이 더 이상 유효 하며 설정의 기본 값으로 다시 되돌릴 `true`합니다. AG 리소스를 포함 하도록 업데이트 해야 하는 또한는 `failover-timeout` 속성입니다. 
>
>속성 값을 업데이트 하려면 `true` 실행:
>
>```bash
>sudo pcs property set start-failure-is-fatal=true
>```
>
>기존 AG 리소스 속성을 업데이트 `failure-timeout` 하 `60s` 실행 (대체 `ag1` 가용성 그룹 리소스의 이름):
>
>```bash
>pcs resource update ag1 meta failure-timeout=60s
>```

## <a name="install-sql-server-resource-agent-for-integration-with-pacemaker"></a>Pacemaker를 사용 하 여 통합에 대 한 SQL Server 리소스 에이전트를 설치 합니다.

모든 노드에서 다음 명령을 실행합니다. 

```bash
sudo apt-get install mssql-server-ha
```

## <a name="create-a-sql-server-login-for-pacemaker"></a>Pacemaker 용 SQL Server 로그인 만들기

[!INCLUDE [SLES-Create-SQL-Login](../includes/ss-linux-cluster-pacemaker-create-login.md)]

## <a name="create-availability-group-resource"></a>가용성 그룹 리소스 만들기

가용성 그룹 리소스를 만들려면 사용 하 여 `pcs resource create` 명령 및 리소스 속성을 설정 합니다. 아래 명령을 만듭니다는 `ocf:mssql:ag` 형식 리소스 이름의 가용성 그룹에 대 한 마스터/슬레이브 `ag1`합니다. 

```bash
sudo pcs resource create ag_cluster ocf:mssql:ag ag_name=ag1 meta failure-timeout=30s --master meta notify=true

```

[!INCLUDE [required-synchronized-secondaries-default](../includes/ss-linux-cluster-required-synchronized-secondaries-default.md)]

## <a name="create-virtual-ip-resource"></a>가상 IP 리소스 만들기

가상 IP 주소 리소스를 만들려면 노드 하나에서 다음 명령을 실행 합니다. 네트워크에서 사용 가능한 정적 IP 주소를 사용 합니다. 스크립트를 실행 하기 전에 사이의 값을 바꿉니다 `< ... >` 유효한 IP 주소를 사용 합니다.

```bash
sudo pcs resource create virtualip ocf:heartbeat:IPaddr2 ip=<10.128.16.240>
```

Pacemaker에서 해당 가상 서버 이름이 없습니다. 문자열 서버 이름으로 가리키는 연결 문자열을 사용 하 고 IP 주소를 사용 하지 하려면 DNS의 ip 리소스 이름과 원하는 가상 서버를 등록 합니다. DR 구성에 대 한 기본 및 DR 사이트에서 DNS 서버를 사용 하 여 원하는 가상 서버 이름 및 IP 주소를 등록 합니다.

## <a name="add-colocation-constraint"></a>공동 배치 제약 조건 추가

Pacemaker 클러스터에서 리소스를 실행할 위치를 선택 하는 등 거의 모든 의사 결정은 점수를 비교 하 여 수행 됩니다. 리소스 당 점수 계산 하 고 클러스터 리소스 관리자가 특정 리소스에 대 한 점수가 가장 높은 노드를 선택 합니다. (노드는 리소스에 대 한 음수 점수 있으면 리소스 수 없습니다. 해당 노드에서 실행 합니다.) 클러스터의 결정을 구성 하려면 제약 조건을 사용 합니다. 제한에는 점수는. 제약 조건에는 무한대 보다 낮은 점수를 인지만 권장 합니다. 무한대의 점수를 반드시 의미 합니다. 주 복제본과 가상 ip 리소스를 동일한 호스트에서이 되도록 무한대의 점수를 사용 하 여 공동 배치 제약 조건을 정의 합니다. 공동 배치 제약 조건을 추가할 노드 하나에서 다음 명령을 실행 합니다. 

```bash
sudo pcs constraint colocation add virtualip ag_cluster-master INFINITY with-rsc-role=Master
```

## <a name="add-ordering-constraint"></a>정렬 제약 조건을 추가 합니다.

공동 배치 제약 조건을 암시적 순서 제약 조건이 있습니다. 가용성 그룹 리소스를 이동 하기 전에 가상 IP 리소스를 이동 합니다. 기본적으로 이벤트 순서는:

1. 사용자 문제 `pcs resource move` 가용성 그룹에 주 노드 1에서 노드 2로 합니다.
1. Node1의 가상 IP 리소스를 중지합니다.
1. 가상 IP 리소스를 노드 2에서 시작합니다.

   >[!NOTE]
   >이 시점에서 IP 주소 일시적으로 node2로 node2는 여전히 이전 장애 조치 하는 동안 보조 합니다. 
   
1. Node1의 기본 가용성 그룹 보조 복제본이 강등 합니다.
1. Node2의 보조 가용성 그룹은 기본으로 승격 됩니다. 

IP 주소를 사전 장애 조치 보조 노드를 일시적으로 가리키는 방지 하려면 정렬 제약 조건을 추가 합니다. 

정렬 제약 조건을 추가할 노드 하나에서 다음 명령을 실행 합니다.

```bash
sudo pcs constraint order promote ag_cluster-master then start virtualip
```

>[!IMPORTANT]
>클러스터를 구성 하 고를 클러스터 리소스로 가용성 그룹을 추가한 후에 가용성 그룹 리소스를 장애 조치할 Transact SQL을 사용할 수 없습니다. Linux의 SQL Server 클러스터 리소스 연계 되지 않습니다와 긴밀 하 게 운영 체제에는 서버 장애 조치 클러스터 (WSFC (Windows) 같습니다. SQL Server 서비스를 클러스터의 현재 상태 인식 없습니다. 모든 오케스트레이션은 클러스터 관리 도구를 통해 수행 됩니다. RHEL 또는 Ubuntu에서 사용 하 여 `pcs`입니다. 

<!---[!INCLUDE [Pacemaker Concepts](..\includes\ss-linux-cluster-pacemaker-concepts.md)]--->

## <a name="next-steps"></a>다음 단계

[HA 가용성 그룹을 작동](sql-server-linux-availability-group-failover-ha.md)

