---
title: 뷰 만들기 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- views [SQL Server], creating
ms.assetid: 0b7bd2a1-544c-42ba-8e7b-4822f34d7b64
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 5eaa6c702c02a3258ac66ec55081965d25a12a55
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/28/2018
ms.locfileid: "52541818"
---
# <a name="create-views"></a>뷰 만들기
  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 또는 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 을 사용하여 [!INCLUDE[tsql](../../includes/tsql-md.md)]에서 뷰를 만들 수 있습니다. 뷰는 다음과 같은 용도로 사용할 수 있습니다.  
  
-   각 사용자가 데이터베이스를 보는 시각에 초점을 맞추고 데이터 조작을 간소화하며 사용자 지정할 수 있습니다.  
  
-   뷰는 원본이 되는 기본 테이블에 직접 액세스할 수 있는 권한을 부여하지 않고 뷰를 통해 데이터에 액세스하도록 하기 때문에 보안 메커니즘으로 사용할 수 있습니다.  
  
-   이전 버전과 호환되는 인터페이스를 통해 스키마가 변경된 기존 테이블을 에뮬레이트할 수 있습니다.  
  
 **항목 내용**  
  
-   **시작하기 전 주의 사항:**  
  
     [제한 사항](#Restrictions)  
  
     [보안](#Security)  
  
-   **뷰를 만들려면:**  
  
     다른 도구는 [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> 시작하기 전에  
  
###  <a name="Restrictions"></a> 제한 사항  
 현재 데이터베이스에서만 뷰를 만들 수 있습니다.  
  
 최대 1,024개의 열을 뷰에 포함시킬 수 있습니다.  
  
###  <a name="Security"></a> 보안  
  
####  <a name="Permissions"></a> Permissions  
 데이터베이스에는 CREATE VIEW 권한이 필요하고 뷰를 만들 구성표에는 ALTER 권한이 필요합니다.  
  
##  <a name="SSMSProcedure"></a> SQL Server Management Studio 사용  
  
#### <a name="to-create-a-view-by-using-the-query-and-view-designer"></a>쿼리 및 뷰 디자이너를 사용하여 뷰를 만들려면  
  
1.  **개체 탐색기**에서 새 뷰를 만들 데이터베이스를 확장합니다.  
  
2.  **뷰** 폴더를 마우스 오른쪽 단추로 클릭한 다음, **새 뷰...** 를 클릭합니다.  
  
3.  에 **테이블 추가** 대화 상자는 다음 탭 중 하나에서 새 뷰에 포함할 요소를 선택 합니다. 새 뷰에 포함할 요소를 선택합니다.  
  
4.  **추가**를 클릭한 다음 **닫기**를 클릭합니다.  
  
5.  **다이어그램 창**에서 새 뷰에 포함할 열 또는 다른 요소를 선택합니다.  
  
6.  **조건 창**에서 열에 대한 추가 정렬 또는 필터 조건을 선택합니다.  
  
7.  **파일** 메뉴에서 **저장***뷰 이름*을 클릭합니다.  
  
8.  **이름 선택** 대화 상자에서 새 뷰의 이름을 입력하고 **확인**을 클릭합니다.  
  
     쿼리 및 뷰 디자이너에 대한 자세한 내용은 [쿼리 및 뷰 디자이너 도구&#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/visual-database-tools.md)를 참조하세요.  
  
##  <a name="TsqlProcedure"></a> Transact-SQL 사용  
  
#### <a name="to-create-a-view"></a>뷰를 만들려면  
  
1.  **개체 탐색기**에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)]인스턴스에 연결합니다.  
  
2.  표준 도구 모음에서 **새 쿼리**를 클릭합니다.  
  
3.  다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.  
  
    ```  
    USE AdventureWorks2012 ;   
    GO  
    CREATE VIEW HumanResources.EmployeeHireDate  
    AS  
    SELECT p.FirstName, p.LastName, e.HireDate  
    FROM HumanResources.Employee AS e JOIN Person.Person AS  p  
    ON e.BusinessEntityID = p.BusinessEntityID ;   
    GO  
    -- Query the view  
    SELECT FirstName, LastName, HireDate  
    FROM HumanResources.EmployeeHireDate  
    ORDER BY LastName;  
  
    ```  
  
 자세한 내용은 [CREATE VIEW&#40;Transact-SQL&#41;](/sql/t-sql/statements/create-view-transact-sql)를 참조하세요.  
  
  
