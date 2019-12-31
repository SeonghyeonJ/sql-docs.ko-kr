---
title: AlwaysOn 가용성 그룹 시작 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], deploying
- Availability Groups [SQL Server], about
ms.assetid: 33f2f2d0-79e0-4107-9902-d67019b826aa
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 2e809d84071089ce57c66bc8f9a388203923fe66
ms.sourcegitcommit: 792c7548e9a07b5cd166e0007d06f64241a161f8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/19/2019
ms.locfileid: "75228761"
---
# <a name="getting-started-with-alwayson-availability-groups-sql-server"></a>AlwaysOn 가용성 그룹 시작(SQL Server)
  이 항목에서는 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 을 지원하도록 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 인스턴스를 구성하고, 가용성 그룹을 만들고 관리하고 모니터링하기 위한 단계를 소개합니다.  
  
  
##  <a name="BeforeYouBegin"></a>시작 하기 전에  
  
###  <a name="RecommendedReading"></a>권장 읽기  
 가용성 그룹을 처음 만드는 경우 다음 항목을 먼저 읽는 것이 좋습니다.  
  
-   [AlwaysOn 가용성 그룹 &#40;SQL Server 개요&#41;](overview-of-always-on-availability-groups-sql-server.md)  
  
-   [AlwaysOn 가용성 그룹 &#40;SQL Server에 대 한 필수 조건, 제한 사항 및 권장 사항&#41;](prereqs-restrictions-recommendations-always-on-availability.md)  
  
##  <a name="ConfigSI"></a>AlwaysOn 가용성 그룹을 지원 하도록 SQL Server 인스턴스 구성  
  
||단계|링크|  
|------|----------|-----------|  
|![확인란](../../media/checkboxemptycenterxtraspacetopandright.gif "확인란")|**사용 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)].** 가용성 그룹에 참여할 모든 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 인스턴스에서 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 기능을 사용하도록 설정해야 합니다.<br /><br /> **필수 조건:**  호스트 컴퓨터는 WSFC (Windows Server 장애 조치 (Failover) 클러스터링) 노드여야 합니다.<br /><br /> 다른 필수 조건에 대한 자세한 내용은 [AlwaysOn 가용성 그룹에 대한 필수 조건, 제한 사항 및 권장 사항&#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md)에서 "SQL Server 인스턴스 필수 조건 및 제한 사항"을 참조하세요.|[AlwaysOn 가용성 그룹 사용 및 사용 안 함](enable-and-disable-always-on-availability-groups-sql-server.md)|  
|![확인란](../../media/checkboxemptycenterxtraspacetopandright.gif "확인란")|**데이터베이스 미러링 끝점을 만듭니다 (없는 경우).** 각 서버 인스턴스에 [데이터베이스 미러링 엔드포인트](../../database-mirroring/the-database-mirroring-endpoint-sql-server.md)가 있는지 확인합니다. 서버 인스턴스는 이 엔드포인트를 사용하여 다른 서버 인스턴스에서의 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 연결을 수신합니다.|데이터베이스 미러링 엔드포인트가 있는지 여부를 확인하려면 [sys.database_mirroring_endpoints](/sql/relational-databases/system-catalog-views/sys-database-mirroring-endpoints-transact-sql)<br /><br /> **Windows 인증의 경우:** 다음을 사용 하 여 데이터베이스 미러링 끝점을 만듭니다.<br /><br /> [새 가용성 그룹 마법사](use-the-availability-group-wizard-sql-server-management-studio.md)<br /><br /> [Transact-sql](../../database-mirroring/create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md)<br /><br /> [SQL Server PowerShell](database-mirroring-always-on-availability-groups-powershell.md)<br /><br /> **인증서 인증의 경우:** 데이터베이스 미러링 끝점을 만들려면 다음을 사용 합니다. <br />                    [Transact-sql](../../database-mirroring/use-certificates-for-a-database-mirroring-endpoint-transact-sql.md)|  
  
##  <a name="ConfigAG"></a>새 가용성 그룹 만들기 및 구성  
  
||단계|링크|  
|------|----------|-----------|  
|![확인란](../../media/checkboxemptycenterxtraspacetopandright.gif "확인란")|**가용성 그룹을 만듭니다.** 가용성 그룹에 추가할 데이터베이스를 호스팅하는 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인스턴스에 가용성 그룹을 만듭니다.<br /><br /> 최소한, 가용성 그룹을 만들 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인스턴스에 초기 주 복제본을 만듭니다. 1~4개의 보조 복제본을 지정할 수 있습니다. 가용성 그룹 및 복제본 속성에 대한 자세한 내용은 [CREATE AVAILABILITY GROUP&#40;Transact-SQL&#41;](/sql/t-sql/statements/create-availability-group-transact-sql)을 참조하세요.<br /><br /> 또한 [가용성 그룹 수신기](../../listeners-client-connectivity-application-failover.md)를 만드는 것이 좋습니다.<br /><br /> **필수 조건:**  지정 된 가용성 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 그룹에 대 한 가용성 복제본을 호스팅하는 인스턴스는 단일 WSFC 클러스터의 개별 노드에 있어야 합니다. 유일한 예외는 다른 WSFC 클러스터로 마이그레이션되는 동안 가용성 그룹이 일시적으로 두 클러스터에 걸쳐 있는 경우입니다.<br /><br /> 다른 필수 조건에 대한 자세한 내용은 [AlwaysOn 가용성 그룹에 대한 필수 조건, 제한 사항 및 권장 사항&#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md)에서 "가용성 그룹 필수 조건 및 제한 사항", "가용성 데이터베이스 필수 조건 및 제한 사항" 및 "SQL Server 인스턴스 필수 조건 및 제한 사항"을 참조하세요.|가용성 그룹을 만들려면 다음 도구 중 하나를 사용합니다.<br /><br /> [새 가용성 그룹 마법사](use-the-availability-group-wizard-sql-server-management-studio.md)<br /><br /> [Transact-sql](create-an-availability-group-transact-sql.md)<br /><br /> [SQL Server PowerShell](create-an-availability-group-transact-sql.md)|  
|![확인란](../../media/checkboxemptycenterxtraspacetopandright.gif "확인란")|**보조 복제본을 가용성 그룹에 조인 합니다.** 보조 복제본을 호스팅하는 각 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 인스턴스에 연결한 다음 로컬 보조 복제본을 가용성 그룹에 조인합니다.|[가용성 그룹에 보조 복제본 조인](join-a-secondary-replica-to-an-availability-group-sql-server.md)<br /><br /> 팁: 새 가용성 그룹 마법사를 사용하는 경우 이 단계가 자동으로 수행됩니다.|  
|![확인란](../../media/checkboxemptycenterxtraspacetopandright.gif "확인란")|**보조 데이터베이스를 준비 합니다.** 보조 복제본을 호스팅하는 각 서버 인스턴스에서 RESTORE WITH NORECOVERY를 사용하여 주 데이터베이스의 백업을 복원합니다.|[보조 데이터베이스 수동 준비](manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md)<br /><br /> 팁: 새 가용성 그룹 마법사는 보조 데이터베이스를 자동으로 준비할 수 있습니다. 자세한 내용은 [초기 데이터 동기화 선택 페이지&#40;AlwaysOn 가용성 그룹 마법사&#41;](select-initial-data-synchronization-page-always-on-availability-group-wizards.md)에서 "전체 초기 데이터 동기화를 사용하기 위한 필수 조건"을 참조하세요.|  
|![확인란](../../media/checkboxemptycenterxtraspacetopandright.gif "확인란")|**가용성 그룹에 보조 데이터베이스를 조인 합니다.** 보조 복제본을 호스팅하는 모든 서버 인스턴스에서 각 로컬 보조 데이터베이스를 가용성 그룹에 조인합니다. 가용성 그룹을 조인하면 지정된 보조 데이터베이스가 해당 주 데이터베이스와의 데이터 동기화를 시작합니다.|[가용성 그룹에 보조 데이터베이스 조인](join-a-secondary-database-to-an-availability-group-sql-server.md)<br /><br /> 팁: 모든 보조 복제본에 모든 보조 데이터베이스가 있는 경우 새 가용성 그룹 마법사가 이 단계를 수행할 수 있습니다.|  
||**가용성 그룹 수신기를 만듭니다.**  이 단계는 가용성 그룹을 만드는 중 가용성 그룹 수신기를 아직 만들지 않은 경우에 필요합니다.|[SQL Server&#41;&#40;가용성 그룹 수신기 만들기 또는 구성](create-or-configure-an-availability-group-listener-sql-server.md)|  
|![확인란](../../media/checkboxemptycenterxtraspacetopandright.gif "확인란")|**수신기의 DNS 호스트 이름을 응용 프로그램 개발자에 게 제공 합니다.**  개발자가 연결 요청을 가용성 그룹 수신기에 연결하기 위해서는 연결 문자열에 이 DNS 이름을 지정해야 합니다. 자세한 내용은 [가용성 그룹 수신기, 클라이언트 연결 및 애플리케이션 장애 조치(failover)&#40;SQL Server&#41;](../../listeners-client-connectivity-application-failover.md)개념을 소개합니다.|“후속 작업: 가용성 그룹 수신기를 만든 후”( [가용성 그룹 수신기 만들기 또는 구성&#40;SQL Server&#41;](create-or-configure-an-availability-group-listener-sql-server.md)|  
|![확인란](../../media/checkboxemptycenterxtraspacetopandright.gif "확인란")|**백업 작업 위치를 구성 합니다.**  보조 데이터베이스에서 백업을 수행하려면 자동화된 백업 기본 설정을 고려하는 백업 작업 스크립트를 만들어야 합니다. 가용성 그룹의 가용성 복제본을 호스팅하는 각 서버 인스턴스에서 가용성 그룹의 각 데이터베이스에 대해 스크립트를 만듭니다.|"후속 작업: 보조 복제본에 백업을 구성한 후"([가용성 복제본에 백업 구성&#40;SQL Server&#41;](configure-backup-on-availability-replicas-sql-server.md))|  
  
##  <a name="ManageAGsEtc"></a>가용성 그룹, 복제본 및 데이터베이스 관리  
  
> [!NOTE]  
>  가용성 그룹 및 복제본 속성에 대한 자세한 내용은 [CREATE AVAILABILITY GROUP&#40;Transact-SQL&#41;](/sql/t-sql/statements/create-availability-group-transact-sql)을 참조하세요.  
  
 기존 가용성 그룹 관리에는 다음 태스크 중 하나 이상이 포함됩니다.  
  
|작업|링크|  
|----------|----------|  
|가용성 그룹의 [유연한 장애 조치(failover) 정책](flexible-automatic-failover-policy-availability-group.md) 을 수정하여 자동 장애 조치를 수행해야 하는 상태를 제어합니다. 이 정책은 자동 장애 조치가 가능한 경우에만 유효합니다.|[가용성 그룹의 유연한 장애 조치 (failover) 정책 구성](configure-flexible-automatic-failover-policy.md)|  
|일반적으로 *강제 장애 조치(failover)* 라고 하는 강제 수동 장애 조치(failover)(데이터가 손실될 수 있음)나 계획된 수동 장애 조치(failover)를 수행합니다. 자세한 내용은 [장애 조치(Failover) 및 장애 조치(Failover) 모드&#40;AlwaysOn 가용성 그룹&#41;](failover-and-failover-modes-always-on-availability-groups.md)를 참조하세요.|[계획 된 수동 장애 조치 (failover) 수행](perform-a-planned-manual-failover-of-an-availability-group-sql-server.md)<br /><br /> [강제 수동 장애 조치 (failover) 수행](perform-a-forced-manual-failover-of-an-availability-group-sql-server.md)|  
|미리 정의된 일련의 정책을 사용하여 가용성 그룹과 해당 복제본 및 데이터베이스의 상태를 확인합니다.|[정책 기반 관리를 사용 하 여 가용성 그룹의 상태 보기](use-always-on-policies-to-view-the-health-of-an-availability-group-sql-server.md)<br /><br /> [AlwaysOn 그룹 대시보드 사용](use-the-always-on-dashboard-sql-server-management-studio.md)|  
|보조 복제본을 추가하거나 제거합니다.|[보조 복제본 추가](add-a-secondary-replica-to-an-availability-group-sql-server.md)<br /><br /> [보조 복제본 제거](remove-a-secondary-replica-from-an-availability-group-sql-server.md)|  
|가용성 데이터베이스를 일시 중지하거나 다시 시작합니다. 보조 데이터베이스를 일시 중지하면 다시 시작할 때까지 현재 시점의 상태로 유지됩니다.|[데이터베이스 일시 중단](suspend-an-availability-database-sql-server.md)<br /><br /> [데이터베이스 다시 시작](resume-an-availability-database-sql-server.md)|  
|데이터베이스를 추가하거나 제거합니다.|[데이터베이스 추가](availability-group-add-a-database.md)<br /><br /> [보조 데이터베이스 제거](remove-a-secondary-database-from-an-availability-group-sql-server.md)<br /><br /> [주 데이터베이스 제거](remove-a-primary-database-from-an-availability-group-sql-server.md)|  
|가용성 그룹 수신기를 다시 구성하거나 만듭니다.|[가용성 그룹 수신기 만들기 또는 구성](create-or-configure-an-availability-group-listener-sql-server.md)|  
|가용성 그룹을 삭제합니다.|[가용성 그룹 삭제](remove-an-availability-group-sql-server.md)|  
|파일 추가 작업의 문제를 해결합니다. 이 단계는 주 데이터베이스와 보조 데이터베이스의 파일 경로가 다른 경우에 필요합니다.|[실패 한 파일 추가 작업 문제 해결](troubleshoot-a-failed-add-file-operation-always-on-availability-groups.md)|  
|가용성 복제본 속성을 변경합니다.|[가용성 모드 변경](change-the-availability-mode-of-an-availability-replica-sql-server.md)<br /><br /> [장애 조치 (Failover) 모드 변경](change-the-failover-mode-of-an-availability-replica-sql-server.md)<br /><br /> [백업 우선 순위 (및 자동화 된 백업 기본 설정) 구성](configure-backup-on-availability-replicas-sql-server.md)<br /><br /> [읽기 전용 액세스 구성](configure-read-only-access-on-an-availability-replica-sql-server.md)<br /><br /> [읽기 전용 라우팅 구성](configure-read-only-routing-for-an-availability-group-sql-server.md)<br /><br /> [세션 제한 시간 변경](change-the-session-timeout-period-for-an-availability-replica-sql-server.md)|  
  
##  <a name="MonitorAGsEtc"></a>가용성 그룹 모니터링  
 AlwaysOn 가용성 그룹의 속성 및 상태를 모니터링하려면 다음 도구를 사용할 수 있습니다.  
  
|도구|간략한 설명|링크|  
|----------|-----------------------|-----------|  
|SQL Server용 System Center 모니터링 팩|SQL Server용 모니터링 팩(SQLMP)은 가용성 그룹, 가용성 복제본 및 IT 관리자의 가용성 데이터베이스를 모니터링하기 위한 권장 솔루션입니다. 특히 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 과 관련된 모니터링 기능은 다음과 같습니다.<br /><br /> 수백 개 컴퓨터 간의 가용성 그룹, 가용성 복제본 및 가용성 데이터베이스의 자동 검색 기능 이 기능을 사용하면 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 인벤토리를 쉽게 추적할 수 있습니다.<br /><br /> 완전한 기능의 System Center Operations Manager(SCOM) 경고 및 티켓 부여. 이러한 기능은 보다 빠른 문제 해결을 위한 세부 지식을 제공합니다.<br /><br /> PBM(정책 기반 관리)을 사용한 AlwaysOn 상태 모니터링에 대한 사용자 정의 확장.<br /><br /> 상태는 가용성 데이터베이스에서 가용성 복제본으로 롤업됩니다.<br /><br /> System Center 운영 관리자 콘솔로부터 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 을 관리하는 사용자 정의 작업.|모니터링 팩(SQLServerMP.msi) 및 *System Center Operations Manager용 SQL Server 관리 팩 가이드* (SQLServerMPGuide.doc)를 다운로드하려면 다음을 참조하세요.<br /><br /> [SQL Server 용 System Center 모니터링 팩](https://www.microsoft.com/download/details.aspx?displaylang=en&id=10631)|  
|[!INCLUDE[tsql](../../../includes/tsql-md.md)]|
  [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 카탈로그 및 동적 관리 뷰는 가용성 그룹과 해당 복제본, 데이터베이스, 수신기 및 WSFC 클러스터 환경에 대한 풍부한 정보를 제공합니다.|[Transact-sql&#41;&#40;가용성 그룹 모니터링](monitor-availability-groups-transact-sql.md)|  
|[!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]|
  **개체 탐색기 정보** 창에는 연결된 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 의 인스턴스에 호스팅된 가용성 그룹에 대한 기본 정보가 표시됩니다.<br /><br /> 팁: 이 창을 사용하여 여러 가용성 그룹, 복제본 또는 데이터베이스를 선택하고 선택한 개체에 대한 일상적인 관리 태스크를 수행합니다(예: 가용성 그룹에서 여러 가용성 복제본 또는 데이터베이스 제거).|[개체 탐색기 세부 정보를 사용 하 여 가용성 그룹 모니터링](use-object-explorer-details-to-monitor-availability-groups.md)|  
|[!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]|**속성** 대화 상자를 사용 하 여 가용성 그룹, 복제본 또는 수신기의 속성을 볼 수 있으며, 경우에 따라 값을 변경할 수 있습니다.|[가용성 그룹 속성](view-availability-group-properties-sql-server.md)<br /><br /> [가용성 복제본 속성](view-availability-replica-properties-sql-server.md)<br /><br /> [가용성 그룹 수신기 속성](view-availability-group-listener-properties-sql-server.md)|  
|시스템 모니터|
  **SQLServer:Availability Replica** 성능 개체에는 가용성 복제본에 대한 정보를 보고하는 성능 카운터가 포함됩니다.|[SQL Server, 가용성 복제본](../../../relational-databases/performance-monitor/sql-server-availability-replica.md)|  
|시스템 모니터|
  **SQLServer:Database Replica** 성능 개체에는 지정된 보조 복제본의 보조 데이터베이스에 대한 정보를 보고하는 성능 카운터가 포함됩니다.<br /><br /> SQL Server의 **SQLServer:Databases** 개체에는 특히 트랜잭션 로그 작업을 모니터링하는 성능 카운터가 포함됩니다. 가용성 데이터베이스에서 트랜잭션 로그 작업 모니터링과 관련된 카운터는 **Log Flush Write Time (ms)**, **Log Flushes/sec**, **Log Pool Cache Misses/sec**, **Log Pool Disk Reads/sec**및 **Log Pool Requests/sec**입니다.|[SQL Server, 데이터베이스 복제본](../../../relational-databases/performance-monitor/sql-server-database-replica.md)<br /><br /> [SQL Server, Databases 개체](../../../relational-databases/performance-monitor/sql-server-databases-object.md)|  
  
##  <a name="RelatedContent"></a>관련 내용  
  
-   **비디오-Alwayson 소개:**  [Microsoft SQL Server 코드 이름 "Denali" alwayson 시리즈, 1 부: 차세대 고가용성 솔루션 소개](https://channel9.msdn.com/Events/TechEd/NorthAmerica/2011/DBI302)  
  
-   **비디오-alwayson:**  [Microsoft SQL Server 코드 이름 "Denali" alwayson 시리즈, 2 부: Alwayson을 사용 하 여 중요 업무용 고가용성 솔루션 빌드](https://channel9.msdn.com/Events/TechEd/NorthAmerica/2011/DBI404)  
  
-   **백서:**  [고가용성 및 재해 복구를 위한 AlwaysOn 솔루션 가이드 Microsoft SQL Server](https://go.microsoft.com/fwlink/?LinkId=227600)  
  
-   **블로그:**  [SQL Server alwayson 팀 블로그: 공식 SQL Server AlwaysOn 팀 블로그](https://blogs.msdn.com/b/sqlalwayson/)  
  
## <a name="see-also"></a>참고 항목  
 [AlwaysOn 가용성 그룹 &#40;SQL Server&#41;](always-on-availability-groups-sql-server.md)   
 [AlwaysOn 가용성 그룹 &#40;SQL Server 개요&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [AlwaysOn 가용성 그룹 &#40;SQL Server에 대 한 서버 인스턴스 구성&#41;](configuration-of-a-server-instance-for-always-on-availability-groups-sql-server.md)   
 [SQL Server&#41;&#40;가용성 그룹 만들기 및 구성](creation-and-configuration-of-availability-groups-sql-server.md)   
 [가용성 그룹 &#40;모니터링 SQL Server&#41;](monitoring-of-availability-groups-sql-server.md)   
 [AlwaysOn 가용성 그룹 &#40;SQL Server에 대 한 Transact-sql 문 개요&#41;](transact-sql-statements-for-always-on-availability-groups.md)   
 [AlwaysOn 가용성 그룹 &#40;SQL Server에 대 한 PowerShell Cmdlet 개요&#41;](overview-of-powershell-cmdlets-for-always-on-availability-groups-sql-server.md)  
  
