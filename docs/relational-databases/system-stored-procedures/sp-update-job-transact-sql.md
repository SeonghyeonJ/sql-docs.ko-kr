---
title: sp_update_job (TRANSACT-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_update_job
- sp_update_job_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_update_job
ms.assetid: cbdfea38-9e42-47f3-8fc8-5978b82e2623
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: c12e078505c8049511e59973c26d6a1417c7eae0
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/27/2019
ms.locfileid: "58537855"
---
# <a name="spupdatejob-transact-sql"></a>sp_update_job(Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  작업의 특성을 변경합니다.  
  

  
 ![항목 링크 아이콘](../../database-engine/configure-windows/media/topic-link.gif "항목 링크 아이콘") [Transact-SQL 구문 규칙](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>구문  
  
```  
  
sp_update_job [ @job_id =] job_id | [@job_name =] 'job_name'  
     [, [@new_name =] 'new_name' ]   
     [, [@enabled =] enabled ]  
     [, [@description =] 'description' ]   
     [, [@start_step_id =] step_id ]  
     [, [@category_name =] 'category' ]   
     [, [@owner_login_name =] 'login' ]  
     [, [@notify_level_eventlog =] eventlog_level ]  
     [, [@notify_level_email =] email_level ]  
     [, [@notify_level_netsend =] netsend_level ]  
     [, [@notify_level_page =] page_level ]  
     [, [@notify_email_operator_name =] 'operator_name' ]  
     [, [@notify_netsend_operator_name =] 'netsend_operator' ]  
     [, [@notify_page_operator_name =] 'page_operator' ]  
     [, [@delete_level =] delete_level ]   
     [, [@automatic_post =] automatic_post ]  
```  
  
## <a name="arguments"></a>인수  
`[ @job_id = ] job_id` 업데이트할 작업의 id. *job_id*됩니다 **uniqueidentifier**합니다.  
  
`[ @job_name = ] 'job_name'` 작업의 이름입니다. *job_name* 됩니다 **nvarchar (128)** 합니다.  
  
> **참고:** 어느 *job_id* 또는 *job_name* 지정 해야 하지만 둘 다 지정할 수 없습니다.  
  
`[ @new_name = ] 'new_name'` 작업에 대 한 새 이름입니다. *new_name* 됩니다 **nvarchar (128)** 합니다.  
  
`[ @enabled = ] enabled` 작업이 사용 되는지 여부를 지정 합니다 (**1**) 또는 사용 안 함 (**0**). *사용 하도록 설정* 됩니다 **tinyint**합니다.  
  
`[ @description = ] 'description'` 작업의 설명입니다. *설명을* 됩니다 **nvarchar(512)** 합니다.  
  
`[ @start_step_id = ] step_id` 작업에 대해 실행 될 첫 번째 단계의 id. *step_id* 됩니다 **int**합니다.  
  
`[ @category_name = ] 'category'` 작업의 범주입니다. *범주* 됩니다 **nvarchar (128)** 합니다.  
  
`[ @owner_login_name = ] 'login'` 작업을 소유한 로그인의 이름입니다. *로그인* 됩니다 **nvarchar (128)** 의 구성원만 합니다 **sysadmin** 고정된 서버 역할 작업 소유권을 변경할 수 있습니다.  
  
`[ @notify_level_eventlog = ] eventlog_level` 이 작업에 대 한 Microsoft Windows 응용 프로그램 로그에 항목을 저장 하는 시기를 지정 합니다. *eventlog_level*됩니다 **int**, 이며 다음이 값 중 하나일 수 있습니다.  
  
|값|설명(동작)|  
|-----------|----------------------------|  
|**0**|안 함|  
|**1**|성공한 경우|  
|**2**|실패한 경우|  
|**3**|Always|  
  
`[ @notify_level_email = ] email_level` 이 작업이 완료 될 때 전자 메일을 보낼 시기를 지정 합니다. *email_level*됩니다 **int**합니다. *email_level*과 같은 값을 사용 하 여 *eventlog_level*합니다.  
  
`[ @notify_level_netsend = ] netsend_level` 이 작업 완료 시 네트워크 메시지를 보낼 시기를 지정 합니다. *netsend_level*됩니다 **int**합니다. *netsend_level*과 같은 값을 사용 하 여 *eventlog_level*합니다.  
  
`[ @notify_level_page = ] page_level` 이 작업이 완료 되 면 페이지를 보낼 시기를 지정 합니다. *page_level* 됩니다 **int**합니다. *page_level*과 같은 값을 사용 하 여 *eventlog_level*합니다.  
  
`[ @notify_email_operator_name = ] 'operator_name'` 받을 전자 메일은 때 운영자의 이름을 *email_level* 에 도달 합니다. *email_name* 됩니다 **nvarchar (128)** 합니다.  
  
`[ @notify_netsend_operator_name = ] 'netsend_operator'` 네트워크 메시지를 받을 운영자의 이름입니다. *netsend_operator* 됩니다 **nvarchar (128)** 합니다.  
  
`[ @notify_page_operator_name = ] 'page_operator'` 페이지를 받을 운영자의 이름입니다. *page_operator* 됩니다 **nvarchar (128)** 합니다.  
  
`[ @delete_level = ] delete_level` 작업 삭제 시기를 지정 합니다. *delete_value*됩니다 **int**합니다. *delete_level*과 같은 값을 사용 하 여 *eventlog_level*합니다.  
  
`[ @automatic_post = ] automatic_post` 예약 되어 있습니다.  
  
## <a name="return-code-values"></a>반환 코드 값  
 **0** (성공) 또는 **1** (실패)  
  
## <a name="remarks"></a>Remarks  
 **sp_update_job** 에서 실행 해야 합니다 **msdb** 데이터베이스입니다.  
  
 **sp_update_job** 매개 변수 값이 제공 되는 설정만 변경 합니다. 매개 변수가 생략되면 현재 설정이 보존됩니다.  
  
## <a name="permissions"></a>사용 권한  
 기본적으로 **sysadmin** 고정 서버 역할의 멤버는 이 저장 프로시저를 실행할 수 있습니다. 다른 사용자는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] msdb **데이터베이스의 다음** 에이전트 고정 데이터베이스 역할 중 하나를 부여 받아야 합니다.  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 이러한 역할의 사용 권한에 대한 자세한 내용은 [SQL Server 에이전트 고정 데이터베이스 역할](../../ssms/agent/sql-server-agent-fixed-database-roles.md)을 참조하세요.  
  
 멤버만 **sysadmin** 이 저장된 프로시저를 사용 하 여 다른 사용자가 소유한 작업의 속성을 편집할 수 있습니다.  
  
## <a name="examples"></a>예  
 다음 예에서는 `NightlyBackups` 작업의 이름, 설명 및 활성화 상태를 변경합니다.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_update_job  
    @job_name = N'NightlyBackups',  
    @new_name = N'NightlyBackups -- Disabled',  
    @description = N'Nightly backups disabled during server migration.',  
    @enabled = 0 ;  
GO  
```  
  
## <a name="see-also"></a>관련 항목  
 [sp_add_job&#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-job-transact-sql.md)   
 [sp_delete_job &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-job-transact-sql.md)   
 [sp_help_job &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-job-transact-sql.md)   
 [시스템 저장 프로시저&#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
