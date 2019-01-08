---
title: MSpub_identity_range (TRANSACT-SQL) | Microsoft Docs
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
manager: craigg
ms.openlocfilehash: a60ae0e3cd8fb4a07ac9a947a8e4a7ea692d9b26
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/03/2018
ms.locfileid: "52821847"
---
# <a name="mspubidentityrange-transact-sql"></a>MSpub_identity_range(Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  합니다 **MSpub_identity_range** 테이블은 id 범위 관리 지원을 제공 합니다. 이 테이블은 게시 데이터베이스 및 구독 데이터베이스에 저장됩니다.  
  
|열 이름|데이터 형식|Description|  
|-----------------|---------------|-----------------|  
|**objid**|**int**|복제에 의해 관리되는 ID 열이 있는 테이블의 ID입니다.|  
|**range**|**bigint**|조정할 때 구독에 할당될 연속 ID 값의 범위 크기를 제어합니다.|  
|**pub_range**|**bigint**|조정할 때 게시에 할당될 연속 ID 값의 범위 크기를 제어합니다.|  
|**current_pub_range**|**bigint**|게시가 현재 사용하고 있는 범위입니다. 보다 다를 수 있습니다 *pub_range* 후 볼 경우 **sp_changearticle** 전과 다음 범위 조정 합니다.|  
|**threshold**|**int**|배포 에이전트가 새 ID 범위를 할당하는 시점을 제어하는 비율 값입니다. 에 지정 된 값의 백분율 *임계값* 는 사용, 배포 에이전트가 새 id 범위를 만듭니다.|  
|**last_seed**|**bigint**|현재 범위의 하한입니다.|  
  
## <a name="see-also"></a>관련 항목  
 [복제 테이블 &#40;TRANSACT-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [복제 뷰&#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
