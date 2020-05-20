---
title: sys. dm_xtp_gc_stats (Transact-sql) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_xtp_gc_stats
- dm_xtp_gc_stats_TSQL
- sys.dm_xtp_gc_stats_TSQL
- sys.dm_xtp_gc_stats
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_xtp_gc_stats dynamic management view
ms.assetid: 8287d611-50e3-43e1-ba8d-3e3793d3ba0e
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 2e9e9502dda9eab45c27065c37b31109c99c4c4f
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/05/2020
ms.locfileid: "82829027"
---
# <a name="sysdm_xtp_gc_stats-transact-sql"></a>sys.dm_xtp_gc_stats(Transact-SQL)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

  [!INCLUDE[hek_2](../../includes/hek-2-md.md)] 가비지 수집 프로세스의 현재 동작에 대한 정보(전체 통계)를 제공합니다.  
  
 행은 정기적인 트랜잭션 처리의 일부로 또는 유휴 작업자라고 하는 기본 가비지 수집 스레드에서 수집되는 가비지입니다. 사용자 트랜잭션이 커밋되면 가비지 수집 큐 ([dm_xtp_gc_queue_stats &#40;transact-sql&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-xtp-gc-queue-stats-transact-sql.md))에서 하나의 작업 항목을 큐에서 제거 합니다. 가비지 수집될 수 있지만 기본 사용자 트랜잭션에 의해 액세스되지 않는 모든 행은 불량 영역 검색(더 적게 액세스되는 인덱스 영역 검색)의 일부로 유휴 작업자에 의해 가비지 수집됩니다.  
  
 자세한 내용은 [메모리 내 OLTP&#40;메모리 내 최적화&#41;](../../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)를 참조하세요.  
  
|열 이름|형식|설명|  
|-----------------|----------|-----------------|  
|rows_examined|**bigint**|서버 시작 이후 가비지 수집 하위 시스템에 의해 검사되는 행의 수입니다.|  
|rows_no_sweep_needed|**bigint**|불량 영역 검색 없이 제거된 행 수입니다.|  
|rows_first_in_bucket|**bigint**|해시 버킷의 첫 번째 행이었던 가비지 수집에 의해 검사되는 행의 수입니다.|  
|rows_first_in_bucket_removed|**bigint**|제거된 해시 버킷의 첫 번째 행이었던 가비지 수집에 의해 검사되는 행의 수입니다.|  
|rows_marked_for_unlink|**bigint**|ref count =0인 인덱스에서 이미 연결이 해제된 것으로 표시된 가비지 수집에 의해 검사되는 행의 수입니다.|  
|parallel_assist_count|**bigint**|사용자 트랜잭션당 처리되는 행 수입니다.|  
|idle_worker_count|**bigint**|유휴 작업자에서 처리하는 가비지 행 수입니다.|  
|sweep_scans_started|**bigint**|가비지 수집 하위 시스템에서 수행하는 불량 영역 검색 수입니다.|  
|sweep_scans_retries|**bigint**|가비지 수집 하위 시스템에서 수행하는 불량 영역 검색 수입니다.|  
|sweep_rows_touched|**bigint**|불량 영역 처리에서 읽는 행입니다.|  
|sweep_rows_expiring|**bigint**|불량 영역 처리에서 읽는 만료되는 행입니다.|  
|sweep_rows_expired|**bigint**|불량 영역 처리에서 읽는 만료된 행입니다.|  
|sweep_rows_expired_removed|**bigint**|불량 영역 처리에서 제거되어 만료된 행입니다.|  
  
## <a name="permissions"></a>권한  
 인스턴스에 대해 VIEW SERVER STATE 권한이 필요합니다.  
  
## <a name="usage-scenario"></a>사용 시나리오  
 다음은 예제 출력입니다.  
  
```  
rows_examined        rows_no_sweep_needed rows_first_in_bucket rows_first_in_bucket_removed  
280085               209512               69905  
rows_first_in_bucket_removed rows_marked_for_unlink parallel_assist_count idle_worker_count  
69905                        0                      8953  
  
idle_worker_count    sweep_scans_started  sweep_scan_retries   sweep_rows_touched  
10306473             670                  0                    1343  
  
sweep_rows_expiring  sweep_rows_expired   sweep_rows_expired_removed  
               0                 673673  
```  
  
## <a name="see-also"></a>참고 항목  
 [메모리 최적화 테이블 동적 관리 뷰 &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/memory-optimized-table-dynamic-management-views-transact-sql.md)  
  
  
