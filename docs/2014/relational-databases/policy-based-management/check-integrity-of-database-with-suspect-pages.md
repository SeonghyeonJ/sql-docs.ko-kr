---
title: 주의 대상 페이지가 있는 데이터베이스의 무결성 검사 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 3b1ec9fe-f6c5-46f7-aa63-6e671be1572d
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 8abad1f3dbeb8a8667999e90de63d80c2328d90c
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2020
ms.locfileid: "62866845"
---
# <a name="check-integrity-of-database-with-suspect-pages"></a>주의 대상 페이지가 있는 데이터베이스의 무결성 검사
  이 규칙은 데이터베이스 상태가 주의 대상으로 설정된 사용자 데이터베이스를 검사합니다. [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 이 824 오류가 포함된 데이터베이스 페이지를 읽는 경우 페이지는 주의 대상 페이지로 간주되고 페이지 ID는 msdb의 suspect_pages 테이블에 기록되며 해당 페이지를 포함하는 데이터베이스는 주의 대상으로 설정됩니다.  
  
 824 오류는 읽기 작업 중에 논리적 일관성 오류가 검색되었음을 나타냅니다. 이 오류는 잘못된 I/O 하위 시스템 구성 요소로 인한 데이터 손상을 나타내는 경우가 많습니다. 이는 데이터베이스 무결성을 위협하는 심각한 오류 상태이며 즉시 수정해야 합니다.  
  
## <a name="best-practices-recommendations"></a>최선의 구현 방법 권장 사항  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 오류 로그에서 이 데이터베이스에 대한 824 오류의 세부 정보를 검토합니다.  
  
-   전체 데이터베이스 일관성 검사([DBCC CHECKDB](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql))를 완료합니다.  
  
-   [MSSQLSERVER_824](https://go.microsoft.com/fwlink/?LinkId=81397)에 정의된 사용자 동작을 구현합니다.  
  
## <a name="for-more-information"></a>참조 항목  
 [suspect_pages 테이블 관리&#40;SQL Server&#41;](../backup-restore/manage-the-suspect-pages-table-sql-server.md)  
  
  
