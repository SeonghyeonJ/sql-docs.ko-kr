---
title: 저장 프로시저 이름 바꾸기 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.technology: stored-procedures
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- stored procedures [SQL Server], renaming
- renaming stored procedures
ms.assetid: 5d2e4c68-7e0b-4405-8919-f5b203e46770
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: b85a6a5e79c004eb3ed2c7c40c6e3b62d526e95a
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/27/2019
ms.locfileid: "58536285"
---
# <a name="rename-a-stored-procedure"></a>저장 프로시저 이름 바꾸기
  이 항목에서는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 에서 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 또는 [!INCLUDE[tsql](../../includes/tsql-md.md)]을 사용하여 저장 프로시저의 이름을 바꾸는 방법에 대해 설명합니다.  
  
 **항목 내용**  
  
-   **시작하기 전 주의 사항:**  
  
     [제한 사항](#Restrictions)  
  
     [보안](#Security)  
  
-   **저장 프로시저의 이름을 바꾸려면:**  
  
     다른 도구는 [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> 시작하기 전에  
  
###  <a name="Restrictions"></a> 제한 사항  
  
-   프로시저 이름은 [식별자](../databases/database-identifiers.md)에 대한 규칙을 따라야 합니다.  
  
-   저장 프로시저의 이름을 변경해도 **sys.sql_modules** 카탈로그 뷰의 정의 열에 있는 해당 개체 이름은 변경되지 않습니다. 따라서 이 개체 유형의 이름을 바꾸지 않는 것이 좋습니다. 대신 저장 프로시저를 삭제하고 새로운 이름으로 다시 만듭니다.  
  
-   프로시저의 이름 또는 정의를 변경할 때 프로시저의 변경 내용이 적용되도록 개체를 업데이트하지 않으면 종속 개체가 실패할 수 있습니다. 자세한 내용은 [저장 프로시저의 종속성 보기](view-the-dependencies-of-a-stored-procedure.md)를 참조하세요.  
  
###  <a name="Security"></a> 보안  
  
####  <a name="Permissions"></a> Permissions  
 CREATE PROCEDURE  
 데이터베이스에 대한 CREATE PROCEDURE 권한과 프로시저를 만들고 있는 스키마에 대한 ALTER 권한이 필요하거나 **db_ddladmin** 고정 데이터베이스 역할의 멤버 자격이 필요합니다.  
  
 ALTER PROCEDURE  
 프로시저에 대한 ALTER 권한이나 **db_ddladmin** 고정 데이터베이스 역할의 멤버 자격이 필요합니다.  
  
##  <a name="SSMSProcedure"></a> SQL Server Management Studio 사용  
  
#### <a name="to-rename-a-stored-procedure"></a>저장 프로시저의 이름을 바꾸려면  
  
1.  개체 탐색기에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 의 인스턴스에 연결한 다음 해당 인스턴스를 확장합니다.  
  
2.  **데이터베이스**를 확장하고 해당 프로시저가 속한 데이터베이스를 확장한 다음 **프로그래밍 기능**을 확장합니다.  
  
3.  [저장 프로시저의 종속성을 결정합니다](view-the-dependencies-of-a-stored-procedure.md).  
  
4.  **저장 프로시저**를 확장하고 이름을 바꿀 프로시저를 마우스 오른쪽 단추로 클릭한 다음 **이름 바꾸기**를 클릭합니다.  
  
5.  프로시저 이름을 수정합니다.  
  
6.  종속 개체 또는 스크립트에서 참조된 프로시저 이름을 수정합니다.  
  
##  <a name="TsqlProcedure"></a> Transact-SQL 사용  
  
#### <a name="to-rename-a-stored-procedure"></a>저장 프로시저의 이름을 바꾸려면  
  
1.  [!INCLUDE[ssDE](../../includes/ssde-md.md)]에 연결합니다.  
  
2.  표준 도구 모음에서 **새 쿼리**를 클릭합니다.  
  
3.  다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다. 이 예에서는 프로시저를 삭제하고 새 이름으로 다시 만들어 프로시저의 이름을 바꾸는 방법을 보여 줍니다. 첫 번째 예에서는 `'HumanResources.uspGetAllEmployeesTest`저장 프로시저를 만듭니다. 두 번째 예에서는 `HumanResources.uspEveryEmployeeTest`저장 프로시저의 이름을 바꿉니다.  
  
```sql  
--Create the stored procedure.  
USE AdventureWorks2012;  
GO  
IF OBJECT_ID ( 'HumanResources.uspGetAllEmployeesTest', 'P' ) IS NOT NULL   
    DROP PROCEDURE HumanResources.uspGetAllEmployeesTest;  
GO  
CREATE PROCEDURE HumanResources.uspGetAllEmployeesTest  
AS  
    SET NOCOUNT ON;  
    SELECT LastName, FirstName, Department  
    FROM HumanResources.vEmployeeDepartmentHistory;  
GO  
  
--Rename the stored procedure.  
USE AdventureWorks2012;  
GO  
IF OBJECT_ID ( 'HumanResources.uspGetAllEmployeesTest', 'P' ) IS NOT NULL   
    DROP PROCEDURE HumanResources.uspGetAllEmployeesTest;  
GO  
CREATE PROCEDURE HumanResources.uspEveryEmployeeTest  
AS  
    SET NOCOUNT ON;  
    SELECT LastName, FirstName, Department  
    FROM HumanResources.vEmployeeDepartmentHistory;  
GO  
```  
  
## <a name="see-also"></a>관련 항목  
 [ALTER PROCEDURE&#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-procedure-transact-sql)   
 [CREATE PROCEDURE&#40;Transact-SQL&#41;](/sql/t-sql/statements/create-procedure-transact-sql)   
 [저장 프로시저 만들기](../stored-procedures/create-a-stored-procedure.md)   
 [저장 프로시저 수정](../stored-procedures/modify-a-stored-procedure.md)   
 [저장 프로시저 삭제](../stored-procedures/delete-a-stored-procedure.md)   
 [저장 프로시저의 정의 보기](view-the-definition-of-a-stored-procedure.md)   
 [저장 프로시저의 종속성 보기](view-the-dependencies-of-a-stored-procedure.md)  
  
  
