---
title: MSSQLSERVER_926 | Microsoft 문서
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 926 (Database Engine error)
ms.assetid: 57e01668-883b-4be4-84a8-a111caaf0486
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 4afdc9adae6f968ca89ff1a9b2bf9e5b67992037
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2020
ms.locfileid: "62912475"
---
# <a name="mssqlserver_926"></a>MSSQLSERVER_926
    
## <a name="details"></a>세부 정보  
  
|||  
|-|-|  
|제품 이름|SQL Server|  
|이벤트 ID|926|  
|이벤트 원본|MSSQLSERVER|  
|구성 요소|SQLEngine|  
|심볼 이름|DB_SUSPECT|  
|메시지 텍스트|데이터베이스 '%.*ls'을(를) 열 수 없습니다. 복구에 의해 주의 대상으로 표시되었습니다. 자세한 내용은 SQL Server 오류 로그를 참조하십시오.|  
  
## <a name="explanation"></a>설명  
 데이터베이스를 일관성 있는 트랜잭션 상태가 되게 하는 복구 프로세스가 실패했으므로 데이터베이스가 주의 대상으로 표시됩니다. 이 문제는 다음 작업에서 발생할 수 있습니다.  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]의 인스턴스 시작  
  
-   데이터베이스 연결  
  
-   RESTORE 데이터베이스 또는 RESTORE LOG 프로시저 사용  
  
## <a name="user-action"></a>사용자 동작  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]오류 로그를 검사하여 오류의 원인을 확인합니다. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]가 실패한 복구로 인해 다시 시작된 경우 복구 실패 원인을 보려면 이전의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 오류 로그를 참조하십시오.  
  
 지속적인 I/O 오류, 조각난 페이지 또는 다른 가능한 하드웨어 문제로 인해 복구가 실패한 경우 기본 하드웨어 문제를 해결하고 백업을 사용하여 데이터베이스를 복원하십시오. 백업을 사용할 수 없는 경우 DBCC CHECKDB의 복구 옵션을 고려하십시오.  
  
 이 문제를 해결할 수 없으면 주 지원 공급자에게 문의하십시오. 검토에 사용할 수 있는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 오류 로그를 보관하십시오.  
  
## <a name="see-also"></a>참고 항목  
 [SQL Server 데이터베이스 백업 및 복원](../backup-restore/back-up-and-restore-of-sql-server-databases.md)   
 [RESTORE&#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql)   
 [sysdatabases &#40;Transact-sql&#41;](/sql/relational-databases/system-compatibility-views/sys-sysdatabases-transact-sql)   
 [데이터베이스 분리 및 연결&#40;SQL Server&#41;](../../relational-databases/databases/database-detach-and-attach-sql-server.md)  
  
  
