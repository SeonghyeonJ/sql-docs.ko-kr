---
title: sp_syspolicy_delete_policy_execution_history (TRANSACT-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_syspolicy_delete_policy_execution_history
- sp_syspolicy_delete_policy_execution_history_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_syspolicy_delete_policy_execution_history
ms.assetid: fe651af9-267e-45ec-b4e7-4b0698fb1be3
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: 6660eba76675fbe261af33f647d60456ced839d2
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63002287"
---
# <a name="spsyspolicydeletepolicyexecutionhistory-transact-sql"></a>sp_syspolicy_delete_policy_execution_history(Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  정책 기반 관리에서 정책의 실행 기록을 삭제합니다. 이 저장 프로시저를 사용하여 특정 정책 또는 모든 정책의 실행 기록을 삭제하거나 특정 날짜 이전의 실행 기록을 삭제할 수 있습니다.  
  
 ![항목 링크 아이콘](../../database-engine/configure-windows/media/topic-link.gif "항목 링크 아이콘") [Transact-SQL 구문 규칙](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>구문  
  
```  
  
sp_syspolicy_delete_policy_execution_history [ @policy_id = ] policy_id ]  
    [ , [ @oldest_date = ] 'oldest_date' ]  
```  
  
## <a name="arguments"></a>인수  
`[ @policy_id = ] policy_id` 실행 기록을 삭제할 정책의 식별자가입니다. *policy_id* 됩니다 **int**, 이며 반드시 지정 해야 합니다. NULL일 수 있습니다.  
  
`[ @oldest_date = ] 'oldest_date'` 정책 실행 기록을 유지 하려는 가장 오래 된 날짜가입니다. 이 날짜 이전의 실행 기록은 모두 삭제됩니다. *oldest_date* 됩니다 **datetime**, 이며 반드시 지정 해야 합니다. NULL일 수 있습니다.  
  
## <a name="return-code-values"></a>반환 코드 값  
 **0** (성공) 또는 **1** (실패)  
  
## <a name="remarks"></a>Remarks  
 sp_syspolicy_delete_policy_execution_history는 msdb 시스템 데이터베이스의 컨텍스트에서 실행해야 합니다.  
  
 값을 얻으려면 *policy_id*, 실행 기록 날짜를 보려면 다음 쿼리를 사용할 수 있습니다.  
  
```  
SELECT a.name AS N'policy_name', b.policy_id, b.start_date, b.end_date  
FROM msdb.dbo.syspolicy_policies AS a   
INNER JOIN msdb.dbo.syspolicy_policy_execution_history AS b  
ON a.policy_id = b.policy_id  
```  
  
 하나 또는 두 값 모두 NULL을 지정하면 다음 동작이 적용됩니다.  
  
-   모든 정책 실행 기록을 삭제 하려면 둘 다에 대해 NULL을 지정 *policy_id* 등에 *oldest_date*합니다.  
  
-   특정 정책에 대 한 모든 정책 실행 기록을 삭제 하려면에 대 한 정책 식별자를 지정 *policy_id*에 NULL을 지정 하 고 *oldest_date*합니다.  
  
-   특정 날짜 이전의 모든 정책에 대 한 정책 실행 기록을 삭제 하려면 NULL을 지정 *policy_id*에 대 한 날짜를 지정 *oldest_date*합니다.  
  
 정책 실행 기록을 보관하려면 개체 탐색기에서 정책 기록 로그를 열고 실행 기록을 파일로 내보냅니다. 정책 기록 로그에 액세스 하려면 확장 **Management**를 마우스 오른쪽 단추로 클릭 **정책 관리**를 클릭 하 고 **기록 보기**합니다.  
  
## <a name="permissions"></a>사용 권한  
 PolicyAdministratorRole 고정 데이터베이스 역할의 멤버 자격이 필요합니다.  
  
> [!IMPORTANT]  
>  가능한 자격 증명 승격: PolicyAdministratorRole 역할의 사용자 수 서버 트리거를 만들고 인스턴스의 작업에 영향을 줄 수 있는 정책 실행을 예약 합니다 [!INCLUDE[ssDE](../../includes/ssde-md.md)]합니다. 예를 들어 PolicyAdministratorRole 역할의 사용자는 대부분의 개체가 [!INCLUDE[ssDE](../../includes/ssde-md.md)]에서 생성되지 않도록 할 수 있는 정책을 만들 수 있습니다. 이렇게 자격 증명을 승격할 수 있기 때문에 PolicyAdministratorRole 역할은 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 구성을 제어할 수 있도록 신뢰할 수 있는 사용자에게만 부여되어야 합니다.  
  
## <a name="examples"></a>예  
 다음 예에서는 ID가 7인 정책에 대해 특정 날짜 이전의 정책 실행 기록을 삭제합니다.  
  
```  
EXEC msdb.dbo.sp_syspolicy_delete_policy_execution_history @policy_id = 7  
, @oldest_date = '2009-02-16 16:00:00.000';  
  
GO  
```  
  
## <a name="see-also"></a>관련 항목  
 [정책 기반 관리 저장 프로시저 &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/policy-based-management-stored-procedures-transact-sql.md)   
 [sp_syspolicy_set_config_history_retention은 &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-syspolicy-set-config-history-retention-transact-sql.md)   
 [sp_syspolicy_purge_history &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-syspolicy-purge-history-transact-sql.md)  
  
  
