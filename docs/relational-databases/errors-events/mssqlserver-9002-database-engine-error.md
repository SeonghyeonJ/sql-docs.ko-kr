---
title: MSSQLSERVER_9002 | Microsoft 문서
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 9002 (Database Engine error)
ms.assetid: 2e50841f-2b99-45f4-aec5-aa4add70cbeb
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 3397d8fc1fbf271ab3bd8032ae14c7d9b61b6020
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68118357"
---
# <a name="mssqlserver9002"></a>MSSQLSERVER_9002
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>세부 정보  
  
|||  
|-|-|  
|제품 이름|SQL Server|  
|이벤트 ID|9002|  
|이벤트 원본|MSSQLSERVER|  
|구성 요소|SQLEngine|  
|심볼 이름|LOG_IS_FULL|  
|메시지 텍스트|데이터베이스 '%.*ls'의 트랜잭션 로그가 꽉 찼습니다. 로그의 공간을 다시 사용할 수 없는 이유를 확인하려면 sys.databases의 log_reuse_wait_desc 열을 참조하십시오.|  
  
## <a name="explanation"></a>설명  
데이터베이스 로그에 공간이 부족합니다. **sys.databases**의 **log_reuse_wait_desc** 열을 확인하여 로그의 공간을 다시 사용할 수 없는 이유를 알 수 있습니다.  
  
## <a name="user-action"></a>사용자 동작  
**sys.databases**를 사용하여 로그가 꽉 찬 이유를 확인하고 문제를 해결하세요. 자세한 내용은 SQL Server 온라인 설명서의 "꽉 찬 트랜잭션 로그 문제 해결(오류 9002)"을 참조하십시오.  
  
## <a name="see-also"></a>참고 항목  
[꽉 찬 트랜잭션 로그 문제 해결&#40;SQL Server 오류 9002&#41;](~/relational-databases/logs/troubleshoot-a-full-transaction-log-sql-server-error-9002.md)  
[sys.databases&#40;Transact-SQL&#41;](~/relational-databases/system-catalog-views/sys-databases-transact-sql.md)  
  
