---
description: log_shipping_monitor_alert(Transact-SQL)
title: log_shipping_monitor_alert (Transact-sql) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- log_shipping_monitor_alert
- log_shipping_monitor_alert_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- log_shipping_monitor_alert system table
ms.assetid: 1c775e48-9898-4149-b9d1-04d465f23438
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 0251792954c4d6a534ae6175843192619e8de8ff
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89525653"
---
# <a name="log_shipping_monitor_alert-transact-sql"></a>log_shipping_monitor_alert(Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  로그 전달에 대한 경고 작업 ID를 저장합니다. 이 테이블은 **msdb** 데이터베이스에 저장 됩니다.   
  
|열 이름|데이터 형식|Description|  
|-----------------|---------------|-----------------|  
|**alert_job_id**|**uniqueidentifier**|로그 전달 경고 작업의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 작업 ID입니다.|  
  
## <a name="see-also"></a>참고 항목  
 [로그 전달 정보&#40;SQL Server&#41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md)   
 [Transact-sql&#41;sp_add_log_shipping_alert_job &#40;](../../relational-databases/system-stored-procedures/sp-add-log-shipping-alert-job-transact-sql.md)   
 [Transact-sql&#41;sp_delete_log_shipping_alert_job &#40;](../../relational-databases/system-stored-procedures/sp-delete-log-shipping-alert-job-transact-sql.md)   
 [Transact-sql&#41;sp_help_log_shipping_alert_job &#40;](../../relational-databases/system-stored-procedures/sp-help-log-shipping-alert-job-transact-sql.md)   
 [시스템 테이블&#40;Transact-SQL&#41;](../../relational-databases/system-tables/system-tables-transact-sql.md)  
  
  
