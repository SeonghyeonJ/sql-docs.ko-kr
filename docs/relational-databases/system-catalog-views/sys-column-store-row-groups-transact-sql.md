---
title: sys.column_store_row_groups (TRANSACT-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.column_store_row_groups_TSQL
- column_store_row_groups
- sys.column_store_row_groups
- column_store_row_groups_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.column_store_row_groups catalog view
ms.assetid: 76e7fef2-d1a4-4272-a2bb-5f5dcd84aedc
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: c98acb87e180dce32a00e77ba6c1af9fbd48b6fa
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68140010"
---
# <a name="syscolumnstorerowgroups-transact-sql"></a>sys.column_store_row_groups(Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2014-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2014-xxxx-xxxx-xxx-md.md)]

  클러스터형 columnstore 인덱스 정보를 세그먼트 단위로 제공하므로 관리자가 시스템 관리 결정을 내리는 데 도움이 됩니다. **sys.column_store_row_groups** (삭제 된 것으로 표시 된 포함) 물리적으로 저장 된 행의 총 수에 대 한 열이 있고 삭제 됨으로 표시 된 행의 수에 대 한 열입니다. 사용 하 여 **sys.column_store_row_groups** 행을 확인 하려면 그룹 삭제 된 행의 비율이 높아 및 다시 작성 해야 합니다.  
   
|열 이름|데이터 형식|설명|  
|-----------------|---------------|-----------------|  
|**object_id**|**int**|이 인덱스가 정의되어 있는 테이블의 ID입니다.|  
|**index_id**|**int**|이 columnstore 인덱스가 있는 테이블의 인덱스 ID입니다.|  
|**partition_number**|**int**|row_group_id 행 그룹을 보유한 테이블 파티션의 ID입니다. partition_number를 사용하여 DMV를 sys.partitions에 조인할 수 있습니다.|  
|**row_group_id**|**int**|이 행 그룹과 연결된 행 그룹 번호입니다. 이 번호는 파티션 내에서 고유합니다.<br /><br /> -1 = 메모리 내 테이블의 꼬리.|  
|**delta_store_hobt_id**|**bigint**|델타 저장소에 열려 있는 행 그룹은 hobt_id 합니다.<br /><br /> 행 그룹 델타 저장소에 없는 경우 NULL입니다.<br /><br /> 메모리 내 테이블의 꼬리에 대 한 NULL입니다.|  
|**state**|**tinyint**|state_description과 연결된 ID 번호입니다.<br /><br /> 0 = INVISIBLE<br /><br /> 1 = OPEN<br /><br /> 2 = CLOSED<br /><br /> 3 = COMPRESSED <br /><br /> 4 = 삭제 표시|  
|**state_description**|**nvarchar(60)**|행 그룹의 영구 상태 설명:<br /><br /> 보이지 않는-숨겨진된 압축 된 세그먼트를 델타 저장소의 데이터에서 만들어지고 있는 합니다. 읽기 작업은 표시되지 않은 압축된 세그먼트가 완료될 때까지 델타 저장소를 사용합니다. 그런 다음 새 세그먼트가 표시되고 원본 델타 저장소가 제거됩니다.<br /><br /> 열림-새 레코드를 수락 하는 읽기/쓰기 행 그룹입니다. 열린 행 그룹은 columnstore 형식으로 압축되지 않았고 여전히 rowstore 형식입니다.<br /><br /> 닫힘-가득 차면 되었지만 아직 tuple mover 프로세스에 의해 압축 행 그룹입니다.<br /><br /> 압축-채워지고 압축 된 행 그룹.|  
|**total_rows**|**bigint**|행 그룹에 물리적으로 저장된 총 행 수입니다. 일부는 삭제되었을 수도 있지만 그대로 저장되어 있습니다. 행 그룹의 최대 행 수는 1,048,576개(16진수 FFFFF)입니다.|  
|**deleted_rows**|**bigint**|행 그룹에서 삭제된 것으로 표시된 총 행 수입니다. 델타 행 그룹에서는 항상 0입니다.|  
|**size_in_bytes**|**bigint**|이 행 그룹에서 DELTA 및 COLUMNSTORE 행 그룹의 모든 데이터 크기(바이트 단위, 메타데이터 또는 공유 사전 제외)입니다.|  
  
## <a name="remarks"></a>설명  
 클러스터형 또는 비클러스터형 columnstore 인덱스가 있는 각 테이블에 대해 columnstore 행 그룹당 한 행을 표시합니다.  
  
 사용 하 여 **sys.column_store_row_groups** 행 그룹과 행 그룹의 크기에 포함 된 행 수를 결정 합니다.  
  
 행 그룹에서 삭제된 행 수가 총 행 수 대비 큰 비율로 증가하면 테이블의 효율성이 저하됩니다. columnstore 인덱스를 다시 작성하여 테이블 크기를 줄이면 테이블을 읽는 데 필요한 디스크 I/O가 줄어듭니다. Columnstore 인덱스 사용을 다시 작성 하는 **다시 작성** 옵션을 합니다 **ALTER INDEX** 문.  
  
 새 데이터를 먼저 삽입 하는 업데이트 가능한 columnstore를 **열려** rowstore 형식으로 이며 델타 테이블 이라고 되기도 하는 행 그룹입니다.  해당 상태가 변경 후 열린 행 그룹이 꽉 차면 **닫힘**합니다. 닫힌된 행 그룹이 tuple mover에 의해 columnstore 형식으로 압축 되 고 상태 변경 **압축**합니다.  Tuple mover는 정기적으로 켜지는 백그라운드 프로세스로, 닫힌 열 그룹 중 columnstore 행 그룹으로 압축할 수 있는 그룹이 있는지 확인합니다.  또한 Tuple mover는 모든 행이 삭제된 행 그룹에 대한 할당을 취소합니다. 할당 취소 된 행 그룹으로 표시 됩니다 **TOMBSTONE**합니다. 튜플 이동 기를 즉시 실행 하려면 사용 합니다 **REORGANIZE** 옵션을는 **ALTER INDEX** 문.  
  
 다 채워진 columnstore 행 그룹은 압축되며, 새 행을 수락하지 않습니다. 압축된 그룹에서 행을 삭제하면 삭제된 것으로 표시되고 행 자체는 그대로 유지됩니다. 압축된 그룹을 업데이트할 때는 압축된 그룹의 삭제 또는 열린 그룹에 대한 삽입을 이용합니다.  
  
## <a name="permissions"></a>사용 권한  
 사용자가 테이블에 대 한 정보를 반환 **VIEW DEFINITION** 테이블에 대 한 합니다.  
  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 자세한 내용은 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)을 참조하세요.  
  
