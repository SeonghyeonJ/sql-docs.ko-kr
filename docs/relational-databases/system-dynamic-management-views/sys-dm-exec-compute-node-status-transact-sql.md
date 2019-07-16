---
title: sys.dm_exec_compute_node_status (TRANSACT-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- DM_EXEC_COMPUTE_NODE_STATUS_TSQL
- DM_EXEC_COMPUTE_NODE_STATUS
dev_langs:
- TSQL
helpviewer_keywords:
- PolyBase,views
- PolyBase
- dm_exec_compute_node_status
- sys.dm_exec_compute_node_status management view
ms.assetid: b606f91f-3a08-4a4f-bb57-32ae155b3738
author: stevestein
ms.author: sstein
monikerRange: '>=aps-pdw-2016||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 1a219ab9606327bd67e26d237a9f8b7b5c2cb8fa
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68097868"
---
# <a name="sysdmexeccomputenodestatus-transact-sql"></a>sys.dm_exec_compute_node_status (Transact SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2016-xxxx-asdw-pdw-md.md)]

  성능 및 모든 PolyBase 노드의 상태에 대 한 추가 정보를 보유합니다. 노드당 하나의 행을 나열합니다.  
  
|열 이름|데이터 형식|설명|범위|  
|-----------------|---------------|-----------------|-----------|  
|compute_node_id|**int**|노드와 연결 된 고유 숫자 id입니다.|형식에 관계 없이 확장 클러스터에서 고유 합니다.|  
|process_id|**int**|||  
|process_name|**nvarchar(255)**|노드의 논리적 이름입니다.|적절 한 길이의 문자열입니다.|  
|allocated_memory|**bigint**|이 노드에서 메모리를 할당 된 총 수입니다.||  
|available_memory|**bigint**|이 노드의 총 사용 가능한 메모리를 지원 합니다.||  
|process_cpu_usage|**bigint**|총 프로세스 CPU 사용량, 틱입니다.||  
|total_cpu_usage|**bigint**|총 CPU 사용량, 틱입니다.||  
|thread_count|**bigint**|이 노드에서 사용 중인 스레드의 총 수입니다.||  
|handle_count|**bigint**|이 노드에서 사용 중인 핸들의 총 수입니다.||  
|total_elapsed_time|**bigint**|시스템 시작 되거나 다시 시작 이후 경과 된 총 시간입니다.|시스템 시작 되거나 다시 시작 이후 경과 된 총 시간입니다. Total_elapsed_time 정수 (밀리초 단위로 24.8 일)에 대 한 최대값을 초과 하는 경우 materialization 오류로 인해 오버플로를 발생 합니다. 시간 (밀리초)의 최 댓 값 24.8 일 하는 것과 같습니다.|  
|is_available|**bit**|이 노드를 사용할 수 있는지 여부를 나타내는 플래그입니다.||  
|sent_time|**datetime**|네트워크 패키지가 전송 된 마지막 시간||  
|received_time|**datetime**|이 노드가 네트워크 패키지를 보낸 최종 시간입니다.||  
|error_id|**nvarchar(36)**|이 노드에서 발생 한 마지막 오류의 고유 식별자입니다.||  
  
## <a name="see-also"></a>관련 항목  
 [PolyBase 동적 관리 뷰를 사용 하 여 문제 해결](https://msdn.microsoft.com/library/ce9078b7-a750-4f47-b23e-90b83b783d80)   
 [동적 관리 뷰 및 함수&#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [데이터베이스 관련 동적 관리 뷰 &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/database-related-dynamic-management-views-transact-sql.md)  
  
  
