---
title: MSpub_identity_range (Transact-sql) | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSpub_identity_range_TSQL
- MSpub_identity_range
dev_langs:
- TSQL
helpviewer_keywords:
- MSpub_identity_range system table
ms.assetid: 68746eef-32e1-42bc-aff0-9798cd0e88b8
author: stevestein
ms.author: sstein
ms.openlocfilehash: b1b204024d65e72eb65eefc9f63f914eab6ace29
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/27/2020
ms.locfileid: "68032605"
---
# <a name="mspub_identity_range-transact-sql"></a>MSpub_identity_range(Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MSpub_identity_range** 테이블은 id 범위 관리 지원을 제공 합니다. 이 테이블은 게시 데이터베이스 및 구독 데이터베이스에 저장됩니다.  
  
|열 이름|데이터 형식|Description|  
|-----------------|---------------|-----------------|  
|**objid**|**int**|복제에 의해 관리되는 ID 열이 있는 테이블의 ID입니다.|  
|**벗어납니다**|**bigint**|조정할 때 구독에 할당될 연속 ID 값의 범위 크기를 제어합니다.|  
|**pub_range**|**bigint**|조정할 때 게시에 할당될 연속 ID 값의 범위 크기를 제어합니다.|  
|**current_pub_range**|**bigint**|게시가 현재 사용하고 있는 범위입니다. **Sp_changearticle** 변경 후와 다음 범위 조정 전에 볼 경우 *pub_range* 와 다를 수 있습니다.|  
|**고대비**|**int**|배포 에이전트가 새 ID 범위를 할당하는 시점을 제어하는 비율 값입니다. *임계값* 에 지정 된 값의 백분율을 사용 하는 경우 배포 에이전트 새 id 범위를 만듭니다.|  
|**last_seed**|**bigint**|현재 범위의 하한입니다.|  
  
## <a name="see-also"></a>참고 항목  
 [Transact-sql&#41;&#40;복제 테이블](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [복제 뷰&#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
