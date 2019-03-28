---
title: sp_syspolicy_configure (TRANSACT-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_syspolicy_configure
- sp_syspolicy_configure_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_syspolicy_configure
ms.assetid: 70c10922-9345-4190-ba69-808a43f760da
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: b9ae7fdde89c9f927fbc56a9ca395138c264e931
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/27/2019
ms.locfileid: "58532115"
---
# <a name="spsyspolicyconfigure-transact-sql"></a>sp_syspolicy_configure(Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  정책 기반 관리 사용 여부와 같은 정책 기반 관리에 대한 설정을 구성합니다.  
  
 ![항목 링크 아이콘](../../database-engine/configure-windows/media/topic-link.gif "항목 링크 아이콘") [Transact-SQL 구문 규칙](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>구문  
  
```  
  
sp_syspolicy_configure [ @name = ] 'name'  
    , [ @value = ] value  
```  
  
## <a name="arguments"></a>인수  
`[ @name = ] 'name'` 구성 하려는 설정의 이름이입니다. *이름을* 됩니다 **sysname**고, 필요 하며, NULL 또는 빈 문자열일 수 없습니다.  
  
 *이름* 다음 값 중 하나일 수 있습니다.  
  
-   'Enabled' - 정책 기반 관리 사용 여부를 결정합니다.  
  
-   'HistoryRetentionInDays' - 정책 평가 기록을 보관할 일 수를 지정합니다. 0으로 설정되면 기록이 자동으로 제거되지 않습니다.  
  
-   'LogOnSuccess' - 정책 기반 관리에서 성공한 정책 평가를 로깅할지 여부를 지정합니다.  
  
`[ @value = ] value` 지정 된 값과 연결 된 값인 *이름을*입니다. *값* 됩니다 **sql_variant**, 이며 반드시 지정 해야 합니다.  
  
-   에 대 한 'Enabled'를 지정 하는 경우 *이름을*, 다음 값 중 하나를 사용할 수 있습니다.  
  
    -   0 = 정책 기반 관리를 사용하지 않습니다.  
  
    -   1 = 정책 기반 관리를 사용합니다.  
  
-   에 대 한 'HistoryRententionInDays'를 지정 하는 경우 *이름을*를 정수 값으로 일 수를 지정 합니다.  
  
-   에 대 한 'LogOnSuccess'를 지정 하는 경우 *이름을*, 다음 값 중 하나를 사용할 수 있습니다.  
  
    -   0 = 실패한 정책 평가만 로깅합니다.  
  
    -   1 = 성공한 정책 평가와 실패한 정책 평가를 모두 로깅합니다.  
  
## <a name="return-code-values"></a>반환 코드 값  
 **0** (성공) 또는 **1** (실패)  
  
## <a name="remarks"></a>Remarks  
 sp_syspolicy_configure는 msdb 시스템 데이터베이스의 컨텍스트에서 실행해야 합니다.  
  
 이러한 설정의 현재 값을 보려면 msdb.dbo.syspolicy_configuration 시스템 뷰를 쿼리합니다.  
  
## <a name="permissions"></a>사용 권한  
 PolicyAdministratorRole 고정 데이터베이스 역할의 멤버 자격이 필요합니다.  
  
> [!IMPORTANT]  
>  가능한 자격 증명 승격: PolicyAdministratorRole 역할의 사용자는 서버 트리거를 만들고 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 인스턴스 작업에 영향을 줄 수 있는 정책 실행을 예약할 수 있습니다. 예를 들어 PolicyAdministratorRole 역할의 사용자는 대부분의 개체가 [!INCLUDE[ssDE](../../includes/ssde-md.md)]에서 생성되지 않도록 할 수 있는 정책을 만들 수 있습니다. 이렇게 자격 증명을 승격할 수 있기 때문에 PolicyAdministratorRole 역할은 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 구성을 제어할 수 있도록 신뢰할 수 있는 사용자에게만 부여되어야 합니다.  
  
## <a name="examples"></a>예  
 다음 예에서는 정책 기반 관리를 사용하도록 설정합니다.  
  
```  
EXEC msdb.dbo.sp_syspolicy_configure @name = N'Enabled'  
, @value = 1;  
  
GO  
```  
  
 다음 예에서는 정책 평가 기록의 보존 일 수를 14일로 설정합니다.  
  
```  
EXEC msdb.dbo.sp_syspolicy_configure @name = N'HistoryRetentionInDays'  
, @value = 14;  
  
GO  
```  
  
 다음 예에서는 성공한 정책 평가와 실패한 정책 평가를 모두 로깅하도록 정책 기반 관리를 구성합니다.  
  
```  
EXEC msdb.dbo.sp_syspolicy_configure @name = N'LogOnSuccess'  
, @value = 1;  
  
GO  
```  
  
## <a name="see-also"></a>관련 항목  
 [정책 기반 관리 저장 프로시저 &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/policy-based-management-stored-procedures-transact-sql.md)   
 [sp_syspolicy_set_config_enabled &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-syspolicy-set-config-enabled-transact-sql.md)   
 [sp_syspolicy_set_config_history_retention은 &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-syspolicy-set-config-history-retention-transact-sql.md)   
 [sp_syspolicy_set_log_on_success &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-syspolicy-set-log-on-success-transact-sql.md)  
  
  
