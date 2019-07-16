---
title: sys.fn_hadr_distributed_ag_replica (TRANSACT-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.fn_hadr_distributed_ag_replica
- sys.fn_hadr_distributed_ag_replica_TSQL
- fn_hadr_distributed_ag_replica
- fn_hadr_distributed_ag_replica_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.fn_hadr_distributed_ag_replica
ms.assetid: a1e5f9cb-c350-4bb4-a04f-7394f6f25d62
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: b4e6437a07aa571fc538f2630124dd52496d08e9
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67906176"
---
# <a name="sysfnhadrdistributedagreplica-transact-sql"></a>sys.fn_hadr_distributed_ag_replica (Transact SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  분산된 가용성 그룹의 복제본을 로컬 가용성 그룹에 매핑하는 데 사용 합니다.  
  
 ![항목 링크 아이콘](../../database-engine/configure-windows/media/topic-link.gif "항목 링크 아이콘") [Transact-SQL 구문 규칙](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>구문  
  
```  
  
sys.fn_hadr_distributed_ag_replica( lag_Id, replica_id )  
```  
  
## <a name="arguments"></a>인수  
 '*lag_Id*'  
 분산된 가용성 그룹의 식별자가입니다. *lag_Id* 형식인 **uniqueidentifier**합니다.  
  
 '*replica_id*'  
 분산된 가용성 그룹에 복제본의 식별자가입니다. *replica_id* 형식인 **uniqueidentifier**합니다.  
  
## <a name="tables-returned"></a>반환된 테이블  
 다음 정보를 반환합니다.  
  
|열 이름|데이터 형식|설명|  
|-----------------|---------------|-----------------|  
|**group_id**|**uniqueidentifier**|로컬 가용성 그룹의 고유 식별자 (GUID)입니다.|  
  
## <a name="examples"></a>예  
  
### <a name="using-sysfnhadrdistributedagreplica"></a>Sys.fn_hadr_distributed_ag_replica를 사용 하 여  
 다음 예제에서는 지정 된 분산된 가용성 그룹 및 복제본을 사용 하 여 연결 된 로컬 가용성 그룹 식별자를 사용 하 여 테이블을 반환 합니다.  
  
```  
DECLARE @lagId uniqueidentifier = '4A03D1A8-4AE6-B153-E7E9-ED22A546008D'  
DECLARE @replicaId uniqueidentifier = 'D5517513-04A8-FD82-14C6-E684EC913935'  
  
SELECT * FROM sys.fn_hadr_distributed_ag_replica(@lagId, @replicaId)  
GO  
```  
  
## <a name="see-also"></a>관련 항목  
 [AlwaysOn 가용성 그룹 함수 &#40;TRANSACT-SQL&#41;](../../relational-databases/system-functions/always-on-availability-groups-functions-transact-sql.md)   
 [AlwaysOn 가용성 그룹 &#40;SQL Server&#41;](../../database-engine/availability-groups/windows/always-on-availability-groups-sql-server.md)   
 [분산 가용성 그룹 &#40;AlwaysOn 가용성 그룹&#41;](../../database-engine/availability-groups/windows/distributed-availability-groups-always-on-availability-groups.md)  
 [CREATE AVAILABILITY GROUP&#40;Transact-SQL&#41;](../../t-sql/statements/create-availability-group-transact-sql.md)   
 [ALTER AVAILABILITY GROUP&#40;Transact-SQL&#41;](../../t-sql/statements/alter-availability-group-transact-sql.md)  
  
  
