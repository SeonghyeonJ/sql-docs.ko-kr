---
title: sys.dm_resource_governor_resource_pool_volumes (TRANSACT-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_resource_governor_resource_pool_volumes_TSQL
- dm_resource_governor_resource_pool_volumes_TSQL
- dm_resource_governor_resource_pool_volumes
- sys.dm_resource_governor_resource_pool_volumes
dev_langs:
- TSQL
helpviewer_keywords:
- dm_resource_governor_resource_pool_volumes
- sys.dm_resource_governor_resource_pool_volumes
ms.assetid: fa692e56-c561-4533-97c5-bc12c600553f
author: stevestein
ms.author: sstein
ms.openlocfilehash: 801997509242bae7af2d2ae438dfdb952be9e1fe
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68090810"
---
# <a name="sysdmresourcegovernorresourcepoolvolumes-transact-sql"></a>sys.dm_resource_governor_resource_pool_volumes (Transact SQL)
[!INCLUDE[tsql-appliesto-ss2014-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2014-xxxx-xxxx-xxx-md.md)]

  각 디스크 볼륨의 현재 리소스 풀 IO 통계에 관한 정보를 반환합니다. 리소스 풀 수준에서이 정보를 확인할 수도 [sys.dm_resource_governor_resource_pools &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-resource-pools-transact-sql.md)합니다.  
  
  
|열 이름|데이터 형식|설명|  
|-----------------|---------------|-----------------|  
|pool_id|**int**|리소스 풀의 ID입니다. Null을 허용하지 않습니다.|  
|volume_name|**sysname**|디스크 volue의 이름입니다. Null을 허용하지 않습니다.|  
|read_io_queued_total|**int**|리소스 관리자를 다시 설정한 후 큐에 놓인 총 읽기 IO입니다. Null을 허용하지 않습니다.|  
|read_io_issued_total|**int**|리소스 관리자 통계를 다시 설정한 후 발생한 총 읽기 IO입니다. Null을 허용하지 않습니다.|  
|read_ios_completed_total|**int**|리소스 관리자 통계를 다시 설정한 후 완료된 총 읽기 IO입니다. Null을 허용하지 않습니다.|  
|read_ios_throttled_total|**int**|리소스 관리자 통계를 다시 설정한 후 정체된 총 읽기 IO입니다. Null을 허용하지 않습니다.|  
|read_bytes_total|**bigint**|리소스 관리자 통계를 다시 설정한 후 읽은 총 바이트 수입니다. Null을 허용하지 않습니다.|  
|read_io_stall_total_ms|**bigint**|읽기 IO 도착과 완료 사이의 총 시간(밀리초)입니다. Null을 허용하지 않습니다.|  
|read_io_stall_queued_ms|**bigint**|읽기 IO 도착과 완료 사이의 총 시간(밀리초)입니다. IO 리소스 관리로 인해 발생한 지연 시간입니다. Null을 허용하지 않습니다.|  
|write_io_queued_total|**int**|리소스 관리자 통계를 다시 설정한 후 큐에 놓인 총 쓰기 IO입니다. Null을 허용하지 않습니다.|  
|write_io_issued_total|**int**|리소스 관리자 통계를 다시 설정한 후 발생한 총 쓰기 IO입니다. Null을 허용하지 않습니다.|  
|write_io_completed_total|**int**|리소스 관리자 통계를 다시 설정한 후 완료된 총 쓰기 IO입니다. Null을 허용하지 않습니다.|  
|write_io_throttled_total|**int**|리소스 관리자 통계를 다시 설정한 후 정체된 총 쓰기 IO입니다. Null을 허용하지 않습니다.|  
|write_bytes_total|**bigint**|리소스 관리자 통계를 다시 설정한 후 쓴 총 바이트 수입니다. Null을 허용하지 않습니다.|  
|write_io_stall_total_ms|**bigint**|쓰기 IO 발생과 완료 사이의 총 시간(밀리초)입니다. Null을 허용하지 않습니다.|  
|write_io_stall_queued_ms|**bigint**|쓰기 IO 도착과 완료 사이의 총 시간(밀리초)입니다. IO 리소스 관리로 인해 발생한 지연 시간입니다. Null을 허용하지 않습니다.|  
|io_issue_violations_total|**int**|총 IO 실행 위반 수입니다. 즉, IO 실행 속도가 예약된 속도보다 낮았던 횟수입니다. Null을 허용하지 않습니다.|  
|io_issue_delay_total_ms|**bigint**|예약된 IO 실행과 실제 IO 실행 사이의 총 시간(밀리초)입니다. Null을 허용하지 않습니다.|  
  
## <a name="permissions"></a>사용 권한  
 VIEW SERVER STATE 권한이 필요합니다.  
  
## <a name="see-also"></a>참조  
 [동적 관리 뷰 및 함수&#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [sys.dm_resource_governor_workload_groups&#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-workload-groups-transact-sql.md)   
 [sys.resource_governor_resource_pools &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-resource-governor-resource-pools-transact-sql.md)   
 [ALTER RESOURCE GOVERNOR&#40;Transact-SQL&#41;](../../t-sql/statements/alter-resource-governor-transact-sql.md)  
  
  

