---
title: sys.dm_os_memory_cache_clock_hands (TRANSACT-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 12/21/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_os_memory_cache_clock_hands_TSQL
- dm_os_memory_cache_clock_hands
- dm_os_memory_cache_clock_hands_TSQL
- sys.dm_os_memory_cache_clock_hands
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_os_memory_cache_clock_hands dynamic management view
ms.assetid: 0660eddc-691c-425f-9d43-71151d644de7
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 6b39f40a36a9b9a639b8b6c90f6a6a37f7a32a4e
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63047189"
---
# <a name="sysdmosmemorycacheclockhands-transact-sql"></a>sys.dm_os_memory_cache_clock_hands(Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  특정 캐시 클럭의 각 포인터 상태를 반환합니다.  
  
> [!NOTE]  
>  이를 호출 하 [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] 나 [!INCLUDE[ssPDW](../../includes/sspdw-md.md)], 이름을 사용 하 여 **sys.dm_pdw_nodes_os_memory_cache_clock_hands**합니다.  
  
|열 이름|데이터 형식|Description|  
|-----------------|---------------|-----------------|  
|**cache_address**|**varbinary(8)**|클럭과 연관된 캐시의 주소입니다. Null을 허용하지 않습니다.|  
|**name**|**nvarchar(256)**|캐시의 이름입니다. Null을 허용하지 않습니다.|  
|**type**|**nvarchar(60)**|캐시 저장소의 유형입니다. 유형이 같은 캐시가 여러 개 있을 수 있습니다. Null을 허용하지 않습니다.|  
|**clock_hand**|**nvarchar(60)**|포인터의 유형입니다. 다음 중 하나일 수 있습니다.<br /><br /> External<br /><br /> 내부<br /><br /> Null을 허용하지 않습니다.|  
|**clock_status**|**nvarchar(60)**|클럭의 상태입니다. 다음 중 하나일 수 있습니다.<br /><br /> Suspended<br /><br /> 실행 중<br /><br /> Null을 허용하지 않습니다.|  
|**rounds_count**|**bigint**|항목을 제거하기 위해 캐시를 통해 이루어진 스윕 횟수입니다. Null을 허용하지 않습니다.|  
|**removed_all_rounds_count**|**bigint**|모든 스윕을 통해 제거된 항목 수입니다. Null을 허용하지 않습니다.|  
|**updated_last_round_count**|**bigint**|마지막 스윕 동안 업데이트된 항목 수입니다. Null을 허용하지 않습니다.|  
|**removed_last_round_count**|**bigint**|마지막 스윕 동안 제거된 항목 수입니다. Null을 허용하지 않습니다.|  
|**last_tick_time**|**bigint**|마지막으로 클럭 포인터가 이동한 시간(밀리초)입니다. Null을 허용하지 않습니다.|  
|**round_start_time**|**bigint**|이전 스윕의 시간(밀리초)입니다. Null을 허용하지 않습니다.|  
|**last_round_start_time**|**bigint**|클럭이 이전 라운드를 완료하는 데 걸린 총 시간(밀리초)입니다. Null을 허용하지 않습니다.|  
|**pdw_node_id**|**int**|**적용 대상**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)], [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> 이 배포에 있는 노드에 대 한 식별자입니다.|  
  
## <a name="permissions"></a>사용 권한  

온 [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], 필요한 `VIEW SERVER STATE` 권한.   
온 [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)], 필요를 `VIEW DATABASE STATE` 데이터베이스의 권한.   
  
## <a name="remarks"></a>Remarks  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서는 메모리 캐시라는 구조의 메모리에 정보를 저장합니다. 캐시의 정보는 데이터, 인덱스 항목, 컴파일된 프로시저 계획 및 다양한 유형의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 정보일 수 있습니다. 정보가 다시 생성되지 않도록 하기 위해 가능한 한 오랫동안 메모리 캐시에 정보가 보관되며 정보가 너무 오래되어서 유용하지 않거나 새 정보를 위해 메모리 공간이 필요한 경우 일반적으로 캐시에서 정보가 제거됩니다. 이전 정보를 제거하는 프로세스를 메모리 스윕이라고 합니다. 메모리 스윕 작업은 자주 수행될 수 있지만 연속적으로 수행되지 않습니다. 메모리 캐시의 스윕은 클럭 알고리즘으로 제어됩니다. 각 클럭에서 포인터라고 하는 메모리 스윕을 여러 개 제어할 수 있습니다. 메모리 캐시 클럭 포인터는 메모리 스윕 그룹 중 하나의 현재 위치입니다.  

## <a name="see-also"></a>관련 항목  
 [SQL Server 운영 체제 관련 동적 관리 뷰 &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-server-operating-system-related-dynamic-management-views-transact-sql.md)    
 [sys.dm_os_memory_cache_counters &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-memory-cache-counters-transact-sql.md)
  

