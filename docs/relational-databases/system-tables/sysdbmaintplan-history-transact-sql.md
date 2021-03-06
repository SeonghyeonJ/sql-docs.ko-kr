---
description: sysdbmaintplan_history(Transact-SQL)
title: sysdbmaintplan_history (Transact-sql) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sysdbmaintplan_history_TSQL
- sysdbmaintplan_history
dev_langs:
- TSQL
helpviewer_keywords:
- sysdbmaintplan_history system table
ms.assetid: 02d36f08-ac93-4463-bb59-284c5cd6ed04
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 473e98da465aa9952261ae3c57d77ab9b5d2629e
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89517794"
---
# <a name="sysdbmaintplan_history-transact-sql"></a>sysdbmaintplan_history(Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  이 테이블은 **msdb** 데이터베이스에 저장 됩니다.  
  
 [!INCLUDE[ssNoteDepNextAvoid](../../includes/ssnotedepnextavoid-md.md)]  
  
  
|열 이름|데이터 형식|Description|  
|-----------------|---------------|-----------------|  
|**sequence_id**|**int**|데이터베이스 유지 관리 계획이 실행한 기록의 시퀀스입니다.|  
|**plan_id**|**uniqueidentifier**|데이터베이스 유지 관리 계획 ID입니다.|  
|**plan_name**|**sysname**|데이터베이스 유지 관리 계획 이름입니다.|  
|**database_name**|**sysname**|데이터베이스 유지 관리 계획과 연관된 데이터베이스의 이름입니다.|  
|**server_name**|**sysname**|시스템 이름입니다.|  
|**activity**|**nvarchar(128)**|데이터베이스 유지 관리 계획(예: 백업 트랜잭션 로그)이 수행한 작업입니다.|  
|**succeeded**|**bit**|**0** = 성공 **1** = 실패|  
|**end_time**|**datetime**|동작이 완료된 시간입니다.|  
|**duration**|**int**|데이터베이스 유지 관리 계획 동작을 완료하는 데 필요한 시간입니다.|  
|**start_time**|**datetime**|동작이 시작된 시간입니다.|  
|**error_number**|**int**|실패 시 보고된 오류 번호입니다.|  
|**message**|**nvarchar(512)**|**Sqlmaint**에 의해 생성 된 메시지입니다.|  
  
  
