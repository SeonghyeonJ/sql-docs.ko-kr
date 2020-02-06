---
title: 데이터베이스 스냅샷 보기(SQL Server) | Microsoft 문서
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- database snapshots [SQL Server], viewing
- displaying database snapshots
- viewing database snapshots
ms.assetid: 123f19b2-0850-4033-8507-59ebdfb368ee
author: stevestein
ms.author: sstein
ms.openlocfilehash: 5f09f279c82a9fb28e259951be2bf78f9ca93aae
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/01/2020
ms.locfileid: "72907906"
---
# <a name="view-a-database-snapshot-sql-server"></a>데이터베이스 스냅샷 보기(SQL Server)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  이 항목에서는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 를 사용하여 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]데이터베이스 스냅샷을 표시하는 방법에 대해 설명합니다.  
  
> [!NOTE]  
>  데이터베이스 스냅샷을 만들거나, 되돌리거나, 삭제하려면 [!INCLUDE[tsql](../../includes/tsql-md.md)]을 사용해야 합니다.  
  
 **항목 내용**  
  
-   **데이터베이스 스냅샷을 보려면:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="SSMSProcedure"></a> SQL Server Management Studio 사용  
 **데이터베이스 스냅샷을 보려면**  
  
1.  개체 탐색기에서 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 인스턴스에 연결한 다음 해당 인스턴스를 확장합니다.  
  
2.  **데이터베이스**를 확장합니다.  
  
3.  **데이터베이스 스냅샷**을 확장한 후 표시할 스냅샷을 선택합니다.  

##  <a name="TsqlProcedure"></a> Transact-SQL 사용  
 **데이터베이스 스냅샷을 보려면**  
  
1.  [!INCLUDE[ssDE](../../includes/ssde-md.md)]에 연결합니다.  
  
2.  표준 도구 모음에서 **새 쿼리**를 클릭합니다.  
  
3.  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]인스턴스의 데이터베이스 스냅샷을 나열하려면 NULL이 아닌 값에 대해 **sys.databases** 카탈로그 뷰의 [source_database_id](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md) 열을 쿼리합니다.  
  
##  <a name="RelatedTasks"></a> 관련 작업  
  
-   [데이터베이스 스냅샷 만들기&#40;Transact-SQL&#41;](../../relational-databases/databases/create-a-database-snapshot-transact-sql.md)  
  
-   [데이터베이스를 데이터베이스 스냅샷으로 되돌리기](../../relational-databases/databases/revert-a-database-to-a-database-snapshot.md)  
  
-   [데이터베이스 스냅샷 삭제&#40;Transact-SQL&#41;](../../relational-databases/databases/drop-a-database-snapshot-transact-sql.md)  
  
## <a name="see-also"></a>참고 항목  
 [데이터베이스 스냅샷&#40;SQL Server&#41;](../../relational-databases/databases/database-snapshots-sql-server.md)  
  
  
