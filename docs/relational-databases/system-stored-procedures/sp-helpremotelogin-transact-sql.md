---
title: sp_helpremotelogin (TRANSACT-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_helpremotelogin_TSQL
- sp_helpremotelogin
dev_langs:
- TSQL
helpviewer_keywords:
- sp_helpremotelogin
ms.assetid: 93f50869-2627-4642-899f-8f626f8833f4
author: stevestein
ms.author: sstein
ms.openlocfilehash: 11d71139786ac1442588f016bf8c576b92853cf3
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67997573"
---
# <a name="sphelpremotelogin-transact-sql"></a>sp_helpremotelogin(Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  로컬 서버에서 정의된 특정 원격 서버 또는 모든 원격 서버에 대한 원격 로그인 정보를 보고합니다.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepNextDontUse](../../includes/ssnotedepnextdontuse-md.md)] 대신 연결된 서버 및 연결된 서버의 저장 프로시저를 사용하십시오.  
  
 ![항목 링크 아이콘](../../database-engine/configure-windows/media/topic-link.gif "항목 링크 아이콘") [Transact-SQL 구문 규칙](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>구문  
  
```  
  
sp_helpremotelogin [ [ @remoteserver = ] 'remoteserver' ]   
     [ , [ @remotename = ] 'remote_name' ]  
```  
  
## <a name="arguments"></a>인수  
 [ @remoteserver **=** ] **'***remoteserver***'**  
 원격 로그인 정보를 반환할 대상이 되는 원격 서버입니다. *remoteserver* 됩니다 **sysname**, 기본값은 NULL입니다. 하는 경우 *remoteserver* 은 지정 하지 않으면 로컬 서버에 정의 된 모든 원격 서버에 대 한 정보 반환 됩니다.  
  
 [ @remotename **=** ] **'***remote_name***'**  
 원격 서버의 특정 원격 로그인입니다. *remote_name* 됩니다 **sysname**, 기본값은 NULL입니다. 하는 경우 *remote_name* 지정 하지 않으면 모든 원격 사용자에 대 한 정보에 대해 정의 된 *remoteserver* 반환 됩니다.  
  
## <a name="return-code-values"></a>반환 코드 값  
 0(성공) 또는 1(실패)  
  
## <a name="result-sets"></a>결과 집합  
  
|열 이름|데이터 형식|설명|  
|-----------------|---------------|-----------------|  
|서버|**sysname**|로컬 서버에서 정의된 원격 서버의 이름입니다.|  
|local_user_name|**sysname**|서버의 원격 로그인이 매핑되는 로컬 서버의 로그인입니다.|  
|remote_user_name|**sysname**|Local_user_name 매핑되는 원격 서버의 로그인입니다.|  
|옵션|**sysname**|Trusted = 원격 서버에서 로컬 서버로 연결할 때 원격 로그인 암호를 제공할 필요가 없습니다.<br /><br /> Untrusted(또는 공백) = 원격 서버에서 로컬 서버로 연결할 때 원격 로그인 암호를 제공해야 합니다.|  
  
## <a name="remarks"></a>설명  
 로컬 서버에 정의 된 원격 서버의 이름을 나열 하려면 sp_helpserver를 사용 합니다.  
  
## <a name="permissions"></a>사용 권한  
 사용 권한을 확인하지 않습니다.  
  
## <a name="examples"></a>예  
  
### <a name="a-reporting-help-on-a-single-server"></a>A. 단일 서버에 관한 도움말 보고  
 다음 예에서는 `Accounts`라는 원격 서버의 모든 원격 사용자에 대한 정보를 표시합니다.  
  
```  
EXEC sp_helpremotelogin 'Accounts';  
```  
  
### <a name="b-reporting-help-on-all-remote-users"></a>2\. 모든 원격 사용자에 관한 도움말 보고  
 다음 예에서는 로컬 서버에 알려진 모든 원격 서버의 모든 원격 사용자에 관한 정보를 표시합니다.  
  
```  
EXEC sp_helpremotelogin;  
```  
  
## <a name="see-also"></a>관련 항목  
 [sp_addremotelogin &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addremotelogin-transact-sql.md)   
 [sp_dropremotelogin &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropremotelogin-transact-sql.md)   
 [sp_helpserver&#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpserver-transact-sql.md)   
 [sp_remoteoption &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-remoteoption-transact-sql.md)   
 [시스템 저장 프로시저&#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
