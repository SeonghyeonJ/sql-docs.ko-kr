---
title: sysmail_stop_sp (TRANSACT-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sysmail_stop_sp_TSQL
- sysmail_stop_sp
dev_langs:
- TSQL
helpviewer_keywords:
- sysmail_stop_sp
ms.assetid: 045ee36f-5bf0-4626-b5ee-e84db06ce16f
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 753375d139a03d5c0cec20dc994d83399e04f094
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68037405"
---
# <a name="sysmailstopsp-transact-sql"></a>sysmail_stop_sp(Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  외부 프로그램이 사용하는 [!INCLUDE[ssSB](../../includes/sssb-md.md)] 개체를 중지하여 데이터베이스 메일을 중지합니다.  
  
 ![항목 링크 아이콘](../../database-engine/configure-windows/media/topic-link.gif "항목 링크 아이콘") [Transact-SQL 구문 규칙](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>구문  
  
```  
  
sysmail_stop_sp  
```  
  
## <a name="arguments"></a>인수  
 없음  
  
## <a name="return-code-values"></a>반환 코드 값  
 **0** (성공) 또는 **1** (실패)  
  
## <a name="remarks"></a>설명  
 이 저장된 프로시저에는 **msdb** 데이터베이스입니다.  
  
 이 저장 프로시저는 보내는 메시지 요청이 있는 데이터베이스 메일 큐를 중지하고 외부 프로그램에 대한 [!INCLUDE[ssSB](../../includes/sssb-md.md)] 활성화를 해제합니다.  
  
 큐가 중지되면 데이터베이스 메일 외부 프로그램이 메시지를 처리할 수 없습니다. 이 저장 프로시저를 통해 문제 해결 또는 유지 관리 목적으로 데이터베이스 메일을 중지할 수 있습니다.  
  
 데이터베이스 메일을 시작 하려면 사용 하 여 **sysmail_start_sp**합니다. 있음을 **sp_send_dbmail** 여전히 허용 될 때 메일을 [!INCLUDE[ssSB](../../includes/sssb-md.md)] 개체가 중지 된 합니다.  
  
> [!NOTE]  
>  이 저장 프로시저는 데이터베이스 메일의 큐만 중지합니다. 이 저장 프로시저는 데이터베이스에서 [!INCLUDE[ssSB](../../includes/sssb-md.md)] 메시지 배달을 비활성화하지 않습니다. 이 저장 프로시저는 데이터베이스 메일 확장 저장 프로시저를 해제하여 노출 영역을 줄일 수 없습니다. 확장된 저장된 프로시저를 사용 하지 않으려면 참조를 [Database Mail XPs 옵션](../../database-engine/configure-windows/database-mail-xps-server-configuration-option.md) 의 합니다 **sp_configure** 시스템 저장 프로시저입니다.  
  
## <a name="permissions"></a>사용 권한  
 이 프로시저 기본의 멤버에 대 한 권한을 실행 합니다 **sysadmin** 고정된 서버 역할입니다.  
  
## <a name="examples"></a>예  
 다음 예제에서는 데이터베이스 메일을 중지 합니다 **msdb** 데이터베이스입니다. 이 예에서는 데이터베이스 메일이 설정되었다고 가정합니다.  
  
```  
USE msdb ;  
GO  
  
EXECUTE dbo.sysmail_stop_sp ;  
GO  
```  
  
## <a name="see-also"></a>관련 항목  
 [데이터베이스 메일](../../relational-databases/database-mail/database-mail.md)   
 [sysmail_start_sp &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sysmail-start-sp-transact-sql.md)   
 [데이터베이스 메일 저장 프로시저 &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/database-mail-stored-procedures-transact-sql.md)  
  
  
