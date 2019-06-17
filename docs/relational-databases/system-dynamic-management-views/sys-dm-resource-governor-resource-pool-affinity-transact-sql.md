---
title: sys.dm_resource_governor_resource_pool_affinity (TRANSACT-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_resource_governor_resource_pool_affinity_TSQL
- sys.dm_resource_governor_resource_pool_affinity
- dm_resource_governor_resource_pool_affinity
- dm_resource_governor_resource_pool_affinity_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- dm_resource_governor_resource_pool_affinity
- sys.dm_resource_governor_resource_pool_affinity
ms.assetid: a197ec19-a2ba-44f5-a4f2-3eee33ebd77d
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 547a1dd14eab2a5627dbd8e3b8b6e09a4c5143b1
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62680292"
---
# <a name="sysdmresourcegovernorresourcepoolaffinity-transact-sql"></a>sys.dm_resource_governor_resource_pool_affinity(Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  리소스 풀 선호도를 추적합니다.  
  
 ![항목 링크 아이콘](../../database-engine/configure-windows/media/topic-link.gif "항목 링크 아이콘") [Transact-SQL 구문 규칙](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
|열 이름|데이터 형식|Description|  
|----------------|---------------|-----------------|  
|Pool_id|**int**|리소스 풀의 ID입니다. Null을 허용하지 않습니다.|  
|Processor_group|**smallint**|Windows 논리 프로세서 그룹의 ID입니다. Null을 허용하지 않습니다.|  
|Scheduler_mask|**bigint**|이 풀과 연결된 스케줄러를 나타내는 이진 마스크입니다. Null을 허용하지 않습니다.|  
  
## <a name="remarks"></a>Remarks  
 AUTO의 선호도를 사용하여 만든 풀은 선호도가 없기 때문에 이 뷰에 표시되지 않습니다. 자세한 내용은 참조 하세요. 합니다 [CREATE RESOURCE POOL &#40;TRANSACT-SQL&#41; ](../../t-sql/statements/create-resource-pool-transact-sql.md) 및 [ALTER RESOURCE POOL &#40;TRANSACT-SQL&#41; ](../../t-sql/statements/alter-resource-pool-transact-sql.md) 문.  
  
## <a name="see-also"></a>관련 항목  
 [sys.dm_resource_governor_external_resource_pool_affinity&#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-external-resource-pool-affinity-transact-sql.md)  
  
  
