---
title: MSmerge_history (TRANSACT-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSmerge_history_TSQL
- MSmerge_history
dev_langs:
- TSQL
helpviewer_keywords:
- MSmerge_history system table
ms.assetid: 936195ad-ca07-41a8-a1a0-6699b6e63403
author: stevestein
ms.author: sstein
ms.openlocfilehash: 7de3f8de87804facf6670cf0dd261464143c2aeb
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68017694"
---
# <a name="msmergehistory-transact-sql"></a>MSmerge_history(Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  합니다 **MSmerge_history** 테이블 자세한 설명은 이전 병합 에이전트 작업 세션 결과가 있는 기록 행을 포함 합니다. 이 테이블은 에이전트가 출력한 각 줄당 한 개의 행을 포함하며 배포 데이터베이스와 각 구독 데이터베이스에 사용됩니다. 배포 데이터베이스의 경우 이 테이블에는 배포자를 사용하는 모든 병합 게시 및 구독에 대한 기록이 포함되고, 각 구독 데이터베이스의 경우 이 테이블에는 구독자가 구독하는 게시에 대한 기록이 포함됩니다.  
  
|열 이름|데이터 형식|설명|  
|-----------------|---------------|-----------------|  
|**session_id**|**int**|병합 에이전트 작업의 ID입니다.|  
|**agent_id**|**int**|병합 에이전트의 ID입니다.|  
|**주석**|**nvarchar(255)**|메시지 텍스트입니다.|  
|**error_id**|**int**|오류 ID는 [MSrepl_errors](../../relational-databases/system-tables/msrepl-errors-transact-sql.md) 시스템 테이블입니다.|  
|**timestamp**|**timestamp**|이 테이블의 타임스탬프 열입니다.|  
|**updatable_row**|**bit**|로 **1** 기록 행을 덮어쓸 수 있는 경우.|  
  
## <a name="see-also"></a>관련 항목  
 [복제 테이블 &#40;TRANSACT-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [복제 뷰&#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
