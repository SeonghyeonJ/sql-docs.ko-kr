---
title: sp_add_log_shipping_alert_job (TRANSACT-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_add_log_shipping_alert_job_TSQL
- sp_add_log_shipping_alert_job
dev_langs:
- TSQL
helpviewer_keywords:
- sp_add_log_shipping_alert_job
ms.assetid: dd95d96e-8963-4aa9-bdcc-3e4b1bc002d3
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 0c654f8e76a25c0588011afecc632d3f85a33455
ms.sourcegitcommit: 2db83830514d23691b914466a314dfeb49094b3c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/27/2019
ms.locfileid: "58492921"
---
# <a name="spaddlogshippingalertjob-transact-sql"></a>sp_add_log_shipping_alert_job(Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  이 저장 프로시저는 이 서버에서 경고 작업을 만들었는지 여부를 확인합니다. 경고 작업이 존재 하지 않는 경우이 저장된 프로시저 경고 작업을 만들고 해당 작업 ID를 추가 합니다 **log_shipping_monitor_alert** 테이블입니다. 경고 작업은 기본적으로 활성화되며 2분마다 한 번씩 실행됩니다.  
  
 ![항목 링크 아이콘](../../database-engine/configure-windows/media/topic-link.gif "항목 링크 아이콘") [Transact-SQL 구문 규칙](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>구문  
  
```  
  
sp_add_log_shipping_alert_job  
[, [ @alert_job_id = ] alert_job_id OUTPUT ]  
```  
  
## <a name="arguments"></a>인수  
`[ @alert_job_id = ] alert_job_id OUTPUT` 합니다 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 로그 전달 경고 작업의 에이전트 작업 ID입니다.  
  
## <a name="return-code-values"></a>반환 코드 값  
 0(성공) 또는 1(실패)  
  
## <a name="result-sets"></a>결과 집합  
 없음  
  
## <a name="remarks"></a>Remarks  
 **sp_add_log_shipping_alert_job** 에서 실행 해야 합니다 **마스터** 모니터 서버의 데이터베이스.  
  
## <a name="permissions"></a>사용 권한  
 멤버는 **sysadmin** 고정된 서버 역할에서이 프로시저를 실행할 수 있습니다.  
  
## <a name="examples"></a>예  
 이 예제에서는 실행을 보여 줍니다 **sp_add_log_shipping_alert_job** 는 경고 작업 ID를 만듭니다.  
  
```  
USE master  
GO  
EXEC sp_add_log_shipping_alert_job;  
```  
  
## <a name="see-also"></a>관련 항목  
 [로그 전달 정보&#40;SQL Server&#41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md)   
 [시스템 저장 프로시저&#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
