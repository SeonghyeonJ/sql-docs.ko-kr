---
title: sp_notify_operator (TRANSACT-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_notify_operator_TSQL
- sp_notify_operator
dev_langs:
- TSQL
helpviewer_keywords:
- sp_notify_operator
ms.assetid: c440f5c9-9884-4196-b07c-55d87afb17c3
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: f12ce5837e47ce9cb647d1f7364ce23ad921e26c
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/27/2019
ms.locfileid: "58526275"
---
# <a name="spnotifyoperator-transact-sql"></a>sp_notify_operator(Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  데이터베이스 메일을 사용하여 운영자에게 전자 메일 메시지를 보냅니다.  
  
 
 ![항목 링크 아이콘](../../database-engine/configure-windows/media/topic-link.gif "항목 링크 아이콘") [Transact-SQL 구문 규칙](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>구문  
  
```  
  
sp_notify_operator  
    [ @profile_name = ] 'profilename' ,  
    [ @id = ] id ,  
    [ @name = ] 'name' ,  
    [ @subject = ] 'subject' ,  
    [ @body = ] 'message' ,  
    [ @file_attachments = ] 'attachment'  
    [ @mail_database = ] 'mail_host_database'  
```  
  
## <a name="arguments"></a>인수  
`[ @profile_name = ] 'profilename'` 메시지를 보내는 데 사용할 데이터베이스 메일 프로필의 이름입니다. *profilename* 됩니다 **nvarchar (128)** 합니다. 하는 경우 *profilename* 지정 하지 않으면 기본 데이터베이스 메일 프로필이 사용 됩니다.  
  
`[ @id = ] id` 메시지를 받을 운영자의 식별자입니다. *id* 됩니다 **int**, 기본값은 NULL입니다. 중 하나 *id* 하거나 *이름* 지정 해야 합니다.  
  
`[ @name = ] 'name'` 메시지를 보낼 운영자의 이름입니다. *이름* 됩니다 **nvarchar (128)**, 기본값은 NULL입니다. 중 하나 *id* 하거나 *이름* 지정 해야 합니다.  
  
> **참고:** 메시지를 보내기 전에 운영자의 전자 메일 주소가 정의되어야 합니다.  
  
`[ @subject = ] 'subject'` 전자 메일 메시지의 제목입니다. *주체* 됩니다 **nvarchar(256)** 기본값은 없습니다.  
  
`[ @body = ] 'message'` 전자 메일 메시지의 본문입니다. *메시지* 됩니다 **nvarchar (max)** 기본값은 없습니다.  
  
`[ @file_attachments = ] 'attachment'` 전자 메일 메시지에 첨부할 파일의 이름입니다. *첨부 파일* 됩니다 **nvarchar(512)**, 기본값은 없습니다.  
  
`[ @mail_database = ] 'mail_host_database'` 메일 호스트 데이터베이스의 이름을 지정합니다. *mail_host_database* 됩니다 **nvarchar (128)** 합니다. 없으면 *mail_host_database* 를 지정 합니다 **msdb** 데이터베이스는 기본적으로 사용 됩니다.  
  
## <a name="return-code-values"></a>반환 코드 값  
 **0** (성공) 또는 **1** (실패)  
  
## <a name="remarks"></a>Remarks  
 지정한 메시지를 지정된 운영자의 전자 메일 주소로 보냅니다. 운영자의 전자 메일 주소가 설정되지 않은 경우 오류를 반환합니다.  
  
 데이터베이스 메일과 메일 호스트 데이터베이스는 운영자에게 알림을 보내기 전에 구성해야 합니다.  
  
## <a name="permissions"></a>사용 권한  
 기본적으로 **sysadmin** 고정 서버 역할의 멤버는 이 저장 프로시저를 실행할 수 있습니다. 다른 사용자는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] msdb **데이터베이스의 다음** 에이전트 고정 데이터베이스 역할 중 하나를 부여 받아야 합니다.  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 이러한 역할의 사용 권한에 대한 자세한 내용은 [SQL Server 에이전트 고정 데이터베이스 역할](../../ssms/agent/sql-server-agent-fixed-database-roles.md)을 참조하세요.  
  
## <a name="examples"></a>예  
 다음 예에서는 `François Ajenstat` 데이터베이스 메일 프로필을 사용하여 운영자 `AdventureWorks Administrator`에게 알림 전자 메일을 보냅니다. 전자 메일의 제목은 `Test Notification`입니다. 전자 메일 메시지에는 "This is a test of notification via e-mail."이라는 문장이 포함되어 있습니다.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_notify_operator  
   @profile_name = N'AdventureWorks Administrator',  
   @name = N'François Ajenstat',  
   @subject = N'Test Notification',  
   @body = N'This is a test of notification via e-mail.' ;  
GO  
```  
  
## <a name="see-also"></a>참고자료  
 [SQL Server 에이전트 저장 프로시저 &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sql-server-agent-stored-procedures-transact-sql.md)   
 [sp_add_operator &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-operator-transact-sql.md)   
 [sp_help_operator &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-operator-transact-sql.md)   
 [sp_delete_operator &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-operator-transact-sql.md)  
  
  
