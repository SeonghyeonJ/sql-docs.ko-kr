---
description: logmarkhistory(Transact-SQL)
title: logmarkhistory (Transact-sql) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- logmarkhistory
- logmarkhistory_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- logmarkhistory system table
ms.assetid: 5c1becc5-f34e-4869-bf69-dfafab684540
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: d52c161baa58924a21966ed4c354fa614e677062
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88419157"
---
# <a name="logmarkhistory-transact-sql"></a>logmarkhistory(Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  표시되어 있는 각각의 커밋된 트랜잭션에 대해 하나의 행을 포함합니다. 이 테이블은 **msdb** 데이터베이스에 저장 됩니다.  
  

|열 이름|데이터 형식|Description|  
|-----------------|---------------|-----------------|  
|**database_name**|**nvarchar(128)**|표시된 트랜잭션이 일어나는 로컬 데이터베이스입니다.|  
|**mark_name**|**nvarchar(128)**|표시된 트랜잭션에 대한 사용자 제공 이름입니다.|  
|**description**|**nvarchar(255)**|표시된 트랜잭션의 사용자 제공 설명입니다. NULL일 수 있습니다.|  
|**user_name**|**nvarchar(128)**|표시된 트랜잭션을 실행하는 데이터베이스 사용자 이름입니다. NULL일 수 있습니다.|  
|**lsn**|**numeric(25,0)**|표시되는 트랜잭션 레코드의 로그 시퀀스 번호입니다.|  
|**mark_time**|**datetime**|표시된 트랜잭션의 커밋 시간입니다(현지 시간).|  
  
## <a name="see-also"></a>참고 항목  
 [데이터베이스를 표시된 트랜잭션으로 복원&#40;SQL Server Management Studio&#41;](../../relational-databases/backup-restore/restore-a-database-to-a-marked-transaction-sql-server-management-studio.md)   
 [표시된 트랜잭션을 사용하여 관련 데이터베이스를 일관되게 복구&#40;전체 복구 모델&#41;](../../relational-databases/backup-restore/use-marked-transactions-to-recover-related-databases-consistently.md)   
 [시스템 테이블&#40;Transact-SQL&#41;](../../relational-databases/system-tables/system-tables-transact-sql.md)  
  
  
