---
title: 장애 조치 (Failover) 클러스터링 및 AlwaysOn 가용성 그룹 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- clustering [SQL Server]
- Availability Groups [SQL Server], WSFC clusters
- Failover Cluster Instances [SQL Server], see failover clustering [SQL Server]
- quorum [SQL Server]
- failover clustering [SQL Server], AlwaysOn Availability Groups
- Availability Groups [SQL Server], Failover Cluster Instances
ms.assetid: 613bfbf1-9958-477b-a6be-c6d4f18785c3
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: e8d4858d55d9c37529e44cdf7759bf9fe6ce2630
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/26/2020
ms.locfileid: "62792006"
---
# <a name="failover-clustering-and-alwayson-availability-groups-sql-server"></a>장애 조치(Failover) 클러스터링 및 AlwaysOn 가용성 그룹(SQL Server)
  [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]에 도입된 고가용성 재해 복구 솔루션인 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]을 사용하려면 WSFC(Windows Server 장애 조치(Failover) 클러스터링)가 필요합니다. 또한 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 을 사용하는 데 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 장애 조치(Failover) 클러스터링이 필요하지 않더라도 FCI(장애 조치(Failover) 클러스터링 인스턴스)를 사용하여 가용성 그룹의 가용성 복제본을 호스팅할 수 있습니다. 각 클러스터링 기술의 역할과 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 환경을 디자인하는 데 고려해야 할 사항을 알고 있어야 합니다.  
  
