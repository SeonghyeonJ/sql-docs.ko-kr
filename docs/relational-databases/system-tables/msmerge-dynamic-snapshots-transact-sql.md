---
title: MSmerge_dynamic_snapshots (TRANSACT-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSmerge_dynamic_snapshots_TSQL
- MSmerge_dynamic_snapshots
dev_langs:
- TSQL
helpviewer_keywords:
- MSmerge_dynamic_snapshots system table
ms.assetid: a5592b3c-731b-4fc9-ae4b-2602ed78248e
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: f7e41f604bf9d87b2db0b22749f58ee7fd2acf2b
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/03/2018
ms.locfileid: "52791815"
---
# <a name="msmergedynamicsnapshots-transact-sql"></a>MSmerge_dynamic_snapshots(Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  합니다 **MSmerge_dynamic_snapshots** 매개 변수가 있는 행 필터를 사용 하 여 병합 게시에 대해 정의 된 각 파티션에 대 한 필터링 된 데이터 스냅숏의 위치를 추적 합니다. 이 테이블에 저장 되는 **게시** 데이터베이스입니다.  
  
|열 이름|데이터 형식|Description|  
|-----------------|---------------|-----------------|  
|**partition_id**|**int**|병합 파티션의 ID입니다.|  
|**dynamic_snapshot_location**|**nvarchar(255)**|파티션에 대한 필터링된 데이터 스냅숏의 위치입니다.|  
|**last_updated**|**datetime**|필터링된 데이터 스냅숏을 새로 고친 날짜입니다.|  
  
## <a name="see-also"></a>관련 항목  
 [복제 테이블&#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)  
  
  
