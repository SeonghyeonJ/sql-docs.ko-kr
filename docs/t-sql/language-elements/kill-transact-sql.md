---
title: KILL (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 08/31/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- KILL_TSQL
- KILL
dev_langs:
- TSQL
helpviewer_keywords:
- WITH STATUSONLY option
- terminating distributed transactions
- distributed transactions [SQL Server], terminating
- in-doubt transactions
- IDs [SQL Server], user processes
- ending distributed transactions [SQL Server]
- stopping distributed transactions
- session IDs [SQL Server]
- system process termination [SQL Server]
- stopping processes
- ending processes [SQL Server]
- UOW [SQL Server]
- orphaned transactions [SQL Server]
- unit of work [SQL Server]
- process termination [SQL Server]
- KILL statement
- terminating process
ms.assetid: 071cf260-c794-4b45-adc0-0e64097938c0
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: be0bccac59c011fc36e8481029d9951cd36cad99
ms.sourcegitcommit: 6443f9a281904af93f0f5b78760b1c68901b7b8d
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53205402"
---
# <a name="kill-transact-sql"></a>KILL(Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  세션 ID 또는 작업 단위(UOW)를 기반으로 하는 사용자 프로세스를 종료합니다. 지정한 세션 ID 또는 UOW에 실행 취소할 작업이 많고 특히 긴 트랜잭션을 롤백하는 경우 KILL 문을 완료하는 데 시간이 걸릴 수도 있습니다.  
  
 KILL을 사용하여 정상적인 연결을 종료할 수 있습니다. 이 경우 내부적으로는 지정한 세션 ID와 연결된 트랜잭션이 종료됩니다. MS DTC([!INCLUDE[msCoName](../../includes/msconame-md.md)] Distributed Transaction Coordinator)를 사용하는 경우 이 문을 사용하여 분리되거나 미결인 분산 트랜잭션을 종료할 수도 있습니다.  
  
 ![항목 링크 아이콘](../../database-engine/configure-windows/media/topic-link.gif "항목 링크 아이콘") [Transact-SQL 구문 규칙](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>구문  
  
```  
-- Syntax for SQL Server  
  
KILL { session ID | UOW } [ WITH STATUSONLY ]   
```  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
KILL 'session_id'  
[;]   
```  
  
## <a name="arguments"></a>인수  
 *session ID*  
 종료할 프로세스의 세션 ID입니다. *session ID*는 사용자가 연결할 때 각 연결에 할당된 고유한 정수(**int**)입니다. 세션 ID 값은 연결되어 있는 동안 해당 연결에 대해 유지됩니다. 연결이 종료되면 이 정수 값은 해제되어 새 연결에 다시 할당될 수 있습니다.  
다음 쿼리는 중지하려는 `session_id`를 식별하는 데 유용할 수 있습니다.  
 ```sql  
 SELECT conn.session_id, host_name, program_name,
     nt_domain, login_name, connect_time, last_request_end_time 
FROM sys.dm_exec_sessions AS sess
JOIN sys.dm_exec_connections AS conn
    ON sess.session_id = conn.session_id;
```  
  
*UOW*  
**적용 대상**: ([!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] ~ [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]
  
 분산 트랜잭션의 UOW(작업 단위) ID를 식별합니다. *UOW*는 sys.dm_tran_locks 동적 관리 뷰의 request_owner_guid 열에서 구할 수 있는 GUID입니다. *UOW*는 오류 로그나 MS DTC 모니터를 통해 가져올 수도 있습니다. 분산 트랜잭션 모니터링 방법은 MS DTC 설명서를 참조하세요.  
  
 KILL *UOW*를 사용하여 분리된 분산 트랜잭션을 종료합니다. 이러한 트랜잭션은 실제 세션 ID에 연결되어 있지 않고 대신 세션 ID='-2'에 인위적으로 연결되어 있습니다. 이 세션 ID를 사용하면 sys.dm_tran_locks, sys.dm_exec_sessions 또는 sys.dm_exec_requests 동적 관리 뷰의 세션 ID 열을 쿼리하여 분리된 트랜잭션을 쉽게 식별할 수 있습니다.  
  
 WITH STATUSONLY  
 이전 KILL 문으로 인해 롤백되고 있는 지정한 *session ID* 또는 *UOW*에 대한 진행률 보고서를 생성합니다. KILL WITH STATUSONLY는 *session ID* 또는 *UOW*를 종료하거나 롤백하지 않으며 롤백의 현재 진행률만 표시합니다.  
  
## <a name="remarks"></a>Remarks  
 KILL은 잠금으로 다른 중요한 프로세스를 차단하는 프로세스를 종료할 때 또는 필요한 시스템 리소스를 사용하는 쿼리를 실행하는 프로세스를 종료할 때 주로 사용됩니다. 시스템 프로세스와 확장 저장 프로시저를 실행하는 프로세스는 종료될 수 없습니다.  
  
 특히 중요한 프로세스가 실행 중일 때는 KILL을 신중하게 사용하세요. 자신의 프로세스를 중지할 수는 없으며 중지할 수 없는 그 밖의 프로세스는 다음과 같습니다.  
  
-   AWAITING COMMAND  
-   CHECKPOINT SLEEP  
-   LAZY WRITER  
-   LOCK MONITOR  
-   SIGNAL HANDLER  
  
@@SPID를 사용하여 현재 세션에 대한 세션 ID 값을 표시할 수 있습니다.  
  
 활성 세션 ID 값에 대한 보고를 가져오려면 sys.dm_tran_locks, sys.dm_exec_sessions 및 sys.dm_exec_requests 동적 관리 뷰의 session_id 열을 쿼리할 수 있습니다. sp_who 시스템 저장 프로시저에서 반환된 SPID 열을 확인할 수도 있습니다. 특정 SPID에 대해 롤백이 진행 중인 경우 특정 SPID에 대한 sp_who 결과 집합의 cmd 열에 KILLED/ROLLBACK이 표시됩니다.  
  
 특정 연결에 데이터베이스 리소스에 대한 잠금이 있으며 다른 연결의 진행률을 차단하는 경우 차단하는 연결의 세션 ID가 `blocking_session_id`의 `sys.dm_exec_requests` 열이나 `blk`에서 반환된 `sp_who` 열에 표시됩니다.  
  
 KILL 명령을 사용하여 미결 분산 트랜잭션을 확인할 수 있습니다. 이러한 트랜잭션은 데이터베이스 서버나 MS DTC 코디네이터의 계획되지 않은 다시 시작으로 인해 발생하는 확인되지 않은 분산 트랜잭션입니다. 미결 트랜잭션에 대한 자세한 내용은 [표시된 트랜잭션을 사용하여 관련 데이터베이스를 일관되게 복구&#40;전체 복구 모델&#41;](../../relational-databases/backup-restore/use-marked-transactions-to-recover-related-databases-consistently.md)을 참조하세요.  
  
## <a name="using-with-statusonly"></a>WITH STATUSONLY 사용  
 KILL WITH STATUSONLY는 세션 ID 또는 UOW가 이전 KILL *session ID*|*UOW* 문으로 인해 현재 롤백되고 있는 경우에만 보고서를 생성합니다. 진행률 보고서는 완료된 롤백 양(백분율)과 남은 예상 시간(초)을 다음과 같은 형식으로 제공합니다.  
  
 `Spid|UOW <xxx>: Transaction rollback in progress. Estimated rollback completion: <yy>% Estimated time left: <zz> seconds`  
  
 KILL *session ID*|*UOW* WITH STATUSONLY 문을 실행할 때 세션 ID 또는 UOW의 롤백이 이미 완료되었거나 세션 ID 또는 UOW가 롤백되고 있지 않은 경우 KILL *세션 ID*|*UOW* WITH STATUSONLY는 다음 오류를 반환합니다.  
  
 ```
"Msg 6120, Level 16, State 1, Line 1"  
"Status report cannot be obtained. Rollback operation for Process ID <session ID> is not in progress."
```  
  
 같은 KILL *session ID*|*UOW* 문을 WITH STATUSONLY 옵션 없이 반복하면 동일한 상태 보고를 가져올 수 있지만 이 방법은 사용하지 않는 것이 좋습니다. KILL *session ID* 문이 실행되기 전에 롤백이 완료되고 세션 ID가 새 태스크에 다시 할당된 경우 KILL 문을 반복하면 새 프로세스를 종료할 수 있습니다. WITH STATUSONLY를 지정하면 이런 경우가 발생하는 것을 방지할 수 있습니다.  
  
## <a name="permissions"></a>Permissions  
 **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:** ALTER ANY CONNECTION 권한이 필요합니다. ALTER ANY CONNECTION은 sysadmin 또는 processadmin 고정 서버 역할의 멤버에 포함되어 있습니다.  
  
 **[!INCLUDE[ssSDS](../../includes/sssds-md.md)]:** KILL DATABASE CONNECTION 권한이 필요합니다. 서버 수준 보안 주체 로그인에 KILL DATABASE CONNECTION이 있습니다.  
  
## <a name="examples"></a>예  
  
### <a name="a-using-kill-to-terminate-a-session"></a>1. KILL을 사용하여 세션 종료  
 다음 예에서는 세션 ID `53`을 종료하는 방법을 보여 줍니다.  
  
```sql  
KILL 53;  
GO  
```  
  
### <a name="b-using-kill-session-id-with-statusonly-to-obtain-a-progress-report"></a>2. KILL 세션 ID WITH STATUSONLY를 사용하여 진행률 보고서 가져오기  
 다음 예에서는 특정 세션 ID에 대한 롤백 진행 상황을 표시합니다.  
  
```sql  
KILL 54;  
KILL 54 WITH STATUSONLY;  
GO  
  
--This is the progress report.  
spid 54: Transaction rollback in progress. Estimated rollback completion: 80% Estimated time left: 10 seconds.  
```  
  
### <a name="c-using-kill-to-terminate-an-orphaned-distributed-transaction"></a>3. KILL을 사용하여 분리된 분산 트랜잭션 종료  
 다음 예에서는 `D5499C66-E398-45CA-BF7E-DC9C194B48CF`의 *UOW*를 사용하여 분리된 분산 트랜잭션(세션 ID = -2)을 종료하는 방법을 보여 줍니다.  
  
```sql  
KILL 'D5499C66-E398-45CA-BF7E-DC9C194B48CF';  
```  

  
## <a name="see-also"></a>참고 항목  
 [KILL STATS JOB &#40;Transact-SQL&#41;](../../t-sql/language-elements/kill-stats-job-transact-sql.md)   
 [KILL QUERY NOTIFICATION SUBSCRIPTION&#40;Transact-SQL&#41;](../../t-sql/language-elements/kill-query-notification-subscription-transact-sql.md)   
 [기본 제공 함수s&#40;Transact-SQL&#41;](~/t-sql/functions/functions.md)   
 [SHUTDOWN &#40;Transact-SQL&#41;](../../t-sql/language-elements/shutdown-transact-sql.md)   
 [@@SPID&#40;Transact-SQL&#41;](../../t-sql/functions/spid-transact-sql.md)   
 [sys.dm_exec_requests &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md)   
 [sys.dm_exec_sessions &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-sessions-transact-sql.md)   
 [sys.dm_tran_locks &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-tran-locks-transact-sql.md)   
 [sp_lock &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-lock-transact-sql.md)   
 [sp_who&#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-who-transact-sql.md)  
  
  
