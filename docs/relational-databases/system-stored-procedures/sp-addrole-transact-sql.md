---
title: sp_addrole (TRANSACT-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_addrole
- sp_addrole_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_addrole
ms.assetid: e8a21642-8440-419a-8585-93d3d9d44f00
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 1711ec3941a5fced5ef9e0c32808d6153b673e2b
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68030925"
---
# <a name="spaddrole-transact-sql"></a>sp_addrole(Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  현재 데이터베이스에 새 데이터베이스 역할을 만듭니다.  
  
> [!IMPORTANT]
>  **sp_addrole** 이전 버전과의 호환성을 위해 포함 되었습니다 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 이후 릴리스에서 지원 되지 않을 수 있습니다. 사용 하 여 [CREATE ROLE](../../t-sql/statements/create-role-transact-sql.md) 대신 합니다.  
  
 ![항목 링크 아이콘](../../database-engine/configure-windows/media/topic-link.gif "항목 링크 아이콘") [Transact-SQL 구문 규칙](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>구문  
  
```  
  
sp_addrole [ @rolename = ] 'role' [ , [ @ownername = ] 'owner' ]   
```  
  
## <a name="arguments"></a>인수  
`[ @rolename = ] 'role'` 새 데이터베이스 역할의 이름이입니다. *역할* 되는 **sysname**, 기본값은 없습니다. *역할* 올바른 식별자 (ID) 여야 하며 현재 데이터베이스에 이미 존재 하지 않아야 합니다.  
  
`[ @ownername = ] 'owner'` 새 데이터베이스 역할의 소유자가입니다. *소유자* 되는 **sysname**, 현재 실행 중인 사용자의 기본값을 사용 하 여 합니다. *소유자* 데이터베이스 사용자 또는 현재 데이터베이스의 데이터베이스 역할 이어야 합니다.  
  
## <a name="return-code-values"></a>반환 코드 값  
 0(성공) 또는 1(실패)  
  
## <a name="remarks"></a>설명  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터베이스 역할의 이름에는 문자, 기호 및 숫자 등을 포함하여 1자에서 128자까지의 문자를 사용할 수 있습니다. 데이터베이스 역할의 이름이 없습니다: 백슬래시 문자를 포함 (\\) NULL 일 또는 빈 문자열 ( **'** ).  
  
 데이터베이스 역할에 추가한 후 사용 하 여 [sp_addrolemember &#40;TRANSACT-SQL&#41; ](../../relational-databases/system-stored-procedures/sp-addrolemember-transact-sql.md) 역할에 보안 주체를 추가 합니다. GRANT, DENY 또는 REVOKE 문을 사용하여 데이터베이스 역할에 사용 권한을 부여하는 경우 데이터베이스 역할의 멤버는 사용 권한이 자신의 계정에 직접 적용되는 것처럼 사용 권한을 상속합니다.  
  
> [!NOTE]  
>  새 서버 역할은 만들 수 없습니다. 역할은 데이터베이스 수준에서만 만들 수 있습니다.  
  
 **sp_addrole** 사용자 정의 트랜잭션 내에서 사용할 수 없습니다.  
  
## <a name="permissions"></a>사용 권한  
 데이터베이스에 대한 CREATE ROLE 권한이 필요합니다. 스키마를 만드는 경우에는 데이터베이스에 대한 CREATE SCHEMA 권한이 필요합니다. 하는 경우 *소유자* 사용자 또는 그룹으로 지정 된 경우 해당 사용자 또는 그룹에 대 한 IMPERSONATE이 필요 합니다. 하는 경우 *소유자* 역할로 지정 된 경우 해당 역할의 멤버 또는 해당 역할에 대 한 ALTER 권한이 필요 합니다. owner를 응용 프로그램 역할로 지정한 경우에는 해당 응용 프로그램 역할에 대한 ALTER 권한이 필요합니다.  
  
## <a name="examples"></a>예  
 다음 예에서는 현재 데이터베이스에 `Managers`라는 새 역할을 추가합니다.  
  
```  
EXEC sp_addrole 'Managers';  
```  
  
## <a name="see-also"></a>관련 항목  
 [시스템 저장 프로시저&#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Security Stored Procedures &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [CREATE ROLE&#40;Transact-SQL&#41;](../../t-sql/statements/create-role-transact-sql.md)  
  
  
