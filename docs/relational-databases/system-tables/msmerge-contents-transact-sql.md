---
title: MSmerge_contents (TRANSACT-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSmerge_contents
- MSmerge_contents_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSmerge_contents system table
ms.assetid: 8d68a61a-683f-4b20-92f9-c0a8d9ba0ad1
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: e5aa95edeb1a947aea517de30efcbbbc3c6c799c
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/03/2018
ms.locfileid: "52750385"
---
# <a name="msmergecontents-transact-sql"></a>MSmerge_contents(Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  합니다 **MSmerge_contents** 테이블 게시 된 후 현재 데이터베이스에서 수정 된 각 행에 대 한 하나의 행을 포함 합니다. 이 테이블은 병합 프로세스에서 변경된 행을 확인하는 데 사용됩니다. 이 테이블은 게시 및 구독 데이터베이스에 저장됩니다.  
  
|열 이름|데이터 형식|Description|  
|-----------------|---------------|-----------------|  
|**tablenick**|**int**|게시된 테이블의 애칭입니다.|  
|**rowguid**|**uniqueidentifier**|지정된 행의 행 식별자입니다.|  
|**generation**|**bigint**|식별 된 행을 생성 합니다 **tablenick** 하 고 **rowguid**합니다.|  
|**partchangegen**|**bigint**|행이 필터링된 게시에 속하는지 여부를 변경할 수 있는 마지막 데이터 변경에 관련된 생성입니다.|  
|**계보**|**varbinary(501)**|이 행에 대한 변경 기록을 유지 관리하기 위해 사용하는 구독자 애칭과 버전 번호 쌍입니다.|  
|**colvl**|**varbinary(7489)**|열의 버전 정보입니다.|  
|**표식**|**uniqueidentifier**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**logical_record_parent_rowguid**|**uniqueidentifier**|최상위 부모 행을 식별 **MSmerge_contents** (의해 **rowguid**) 논리적 레코드에서 각 해당 자식 행에 대 한 합니다.|  
|**logical_record_lineage**|**varbinary(501)**|논리적 레코드의 최상위 부모 행에 대한 변경 기록을 유지 관리하기 위해 사용하는 구독자 애칭과 버전 번호 쌍입니다. 논리적 레코드의 모든 자식 행에 대한 이 값은 NULL입니다.|  
|**logical_relation_change_gen**|**bigint**|논리적 레코드에서 기존 행을 논리적 레코드 안팎으로 이동시켜 다시 맞추도록 만든 마지막 변경과 관련된 생성 값입니다.|  
  
## <a name="see-also"></a>관련 항목  
 [복제 테이블 &#40;TRANSACT-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [복제 뷰&#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
