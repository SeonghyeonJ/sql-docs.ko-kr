---
description: sys.dm_exec_compute_nodes (Transact-sql)
title: sys.dm_exec_compute_nodes (Transact-sql) | Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- DM_EXEC_COMPUTE_NODES_TSQL
- DM_EXEC_COMPUTE_NODES
- SYS.DM_EXEC_COMPUTE_NODES_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_exec_compute_nodes management view
- PolyBase, views
- PolyBase management views
- dm_exec_compute_nodes management view
ms.assetid: 0de4b7a4-401f-4e2d-9ab0-c54587e05154
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 85a63b9df2e4d1bbb7a0f4c9096ae8ff192315eb
ms.sourcegitcommit: 32135463a8494d9ed1600a58f51819359e3c09dc
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/08/2020
ms.locfileid: "91834162"
---
# <a name="sysdm_exec_compute_nodes-transact-sql"></a>sys.dm_exec_compute_nodes (Transact-sql)

[!INCLUDE [sqlserver2016-asa-pdw](../../includes/applies-to-version/sqlserver2016-asa-pdw.md)]

  PolyBase 데이터 관리에 사용 되는 노드에 대 한 정보를 보관 합니다. 노드당 하나의 행을 나열 합니다.  
  
 이 DMV를 사용 하 여 역할, 이름 및 IP 주소를 사용 하 여 스케일 아웃 클러스터의 모든 노드 목록을 볼 수 있습니다.  
  
|열 이름|데이터 형식|Description|범위|  
|-----------------|---------------|-----------------|-----------|  
|compute_node_id|**int**|노드와 연결 된 고유 숫자 id입니다. 이 보기의 키입니다.|형식에 관계 없이 스케일 아웃 클러스터에서 고유 합니다.|  
|type|**nvarchar(32)**|노드의 유형입니다.|' COMPUTE ', ' HEAD '|  
|name|**nvarchar(32)**|노드의 논리적 이름입니다.|적절 한 길이의 문자열입니다.|  
|address|**nvarchar(32)**|이 노드의 IP 주소입니다.|IP 주소 범위|  
  
## <a name="see-also"></a>참고 항목  
 [동적 관리 뷰를 사용한 PolyBase 문제 해결](/previous-versions/sql/sql-server-2016/mt146389(v=sql.130))   
 [동적 관리 뷰 및 함수&#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Transact-sql&#41;&#40;데이터베이스 관련 동적 관리 뷰 ](../../relational-databases/system-dynamic-management-views/database-related-dynamic-management-views-transact-sql.md)  
  
