---
title: sp_syspolicy_add_policy_category_subscription (TRANSACT-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_syspolicy_add_policy_category_subscription
- sp_syspolicy_add_policy_category_subscription_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_syspolicy_add_policy_category_subscription
ms.assetid: 4284f550-9a3f-4726-8181-15e407fbf08f
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 795a806b1b945407a2db947f6037c435efe68b56
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68010516"
---
# <a name="spsyspolicyaddpolicycategorysubscription-transact-sql"></a>sp_syspolicy_add_policy_category_subscription(Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  지정된 데이터베이스에 정책 범주 구독을 추가합니다.  
  
 ![항목 링크 아이콘](../../database-engine/configure-windows/media/topic-link.gif "항목 링크 아이콘") [Transact-SQL 구문 규칙](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>구문  
  
```  
  
sp_syspolicy_add_policy_category_subscription [ @target_type = ] 'target_type'  
    , [ @target_object = ] 'target_object'  
    , [ @policy_category = ] 'policy_category'  
    [ , [ @policy_category_subscription_id = ] policy_category_subscription_id OUTPUT ]  
```  
  
## <a name="arguments"></a>인수  
`[ @target_type = ] 'target_type'` 범주 구독의 대상 유형이입니다. *target_type* 됩니다 **sysname**고, 필요 하며, 'DATABASE'로 설정 되어야 합니다.  
  
`[ @target_object = ] 'target_object'` 범주를 구독할 데이터베이스의 이름이입니다. *target_object* 됩니다 **sysname**, 이며 반드시 지정 해야 합니다.  
  
`[ @policy_category = ] 'policy_category'` 구독할 정책 범주의 이름이입니다. *policy_category* 됩니다 **sysname**, 이며 반드시 지정 해야 합니다.  
  
 값을 얻으려면 *policy_category*, msdb.dbo.syspolicy_policy_categories 시스템 뷰를 쿼리 합니다.  
  
`[ @policy_category_subscription_id = ] policy_category_subscription_id` 범주 구독의 식별자가입니다. *policy_category_subscription_id* 됩니다 **int**, 이며 OUTPUT으로 반환 됩니다.  
  
## <a name="return-code-values"></a>반환 코드 값  
 **0** (성공) 또는 **1** (실패)  
  
## <a name="remarks"></a>설명  
 sp_syspolicy_add_policy_category_subscription은 msdb 시스템 데이터베이스의 컨텍스트에서 실행해야 합니다.  
  
 없는 정책 범주를 지정하면 새 정책 범주가 만들어지고 저장 프로시저를 실행할 때 모든 데이터베이스에 대해 구독이 위임됩니다. 이후에 새 범주의 위임된 구독을 제거하면 *target_object*로 지정한 데이터베이스에 대해서만 구독이 적용됩니다. 위임된 구독 설정을 변경하는 방법은 [sp_syspolicy_update_policy_category&#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-syspolicy-update-policy-category-transact-sql.md)를 참조하세요.  
  
## <a name="permissions"></a>사용 권한  
 이 저장 프로시저는 현재 저장 프로시저 소유자의 컨텍스트에서 실행됩니다.  
  
## <a name="examples"></a>예  
 다음 예에서는 'Table Naming Policies'라는 정책 범주를 구독하도록 지정된 데이터베이스를 구성합니다.  
  
```  
EXEC msdb.dbo.sp_syspolicy_add_policy_category_subscription @target_type = N'DATABASE'  
, @target_object = N'AdventureWorks2012'  
, @policy_category = N'Table Naming Policies';  
  
GO  
```  
  
## <a name="see-also"></a>관련 항목  
 [정책 기반 관리 저장 프로시저 &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/policy-based-management-stored-procedures-transact-sql.md)   
 [sp_syspolicy_update_policy_category_subscription은 &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-syspolicy-update-policy-category-subscription-transact-sql.md)   
 [sp_syspolicy_unsubscribe_from_policy_category &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-syspolicy-unsubscribe-from-policy-category-transact-sql.md)  
  
  
