---
title: SQL Server 2019 빅 데이터 클러스터에 대 한 릴리스 | Microsoft Docs
description: 이 문서에서는 최신 업데이트 및 SQL Server 2019 (미리 보기) 빅 데이터 클러스터에 대 한 알려진된 문제를 설명 합니다.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 10/04/2018
ms.topic: conceptual
ms.prod: sql
ms.openlocfilehash: 13d5cfa95b9a37ecf26658ee255f93c8099faa8f
ms.sourcegitcommit: 0d6e4cafbb5d746e7d00fdacf8f3ce16f3023306
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/11/2018
ms.locfileid: "49085556"
---
# <a name="release-notes-for-sql-server-2019-big-data-clusters"></a>SQL Server 2019 빅 데이터 클러스터에 대 한 릴리스 정보

이 문서에서는 최신 릴리스의 SQL Server 빅 데이터 클러스터에 대 한 최신 업데이트 및 알려진된 문제를 제공 합니다.

[!INCLUDE [Limited public preview note](../includes/big-data-cluster-preview-note.md)]

## <a name="ctp-20-october-2018"></a>CTP 2.0 (2018 년 10 월)

다음 섹션에서는 새로운 기능 및 SQL Server 2019 CTP 2.0에서 빅 데이터 클러스터에 대해 알려진된 문제를 설명합니다.

### <a name="whats-in-the-ctp-20-release"></a>CTP 2.0 릴리스에서 란?

- Mssqlctl 관리 도구를 사용 하 여 간단한 배포 환경
- Azure Data Studio에서 네이티브 전자 필기장 환경
- 쿼리 저장소 SQL Server 인스턴스를 통해 HDFS 파일
- 마스터 SQL Server, Oracle, MongoDB, HDFS를 통해 데이터 가상화
- SQL Server 및 Azure Data Studio에서 Oracle 데이터 가상화 마법사
- 마스터 ML 서비스
- 모니터링 및 문제 해결에 사용할 수 있는 클러스터 관리 포털
- Azure Data Studio에서 Spark 작업 제출 
- 클러스터 관리 포털에서 Spark UI
- 저장소 클래스에 탑재 된 볼륨
- 마스터에서 데이터 풀에 대 한 쿼리
- SSMS에서 분산된 쿼리 계획을 보여 줍니다.
- Mssqlctl 관리 도구에 대 한 pip 패키지
- 컨트롤러 서비스를 통해 기본 제공 배포 엔진

### <a name="known-issues"></a>알려진 문제

다음 섹션에서는 CTP 2.0에서 SQL Server 빅 데이터 클러스터에 대해 알려진된 문제를 제공합니다.

#### <a name="deployment"></a>배포

- Azure Kubernetes Service (AKS)를 사용 하는 경우 권장 되는 Kubernetes 버전이 1.10. *, 디스크 크기 조정 지원 하지 않는 합니다. 그에 따라 저장소 크기 해야 배포 시. 저장소 크기를 조정 하는 방법에 대 한 자세한 내용은 참조는 [데이터 지 속성](concept-data-persistence.md) 문서. Vm에 배포 된 kubernetes의 경우 권장 되는 버전 1.11입니다.

- AKS를 배포한 후 배포에서 다음 두 경고 이벤트를 볼 수 있습니다. 이러한 이벤트는 알려진 문제, 있지만 AKS에서 빅 데이터 클러스터를 성공적으로 배포를 방지 하지 않습니다.

   `Warning  FailedMount: Unable to mount volumes for pod "mssql-storage-pool-default-1_sqlarisaksclus(c83eae70-c81b-11e8-930f-f6b6baeb7348)": timeout expired waiting for volumes to attach or mount for pod "sqlarisaksclus"/"mssql-storage-pool-default-1". list of unmounted volumes=[storage-pool-storage hdfs storage-pool-mlservices-storage hadoop-logs]. list of unattached volumes=[storage-pool-storage hdfs storage-pool-mlservices-storage hadoop-logs storage-pool-java-storage secrets default-token-q9mlx]`

   `Warning  Unhealthy: Readiness probe failed: cat: /tmp/provisioner.done: No such file or directory`

