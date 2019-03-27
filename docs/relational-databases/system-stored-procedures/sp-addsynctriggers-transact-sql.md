---
title: sp_addsynctriggers (TRANSACT-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_addsynctriggers_TSQL
- sp_addsynctriggers
helpviewer_keywords:
- sp_addsynctriggers
ms.assetid: e37d0c3b-19bf-4719-9535-96ba361372b3
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 3ae733d560c227ccf282dfe4caed3935d9ffaebe
ms.sourcegitcommit: 2db83830514d23691b914466a314dfeb49094b3c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/27/2019
ms.locfileid: "58493645"
---
# <a name="spaddsynctriggers-transact-sql"></a>sp_addsynctriggers(Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  업데이트할 수 있는 모든 유형의 구독(즉시 업데이트, 대기 업데이트 및 장애 조치로 지연 업데이트를 사용하는 즉시 업데이트)에 사용되는 구독자에서 트리거를 만들 수 있습니다. 이 저장 프로시저는 구독 데이터베이스의 구독자에서 실행됩니다.  
  
> [!IMPORTANT]  
>  합니다 [sp_script_synctran_commands](../../relational-databases/system-stored-procedures/sp-script-synctran-commands-transact-sql.md) 프로시저를 대신 사용 해야 **sp_addsynctrigger**합니다. [sp_script_synctran_commands](../../relational-databases/system-stored-procedures/sp-script-synctran-commands-transact-sql.md) 포함 된 스크립트를 생성 합니다 **sp_addsynctrigger** 호출 합니다.  
  
 ![항목 링크 아이콘](../../database-engine/configure-windows/media/topic-link.gif "항목 링크 아이콘") [Transact-SQL 구문 규칙](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>구문  
  
```  
  
sp_addsynctriggers [ @sub_table = ] 'sub_table'  
        , [ @sub_table_owner = ] 'sub_table_owner'  
        , [ @publisher = ] 'publisher'  
        , [ @publisher_db = ] 'publisher_db'  
        , [ @publication = ] 'publication'   
        , [ @ins_proc = ] 'ins_proc'   
        , [ @upd_proc = ] 'upd_proc'   
        , [ @del_proc = ] 'del_proc'   
        , [ @cftproc = ] 'cftproc'  
        , [ @proc_owner = ] 'proc_owner'  
    [ , [ @identity_col = ] 'identity_col' ]  
    [ , [ @ts_col = ] 'timestamp_col' ]  
    [ , [ @filter_clause = ] 'filter_clause' ]   
        , [ @primary_key_bitmap = ] 'primary_key_bitmap'  
    [ , [ @identity_support = ] identity_support ]  
    [ , [ @independent_agent = ] independent_agent ]  
        , [ @distributor = ] 'distributor'   
    [ , [ @pubversion = ] pubversion  
```  
  
## <a name="arguments"></a>인수  
`[ @sub_table = ] 'sub_table'` 구독자 테이블의 이름이입니다. *sub_table* 됩니다 **sysname**, 기본값은 없습니다.  
  
`[ @sub_table_owner = ] 'sub_table_owner'` 구독자 테이블의 소유자 이름이입니다. *sub_table_owner* 됩니다 **sysname**, 기본값은 없습니다.  
  
`[ @publisher = ] 'publisher'` 게시자 서버의 이름이입니다. *게시자* 됩니다 **sysname**, 기본값은 없습니다.  
  
`[ @publisher_db = ] 'publisher_db'` 게시자 데이터베이스의 이름이입니다. *publisher_db* 됩니다 **sysname**, 기본값은 없습니다. NULL인 경우 현재 데이터베이스가 사용됩니다.  
  
`[ @publication = ] 'publication'` 게시의 이름이입니다. *게시* 됩니다 **sysname**, 기본값은 없습니다.  
  
`[ @ins_proc = ] 'ins_proc'` 게시자에서 동기 트랜잭션 삽입을 지 원하는 저장된 프로시저의 이름이입니다. *ins_proc* 됩니다 **sysname**, 기본값은 없습니다.  
  
`[ @upd_proc = ] 'upd_proc'` 게시자에서 동기 트랜잭션 업데이트를 지 원하는 저장된 프로시저의 이름이입니다. *ins_proc* 됩니다 **sysname**, 기본값은 없습니다.  
  
`[ @del_proc = ] 'del_proc'` 게시자에서 동기 트랜잭션 삭제를 지 원하는 저장된 프로시저의 이름이입니다. *ins_proc* 됩니다 **sysname**, 기본값은 없습니다.  
  
`[ @cftproc = ] 'cftproc'` 지연 업데이트를 허용 하는 게시에서 사용 하는 자동 생성 프로시저의 이름이입니다. *cftproc* 됩니다 **sysname**, 기본값은 없습니다. 즉시 업데이트를 허용하는 게시의 경우 이 값은 NULL입니다. 이 매개 변수는 지연 업데이트(지연 업데이트 및 장애 조치로 지연 업데이트를 사용하는 즉시 업데이트)를 허용하는 게시에 적용됩니다.  
  
`[ @proc_owner = ] 'proc_owner'` 업데이트 (지연 및/또는 즉시) 게시에 대 한 자동으로 생성 된 저장된 프로시저는 모든 게시자에서 생성 된 사용자 계정을 지정 합니다. *proc_owner* 됩니다 **sysname** 기본값은 없습니다.  
  
`[ @identity_col = ] 'identity_col'` 게시자에서 id 열의 이름이입니다. *identity_col* 됩니다 **sysname**, 기본값은 NULL입니다.  
  
`[ @ts_col = ] 'timestamp_col'` 이름인 합니다 **타임 스탬프** 게시자의 열입니다. *timestamp_col* 됩니다 **sysname**, 기본값은 NULL입니다.  
  
`[ @filter_clause = ] 'filter_clause'` 제한은 행 필터를 정의 하는 (WHERE) 절입니다. 제약 조건 절을 입력할 때는 키워드인 WHERE를 생략합니다. *filter_clause*됩니다 **nvarchar(4000)**, 기본값은 NULL입니다.  
  
`[ @primary_key_bitmap = ] 'primary_key_bitmap'` 테이블의 기본 키 열의 비트 맵입니다. *primary_key_bitmap* 됩니다 **varbinary(4000)**, 기본값은 없습니다.  
  
`[ @identity_support = ] identity_support` 사용 하도록 설정 하 고 지연 업데이트를 사용할 경우 자동 id 범위 처리를 사용 하지 않도록 설정 합니다. *identity_support* 되는 **비트**, 기본값은 **0**합니다. **0** id 임을 의미 지원 범위 **1** 자동 id 범위 처리를 사용 하도록 설정 합니다.  
  
`[ @independent_agent = ] independent_agent` 이 게시에 대 한 단일 배포 에이전트 (독립 에이전트) 또는 게시 데이터베이스 및 구독 데이터베이스 쌍 (공유 에이전트) 당 하나의 배포 에이전트가 있는지 여부를 나타냅니다. 이 값은 게시자에서 정의된 게시의 independent_agent 속성 값을 반영합니다. *independent_agent* 은 bit 이며 기본값은 **0**합니다. 하는 경우 **0**, 에이전트는 공유 에이전트입니다. 하는 경우 **1**, 에이전트는 독립 에이전트입니다.  
  
`[ @distributor = ] 'distributor'` 배포자의 이름이입니다. *배포자* 됩니다 **sysname**, 기본값은 없습니다.  
  
`[ @pubversion = ] pubversion` 게시자의 버전을 나타냅니다. *pubversion* 됩니다 **int**, 기본값은 1입니다. **1** 게시자 버전은 즉 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] 서비스 팩 2 또는 이전 **2** 게시자가 즉 [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] 서비스 팩 3(sp3) 이상. *pubversion* 으로 명시적으로 설정 되어 있어야 **2** 게시자 버전 경우 [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] SP3 이상.  
  
## <a name="return-code-values"></a>반환 코드 값  
 **0** (성공) 또는 **1** (실패)  
  
## <a name="remarks"></a>Remarks  
 **sp_addsynctriggers** 구독 초기화의 일부로 배포 에이전트에서 사용 됩니다. 일반적으로 사용자는 이 저장 프로시저를 실행하지 않지만 no-sync 구독을 수동으로 설정해야 하는 경우 유용할 수 있습니다.  
  
## <a name="permissions"></a>사용 권한  
 멤버는 **sysadmin** 고정된 서버 역할 또는 **db_owner** 고정된 데이터베이스 역할을 실행할 수 있습니다 **sp_addsynctriggers**합니다.  
  
## <a name="see-also"></a>관련 항목  
 [Updatable Subscriptions for Transactional Replication](../../relational-databases/replication/transactional/updatable-subscriptions-for-transactional-replication.md)   
 [sp_script_synctran_commands &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-script-synctran-commands-transact-sql.md)   
 [시스템 저장 프로시저&#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
