---
title: sys.pdw_distributions (TRANSACT-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 572b5187-9753-4063-adf8-65dea87d11f8
author: ronortloff
ms.author: rortloff
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 7deddb57cdc02410fe161728f45190492ac18a16
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68127546"
---
# <a name="syspdwdistributions-transact-sql"></a>sys.pdw_distributions (Transact SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  어플라이언스에서 배포에 대 한 정보를 보유합니다. 어플라이언스 분산 당 하나의 행을 나열합니다.  
  
|열 이름|데이터 형식|설명|범위|  
|-----------------|---------------|-----------------|-----------|  
|distribution_id|**int**|배포와 관련 된 고유 숫자 id입니다.<br /><br /> 이 보기에 대 한 키입니다.|계산 노드당 배포 수가 곱한 어플라이언스의 계산 노드 수는 1입니다.|  
|pdw_node_id|**int**|이 배포에는 노드의 ID입니다.|참조에 pdw_node_id [sys.dm_pdw_nodes &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-nodes-transact-sql.md)합니다.|  
|name|**nvarchar(32)**|분산된 테이블에 대 한 접미사로 사용 하 고 배포에 연관 된 식별자는 문자열입니다.|문자열 구성의 ' A-z ','a-z', ' 0-9', '_','-'.|  
|position|**int**|해당 노드에서 다른 배포판에 해당 노드 내에서 배포의 위치입니다.|노드당 배포 수가 1입니다.|  
  
## <a name="see-also"></a>관련 항목  
 [SQL Data Warehouse 및 병렬 데이터 웨어하우스 카탈로그 뷰](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)  
  
  
