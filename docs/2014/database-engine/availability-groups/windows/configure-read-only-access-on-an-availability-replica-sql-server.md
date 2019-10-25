---
title: 가용성 복제본에 대한 읽기 전용 액세스 구성(SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 10/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- connection access to availability replicas
- Availability Groups [SQL Server], readable secondary replicas
- active secondary replicas [SQL Server], read-only access to
- Availability Groups [SQL Server], read-only routing
- Availability Groups [SQL Server], client connectivity
ms.assetid: 22387419-22c4-43fa-851c-5fecec4b049b
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: d93f78c157d5551e805437f156b8972ca8616c2b
ms.sourcegitcommit: f912c101d2939084c4ea2e9881eb98e1afa29dad
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/23/2019
ms.locfileid: "72797740"
---
# <a name="configure-read-only-access-on-an-availability-replica-sql-server"></a>가용성 복제본에 대한 읽기 전용 액세스 구성(SQL Server)
  기본적으로 주 복제본에 대한 읽기/쓰기 및 읽기 전용 액세스가 모두 허용되며 AlwaysOn 가용성 그룹의 보조 복제본에 대한 연결은 허용되지 않습니다. 이 항목에서는 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 에서 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)]또는 PowerShell을 사용하여 AlwaysOn 가용성 그룹의 가용성 복제본에 대한 연결 액세스를 구성하는 방법에 대해 설명합니다.  
  
 보조 복제본에 대해 읽기 전용 액세스를 사용하도록 설정할 경우의 영향에 대한 자세한 내용과 연결 액세스 소개는 [가용성 복제본에 대한 클라이언트 연결 액세스 정보&#40;SQL Server&#41;](about-client-connection-access-to-availability-replicas-sql-server.md) 및 [활성 보조: 읽기 가능한 보조 복제본&#40;AlwaysOn 가용성 그룹&#41;](active-secondaries-readable-secondary-replicas-always-on-availability-groups.md)을 참조하세요.  
  
  
  
##  <a name="BeforeYouBegin"></a> 시작하기 전에  
  
###  <a name="Prerequisites"></a> 사전 요구 사항 및 제한 사항  
  
-   다른 연결 액세스를 구성하려면 주 복제본을 호스팅하는 서버 인스턴스에 연결되어 있어야 합니다.  
  
###  <a name="Security"></a> 보안  
  
####  <a name="Permissions"></a> Permissions  
  
|태스크|Permissions|  
|----------|-----------------|  
|가용성 그룹을 만들 때 복제본을 구성하려면|CREATE AVAILABILITY GROUP 서버 권한, ALTER ANY AVAILABILITY GROUP 권한, CONTROL SERVER 권한 중 하나와 **sysadmin** 고정 서버 역할의 멤버 자격이 필요합니다.|  
|가용성 복제본을 수정하려면|가용성 그룹에 대한 ALTER AVAILABILITY GROUP 권한, CONTROL AVAILABILITY GROUP 권한, ALTER ANY AVAILABILITY GROUP 권한 또는 CONTROL SERVER 권한이 필요합니다.|  
  
  
##  <a name="SSMSProcedure"></a> SQL Server Management Studio 사용  
 **가용성 복제본에 대한 액세스를 구성하려면**  
  
1.  개체 탐색기에서 주 복제본을 호스팅하는 서버 인스턴스에 연결하고 서버 트리를 확장합니다.  
  
2.  **AlwaysOn 고가용성** 및 **가용성 그룹** 노드를 확장합니다.  
  
3.  복제본을 변경할 가용성 그룹을 클릭합니다.  
  
4.  가용성 복제본을 마우스 오른쪽 단추로 클릭하고 **속성**을 클릭합니다.  
  
5.  **가용성 복제본 속성** 대화 상자에서 다음과 같이 주 역할 및 보조 역할에 대한 연결 액세스를 변경할 수 있습니다.  
  
    -   보조 역할의 경우 **읽기용 보조** 드롭 목록의 다음 값 중에서 새 값을 선택합니다.  
  
         **아니오**  
         이 복제본의 보조 데이터베이스에 대한 사용자 연결이 허용되지 않습니다. 즉, 읽기 액세스가 가능하지 않습니다. 이 값은 기본 설정입니다.  
  
         **읽기 전용만**  
         이 복제본의 보조 데이터베이스에 대한 읽기 전용 연결만 허용됩니다. 즉, 모든 보조 데이터베이스에 대한 읽기 액세스가 가능합니다.  
  
         **예**  
         이 복제본의 보조 데이터베이스에 대한 모든 연결이 허용되지만 읽기 액세스만 가능합니다. 즉, 모든 보조 데이터베이스에 대한 읽기 액세스가 가능합니다.  
  
    -   주 역할의 경우 **주 역할의 연결 모드** 드롭 목록의 다음 값 중에서 새 값을 선택합니다.  
  
         **모든 연결 허용**  
         주 복제본의 데이터베이스에 대한 모든 연결이 허용됩니다. 이 값은 기본 설정입니다.  
  
         **읽기/쓰기 연결 허용**  
         애플리케이션 의도 속성이 **ReadWrite** 로 설정되었거나 애플리케이션 의도 연결 속성이 설정되지 않은 경우에는 연결이 허용됩니다. 애플리케이션 의도 연결 속성이 **ReadOnly** 로 설정된 연결은 허용되지 않습니다. 따라서 고객이 읽기 전용 작업을 실수로 주 복제본에 연결하는 것을 방지할 수 있습니다. 애플리케이션 의도 연결 속성에 대한 자세한 내용은 [Using Connection String Keywords with SQL Server Native Client](../../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md)을 참조하십시오.  
  
  
##  <a name="TsqlProcedure"></a> Transact-SQL 사용  
 **가용성 복제본에 대한 액세스를 구성하려면**  
  
> [!NOTE]  
>  이 절차에 대한 예는 이 섹션의 뒷부분에 나오는 [예제(Transact-SQL)](#TsqlExample)을 참조하세요.  
  
1.  주 복제본을 호스팅하는 서버 인스턴스에 연결합니다.  
  
2.  새 가용성 그룹에 대한 복제본을 지정하려는 경우 [CREATE AVAILABILITY GROUP](/sql/t-sql/statements/create-availability-group-transact-sql)[!INCLUDE[tsql](../../../includes/tsql-md.md)] 문을 사용합니다. 기존 가용성 그룹의 복제본을 추가하거나 수정하려는 경우에는 [ALTER AVAILABILITY GROUP](/sql/t-sql/statements/alter-availability-group-transact-sql)[!INCLUDE[tsql](../../../includes/tsql-md.md)] 문을 사용합니다.  
  
    -   보조 역할에 대한 연결 액세스를 구성하려면 ADD REPLICA 또는 MODIFY REPLICA WITH 절에서 다음과 같이 SECONDARY_ROLE 옵션을 지정합니다.  
  
         SECONDARY_ROLE **(** ALLOW_CONNECTIONS **=** { NO | READ_ONLY | ALL } **)**  
  
         각 항목이 나타내는 의미는 다음과 같습니다.  
  
         아니요  
         이 복제본의 보조 데이터베이스에 대한 직접 연결이 허용되지 않습니다. 즉, 읽기 액세스가 가능하지 않습니다. 이 값은 기본 설정입니다.  
  
         READ_ONLY  
         이 복제본의 보조 데이터베이스에 대한 읽기 전용 연결만 허용됩니다. 즉, 모든 보조 데이터베이스에 대한 읽기 액세스가 가능합니다.  
  
         ALL  
         이 복제본의 보조 데이터베이스에 대한 모든 연결이 허용되지만 읽기 액세스만 가능합니다. 즉, 모든 보조 데이터베이스에 대한 읽기 액세스가 가능합니다.  
  
3.  주 역할에 대한 연결 액세스를 구성하려면 ADD REPLICA 또는 MODIFY REPLICA WITH 절에서 다음과 같이 PRIMARY_ROLE 옵션을 지정합니다.  
  
     PRIMARY_ROLE **(** ALLOW_CONNECTIONS **=** { READ_WRITE | ALL } **)**  
  
     각 항목이 나타내는 의미는 다음과 같습니다.  
  
     READ_WRITE  
     애플리케이션 의도 연결 속성이 **ReadOnly** 로 설정된 연결은 허용되지 않습니다.  애플리케이션 의도 속성이 **ReadWrite** 로 설정되었거나 애플리케이션 의도 연결 속성이 설정되지 않은 경우에는 연결이 허용됩니다. 애플리케이션 의도 연결 속성에 대한 자세한 내용은 [Using Connection String Keywords with SQL Server Native Client](../../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md)을 참조하십시오.  
  
     ALL  
     주 복제본의 데이터베이스에 대한 모든 연결이 허용됩니다. 이 값은 기본 설정입니다.  
  
###  <a name="TsqlExample"></a> 예(Transact-SQL)  
 다음 예제에서는 *AG2*라는 가용성 그룹에 보조 복제본을 추가합니다. 독립 실행형 서버 인스턴스인 *COMPUTER03\HADR_INSTANCE*가 새 가용성 복제본을 호스트하도록 지정됩니다. 이 복제본은 주 역할에 대해 읽기/쓰기 연결만 허용하고 보조 역할에 대해 읽기 전용 연결만 허용하도록 구성되어 있습니다.  
  
```sql
ALTER AVAILABILITY GROUP AG2   
   ADD REPLICA ON   
      'COMPUTER03\HADR_INSTANCE' WITH   
         (  
         ENDPOINT_URL = 'TCP://COMPUTER03:7022',  
         PRIMARY_ROLE ( ALLOW_CONNECTIONS = READ_WRITE ),  
         SECONDARY_ROLE (ALLOW_CONNECTIONS = READ_ONLY )  
         );   
GO  
```  
  
  
##  <a name="PowerShellProcedure"></a> PowerShell 사용  

### <a name="to-configure-access-on-an-availability-replica"></a>가용성 복제본에 대한 액세스를 구성하려면
  
> [!NOTE]  
>  코드 예제를 보려면이 섹션의 뒷부분에 나오는 PowerShell 예제를 참조 하세요.  
  
1.  주 복제본을 호스팅하는 서버 인스턴스로 디렉터리를 변경(`cd`)합니다.  
  
2.  가용성 그룹에 가용성 복제본을 추가하는 경우 `New-SqlAvailabilityReplica` cmdlet을 사용합니다. 기존 가용성 복제본을 수정하는 경우 `Set-SqlAvailabilityReplica` cmdlet을 사용합니다. 관련 매개 변수는 다음과 같습니다.  
  
    -   보조 역할에 대 한 연결 액세스를 구성 하려면 `ConnectionModeInSecondaryRole`*secondary_role_keyword* 매개 변수를 지정 합니다. 여기서 *secondary_role_keyword* 은 다음 값 중 하나입니다.  
  
         `AllowNoConnections`  
         보조 복제본의 데이터베이스에 대한 직접 연결이 허용되지 않으며 읽기 액세스를 위해 데이터베이스에 연결할 수 없습니다. 이 값은 기본 설정입니다.  
  
         `AllowReadIntentConnectionsOnly`  
         애플리케이션 의도 속성이 **ReadOnly**로 설정된 경우에만 보조 복제본의 데이터베이스에 연결할 수 있습니다. 이 속성에 대한 자세한 내용은 [Using Connection String Keywords with SQL Server Native Client](../../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md)을 참조하십시오.  
  
         `AllowAllConnections`  
         보조 복제본의 데이터베이스에 대해 읽기 전용 액세스를 위한 모든 연결이 허용됩니다.  
  
    -   주 역할에 대 한 연결 액세스를 구성 하려면 `ConnectionModeInPrimaryRole`*primary_role_keyword*를 지정 합니다. 여기서 *primary_role_keyword* 은 다음 값 중 하나입니다.  
  
         `AllowReadWriteConnections`  
         애플리케이션 의도 연결 속성이 ReadOnly로 설정된 연결은 허용되지 않습니다. 애플리케이션 의도 속성이 ReadWrite로 설정되었거나 애플리케이션 의도 연결 속성이 설정되지 않은 경우에는 연결이 허용됩니다. 애플리케이션 의도 연결 속성에 대한 자세한 내용은 [Using Connection String Keywords with SQL Server Native Client](../../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md)을 참조하십시오.  
  
         `AllowAllConnections`  
         주 복제본의 데이터베이스에 대한 모든 연결이 허용됩니다. 이 값은 기본 설정입니다.  
  
    > [!NOTE]  
    >  cmdlet의 구문을 보려면 `Get-Help` PowerShell 환경에서 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] cmdlet을 사용합니다. 자세한 내용은 [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md)을 참조하세요.  
  
SQL Server PowerShell 공급자를 설정 하 고 사용 하려면 [SQL Server PowerShell 공급자](../../../powershell/sql-server-powershell-provider.md)를 참조 하세요.
  
다음 예에서는 `ConnectionModeInSecondaryRole` 및 `ConnectionModeInPrimaryRole` 매개 변수를 모두 `AllowAllConnections`으로 설정합니다.  
  
```powershell
Set-Location SQLSERVER:\SQL\PrimaryServer\default\AvailabilityGroups\MyAg  
$primaryReplica = Get-Item "AvailabilityReplicas\PrimaryServer"  

Set-SqlAvailabilityReplica -ConnectionModeInSecondaryRole "AllowAllConnections" `
 -InputObject $primaryReplica  
Set-SqlAvailabilityReplica -ConnectionModeInPrimaryRole "AllowAllConnections" `
-InputObject $primaryReplica
```  

##  <a name="FollowUp"></a> 후속 작업: 가용성 복제본에 대한 읽기 전용 액세스를 구성한 후의 작업  
 **읽을 수 있는 보조 복제본에 대한 읽기 전용 액세스**  
  
-   [Bcp 유틸리티](../../../tools/bcp-utility.md) 또는 [sqlcmd 유틸리티](../../../tools/sqlcmd-utility.md)를 사용 하는 경우 `-K ReadOnly` 스위치를 지정 하 여 읽기 전용 액세스를 사용 하도록 설정 된 보조 복제본에 대 한 읽기 전용 액세스를 지정할 수 있습니다.  
  
-   클라이언트 애플리케이션을 읽을 수 있는 보조 복제본에 연결할 수 있도록 설정하려면:  
  
    ||필수 구성 요소|링크|  
    |-|------------------|----------|  
    |![상자](../../media/checkboxemptycenterxtraspacetopandright.gif "상자")|가용성 그룹에 수신기가 있는지 확인합니다.|[가용성 그룹 수신기 만들기 또는 구성&#40;SQL Server&#41;](create-or-configure-an-availability-group-listener-sql-server.md)|  
    |![상자](../../media/checkboxemptycenterxtraspacetopandright.gif "상자")|가용성 그룹에 대한 읽기 전용 라우팅을 구성합니다.|[가용성 그룹에 대한 읽기 전용 라우팅 구성&#40;SQL Server&#41;](configure-read-only-routing-for-an-availability-group-sql-server.md)|  
  
 **장애 조치(Failover) 후 트리거 및 작업에 영향을 줄 수 있는 요소**  
  
 읽을 수 없는 보조 데이터베이스 또는 읽을 수 있는 보조 데이터베이스에서 실행할 때 실패하는 트리거 및 작업이 있는 경우 트리거와 작업을 스크립팅하여 지정된 복제본에서 데이터베이스가 주 데이터베이스인지 읽을 수 있는 보조 데이터베이스인지 확인해야 합니다. 이 정보를 얻으려면 [DATABASEPROPERTYEX](/sql/t-sql/functions/databasepropertyex-transact-sql) 함수를 사용하여 데이터베이스의 **Updatability** 속성을 반환합니다. 읽기 전용 데이터베이스를 식별하려면 다음과 같이 READ_ONLY를 값으로 지정합니다.  
  
```  
DATABASEPROPERTYEX([db name],'Updatability') = N'READ_ONLY'  
```  
  
 쓰기 전용 데이터베이스를 식별하려면 READ_WRITE를 값으로 지정합니다.  
  
  
##  <a name="RelatedTasks"></a> 관련 태스크  
  
-   [가용성 그룹에 대한 읽기 전용 라우팅 구성&#40;SQL Server&#41;](configure-read-only-routing-for-an-availability-group-sql-server.md)  
  
-   [가용성 그룹 수신기 만들기 또는 구성&#40;SQL Server&#41;](create-or-configure-an-availability-group-listener-sql-server.md)  
  
  
##  <a name="RelatedContent"></a> 관련 내용  
  
-   [AlwaysOn: 읽기 가능한 보조 복제본의 가치 제안](https://blogs.msdn.com/b/sqlserverstorageengine/archive/2011/12/22/alwayson-value-proposition-of-readable-secondary.aspx)  
  
-   [AlwaysOn: 읽기 작업에 보조 복제본을 사용 하도록 설정 하는 두 가지 옵션이 있습니다.](https://blogs.msdn.com/b/sqlserverstorageengine/archive/2011/12/22/alwayson-why-there-are-two-options-to-enable-a-secondary-replica-for-read-workload.aspx)  
  
-   [AlwaysOn: 읽기 가능한 보조 복제본 설정](https://blogs.msdn.com/b/sqlserverstorageengine/archive/2011/12/22/alwayson-setting-up-readable-seconary-replica.aspx)  
  
-   [AlwaysOn: 읽기 가능한 보조를 사용 하도록 설정 했지만 쿼리가 차단 되었습니까?](https://blogs.msdn.com/b/sqlserverstorageengine/archive/2011/12/22/alwayson-i-just-enabled-readble-secondary-but-my-query-is-blocked.aspx)  
  
-   [AlwaysOn: 읽기 가능한 보조 복제본, 읽기 전용 데이터베이스 및 데이터베이스 스냅숏에서 최신 통계를 사용 하도록 설정](https://blogs.msdn.com/b/sqlserverstorageengine/archive/2011/12/22/alwayson-making-upto-date-statistics-available-on-readable-secondary-read-only-database-and-database-snapshot.aspx)  
  
-   [AlwaysOn: 읽기 전용 데이터베이스, 데이터베이스 스냅숏 및 보조 복제본에 대 한 통계 문제](https://blogs.msdn.com/b/sqlserverstorageengine/archive/2011/12/22/alwayson-challenges-with-statistics-on-readonly-database-database-snapshot-and-secondary-replica.aspx)  
  
-   [AlwaysOn: 보조 복제본에서 보고 작업을 실행할 때 주 작업에 미치는 영향](https://blogs.msdn.com/b/sqlserverstorageengine/archive/2011/12/22/alwayson-impact-on-the-primary-workload-when-you-run-reporting-workload-on-the-secondary-replica.aspx)  
  
-   [AlwaysOn: 읽기 가능한 보조 복제본의 보고 작업을 스냅숏 격리로 매핑할 때의 영향](https://blogs.msdn.com/b/sqlserverstorageengine/archive/2011/12/22/alwayson-impact-of-mapping-reporting-workload-to-snapshot-isolation-on-readable-secondary.aspx)  
  
-   [AlwaysOn: 보조 복제본에서 보고 작업을 실행할 때 REDO 스레드 차단 최소화](https://blogs.msdn.com/b/sqlserverstorageengine/archive/2011/12/22/alwayson-minimizing-blocking-of-redo-thread-when-running-reporting-workload-on-secondary-replica.aspx)  
  
-   [AlwaysOn: 읽기 가능한 보조 복제본 및 데이터 대기 시간](https://blogs.msdn.com/b/sqlserverstorageengine/archive/2011/12/22/alwayson.aspx)  
  
  
## <a name="see-also"></a>관련 항목:  
 [AlwaysOn 가용성 그룹 &#40;SQL Server&#41; 개요](overview-of-always-on-availability-groups-sql-server.md)    
 [활성 보조: 읽기 가능한 보조 &#40;복제본 AlwaysOn 가용성 그룹&#41;](active-secondaries-readable-secondary-replicas-always-on-availability-groups.md)  
 [가용성 복제본에 대한 클라이언트 연결 액세스 정보&#40;SQL Server&#41;](about-client-connection-access-to-availability-replicas-sql-server.md)  
