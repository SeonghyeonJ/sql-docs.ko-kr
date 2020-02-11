---
title: sp_adduser (Transact-sql) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_adduser
- sp_adduser_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_adduser
ms.assetid: 61a40eb4-573f-460c-9164-bd1bbfaf8b25
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: a2984479c8a1be35f8ccfa63d14b3250939f56c3
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68117899"
---
# <a name="sp_adduser-transact-sql"></a>sp_adduser(Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  현재 데이터베이스에 새 사용자를 추가합니다.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]대신 [CREATE USER](../../t-sql/statements/create-user-transact-sql.md) 를 사용 해야 합니다.  
  
 ![항목 링크 아이콘](../../database-engine/configure-windows/media/topic-link.gif "항목 링크 아이콘") [Transact-SQL 구문 표기 규칙](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>구문  
  
```  
  
sp_adduser [ @loginame = ] 'login'   
    [ , [ @name_in_db = ] 'user' ]   
    [ , [ @grpname = ] 'role' ]   
```  
  
## <a name="arguments"></a>인수  
`[ @loginame = ] 'login'`[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 로그인 또는 Windows 로그인의 이름입니다. *login* 은 **sysname**이며 기본값은 없습니다. *로그인* 은 기존 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 로그인 또는 Windows 로그인 이어야 합니다.  
  
`[ @name_in_db = ] 'user'`새 데이터베이스 사용자의 이름입니다. *사용자* 는 **sysname**이며 기본값은 NULL입니다. *사용자* 를 지정 하지 않으면 새 데이터베이스 사용자의 이름에 대 한 기본값은 *로그인* 이름입니다. *사용자* 를 지정 하면 데이터베이스에서 서버 수준 로그인 이름과 다른 이름을 사용 합니다.  
  
`[ @grpname = ] 'role'`새 사용자가 멤버가 되는 데이터베이스 역할입니다. *role* 은 **sysname**이며 기본값은 NULL입니다. *role* 은 현재 데이터베이스에서 유효한 데이터베이스 역할 이어야 합니다.  
  
## <a name="return-code-values"></a>반환 코드 값  
 0(성공) 또는 1(실패)  
  
## <a name="remarks"></a>설명  
 또한 **sp_adduser** 은 사용자의 이름이 포함 된 스키마를 만듭니다.  
  
 사용자를 추가한 다음 GRANT, DENY 및 REVOKE 문을 통해 사용자의 작업을 제어하는 사용 권한을 정의합니다.  
  
 **Server_principals** 를 사용 하 여 유효한 로그인 이름 목록을 표시 합니다.  
  
 올바른 역할 이름 목록을 표시 하려면 **sp_helprole** 을 사용 합니다. 역할을 지정하면 사용자가 해당 역할에 대해 정의된 사용 권한을 자동으로 갖게 됩니다. 역할을 지정 하지 않으면 사용자가 기본 **public** 역할에 부여 된 사용 권한을 얻게 됩니다. 사용자를 역할에 추가 하려면 *사용자 이름* 값을 제공 해야 합니다. *사용자 이름은* *login_id*와 동일할 수 있습니다.  
  
 사용자 **게스트가** 모든 데이터베이스에 이미 있습니다. 사용자 **게스트** 를 추가 하면 이전에 사용 하지 않도록 설정 된 경우이 사용자를 사용할 수 있습니다. 기본적으로 사용자 **게스트** 는 새 데이터베이스에서 사용할 수 없습니다.  
  
 **sp_adduser** 은 사용자 정의 트랜잭션 내에서 실행할 수 없습니다.  
  
 **게스트 사용자** 가 모든 데이터베이스 내에 이미 있으므로 **게스트** 사용자를 추가할 수 없습니다. **게스트** 사용자를 사용 하도록 설정 하려면 다음과 같이 **게스트** 연결 권한을 부여 합니다.  
  
```  
GRANT CONNECT TO guest;  
GO  
```  
  
## <a name="permissions"></a>사용 권한  
 데이터베이스에 대한 소유권이 필요합니다.  
  
## <a name="examples"></a>예  
  
### <a name="a-adding-a-database-user"></a>A. 데이터베이스 사용자 추가  
 다음 예에서는 `Vidur`라는 기존 `Recruiting` 로그인을 사용하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터베이스 사용자를 현재 데이터베이스의 기존 `Vidur` 역할에 추가합니다.  
  
```  
EXEC sp_adduser 'Vidur', 'Vidur', 'Recruiting';  
```  
  
### <a name="b-adding-a-database-user-with-the-same-login-id"></a>B. 동일한 로그인 ID로 데이터베이스 사용자 추가  
 다음 예에서는 `Arvind` 사용자를 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]라는 `Arvind` 로그인에 대한 현재 데이터베이스에 추가합니다. 이 사용자는 기본 **public** 역할에 속합니다.  
  
```  
EXEC sp_adduser 'Arvind';  
```  
  
### <a name="c-adding-a-database-user-with-a-different-name-than-its-server-level-login"></a>C. 서버 수준 로그인과는 다른 이름으로 데이터베이스 사용자 추가  
 다음 예에서는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]라는 `BjornR` 로그인을 `Bjorn`이라는 사용자 이름의 현재 데이터베이스에 추가하고 `Bjorn` 데이터베이스 사용자를 `Production` 데이터베이스 역할에 추가합니다.  
  
```  
EXEC sp_adduser 'BjornR', 'Bjorn', 'Production';  
```  
  
## <a name="see-also"></a>참고 항목  
 [Transact-sql&#41;&#40;보안 저장 프로시저](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [sys.server_principals&#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-server-principals-transact-sql.md)   
 [Transact-sql&#41;sp_addrole &#40;](../../relational-databases/system-stored-procedures/sp-addrole-transact-sql.md)   
 [Transact-sql&#41;사용자 &#40;만들기](../../t-sql/statements/create-user-transact-sql.md)   
 [Transact-sql&#41;sp_dropuser &#40;](../../relational-databases/system-stored-procedures/sp-dropuser-transact-sql.md)   
 [Transact-sql&#41;sp_grantdbaccess &#40;](../../relational-databases/system-stored-procedures/sp-grantdbaccess-transact-sql.md)   
 [Transact-sql&#41;sp_grantlogin &#40;](../../relational-databases/system-stored-procedures/sp-grantlogin-transact-sql.md)   
 [시스템 저장 프로시저&#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
