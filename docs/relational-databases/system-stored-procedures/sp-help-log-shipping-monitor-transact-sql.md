---
title: sp_help_log_shipping_monitor (Transact-sql) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_help_log_shipping_monitor_TSQL
- sp_help_log_shipping_monitor
dev_langs:
- TSQL
helpviewer_keywords:
- sp_help_log_shipping_monitor
ms.assetid: a4e96c45-6dcd-471a-a494-b5c619459855
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: d2b8fc2ac96821427aaf0ef2550fb6624a923d7f
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/27/2020
ms.locfileid: "68000937"
---
# <a name="sp_help_log_shipping_monitor-transact-sql"></a>sp_help_log_shipping_monitor(Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  주 서버, 보조 서버 또는 모니터 서버에 등록된 주 데이터베이스 및 보조 데이터베이스의 상태와 기타 정보를 포함하는 결과 집합을 반환합니다.  
  
 ![항목 링크 아이콘](../../database-engine/configure-windows/media/topic-link.gif "항목 링크 아이콘") [Transact-SQL 구문 표기 규칙](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>구문  
  
```  
  
sp_help_log_shipping_monitor  
```  
  
## <a name="arguments"></a>인수  
 없음  
  
## <a name="return-code-values"></a>반환 코드 값  
 **0** (성공) 또는 **1** (실패)  
  
## <a name="result-sets"></a>결과 집합  
  
|열 이름|데이터 형식|Description|  
|-----------------|---------------|-----------------|  
|**status**|**bit**|로그 전달 데이터베이스 에이전트의 전체 상태입니다.<br /><br /> **0** = 정상 및 에이전트 안 함 오류<br /><br /> **1** = 그렇지 않으면입니다.|  
|**is_primary**|**bit**|이 행이 주 데이터베이스에 대한 행인지 여부를 나타냅니다.<br /><br /> **1** = 주 데이터베이스에 대 한 행입니다.<br /><br /> **0** = 보조 데이터베이스에 대 한 행입니다.|  
|**서버인**|**sysname**|이 데이터베이스가 상주하는 주 서버 또는 보조 서버의 이름입니다.|  
|**database_name**|**sysname**|데이터베이스 이름입니다.|  
|**time_since_last_backup**|**int**|마지막 로그 백업 이후에 경과한 시간(분)입니다.<br /><br /> NULL = 정보를 사용할 수 없거나 관련이 없습니다.|  
|**last_backup_file**|**nvarchar (500)**|마지막 로그 백업 파일의 이름입니다.<br /><br /> NULL = 정보를 사용할 수 없거나 관련이 없습니다.|  
|**backup_threshold**|**int**|마지막 백업 후 threshold_alert 오류가 발생하기까지의 시간(분)입니다. **backup_threshold** 은 **int**이며 기본값은 **60 분**입니다.<br /><br /> NULL = 정보를 사용할 수 없거나 관련이 없습니다.<br /><br /> 이 값은 [sp_add_log_shipping_primary_database &#40;transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-add-log-shipping-primary-database-transact-sql.md)를 사용 하 여 변경할 수 있습니다.|  
|**is_backup_alert_enabled**|**bit**|**Backup_threshold** 를 초과할 때 경고가 발생 하는지 여부를 지정 합니다. 기본값인**1**은 경고가 발생 한다는 것을 의미 합니다.<br /><br /> NULL = 정보를 사용할 수 없거나 관련이 없습니다.<br /><br /> 이 값은 [sp_add_log_shipping_primary_database &#40;transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-add-log-shipping-primary-database-transact-sql.md)를 사용 하 여 변경할 수 있습니다.|  
|**time_since_last_copy**|**int**|마지막 로그 백업을 복사한 이후에 경과한 시간(분)입니다.<br /><br /> NULL = 정보를 사용할 수 없거나 관련이 없습니다.|  
|**last_copied_file**|**nvarchar (500)**|마지막으로 복사한 로그 백업 파일의 이름입니다.<br /><br /> NULL = 정보를 사용할 수 없거나 관련이 없습니다.|  
|**time_since_last_restore**|**int**|마지막 로그 백업을 복원한 이후에 경과한 시간(분)입니다.<br /><br /> NULL = 정보를 사용할 수 없거나 관련이 없습니다.|  
|**last_restored_file**|**nvarchar (500).**|마지막으로 복원한 로그 백업 파일의 이름입니다.<br /><br /> NULL = 정보를 사용할 수 없거나 관련이 없습니다.|  
|**last_restored_latency**|**int**|마지막 백업 생성에서 백업 복원 시까지의 기간(분)입니다.<br /><br /> NULL = 정보를 사용할 수 없거나 관련이 없습니다.|  
|**restore_threshold**|**int**|복원 작업 간 허용되는 시간(분)입니다. 이 시간이 지나면 경고가 발생합니다. **restore_threshold** 는 NULL 일 수 없습니다.|  
|**is_restore_alert_enabled**|**bit**|**Restore_threshold** 를 초과할 때 경고가 발생 하는지 여부를 지정 합니다. 기본값인**1**은 경고가 발생 한다는 것을 의미 합니다.<br /><br /> NULL = 정보를 사용할 수 없거나 관련이 없습니다.<br /><br /> 복원 임계값을 설정 하려면 [sp_add_log_shipping_secondary_database](../../relational-databases/system-stored-procedures/sp-add-log-shipping-secondary-database-transact-sql.md)을 사용 합니다.|  
  
## <a name="remarks"></a>설명  
 **sp_help_log_shipping_monitor** 는 모니터 서버에 있는 **master** 데이터베이스에서 실행 해야 합니다.  
  
## <a name="permissions"></a>사용 권한  
 **sysadmin** 고정 서버 역할의 멤버 자격이 필요합니다.  
  
## <a name="see-also"></a>참고 항목  
 [로그 전달 &#40;SQL Server&#41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md)   
 [시스템 저장 프로시저&#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
