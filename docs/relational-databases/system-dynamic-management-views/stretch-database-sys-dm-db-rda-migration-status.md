---
title: sys.dm_db_rda_migration_status (TRANSACT-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: language-reference
f1_keywords:
- sys.dm_db_rda_migration_status
- sys.dm_db_rda_migration_status_TSQL
- dm_db_rda_migration_status
- dm_db_rda_migration_status_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_db_rda_migration_status dynamic management view
ms.assetid: faf3901c-a0e0-4e0c-8b1b-86d9f15f34dd
author: pmasl
ms.author: pelopes
ms.openlocfilehash: 21e5230e4f3efd86fe90382202f0b21a0187a214
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67937068"
---
# <a name="stretch-database---sysdmdbrdamigrationstatus"></a>Stretch Database - sys.dm_db_rda_migration_status
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  각 일괄 처리의 로컬 인스턴스에서 각 스트레치 사용 테이블에서 마이그레이션된 데이터의 행이 하나씩 들어 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]합니다. 일괄 처리의 시작 시간과 종료 시간으로 식별 됩니다.  
  
 **sys.dm_db_rda_migration_status** 범위 현재 데이터베이스 컨텍스트를 지정 합니다. 마이그레이션 상태를 보려는 스트레치 사용 테이블의 데이터베이스 컨텍스트에 있는지 확인 합니다.  
  
 [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)], 출력 **sys.dm_db_rda_migration_status** 200 개 행으로 제한 됩니다.  
  
|열 이름|데이터 형식|설명|  
|-----------------|---------------|-----------------|  
|**table_id**|**int**|행 마이그레이션된 테이블의 ID입니다.|  
|**database_id**|**int**|행 마이그레이션된 데이터베이스의 ID입니다.|  
|**migrated_rows**|**bigint**|행 수가이 일괄 처리에서 마이그레이션.|  
|**start_time_utc**|**datetime**|일괄 처리가 시작 된 UTC 시간입니다.|  
|**end_time_utc**|**datetime**|일괄 처리의 완료는 UTC 시간입니다.|  
|**error_number**|**int**|일괄 처리에 실패 하면 발생 한 오류의 오류 번호 그렇지 않으면 null입니다.|  
|**error_severity**|**int**|일괄 처리에 실패 하면 발생 한 오류의 심각도 그렇지 않으면 null입니다.|  
|**error_state**|**int**|일괄 처리에 실패 하면 발생 한 오류의 상태 그렇지 않으면 null입니다.<br /><br /> 합니다 **error_state** 조건 또는 오류가 발생 하는 위치를 나타냅니다.|  
  
## <a name="see-also"></a>관련 항목  
 [Stretch Database](../../sql-server/stretch-database/stretch-database.md)  
  
  
