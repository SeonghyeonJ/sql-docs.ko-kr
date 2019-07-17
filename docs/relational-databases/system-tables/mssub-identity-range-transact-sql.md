---
title: MSsub_identity_range (TRANSACT-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSsub_identity_range_TSQL
- MSsub_identity_range
dev_langs:
- TSQL
helpviewer_keywords:
- MSsub_identity_range system table
ms.assetid: 26e20d28-14ed-44fc-af3b-4de386de4bb8
author: stevestein
ms.author: sstein
ms.openlocfilehash: 4ec1f915e7cc70cb2d8ed0f09a9b0394dc7e09aa
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68221961"
---
# <a name="mssubidentityrange-transact-sql"></a>MSsub_identity_range(Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  합니다 **MSsub_identity_range** 표에서 구독에 대 한 id 범위 관리 지원을 제공 합니다. 이 테이블은 구독 데이터베이스에 저장됩니다.  
  
|열 이름|데이터 형식|설명|  
|-----------------|---------------|-----------------|  
|**objid**|**int**|복제에 의해 관리되는 ID 열이 있는 테이블의 ID입니다.|  
|**range**|**bigint**|조정 시 구독자에 할당될 연속 ID 값의 범위 크기를 제어합니다.|  
|**last_seed**|**bigint**|현재 범위의 하한입니다.|  
|**threshold**|**int**|배포 에이전트가 새 ID 범위를 할당하는 시점을 제어하는 비율 값입니다. 에 지정 된 값의 백분율 *임계값* 는 사용, 배포 에이전트가 새 id 범위를 만듭니다.|  
  
## <a name="see-also"></a>관련 항목  
 [복제 테이블 &#40;TRANSACT-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [복제 뷰&#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
