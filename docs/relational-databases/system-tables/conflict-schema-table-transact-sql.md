---
title: conflict_&lt;스키마&gt;_&lt;테이블&gt; (TRANSACT-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 01/15/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- conflict_
- conflict_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- conflict_<schema>_<table>
ms.assetid: 15ddd536-db03-454e-b9b5-36efe1f756d7
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: dd226aef62c2d05eead5e2b5f72b2f358422025a
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/03/2018
ms.locfileid: "52808905"
---
# <a name="conflictltschemagtlttablegt-transact-sql"></a>conflict_&lt;스키마&gt;_&lt;테이블&gt; (Transact SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  conflict_\<스키마 > _\<테이블 > 테이블이 피어 투 피어 복제에서 충돌 하는 행에 대 한 정보를 포함 합니다. 스키마 안에 각 복제 테이블에 대한 충돌 테이블이 존재하는데 충돌 테이블 이름 끝에 게시 및 아티클 이름이 붙습니다. 이러한 아티클별 충돌 테이블은 각 게시 데이터베이스 존재합니다.  
  
 피어 투 피어 복제의 경우 충돌이 감지되면 기본적으로 배포 에이전트가 실패합니다. 오류 로그에 충돌 오류가 기록되지만 충돌 테이블에는 충돌 데이터가 기록되지 않으므로 해당 데이터를 볼 수 없습니다. 배포 에이전트가 계속할 수 있으면 충돌이 감지된 각 노드에 로컬로 충돌이 기록됩니다. 자세한 내용은 [Conflict Detection in Peer-to-Peer Replication](../../relational-databases/replication/transactional/peer-to-peer-conflict-detection-in-peer-to-peer-replication.md)의 "충돌 처리"를 참조하십시오.  
  
|열 이름|데이터 형식|Description|  
|-----------------|---------------|-----------------|  
|__$originator_id|**int**|충돌을 일으키는 변경이 시작된 노드의 ID입니다. 실행 id 목록을 [sp_help_peerconflictdetection](../../relational-databases/system-stored-procedures/sp-help-peerconflictdetection-transact-sql.md)합니다.|  
|__$origin_datasource|**int**|충돌을 일으키는 변경이 시작된 노드입니다.|  
|__$tranid|**nvarchar (40)**|__$origin_datasource에 적용될 때 충돌의 일으키는 변경의 LSN(로그 시퀀스 번호)입니다.|  
|__$conflict_type|**int**|충돌의 유형이며 다음 값 중 하나일 수 있습니다.<br /><br /> 1: 로컬 행이 다른 업데이트에 의해 변경되었거나 삭제된 후 다시 삽입되었기 때문에 업데이트가 실패했습니다.<br /><br /> 2: 로컬 행이 이미 삭제되었기 때문에 업데이트가 실패했습니다.<br /><br /> 3: 로컬 행이 다른 업데이트에 의해 변경되었거나 삭제된 후 다시 삽입되었기 때문에 삭제가 실패했습니다.<br /><br /> 4: 로컬 행이 이미 삭제되었기 때문에 삭제가 실패했습니다.<br /><br /> 5: 로컬 행이 이미 삽입되었거나 삽입된 후 업데이트되었기 때문에 삽입이 실패했습니다.|  
|__$is_winner|**bit**|이 테이블의 행이 충돌 시 우선 적용되는지, 즉 로컬 노드에 적용되는지 여부를 나타냅니다.|  
|__$pre_version|**varbinary (32)**|충돌을 일으키는 변경이 시작된 데이터베이스 버전입니다.|  
|__$reason_code|**int**|충돌 상태를 나타내는 코드이며 다음 값 중 하나입니다.<br /><br /> 0<br /><br /> 1<br /><br /> 2<br /><br /> <br /><br /> 자세한 내용은 **__ $reason_text**합니다.|  
|__$reason_text|**nvarchar (720)**|충돌 상태를 나타내는 텍스트이며 다음 값 중 하나입니다.<br /><br /> Resolved (1)<br /><br /> Unresolved (2)<br /><br /> Unknown (0)|  
|__$update_bitmap|**varbinary (** *n* **)** 합니다. 크기가 내용에 따라 달라 집니다.|업데이트/업데이트 충돌이 발생했을 때 업데이트된 열을 나타내는 비트맵입니다.|  
|__$inserted_date|**datetime**|충돌을 일으키는 행이 이 테이블에 삽입된 날짜와 시간입니다.|  
|__$row_id|**timestamp**|충돌을 일으키는 행과 연관된 행 버전입니다.|  
|__$change_id|**이진 (8)**|로컬 행의 경우 이 값은 해당 로컬 행과 충돌하는 들어오는 행의 __$row_id에 해당합니다. 들어오는 행의 경우 이 값은 NULL입니다.|  
|\<기본 테이블 열 이름 >|\<기본 테이블 열 형식 >|충돌 테이블에는 기본 테이블에 있는 각 열에 대한 열이 하나씩 있습니다.|  
  
## <a name="see-also"></a>관련 항목  
 [복제 테이블 &#40;TRANSACT-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [복제 뷰&#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
