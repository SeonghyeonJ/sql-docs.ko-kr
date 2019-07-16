---
title: sys.pdw_nodes_partitions (TRANSACT-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: b4216752-4813-4b2c-b259-7d8ffc6cc190
author: ronortloff
ms.author: rortloff
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 00ce680a0648b7641249d5fba6b7d0fa493deebd
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68001141"
---
# <a name="syspdwnodespartitions-transact-sql"></a>sys.pdw_nodes_partitions (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  모든 테이블 및 대부분의 인덱스의 각 파티션에 대해 행을 포함 한 [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] 데이터베이스입니다. 모든 테이블 및 인덱스는 명시적으로 분할 여부 또는 하나 이상의 파티션을 포함 합니다.  
  
|열 이름|데이터 형식|설명|  
|-----------------|---------------|-----------------|  
|partition_id|`bigint`|파티션의 id입니다. 데이터베이스 내에서 고유합니다.|  
|object_id|`int`|이 파티션이 속한 개체의 id입니다. 모든 테이블 또는 뷰는 최소한 하나 이상의 파티션으로 구성됩니다.|  
|index_id|`int`|이 파티션이 속한 개체 내부의 인덱스의 id입니다.|  
|partition_number|`int`|소유하는 인덱스나 힙 내의 1부터 시작하는 파티션 번호입니다. 에 대 한 [!INCLUDE[ssSDW](../../includes/sssdw-md.md)],이 열의 값은 1입니다.|  
|hobt_id|`bigint`|이 파티션에 대한 행을 포함하는 데이터 힙 또는 B-트리의 ID입니다.|  
|rows|`bigint`|이 파티션에 있는 행의 대략적인 수입니다. |  
|data_compression|`int`|각 파티션의 압축 상태를 나타냅니다.<br /><br /> 0 = 없음<br /><br /> 1 = ROW<br /><br /> 2 = PAGE<br /><br /> 3 = COLUMNSTORE|  
|data_compression_desc|`nvarchar(60)`|각 파티션의 압축 상태를 나타냅니다. 가능한 값은 NONE, ROW 및 PAGE입니다.|  
|pdw_node_id|`int`|고유 식별자를 [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] 노드.|  
  
## <a name="permissions"></a>사용 권한  
 CONTROL SERVER 권한이 필요합니다.  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>예제: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] 및 [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  

### <a name="example-a-display-rows-in-each-partition-within-each-distribution"></a>예제 A: 각 배포 내에서 각 파티션에 있는 행을 표시 합니다. 

적용 대상: [!INCLUDE[ssSDW](../../includes/sssdw-md.md)], [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]
 
각 배포 내에서 각 파티션에 있는 행의 수를 표시 하려면 사용 하 여 [DBCC PDW_SHOWPARTITIONSTATS (SQL Server PDW)](../../t-sql/database-console-commands/dbcc-pdw-showpartitionstats-transact-sql.md) 합니다.

### <a name="example-b-uses-system-views-to-view-rows-in-each-partition-of-each-distribution-of-a-table"></a>예제 B: 시스템 뷰를 사용 하 여 테이블의 각 배포의 각 파티션에 있는 행을 보려면

적용 대상: [!INCLUDE[ssSDW](../../includes/sssdw-md.md)]
 
이 쿼리는 테이블의 각 배포의 각 파티션에 있는 행의 수를 반환 합니다. `myTable`합니다.  
 
```  
SELECT o.name, pnp.index_id, pnp.partition_id, pnp.rows,   
    pnp.data_compression_desc, pnp.pdw_node_id  
FROM sys.pdw_nodes_partitions AS pnp  
JOIN sys.pdw_nodes_tables AS NTables  
    ON pnp.object_id = NTables.object_id  
AND pnp.pdw_node_id = NTables.pdw_node_id  
JOIN sys.pdw_table_mappings AS TMap  
    ON NTables.name = TMap.physical_name 
    AND substring(TMap.physical_name,40, 10) = pnp.distribution_id 
JOIN sys.objects AS o  
    ON TMap.object_id = o.object_id  
WHERE o.name = 'myTable'  
ORDER BY o.name, pnp.index_id, pnp.partition_id;  
```    
  
## <a name="see-also"></a>관련 항목  
 [SQL Data Warehouse 및 병렬 데이터 웨어하우스 카탈로그 뷰](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)  
  
  

