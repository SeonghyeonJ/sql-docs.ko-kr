---
title: sp_browsereplcmds (TRANSACT-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_browsereplcmds_TSQL
- sp_browsereplcmds
helpviewer_keywords:
- sp_browsereplcmds
ms.assetid: 30abcb41-1d18-4f43-a692-4c80914c0450
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 7918e257428fd85ddb54867ee5144f45a3bf89f1
ms.sourcegitcommit: 2db83830514d23691b914466a314dfeb49094b3c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/27/2019
ms.locfileid: "58493845"
---
# <a name="spbrowsereplcmds-transact-sql"></a>sp_browsereplcmds(Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  배포 데이터베이스에 복제되어 저장된 결과 집합을 읽을 수 있는 버전으로 반환합니다. 이 결과 집합은 진단 도구에서 사용됩니다. 이 저장 프로시저는 배포 데이터베이스의 배포자에서 실행됩니다.  
  
 ![항목 링크 아이콘](../../database-engine/configure-windows/media/topic-link.gif "항목 링크 아이콘") [Transact-SQL 구문 규칙](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>구문  
  
```  
  
sp_browsereplcmds [ [ @xact_seqno_start = ] 'xact_seqno_start' ]  
    [ , [ @xact_seqno_end = ] 'xact_seqno_end' ]   
    [ , [ @originator_id = ] 'originator_id' ]  
    [ , [ @publisher_database_id = ] 'publisher_database_id' ]  
    [ , [ @article_id = ] 'article_id' ]  
    [ , [ @command_id= ] command_id ]  
    [ , [ @agent_id = ] agent_id ]  
    [ , [ @compatibility_level = ] compatibility_level ]  
```  
  
## <a name="arguments"></a>인수  
`[ @xact_seqno_start = ] 'xact_seqno_start'` 반환할 가장 낮은 값된 정확한 시퀀스 번호를 지정 합니다. *xact_seqno_start* 됩니다 **nchar(22)**, 기본값은 0x00000000000000000000입니다.  
  
`[ @xact_seqno_end = ] 'xact_seqno_end'` 반환할 가장 높은 정확한 시퀀스 번호를 지정 합니다. *xact_seqno_end* 됩니다 **nchar(22)**, 기본값은 0xFFFFFFFFFFFFFFFFFFFF입니다.  
  
`[ @originator_id = ] 'originator_id'` 지정 된 명령을 *originator_id* 반환 됩니다. *originator_id* 됩니다 **int**, 기본값은 NULL입니다.  
  
`[ @publisher_database_id = ] 'publisher_database_id'` 지정 된 명령을 *publisher_database_id* 반환 됩니다. *publisher_database_id* 됩니다 **int**, 기본값은 NULL입니다.  
  
`[ @article_id = ] 'article_id'` 지정 된 명령을 *article_id* 반환 됩니다. *article_id* 됩니다 **int**, 기본값은 NULL입니다.  
  
`[ @command_id = ] command_id` 명령의 위치인 [MSrepl_commands &#40;TRANSACT-SQL&#41; ](../../relational-databases/system-tables/msrepl-commands-transact-sql.md) 디코딩할 합니다. *command_id* 됩니다 **int**, 기본값은 NULL입니다. 지정 하는 경우 다른 모든 매개 변수 또한 지정 해야 하 고 *xact_seqno_start*같아야 *xact_seqno_end*.  
  
`[ @agent_id = ] agent_id` 특정 복제 에이전트에 대 한 명령만 반환 되도록 지정 합니다. *agent_id* 됩니다 **int**, 기본값은 NULL입니다.  
  
`[ @compatibility_level = ] compatibility_level` 버전이 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 기반이 *compatibility_level* 은 **int**, 이며 기본값은 9000000입니다.  
  
## <a name="return-code-values"></a>반환 코드 값  
 **0** (성공) 또는 **1** (실패)  
  
## <a name="result-sets"></a>결과 집합  
  
|열 이름|데이터 형식|Description|  
|-----------------|---------------|-----------------|  
|**xact_seqno**|**varbinary(16)**|명령의 시퀀스 번호입니다.|  
|**originator_srvname**|**sysname**|트랜잭션이 시작된 서버입니다.|  
|**originator_db**|**sysname**|트랜잭션이 시작된 데이터베이스입니다.|  
|**article_id**|**int**|아티클의 ID입니다.|  
|**type**|**int**|명령의 유형입니다.|  
|**partial_command**|**bit**|부분 명령인지 여부를 나타냅니다.|  
|**hashkey**|**int**|내부적으로만 사용됩니다.|  
|**originator_publication_id**|**int**|트랜잭션이 시작된 게시의 ID입니다.|  
|**originator_db_version**|**int**|트랜잭션이 시작된 데이터베이스의 버전입니다.|  
|**originator_lsn**|**varbinary(16)**|원본 게시에서 명령의 LSN(로그 시퀀스 번호)을 식별합니다. 피어 투 피어 트랜잭션 복제에 사용됩니다.|  
|**명령**|**nvarchar(1024)**|[!INCLUDE[tsql](../../includes/tsql-md.md)] 명령입니다.|  
|**command_id**|**int**|명령 ID [MSrepl_commands](../../relational-databases/system-tables/msrepl-commands-transact-sql.md)합니다.|  
  
 긴 명령은 결과 집합에서 여러 행으로 분할될 수 있습니다.  
  
## <a name="remarks"></a>Remarks  
 **sp_browsereplcmds** 트랜잭션 복제에 사용 됩니다.  
  
## <a name="permissions"></a>사용 권한  
 멤버만 합니다 **sysadmin** 고정 서버 역할의 멤버는 **db_owner** 하거나 **replmonitor** 배포 데이터베이스의 고정된 데이터베이스 역할 실행할수있습니다**sp_browsereplcmds**합니다.  
  
## <a name="see-also"></a>관련 항목  
 [sp_replcmds&#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-replcmds-transact-sql.md)   
 [sp_replshowcmds &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-replshowcmds-transact-sql.md)   
 [시스템 저장 프로시저&#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
