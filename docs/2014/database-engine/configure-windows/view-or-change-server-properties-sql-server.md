---
title: 서버 속성 보기 또는 변경(SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- viewing server properties
- server properties [SQL Server]
- displaying server properties
- servers [SQL Server], viewing
ms.assetid: 55f3ac04-5626-4ad2-96bd-a1f1b079659d
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 5c5ff985b62e39287b696e96f10142daf90ae0a3
ms.sourcegitcommit: a165052c789a327a3a7202872669ce039bd9e495
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72783132"
---
# <a name="view-or-change-server-properties-sql-server"></a>서버 속성 보기 또는 변경(SQL Server)
  이 항목에서는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]또는 SQL Server 구성 관리자를 사용하여 [!INCLUDE[tsql](../../includes/tsql-md.md)]인스턴스의 속성을 보거나 변경하는 방법에 대해 설명합니다.  
  
 **항목 내용**  
  
-   **시작하기 전에:**  
  
     [제한 사항](#Restrictions)  
  
     [보안](#Security)  
  
-   **서버 속성을 보거나 변경하려면:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [SQL Server 구성 관리자](#PowerShellProcedure)  
  
-   **후속 작업:**  [서버 속성을 변경한 후](#FollowUp)  
  
##  <a name="BeforeYouBegin"></a> 시작하기 전에  
  
###  <a name="Restrictions"></a> 제한 사항  
  
-   sp_configure를 사용할 때는 구성 옵션을 설정한 뒤에 RECONFIGURE 또는 RECONFIGURE WITH OVERRIDE를 실행해야 합니다. RECONFIGURE WITH OVERRIDE 문은 각별한 주의가 필요한 구성 옵션에 주로 사용되지만 모든 구성 옵션에 사용할 수 있으며 RECONFIGURE 대신 사용할 수 있습니다.  
  
    > [!NOTE]  
    >  RECONFIGURE는 트랜잭션 내에서 실행됩니다. 다시 구성 작업 중 하나가 실패하면 다시 구성 작업이 하나도 적용되지 않습니다.  
  
-   일부 속성 페이지는 WMI(Windows Management Instrumentation)를 통해 얻은 정보를 표시합니다. 이러한 페이지를 표시하려면 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]를 실행 중인 컴퓨터에 WMI가 설치되어 있어야 합니다.  
  
###  <a name="Security"></a> 보안  
  
####  <a name="Permissions"></a> Permissions  
 자세한 내용은 [서버 수준 역할](../../relational-databases/security/authentication-access/server-level-roles.md)을 참조하세요.  
  
 매개 변수 없이 또는 첫 번째 매개 변수만 사용 하는 `sp_configure`에 대 한 실행 권한은 기본적으로 모든 사용자에 게 부여 됩니다. 구성 옵션을 변경 하거나 RECONFIGURE 문을 실행 하는 두 매개 변수를 사용 하 여 `sp_configure`를 실행 하려면 사용자에 게 ALTER SETTINGS 서버 수준 권한이 있어야 합니다. **sysadmin** 및 **serveradmin** 고정 서버 역할은 ALTER SETTINGS 권한을 암시적으로 보유하고 있습니다.  
  
##  <a name="SSMSProcedure"></a> SQL Server Management Studio 사용  
  
#### <a name="to-view-or-change-server-properties"></a>서버 속성을 보거나 변경하려면  
  
1.  개체 탐색기에서 서버를 마우스 오른쪽 단추로 클릭한 다음 **속성**을 클릭합니다.  
  
2.  **서버 속성** 대화 상자에서 해당 페이지에 대한 서버 정보를 보거나 변경할 페이지를 클릭합니다. 일부 속성은 읽기 전용입니다.  
  
##  <a name="TsqlProcedure"></a> Transact-SQL 사용  
  
#### <a name="to-view-server-properties-by-using-the-serverproperty-built-in-function"></a>SERVERPROPERTY 기본 제공 함수를 사용하여 서버 속성을 보려면  
  
1.  [!INCLUDE[ssDE](../../includes/ssde-md.md)]에 연결합니다.  
  
2.  표준 도구 모음에서 **새 쿼리**를 클릭합니다.  
  
3.  다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다. 이 예제에서는 [문에](/sql/t-sql/functions/serverproperty-transact-sql) SERVERPROPERTY `SELECT` 기본 제공 함수를 사용하여 현재 서버에 대한 정보를 반환합니다. 이 시나리오는 한 Windows 기반 서버에 여러 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스가 설치되어 있고 클라이언트가 현재 연결에서 사용되는 인스턴스에 대한 또 다른 연결을 열어야 하는 경우에 유용합니다.  
  
    ```sql  
    SELECT CONVERT( sysname, SERVERPROPERTY('servername'));  
    GO  
    ```  
  
#### <a name="to-view-server-properties-by-using-the-sysservers-catalog-view"></a>sys.servers 카탈로그 뷰를 사용하여 서버 속성을 보려면  
  
1.  [!INCLUDE[ssDE](../../includes/ssde-md.md)]에 연결합니다.  
  
2.  표준 도구 모음에서 **새 쿼리**를 클릭합니다.  
  
3.  다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다. 이 예제에서는 [sys.servers](/sql/relational-databases/system-catalog-views/sys-servers-transact-sql) 카탈로그 뷰를 쿼리하여 현재 서버의 이름(`name`)과 ID(`server_id`) 및 연결된 서버에 연결하기 위한 OLE DB 공급자의 이름(`provider`)을 반환합니다.  
  
    ```sql  
    USE AdventureWorks2012;   
    GO  
    SELECT name, server_id, provider  
    FROM sys.servers ;   
    GO
    ```  
  
#### <a name="to-view-server-properties-by-using-the-sysconfigurations-catalog-view"></a>sys.configurations 카탈로그 뷰를 사용하여 서버 속성을 보려면  
  
1.  [!INCLUDE[ssDE](../../includes/ssde-md.md)]에 연결합니다.  
  
2.  표준 도구 모음에서 **새 쿼리**를 클릭합니다.  
  
3.  다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다. 이 예에서는 [sys.configurations](/sql/relational-databases/system-catalog-views/sys-configurations-transact-sql) 카탈로그 뷰를 쿼리하여 현재 서버의 각 서버 구성 옵션에 대한 정보를 반환합니다. 이 예에서는 옵션의 이름(`name`)과 설명(`description`) 및 옵션이 고급 옵션인지 여부(`is_advanced`)를 반환합니다.  
  
    ```sql
    USE AdventureWorks2012;
    GO  
    SELECT name, description, is_advanced  
    FROM sys.configurations ;
    GO
    ```  
  
#### <a name="to-change-a-server-property-by-using-sp_configure"></a>sp_configure를 사용하여 서버 속성을 변경하려면  
  
1.  [!INCLUDE[ssDE](../../includes/ssde-md.md)]에 연결합니다.  
  
2.  표준 도구 모음에서 **새 쿼리**를 클릭합니다.  
  
3.  다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다. 이 예제에서는 [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) 를 사용하여 서버 속성을 변경하는 방법을 보여 줍니다. 이 예에서는 `fill factor` 옵션의 값을 `100`으로 변경합니다. 변경 내용을 적용하려면 서버를 다시 시작해야 합니다.  
  
```sql  
Use AdventureWorks2012;  
GO  
sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE;  
GO  
sp_configure 'fill factor', 100;  
GO  
RECONFIGURE;  
GO  
```  
  
 자세한 내용은 [서버 구성 옵션&#40;SQL Server&#41;](server-configuration-options-sql-server.md)를 실행 중인 컴퓨터에 WMI가 설치되어 있어야 합니다.  
  
##  <a name="PowerShellProcedure"></a> SQL Server 구성 관리자 사용  
 일부 서버 속성은 SQL Server 구성 관리자를 사용하여 보거나 변경할 수 있습니다. 예를 들어 SQL Server 인스턴스의 버전 및 에디션을 보거나 오류 로그 파일이 저장된 위치를 변경할 수 있습니다. [서버 관련 동적 관리 뷰 및 함수](/sql/relational-databases/system-dynamic-management-views/server-related-dynamic-management-views-and-functions-transact-sql)를 쿼리하여 이러한 속성을 볼 수도 있습니다.  
  
#### <a name="to-view-or-change-server-properties"></a>서버 속성을 보거나 변경하려면  
  
1.  **시작** 메뉴에서 **모든 프로그램**, [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)], **구성 도구**를 차례로 가리킨 다음 **SQL Server 구성 관리자**를 클릭합니다.  
  
2.  **SQL Server 구성 관리자**에서 **SQL Server 서비스**를 클릭합니다.  
  
3.  세부 정보 창에서 **SQL Server (\<***instancename***>)** 를 마우스 오른쪽 단추로 클릭한 다음 **속성**을 클릭합니다.  
  
4.  **SQL Server(\<***instancename***>) 속성** 대화 상자에서 **서비스** 탭 또는 **고급** 탭의 서버 속성을 변경한 다음 **확인**을 클릭합니다.  
  
##  <a name="FollowUp"></a> 후속 작업: 서버 속성을 변경한 후  
 일부 속성의 경우 변경 내용을 적용하려면 서버를 다시 시작해야 할 수도 있습니다.  
  
## <a name="see-also"></a>관련 항목:  
 [서버 구성 옵션&#40;SQL Server&#41;](server-configuration-options-sql-server.md)   
 [SET 문&#40;Transact-SQL&#41;](/sql/t-sql/statements/set-statements-transact-sql)   
 [SERVERPROPERTY&#40;Transact-SQL&#41;](/sql/t-sql/functions/serverproperty-transact-sql)   
 [sp_configure&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)   
 [RECONFIGURE&#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql)   
 [SELECT&#40;Transact-SQL&#41;](/sql/t-sql/queries/select-transact-sql)   
 [WMI를 구성하여 SQL Server 도구에 서버 상태 표시](../../ssms/configure-wmi-to-show-server-status-in-sql-server-tools.md)   
 [SQL Server 구성 관리자](../../relational-databases/sql-server-configuration-manager.md)   
 [구성 함수&#40;Transact-SQL&#41;](/sql/t-sql/functions/configuration-functions-transact-sql)   
 [서버 관련 동적 관리 뷰 및 함수&#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/server-related-dynamic-management-views-and-functions-transact-sql)  
