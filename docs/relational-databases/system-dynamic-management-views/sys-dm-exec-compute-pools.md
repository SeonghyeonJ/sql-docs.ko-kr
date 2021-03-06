---
description: sys. dm_exec_compute_pools (Transact-sql)
title: sys. dm_exec_compute_pools (Transact-sql) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2019
ms.prod: sql
ms.prod_service: database-engine, big-data-clusters
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_exec_compute_pools
- dm_exec_compute_pools_TSQL
- dm_exec_compute_pools
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_exec_compute_pools dynamic management view
ms.assetid: ''
author: markingmyname
ms.author: maghan
monikerRange: '>=sql-server-ver15||=sqlallproducts-allversions||>=sql-server-linux-2017'
ms.openlocfilehash: 9e0e4cfda23c90807436b6f7b8b4179d2cb22620
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89533730"
---
# <a name="sysdm_exec_compute_pools-transact-sql"></a>sys. dm_exec_compute_pools (Transact-sql)
[!INCLUDE[sqlserver2019](../../includes/applies-to-version/sqlserver2019.md)]

|열 이름|데이터 형식|Description|  
|-----------------|---------------|-----------------|  
|name|`sysname`|계산 풀의 이름입니다. Null을 허용하지 않습니다. `default`기본 계산 풀에 대해를 반환 합니다. |
|compute_pool_id|`int`|풀에 대 한 고유 식별자입니다. 이 보기의 키입니다.|  
|위치|`sysname`|SQL 빅 데이터 클러스터의 컨트롤러에 대 한 끝점입니다. Null을 허용하지 않습니다. |

## <a name="permissions"></a>사용 권한

에 [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] 는 `VIEW SERVER STATE` 권한이 필요 합니다.

## <a name="see-also"></a>참고 항목

[무엇 [!INCLUDE[big-data-clusters-2019](../../includes/ssbigdataclusters-ss-nover.md)] ](../../big-data-cluster/big-data-cluster-overview.md)인가요?