## <a name="examples"></a>예  
 다음 예제에서는 조인 합니다 **sys.column_store_row_groups** 특정 테이블에 대 한 정보를 반환할 다른 시스템 테이블에는 테이블입니다. 계산된 `PercentFull` 열은 행 그룹의 효율성 예상치입니다. 앞의 주석 하이픈을 단일 테이블 제거에 대 한 정보를 찾을 수 합니다 **여기서** 절 하 고 테이블 이름을 제공 합니다.  
  
```  
SELECT i.object_id, object_name(i.object_id) AS TableName,   
i.name AS IndexName, i.index_id, i.type_desc,   
CSRowGroups.*,   
100*(total_rows - ISNULL(deleted_rows,0))/total_rows AS PercentFull    
FROM sys.indexes AS i  
JOIN sys.column_store_row_groups AS CSRowGroups  
    ON i.object_id = CSRowGroups.object_id  
AND i.index_id = CSRowGroups.index_id   
--WHERE object_name(i.object_id) = '<table_name>'   
ORDER BY object_name(i.object_id), i.name, row_group_id;  
```  
  
## <a name="see-also"></a>관련 항목  
 [개체 카탈로그 뷰 &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [카탈로그 뷰&#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [SQL Server 시스템 카탈로그 FAQ](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)   
 [sys.columns&#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-columns-transact-sql.md)   
 [sys.all_columns &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-all-columns-transact-sql.md)   
 [sys.computed_columns &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-computed-columns-transact-sql.md)   
 [Columnstore 인덱스 가이드](~/relational-databases/indexes/columnstore-indexes-overview.md)     
 [sys.column_store_dictionaries &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-column-store-dictionaries-transact-sql.md)   
 [sys.column_store_segments&#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-column-store-segments-transact-sql.md)  
  
  

