---
description: sys.dm_fts_population_ranges(Transact-SQL)
title: sys. dm_fts_population_ranges (Transact-sql) | Microsoft Docs
ms.custom: ''
ms.date: 03/29/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_fts_population_ranges
- sys.dm_fts_population_ranges_TSQL
- dm_fts_population_ranges_TSQL
- dm_fts_population_ranges
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_fts_population_ranges dynamic management view
ms.assetid: 58d8564b-9c43-4965-a31c-2893890334ef
author: pmasl
ms.author: pelopes
ms.reviewer: mikeray
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 546eb1cd48acaf57c5b930ffb35bb4d88bcfd42e
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88493719"
---
# <a name="sysdm_fts_population_ranges-transact-sql"></a>sys.dm_fts_population_ranges(Transact-SQL)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

  현재 진행 중인 전체 텍스트 인덱스 채우기와 관련된 특정 범위에 대한 정보를 반환합니다.  
   
|열 이름|데이터 형식|Description|  
|-----------------|---------------|-----------------|  
|**memory_address**|**varbinary(8)**|전체 텍스트 인덱스 채우기의 해당 하위 범위와 관련된 작업에 할당된 메모리 버퍼의 주소입니다.|  
|**parent_memory_address**|**varbinary(8)**|전체 텍스트 인덱스와 관련된 모든 채우기 범위의 부모 개체를 나타내는 메모리 버퍼의 주소입니다.|  
|**is_retry**|**bit**|값이 1이면 이 하위 범위에서 오류가 발생한 행에 대한 작업을 다시 시도합니다.|  
|**session_id**|**smallint**|현재 이 태스크를 처리 중인 세션의 ID입니다.|  
|**processed_row_count**|**int**|이 범위에서 처리된 행 수입니다. 정방향 진행률은 일괄 처리마다 커밋하지 않고 5분마다 유지 및 계산됩니다.|  
|**error_count**|**int**|이 범위에서 오류가 발생한 행 수입니다. 정방향 진행률은 일괄 처리마다 커밋하지 않고 5분마다 유지 및 계산됩니다.|  
  
## <a name="permissions"></a>사용 권한  

에 [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] 는 `VIEW SERVER STATE` 권한이 필요 합니다.   
[!INCLUDE[ssSDS_md](../../includes/sssds-md.md)]Premium 계층에서는 데이터베이스에 대 한 권한이 필요 합니다 `VIEW DATABASE STATE` . [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)]표준 및 기본 계층에서는 **서버 관리자** 또는 **Azure Active Directory 관리자** 계정이 필요 합니다.   
 
## <a name="physical-joins"></a>물리적 조인  
 ![이 동적 관리 뷰의 유효 조인](../../relational-databases/system-dynamic-management-views/media/join-dm-fts-population-ranges-1.gif "이 동적 관리 뷰의 유효 조인")  
  
## <a name="relationship-cardinalities"></a>관계 카디널리티  
  
|보낸 사람|대상|관계|  
|----------|--------|------------------|  
|dm_fts_population_ranges.parent_memory_address|dm_fts_index_population.memory_address|다 대 일|  
  
## <a name="see-also"></a>관련 항목  
  [Transact-sql&#41;전체 텍스트 검색 및 의미 체계 검색 동적 관리 뷰 및 함수 &#40;](../../relational-databases/system-dynamic-management-views/full-text-and-semantic-search-dynamic-management-views-functions.md)  
  
  

