---
title: sp_addsrvrolemember (Transact-sql) | Microsoft Docs
ms.custom: ''
ms.date: 03/20/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_addsrvrolemember
- sp_addsrvrolemember_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_addsrvrolemember
ms.assetid: 777f0e09-8ee5-4cb2-a3ac-939d02c3cd22
author: stevestein
ms.author: sstein
ms.openlocfilehash: 2c927bdff462922d1846188366fbb92ce0d3663c
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68022420"
---
# <a name="sp_addsrvrolemember-transact-sql"></a>sp_addsrvrolemember(Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  고정 서버 역할의 멤버로서 로그인을 추가합니다.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]대신 [ALTER SERVER ROLE](../../t-sql/statements/alter-server-role-transact-sql.md) 을 사용 하십시오.  
  
 ![항목 링크 아이콘](../../database-engine/configure-windows/media/topic-link.gif "항목 링크 아이콘") [Transact-SQL 구문 표기 규칙](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>구문  
  
```  
  
sp_addsrvrolemember [ @loginame= ] 'login'   
    , [ @rolename = ] 'role'  
```  
  
## <a name="arguments"></a>인수  
 [ @loginame **=** ] **'**_로그인_**'**  
 고정 서버 역할에 추가할 로그인의 이름입니다. *login* 은 **sysname**이며 기본값은 없습니다. *로그인은* [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 로그인 또는 Windows 로그인 일 수 있습니다. Windows 로그인에 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에 대한 액세스 권한이 부여되어 있지 않으면 자동으로 부여됩니다.  
  
 [ @rolename **=** ] **'**_role_**'**  
 로그인을 추가할 고정 서버 역할의 이름입니다. *role* 은 **sysname**이며 기본값은 NULL이 고 다음 값 중 하나 여야 합니다.  
  
-   sysadmin  
  
-   securityadmin  
  
-   serveradmin  
  
-   setupadmin  
  
-   processadmin  
  
-   diskadmin  
  
-   dbcreator  
  
-   bulkadmin  

## <a name="return-code-values"></a>반환 코드 값  
 0(성공) 또는 1(실패)  
  
## <a name="remarks"></a>설명  
 로그인을 고정 서버 역할에 추가하면 이 역할과 연결된 사용 권한을 얻게 됩니다.  
  
 sa 로그인과 public의 역할 멤버 자격은 변경할 수 없습니다.  
  
 고정 데이터베이스 또는 사용자 정의 역할에 멤버를 추가하려면 sp_addrolemember를 사용하십시오.  
  
 사용자 정의 트랜잭션 내에서는 sp_addsrvrolemember를 실행할 수 없습니다.  
  
## <a name="permissions"></a>사용 권한  
 새 멤버를 추가할 역할의 멤버 자격이 필요합니다.  
  
## <a name="examples"></a>예  
 다음 예에서는 Windows 로그인 `Corporate\HelenS` 을 `sysadmin` 고정 서버 역할에 추가 합니다.  
  
```  
EXEC sp_addsrvrolemember 'Corporate\HelenS', 'sysadmin';  
GO  
```  
  
## <a name="see-also"></a>참고 항목  
 [Transact-sql&#41;&#40;보안 저장 프로시저](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [Transact-sql&#41;sp_addrolemember &#40;](../../relational-databases/system-stored-procedures/sp-addrolemember-transact-sql.md)   
 [Transact-sql&#41;sp_dropsrvrolemember &#40;](../../relational-databases/system-stored-procedures/sp-dropsrvrolemember-transact-sql.md)   
 [시스템 저장 프로시저&#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [보안 함수&#40;Transact-SQL&#41;](../../t-sql/functions/security-functions-transact-sql.md)   
 [Transact-sql&#41;&#40;서버 역할 만들기](../../t-sql/statements/create-server-role-transact-sql.md)   
 [DROP SERVER ROLE &#40;Transact-sql&#41;](../../t-sql/statements/drop-server-role-transact-sql.md)  
  
  