> [!NOTE]  
>  [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 개념에 대한 자세한 내용은 [AlwaysOn 가용성 그룹 개요&#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)를 참조하세요.  
  

  
##  <a name="windows-server-failover-clustering-and-availability-groups"></a><a name="WSFC"></a>Windows Server 장애 조치 (Failover) 클러스터링 및 가용성 그룹  
 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 을 배포하려면 WSFC(Windows Server 장애 조치(Failover) 클러스터링) 클러스터가 필요합니다. [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]을 사용하도록 설정하려면 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인스턴스가 WSFC 노드에 있고 WSFC 클러스터 및 노드가 온라인 상태여야 합니다. 또한 지정된 가용성 그룹의 각 가용성 복제본은 동일한 WSFC 클러스터의 서로 다른 노드에 있어야 합니다. 유일한 예외는 다른 WSFC 클러스터로 마이그레이션되는 동안 가용성 그룹이 일시적으로 두 클러스터에 걸쳐 있는 경우입니다.  
  
 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 은 WSFC(Windows Server 장애 조치(failover) 클러스터링) 클러스터를 사용하여 지정된 가용성 그룹에 속해 있는 가용성 복제본의 현재 역할을 모니터링 및 관리하고 장애 조치(failover) 이벤트가 가용성 복제본에 미치는 영향을 확인합니다. WSFC 리소스 그룹은 생성하는 모든 가용성 그룹에 대해 만들어집니다. WSFC 클러스터는 이 리소스 그룹을 모니터링하여 주 복제본의 상태를 평가합니다.  
  
 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 에 대한 쿼럼은 지정된 클러스터 노드가 가용성 복제본을 호스팅하는지 여부에 관계없이 WSFC 클러스터의 모든 노드를 기반합니다. 데이터베이스 미러링과 달리 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]에는 모니터 역할이 없습니다.  
  
 WSFC 클러스터의 전반적인 상태는 클러스터에 있는 노드 쿼럼의 투표에 의해 결정됩니다. 계획되지 않은 재해나 영구적인 하드웨어 또는 통신 장애로 인해 WSFC 클러스터가 오프라인으로 전환된 경우 수동 관리 작업을 수행해야 합니다. Windows Server 또는 WSFC 클러스터 관리자는 강제 쿼럼을 수행하고 내결함성이 없는 구성에서 활성 클러스터 노드를 다시 온라인으로 전환해야 합니다.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 레지스트리 키는 WSFC 클러스터의 하위 키입니다. WSFC 클러스터를 삭제한 다음 다시 만들려는 경우 원본 WSFC 클러스터에서 가용성 복제본을 호스팅한 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 의 각 인스턴스에서 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 기능을 사용하지 않도록 설정한 후 다시 사용하도록 설정해야 합니다.  
  
 WSFC(Windows Server 장애 조치(failover) 클러스터링) 노드에서 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]를 실행하는 방법과 WSFC 쿼럼에 대한 자세한 내용은 [SQL Server의 WSFC&#40;Windows Server 장애 조치(failover) 클러스터링&#41;](../../../sql-server/failover-clusters/windows/windows-server-failover-clustering-wsfc-with-sql-server.md)를 참조하세요.  
  
### <a name="cross-cluster-migration-of-alwayson-availability-groups-for-os-upgrade"></a>OS 업그레이드를 위한 AlwaysOn 가용성 그룹의 클러스터 간 마이그레이션  
 [!INCLUDE[ssSQL11SP1](../../../includes/sssql11sp1-md.md)]부터 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 에서는 새 WSFC(Windows Server 장애 조치(Failover) 클러스터링) 클러스터에 배포하기 위해 가용성 그룹의 클러스터 간 마이그레이션을 지원합니다. 클러스터 간 마이그레이션은 작동 중단 시간을 최소화하면서 하나의 가용성 그룹이나 일련의 가용성 그룹을 새 대상 WSFC 클러스터로 이동합니다. 클러스터 간 마이그레이션 프로세스를 사용하면 [!INCLUDE[win8srv](../../../includes/win8srv-md.md)] 클러스터로 업그레이드할 때 SLA(서비스 수준 계약)를 유지 관리할 수 있습니다. [!INCLUDE[ssSQL11SP1](../../../includes/sssql11sp1-md.md)] 이상 버전은 대상 WSFC 클러스터에 설치하고 AlwaysOn에 대해 사용하도록 설정해야 합니다. 클러스터 간 마이그레이션의 성공 여부는 대상 WSFC 클러스터의 철저한 계획 및 준비에 의해 결정됩니다.  
  
 자세한 내용은 [OS 업그레이드를 위한 AlwaysOn 가용성 그룹의 클러스터 간 마이그레이션](https://msdn.microsoft.com/library/jj873730.aspx)을 참조하십시오.  
  
##  <a name="ssnoversion-failover-cluster-instances-fcis-and-availability-groups"></a><a name="SQLServerFC"></a> [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] FCI(장애 조치(failover) 클러스터 인스턴스) 및 가용성 그룹  
 WSFC 클러스터와 함께 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 장애 조치(Failover) 클러스터링을 구현하여 서버 인스턴스 수준에서 장애 조치(Failover)의 두 번째 계층을 설정할 수 있습니다. 가용성 복제본은 독립 실행형 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인스턴스 또는 FCI 인스턴스에서 호스팅할 수 있습니다. 지정된 가용성 그룹의 복제본은 하나의 FCI 파트너에서만 호스팅할 수 있습니다. 가용성 복제본이 FCI에서 실행 중인 경우 가용성 그룹에 대한 가능한 소유자 목록에는 활성 FCI 노드만 포함됩니다.  
  
 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 은 어떤 형태의 공유 스토리지에도 종속되지 않습니다. 하지만 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] FCI(장애 조치(Failover) 클러스터 인스턴스)를 사용하여 하나 이상의 가용성 복제본을 호스팅하는 경우 각 FCI에는 표준 SQL Server 장애 조치(Failover) 클러스터 인스턴스 설치와 같이 공유 스토리지가 있어야 합니다.  
  
 필수 조건에 대한 자세한 내용은 [AlwaysOn 가용성 그룹에 대한 필수 조건, 제한 사항 및 권장 사항&#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md)의 "가용성 복제본을 호스트하기 위해 SQL Server FCI(장애 조치(failover) 클러스터 인스턴스) 사용에 대한 필수 조건 및 제한 사항" 섹션을 참조하세요.  
  
### <a name="comparison-of-failover-cluster-instances-and-availability-groups"></a>장애 조치(Failover) 클러스터 인스턴스와 가용성 그룹 비교  
 FCI의 노드 수에 관계 없이 전체 FCI는 가용성 그룹 내의 단일 복제본을 호스팅합니다. 다음 표에서는 FCI의 노드와 가용성 그룹 내 복제본 간의 개념적인 차이에 대해 설명합니다.  
  
||FCI 내의 노드|가용성 그룹 내의 복제본|  
|-|-------------------------|-------------------------------------------|  
|**WSFC 클러스터 사용**|예|예|  
|**보호 수준**|인스턴스|데이터베이스|  
|**저장소 유형**|Shared|공유되지 않음<br /><br /> 가용성 그룹의 복제본은 스토리지를 공유하지 않는 반면 FCI가 호스트하는 복제본은 해당 FCI가 요구하는 대로 공유 스토리지 솔루션을 사용합니다. 스토리지 솔루션은 FCI 내 노드에 의해서만 공유되고 가용성 그룹의 복제본 사이에서는 공유되지 않습니다.|  
|**스토리지 솔루션**|직접 연결됨, SAN, 탑재 지점, SMB|노드 유형에 따라 다름|  
|**읽기 가능한 보조 복제본**|아니요*|예|  
|**적용할 수 있는 장애 조치(Failover) 정책 설정**|WSFC 쿼럼<br /><br /> FCI별<br /><br /> 가용성 그룹 설정**|WSFC 쿼럼<br /><br /> 가용성 그룹 설정|  
|**장애 조치(Failover)가 실행된 리소스**|서버, 인스턴스 및 데이터베이스|데이터베이스에만 해당|  
  
 *가용성 그룹의 동기적 보조 복제본은 항상 해당 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인스턴스에서 실행되는 반면 FCI의 보조 노드는 실제로 해당 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인스턴스를 시작하지 않았으며 따라서 읽을 수 없습니다. FCI에서 보조 노드는 리소스 그룹 소유권이 FCI 장애 조치(Failover) 중 보조 노드로 전달된 경우에만 해당 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인스턴스를 시작합니다. 하지만 FCI가 호스팅하는 데이터베이스가 가용성 그룹에 속해 있을 때 활성 FCI 노드에서 로컬 가용성 복제본이 읽기 가능한 보조 복제본으로 실행되는 경우 이 데이터베이스는 읽을 수 있습니다.  
  
 **가용성 그룹에 대한 장애 조치(Failover) 정책 설정은 독립 실행형 인스턴스에서 호스팅되는지 FCI 인스턴스에서 호스팅되는지에 관계없이 모든 복제본에 적용됩니다.  
  
> [!NOTE]  
>  https://go.microsoft.com/fwlink/?linkid=232473)장애 조치 (Failover) 클러스터링 내의 **노드 수** 및 다양 한 버전의 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] **AlwaysOn 가용성 그룹** 에 대 한 자세한 내용은 [SQL Server 2012 버전에서 지 원하는 기능](https://go.microsoft.com/fwlink/?linkid=232473) 을 참조 하세요.  
  
### <a name="considerations-for-hosting-an-availability-replica-on-an-fci"></a>FCI에서 가용성 복제본을 호스팅하는 경우의 고려 사항  
  
> [!IMPORTANT]  
>  SQL Server FCI(장애 조치(Failover) 클러스터 인스턴스)에서 가용성 복제본을 호스팅하려는 경우 Windows Server 2008 호스트 노드가 FCI에 대한 AlwaysOn 필수 구성 요소 및 제한 사항을 충족하는지 확인해야 합니다. 자세한 내용은 [AlwaysOn 가용성 그룹에 대한 필수 조건, 제한 사항 및 권장 사항&#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md)을 참조하세요.  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] FCI(장애 조치(failover) 클러스터 인스턴스)는 가용성 그룹에 따라 AlwaysOn 자동 장애 조치(failover)를 지원하지 않으므로 FCI에서 호스트하는 모든 가용성 복제본은 수동 장애 조치(failover)에 대해서만 구성될 수 있습니다.  
  
 일부 노드에서는 사용할 수 없는 공유 디스크를 포함하도록 WSFC(Windows Server 장애 조치(Failover) 클러스터링) 클러스터를 구성해야 할 수 있습니다. 예를 들어 세 개의 노드와 두 데이터 센터에 걸쳐 있는 WSFC 클러스터가 있다고 가정합니다. 노드 중 두 개는 주 데이터 센터에서 SQL Server FCI(장애 조치(Failover) 클러스터링 인스턴스)를 호스팅하며 동일한 공유 디스크에 대한 액세스 권한이 있습니다. 세 번째 노드는 다른 데이터 센터에서 독립 실행형 SQL Server 인스턴스를 호스팅하며 주 데이터 센터의 공유 디스크에 대한 액세스 권한이 없습니다. 이 WSFC 클러스터 구성은 FCI가 주 복제본을 호스팅하고 독립 실행형 인스턴스가 보조 복제본을 호스팅하는 경우 가용성 그룹 배포를 지원합니다.  
  
 지정된 가용성 그룹에 대한 가용성 복제본을 호스팅하도록 FCI를 선택하는 경우 FCI 장애 조치(Failover)로 인해 단일 WSFC 노드가 동일한 가용성 그룹에 대해 두 개의 가용성 복제본을 호스팅하려고 시도해서는 안 됩니다.  
  
 다음 예에서는 이 구성을 사용할 경우 발생할 수 있는 문제를 보여 줍니다.  
  
 Marcel은 `NODE01` 및 `NODE02`라는 두 개의 노드가 있는 WSFC 클러스터를 구성합니다. Marcel은 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 및 `fciInstance1`모두에 `NODE01` 장애 조치(Failover) 클러스터 인스턴스 `NODE02` 을 설치합니다. 여기에서 `NODE01` 은 `fciInstance1`의 현재 소유자입니다.  
 Marcel은 `NODE02`에 독립 실행형 인스턴스인 또 다른 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]인스턴스, `Instance3`을 설치합니다.  
 Marcel은 `NODE01`에서 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]을 사용하도록 fciInstance1을 설정합니다. `NODE02`에서 Marcel은 `Instance3` 을 사용하도록 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]을 설정합니다. 그런 다음 Marcel은 `fciInstance1` 이 주 복제본을 호스팅하고 `Instance3` 이 보조 복제본을 호스팅하는 가용성 그룹을 설정합니다.  
 어느 시점에 `fciInstance1` 에서 `NODE01`을 사용할 수 없게 되면 WSFC 클러스터를 통해 `fciInstance1` 에서 `NODE02`로 장애 조치(Failover)가 수행됩니다. 장애 조치(Failover) 후 `fciInstance1` 은 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]에서 주 역할로 실행되는 `NODE02`사용 인스턴스가 되지만 `Instance3` 은 이제 `fciInstance1`과 동일한 WSFC 노드에 있습니다. 이 경우 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 제약 조건을 위반하게 됩니다.  
 이 시나리오에서 발생한 문제를 해결하려면 독립 실행형 인스턴스인 `Instance3`이 `NODE01` 및 `NODE02`와 동일한 WSFC 클러스터의 다른 노드에 있어야 합니다.  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 장애 조치(failover) 클러스터링에 대한 자세한 내용은 [AlwaysOn 장애 조치(Failover) 클러스터 인스턴스&#40;SQL Server&#41;](../../../sql-server/failover-clusters/windows/always-on-failover-cluster-instances-sql-server.md)를 참조하세요.  
  
##  <a name="restrictions-on-using-the-wsfc-failover-cluster-manager-with-availability-groups"></a><a name="FCMrestrictions"></a>가용성 그룹에 WSFC 장애 조치(Failover) 클러스터 관리자 사용에 대 한 제한 사항  
 다음의 예처럼 장애 조치(Failover) 클러스터 관리자를 사용하여 가용성 그룹을 조작하지 마세요.  
  
-   가용성 그룹에 대한 클러스터형 서비스(리소스 그룹)에 리소스를 추가하거나 제거하지 마세요.  
  
-   가능한 소유자 및 기본 설정 소유자와 같은 가용성 그룹 속성을 변경하지 마세요. 이러한 속성은 가용성 그룹에 의해 자동으로 설정됩니다.  
  
-   장애 조치(Failover) 클러스터 관리자를 사용하여 가용성 그룹을 다른 노드로 옮기거나 가용성 그룹을 장애 조치(Failover)을 수행하지 마세요. 장애 조치(Failover) 클러스터 관리자에서는 가용성 복제본의 동기화 상태를 인식하지 못하기 때문에 이로 인해 작동 중지 시간이 길어질 수 있습니다. [!INCLUDE[tsql](../../../includes/tsql-md.md)] 또는 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]를 사용해야 합니다.  
  
