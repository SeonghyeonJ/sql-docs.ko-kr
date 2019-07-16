---
title: sp_password (TRANSACT-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_password
- sp_password_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_password
ms.assetid: 0ecbec81-e637-44a9-a61e-11bf060ef084
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: c02b9327dbff75e3c0816bb3eec19e3cb3135d50
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68008925"
---
# <a name="sppassword-transact-sql"></a>sp_password(Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  추가 하거나 변경에 대 한 암호를 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 로그인 합니다.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] 사용 하 여 [ALTER LOGIN](../../t-sql/statements/alter-login-transact-sql.md) 대신 합니다.  
  
 ![항목 링크 아이콘](../../database-engine/configure-windows/media/topic-link.gif "항목 링크 아이콘") [Transact-SQL 구문 규칙](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>구문  
  
```  
  
sp_password [ [ @old = ] 'old_password' , ]  
     { [ @new =] 'new_password' }  
     [ , [ @loginame = ] 'login' ]  
```  
  
## <a name="arguments"></a>인수  
`[ @old = ] 'old_password'` 이전 암호가입니다. *old_password* 됩니다 **sysname**, 기본값은 NULL입니다.  
  
`[ @new = ] 'new_password'` 새 암호가입니다. *new_password* 됩니다 **sysname**, 기본값은 없습니다. *old_password* 명명 된 매개 변수 사용 되지 않습니다 지정 해야 합니다.  
  
> [!IMPORTANT]  
>  NULL 암호를 사용하지 마십시오. 강력한 암호를 사용하세요. 자세한 내용은 [Strong Passwords](../../relational-databases/security/strong-passwords.md)을 참조하세요.  
  
`[ @loginame = ] 'login'` 암호 변경의 영향을 받는 로그인의 이름이입니다. *login*은 **sysname**이며 기본값은 NULL입니다. *로그인* 이미 존재 해야 하며의 멤버만 지정할 수 있습니다 합니다 **sysadmin** 하거나 **securityadmin** 고정 서버 역할입니다.  
  
## <a name="return-code-values"></a>반환 코드 값  
 0(성공) 또는 1(실패)  
  
## <a name="remarks"></a>설명  
 **sp_password** ALTER LOGIN을 호출 합니다. 이 문에서는 추가 옵션을 지정할 수 있습니다. 암호 변경에 대 한 내용은 참조 하세요 [ALTER LOGIN &#40;TRANSACT-SQL&#41;](../../t-sql/statements/alter-login-transact-sql.md)합니다.  
  
 **sp_password** 사용자 정의 트랜잭션 내에서 실행할 수 없습니다.  
  
## <a name="permissions"></a>사용 권한  
 ALTER ANY LOGIN 권한이 필요합니다. 이전 암호를 제공하지 않고 암호를 다시 설정하려는 경우나 변경되고 있는 로그인에 CONTROL SERVER 권한이 있는 경우에는 CONTROL SERVER 권한도 필요합니다.  
  
 보안 주체는 자신의 암호를 변경할 수 있습니다.  
  
## <a name="examples"></a>예  
  
### <a name="a-changing-the-password-of-a-login-without-knowing-the-old-password"></a>A. 이전 암호를 모른 채 로그인의 암호 변경  
 다음 예에서는 `ALTER LOGIN`을 사용하여 `Victoria` 로그인의 암호를 `B3r1000d#2-36`으로 변경하는 방법을 보여 줍니다. 이것은 기본적으로 사용되는 방법입니다. 이 명령을 실행하고 있는 사용자는 CONTROL SERVER 권한을 가져야 합니다.  
  
```  
ALTER LOGIN Victoria WITH PASSWORD = 'B3r1000d#2-36';  
GO  
```  
  
### <a name="b-changing-a-password"></a>2\. 암호 변경  
 다음 예에서는 `ALTER LOGIN`을 사용하여 `Victoria` 로그인의 암호를 `B3r1000d#2-36`에서 `V1cteAmanti55imE`로 변경하는 방법을 보여 줍니다. 이것은 기본적으로 사용되는 방법입니다. `Victoria` 사용자는 추가 사용 권한 없이도 이 명령을 실행할 수 있습니다. 다른 사용자는 ALTER ANY LOGIN 권한을 가져야 합니다.  
  
```  
ALTER LOGIN Victoria WITH   
     PASSWORD = 'V1cteAmanti55imE'   
     OLD_PASSWORD = 'B3r1000d#2-36';  
GO  
```  
  
## <a name="see-also"></a>관련 항목  
 [Security Stored Procedures &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [ALTER LOGIN &#40;Transact-SQL&#41;](../../t-sql/statements/alter-login-transact-sql.md)   
 [CREATE LOGIN &#40;Transact-SQL&#41;](../../t-sql/statements/create-login-transact-sql.md)   
 [sp_addlogin&#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addlogin-transact-sql.md)   
 [sp_adduser&#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-adduser-transact-sql.md)   
 [sp_grantlogin&#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-grantlogin-transact-sql.md)   
 [sp_revokelogin&#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-revokelogin-transact-sql.md)   
 [시스템 저장 프로시저&#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
