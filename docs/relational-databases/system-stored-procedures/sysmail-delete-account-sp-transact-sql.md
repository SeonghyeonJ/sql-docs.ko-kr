---
description: sysmail_delete_account_sp(Transact-SQL)
title: sysmail_delete_account_sp (Transact-sql) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sysmail_delete_account_sp
- sysmail_delete_account_sp_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sysmail_delete_account_sp
ms.assetid: 2adcac78-4a4a-407e-9666-1d9c43c73cc2
author: markingmyname
ms.author: maghan
ms.openlocfilehash: ccc7cbbbae49362eabc1612547e37589d80894a3
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89538519"
---
# <a name="sysmail_delete_account_sp-transact-sql"></a>sysmail_delete_account_sp(Transact-SQL)
[!INCLUDE [SQL Server - ASDBMI](../../includes/applies-to-version/sql-asdbmi.md)]

  데이터베이스 메일 SMTP 계정을 삭제합니다. 데이터베이스 메일 구성 마법사를 사용하여 계정을 삭제할 수도 있습니다.  
  
 ![항목 링크 아이콘](../../database-engine/configure-windows/media/topic-link.gif "항목 링크 아이콘") [Transact-SQL 구문 표기 규칙](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>구문  
  
```  
  
sysmail_delete_account_sp { [ @account_id = ] account_id | [ @account_name = ] 'account_name' }   
```  
  
## <a name="arguments"></a>인수  
`[ @account_id = ] account_id` 삭제할 계정의 ID 번호입니다. *account_id* 는 **int**이며 기본값은 없습니다. *Account_id* 또는 *account_name* 를 지정 해야 합니다.  
  
`[ @account_name = ] 'account_name'` 삭제할 계정의 이름입니다. *account_name* 는 **sysname**이며 기본값은 없습니다. *Account_id* 또는 *account_name* 를 지정 해야 합니다.  
  
## <a name="return-code-values"></a>반환 코드 값  
 **0** (성공) 또는 **1** (실패)  
  
## <a name="result-sets"></a>결과 집합  
 None  
  
## <a name="remarks"></a>설명  
 이 프로시저는 프로필의 계정 사용 여부에 관계없이 지정된 계정을 삭제합니다. 계정이 없는 프로필은 전자 메일을 보낼 수 없습니다.  
  
 **Sysmail_delete_account_sp** 저장 프로시저는 **msdb** 데이터베이스에 있으며 **dbo** 스키마가 소유 합니다. 현재 데이터베이스가 **msdb**가 아닌 경우 세 부분으로 된 이름을 사용 하 여 프로시저를 실행 해야 합니다.  
  
## <a name="permissions"></a>사용 권한  
 이 프로시저에 대 한 실행 권한은 기본적으로 **sysadmin** 고정 서버 역할의 멤버로 사용 됩니다.  
  
## <a name="examples"></a>예제  
 다음 예에서는 `AdventureWorks Administrator`라는 데이터베이스 메일 계정을 삭제합니다.  
  
```  
EXECUTE msdb.dbo.sysmail_delete_account_sp  
    @account_name = 'AdventureWorks Administrator' ;  
```  
  
## <a name="see-also"></a>참고 항목  
 [데이터베이스 메일](../../relational-databases/database-mail/database-mail.md)   
 [데이터베이스 메일 계정 만들기](../../relational-databases/database-mail/create-a-database-mail-account.md)   
 [데이터베이스 메일 구성 개체](../../relational-databases/database-mail/database-mail-configuration-objects.md)   
 [Transact-sql&#41;sysmail_add_account_sp &#40;](../../relational-databases/system-stored-procedures/sysmail-add-account-sp-transact-sql.md)   
 [Transact-sql&#41;sysmail_delete_profile_sp &#40;](../../relational-databases/system-stored-procedures/sysmail-delete-profile-sp-transact-sql.md)   
 [Transact-sql&#41;sysmail_delete_profileaccount_sp &#40;](../../relational-databases/system-stored-procedures/sysmail-delete-profileaccount-sp-transact-sql.md)   
 [Transact-sql&#41;sysmail_help_account_sp &#40;](../../relational-databases/system-stored-procedures/sysmail-help-account-sp-transact-sql.md)   
 [Transact-sql&#41;sysmail_help_profile_sp &#40;](../../relational-databases/system-stored-procedures/sysmail-help-profile-sp-transact-sql.md)   
 [Transact-sql&#41;sysmail_help_profileaccount_sp &#40;](../../relational-databases/system-stored-procedures/sysmail-help-profileaccount-sp-transact-sql.md)   
 [Transact-sql&#41;sysmail_update_profileaccount_sp &#40;](../../relational-databases/system-stored-procedures/sysmail-update-profileaccount-sp-transact-sql.md)  
  
  