##  <a name="related-content"></a><a name="RelatedContent"></a> 관련 내용  
  
-   **블로그:**  
  
     [제한된 보안을 사용하여 SQL Server의 Windows 장애 조치(Failover) 클러스터링 구성(가용성 그룹 또는 FCI)](https://blogs.msdn.com/b/sqlalwayson/archive/2012/06/05/configure-windows-failover-clustering-for-sql-server-availability-group-or-fci-with-limited-security.aspx)  
  
     [SQL Server AlwaysOn 팀 블로그: 공식 SQL Server AlwaysOn 팀 블로그](https://blogs.msdn.com/b/sqlalwayson/)  
  
     [CSS SQL Server 엔지니어 블로그](https://blogs.msdn.com/b/psssql/)  
  
-   **백서:**  
  
     [AlwaysOn 아키텍처 가이드: 장애 조치(Failover) 클러스터 인스턴스 및 가용성 그룹을 사용하여 고가용성 및 재해 복구 솔루션 구축](https://msdn.microsoft.com/library/jj215886.aspx)  
  
     [고가용성 및 재해 복구를 위한 Microsoft SQL Server AlwaysOn 솔루션 가이드](https://go.microsoft.com/fwlink/?LinkId=227600)  
  
     [SQL Server 2012에 대한 Microsoft 백서](https://msdn.microsoft.com/library/hh403491.aspx)  
  
     [SQL Server 고객 자문 팀 백서](http://sqlcat.com/)  
  
## <a name="see-also"></a>참고 항목  
 [AlwaysOn 가용성 그룹 &#40;&#41;SQL Server 개요](overview-of-always-on-availability-groups-sql-server.md) AlwaysOn 가용성 그룹 &#40;SQL Server [사용 및 사용 안 함](enable-and-disable-always-on-availability-groups-sql-server.md)&#41;&#40;&#41;[가용성 그룹 모니터링](monitor-availability-groups-transact-sql.md)  
 [AlwaysOn 장애 조치 (Failover) 클러스터 인스턴스 &#40;SQL Server&#41;](../../../sql-server/failover-clusters/windows/always-on-failover-cluster-instances-sql-server.md) 
  
  