- 빅 데이터 클러스터 배포에 실패 하면 연결된 된 네임 스페이스 제거 되지 않습니다. 이 클러스터에서 분리 된 네임 스페이스를 발생할 수 있습니다. 동일한 이름 사용 하 여 클러스터를 배포 하기 전에 네임 스페이스를 수동으로 삭제 됩니다.

#### <a name="external-tables"></a>외부 테이블

- 지원 되지 않는 열 형식에는 테이블에 대 한 데이터 풀 외부 테이블을 만들 가능성이 있습니다. 외부 테이블을 쿼리 하는 경우 메시지가 다음과 비슷합니다.

   `Msg 7320, Level 16, State 110, Line 44 Cannot execute the query "Remote Query" against OLE DB provider "SQLNCLI11" for linked server "(null)". 105079; Columns with large object types are not supported for external generic tables.`

- 저장소 풀 외부 테이블을 쿼리 하는 경우 오류가 발생할 수 있습니다는 동시에 기본 파일은 HDFS에 복사 되는 경우.

   `Msg 7320, Level 16, State 110, Line 157 Cannot execute the query "Remote Query" against OLE DB provider "SQLNCLI11" for linked server "(null)". 110806;A distributed query failed: One or more errors occurred.`

#### <a name="spark-and-notebooks"></a>Spark 및 notebook

- POD IP 주소는 Pod 다시 시작으로 Kubernetes 환경에서 변경 될 수 있습니다. 마스터 pod를 다시 시작 되는 시나리오에서 Spark 세션을 사용 하 여 못할 `NoRoteToHostException`합니다. 이 새 IP를 사용 하 여 새로 고쳐지는 가져오기 하지 JVM 캐시 주소입니다.

- Windows에 이미 설치 된 Jupyter 및 별도 Python을 있다면 Spark 노트북 실패할 수 있습니다. 이 문제를 해결 하려면 Jupyter를 최신 버전으로 업그레이드 합니다.

- 노트북을 클릭할 경우에 **텍스트 추가** 명령, 텍스트 셀이 편집 모드 보다는 미리 보기 모드에서 추가 됩니다. 편집 모드에 있고 셀을 편집 하 여 전환한 다음 미리 보기 아이콘을 클릭할 수 있습니다.

#### <a name="hdfs"></a>HDFS

- 미리 HDFS의 파일을 마우스 오른쪽 단추로 클릭 하는 경우 다음 오류가 표시 될 수 있습니다.

   `Error previewing file: File exceeds max size of 30MB`

   현재는 Azure Data Studio에서 30 MB 보다 큰 파일을 미리 볼 수 없습니다.

- 구성 변경 내용은 hdfs-site.xml 변경 내용을 포함 하는 HDFS에 지원 되지 않습니다.

#### <a name="security"></a>보안

- SA_PASSWORD는 (예: 코드 덤프 파일)의 일부 환경의 및 검색할 수입니다. 배포 후 마스터 인스턴스에서 SA_PASSWORD 다시 설정 해야 합니다. 이 변경은 버그 아니라 보안 단계입니다. Linux 컨테이너에서 SA_PASSWORD 변경 하는 방법에 대 한 자세한 내용은 참조 하세요. [SA 암호 변경](../linux/quickstart-install-connect-docker.md#sapassword)합니다.

- AKS 로그는 빅 데이터 클러스터 배포에 대 한 SA 암호를 포함할 수 있습니다.

## <a name="next-steps"></a>다음 단계

SQL Server 빅 데이터 클러스터에 대 한 자세한 내용은 참조 하세요. [SQL Server 2019 빅 데이터 클러스터 이란?](big-data-cluster-overview.md)합니다.