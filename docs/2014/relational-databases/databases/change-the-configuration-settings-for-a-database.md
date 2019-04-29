---
title: 데이터베이스 메일의 구성 설정 변경 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- database configuration [SQL Server]
- configuration options [SQL Server], databases
- modifying database configuration settings
ms.assetid: c29c3385-5043-400f-bb4e-044a4c9a9a4b
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 05dc6188a46e0e2d43b7a4bc3275fae7d4cd8da6
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62917563"
---
# <a name="change-the-configuration-settings-for-a-database"></a>데이터베이스 메일의 구성 설정 변경
  이 항목에서는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 또는 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 을 사용하여 [!INCLUDE[tsql](../../includes/tsql-md.md)]에서 데이터베이스 수준 옵션을 변경하는 방법에 대해 설명합니다. 데이터베이스 수준의 옵션은 각 데이터베이스의 고유한 옵션이므로 다른 데이터베이스에는 영향을 주지 않습니다.  
  
 **항목 내용**  
  
-   **시작하기 전 주의 사항:**  
  
     [제한 사항](#Restrictions)  
  
     [보안](#Security)  
  
-   **다음을 사용하여 데이터베이스의 옵션 설정을 변경합니다.**  
  
     다른 도구는 [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> 시작하기 전에  
  
###  <a name="Restrictions"></a> 제한 사항  
  
-   시스템 관리자, 데이터베이스 소유자, **sysadmin** 및 **dbcreator** 고정 서버 역할과 **db_owner** 고정 데이터베이스 역할의 멤버만 이 옵션을 수정할 수 있습니다.  
  
###  <a name="Security"></a> 보안  
  
####  <a name="Permissions"></a> Permissions  
 데이터베이스에 대한 ALTER 권한이 필요합니다.  
  
##  <a name="SSMSProcedure"></a> SQL Server Management Studio 사용  
  
#### <a name="to-change-the-option-settings-for-a-database"></a>데이터베이스의 옵션 설정을 변경하려면  
  
1.  개체 탐색기에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 인스턴스에 연결하고 서버와 **데이터베이스**를 차례로 확장한 다음 데이터베이스를 마우스 오른쪽 단추로 클릭하고 **속성**을 클릭합니다.  
  
2.  **데이터베이스 속성** 대화 상자에서 **옵션** 을 클릭하면 대부분의 구성 설정에 액세스할 수 있습니다. 파일 및 파일 그룹 구성, 미러링 및 로그 전달은 해당 페이지에서 설정할 수 있습니다.  
  
##  <a name="TsqlProcedure"></a> Transact-SQL 사용  
  
#### <a name="to-change-the-option-settings-for-a-database"></a>데이터베이스의 옵션 설정을 변경하려면  
  
1.  [!INCLUDE[ssDE](../../includes/ssde-md.md)]에 연결합니다.  
  
2.  표준 도구 모음에서 **새 쿼리**를 클릭합니다.  
  
3.  다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다. 이 예에서는 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 예제 데이터베이스에 대해 복구 모델 및 데이터 페이지 확인 옵션을 설정합니다.  
  
 [!code-sql[DatabaseDDL#AlterDatabase7](../../snippets/tsql/SQL14/tsql/databaseddl/transact-sql/alterdatabase.sql#alterdatabase7)]  
  
 더 많은 예제를 보려면 [ALTER DATABASE SET 옵션&#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-options)을 참조하세요.  
  
## <a name="see-also"></a>관련 항목  
 [ALTER DATABASE 호환성 수준&#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-compatibility-level)   
 [ALTER DATABASE 데이터베이스 미러링&#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-database-mirroring)   
 [ALTER DATABASE SET HADR&#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-hadr)   
 [데이터베이스 이름 바꾸기](rename-a-database.md)   
 [데이터베이스 축소](shrink-a-database.md)  
  
  
