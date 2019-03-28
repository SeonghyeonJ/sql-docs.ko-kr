---
title: sp_update_proxy (TRANSACT-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_update_proxy
- sp_update_proxy_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- ALTER PROXY statement
- sp_update_proxy
ms.assetid: 864fd0e6-9d61-4f07-92ef-145318d2f881
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: 29a95b506fbbfb5342410d8d393f0091dd98834b
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/27/2019
ms.locfileid: "58534465"
---
# <a name="spupdateproxy-transact-sql"></a>sp_update_proxy(Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  기존 프록시의 속성을 변경합니다.  
  
 ![항목 링크 아이콘](../../database-engine/configure-windows/media/topic-link.gif "항목 링크 아이콘") [Transact-SQL 구문 규칙](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>구문  
  
```  
  
sp_update_proxy   
    [ @proxy_id = ] id,  
    [ @proxy_name = ] 'proxy_name',  
    [ @credential_name = ] 'credential_name' ,  
    [ @credential_id = ] credential_id ,  
    [ @new_name = ] 'new_name' ,  
    [ @enabled = ] is_enabled ,  
    [ @description = ] 'description'  
```  
  
## <a name="arguments"></a>인수  
`[ @proxy_id = ] id` 변경할 프록시의 프록시 id. 합니다 *proxy_id* 됩니다 **int**, 기본값은 NULL 사용 하 여 합니다.  
  
`[ @proxy_name = ] 'proxy_name'` 변경할 프록시의 이름입니다. 합니다 *proxy_name* 됩니다 **sysname**, 기본값은 NULL 사용 하 여 합니다.  
  
`[ @credential_name = ] 'credential_name'` 프록시에 대 한 새 자격 증명의 이름입니다. 합니다 *credential_name* 됩니다 **sysname**, 기본값은 NULL 사용 하 여 합니다. 어느 *credential_name* 하거나 *credential_id* 지정할 수 있습니다.  
  
`[ @credential_id = ] credential_id` 프록시에 대 한 새 자격 증명의 id. 합니다 *credential_id* 됩니다 **int**, 기본값은 NULL 사용 하 여 합니다. 어느 *credential_name* 하거나 *credential_id* 지정할 수 있습니다.  
  
`[ @new_name = ] 'new_name'` 프록시의 새 이름입니다. 합니다 *new_name* 됩니다 **sysname**, 기본값은 NULL 사용 하 여 합니다. 프로시저 변경 프록시의 이름을 제공 하면 *new_name*합니다. 이 인수가 NULL이면 프록시의 이름은 변경되지 않은 상태로 유지됩니다.  
  
`[ @enabled = ] is_enabled` 프록시 사용 여부입니다. *is_enabled* 플래그가 **tinyint**, 기본값은 NULL입니다. 때 *is_enabled* 됩니다 **0**, 프록시를 사용 하지 않는 및 작업 단계에서 사용할 수 없습니다. 이 인수가 NULL이면 프록시의 상태는 변경되지 않은 상태로 유지됩니다.  
  
`[ @description = ] 'description'` 프록시의 새 설명입니다. *설명을* 됩니다 **nvarchar(512)**, 기본값은 NULL 사용 하 여 합니다. 이 인수가 NULL이면 프록시에 대한 설명은 변경되지 않은 상태로 유지됩니다.  
  
## <a name="return-code-values"></a>반환 코드 값  
 **0** (성공) 또는 **1** (실패)  
  
## <a name="remarks"></a>Remarks  
 어느 **@proxy_name** 하거나 **@proxy_id** 지정 해야 합니다. 두 인수가 모두 지정될 경우 두 인수는 같은 프록시를 참조해야 합니다. 그렇지 않으면 저장 프로시저가 실패합니다.  
  
 어느 **@credential_name** 하거나 **@credential_id** 프록시에 대 한 자격 증명을 변경 하려면 반드시 지정 해야 합니다. 두 인수를 모두 지정하면 두 인수는 같은 자격 증명을 참조해야 합니다. 그렇지 않으면 저장 프로시저가 실패합니다.  
  
 이 프로시저는 프록시를 변경하지만 프록시에 대한 액세스 권한은 변경하지 않습니다. 프록시에 대 한 액세스를 변경 하려면 사용 하 여 **sp_grant_login_to_proxy** 하 고 **sp_revoke_login_from_proxy**합니다.  
  
## <a name="permissions"></a>사용 권한  
 멤버는 **sysadmin** 고정된 보안 역할에서이 프로시저를 실행할 수 있습니다.  
  
## <a name="examples"></a>예  
 다음 예에서는 프록시 `Catalog application proxy`에 설정된 값을 `0`으로 설정합니다.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_update_proxy  
    @proxy_name = 'Catalog application proxy',  
    @enabled = 0;  
GO  
```  
  
## <a name="see-also"></a>관련 항목  
 [SQL Server 에이전트 저장 프로시저 &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sql-server-agent-stored-procedures-transact-sql.md)   
 [SQL Server 에이전트 보안 구현](../../ssms/agent/implement-sql-server-agent-security.md)   
 [sp_add_proxy &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-proxy-transact-sql.md)   
 [sp_delete_proxy &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-proxy-transact-sql.md)   
 [sp_grant_login_to_proxy &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-grant-login-to-proxy-transact-sql.md)   
 [sp_revoke_login_from_proxy &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-revoke-login-from-proxy-transact-sql.md)  
  
  
