---
title: 데이터베이스를 복원하여 리소스 풀에 바인딩 | Microsoft 문서
description: SQL Server에서 메모리 최적화 테이블이 포함된 데이터베이스를 복원하는 방법을 알아봅니다. 데이터베이스를 명명된 리소스 풀에 바인딩하여 모범 사례를 따릅니다.
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 0d20a569-8a27-409c-bcab-0effefb48013
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 4f5035a7dd7818e14ec594d04edabad138242527
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89546936"
---
# <a name="restore-a-database-and-bind-it-to-a-resource-pool"></a>데이터베이스를 복원하여 리소스 풀에 바인딩
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  메모리 최적화 테이블이 포함된 데이터베이스를 복원하기에 충분한 메모리가 있더라도 최선의 구현 방법에 따라 데이터베이스를 명명된 리소스 풀에 바인딩하려고 합니다. 데이터베이스가 있어야 풀에 바인딩할 수 있기 때문에 데이터베이스를 복원하려면 여러 단계를 수행해야 합니다. 이 항목에서는 각 단계를 안내합니다.  
  
## <a name="restoring-a-database-with-memory-optimized-tables"></a>메모리 최적화 테이블이 포함된 데이터베이스 복원  
 다음 단계에서는 데이터베이스 IMOLTP_DB를 완전히 복원하고 Pool_IMOLTP에 바인딩합니다.  
  
1.  [NORECOVERY를 사용하여 복원](../../relational-databases/in-memory-oltp/restore-a-database-and-bind-it-to-a-resource-pool.md#bkmk_NORECOVERY)  
  
2.  [리소스 풀 만들기](../../relational-databases/in-memory-oltp/restore-a-database-and-bind-it-to-a-resource-pool.md#bkmk_createPool)  
  
3.  [데이터베이스와 리소스 풀 바인딩](../../relational-databases/in-memory-oltp/restore-a-database-and-bind-it-to-a-resource-pool.md#bkmk_bind)  
  
4.  [RECOVERY를 사용하여 복원](../../relational-databases/in-memory-oltp/restore-a-database-and-bind-it-to-a-resource-pool.md#bkmk_RECOVERY)  
  
5.  [리소스 풀 성능 모니터링](../../relational-databases/in-memory-oltp/restore-a-database-and-bind-it-to-a-resource-pool.md#bkmk_Monitor)  
  
###  <a name="restore-with-norecovery"></a><a name="bkmk_NORECOVERY"></a> NORECOVERY를 사용하여 복원  
 데이터베이스를 복원할 때 NORECOVERY 를 사용하면 메모리를 사용하지 않고 데이터베이스가 만들어지고 디스크 이미지가 복원됩니다.  
  
```sql  
RESTORE DATABASE IMOLTP_DB   
   FROM DISK = 'C:\IMOLTP_test\IMOLTP_DB.bak'  
   WITH NORECOVERY  
```  
  
###  <a name="create-the-resource-pool"></a><a name="bkmk_createPool"></a> 리소스 풀 만들기  
 다음 [!INCLUDE[tsql](../../includes/tsql-md.md)] 에서는 메모리의 50%를 사용할 수 있는 Pool_IMOLTP라는 리소스 풀을 만듭니다.  풀이 만들어진 후 Pool_IMOLTP를 포함하도록 리소스 관리자가 다시 구성됩니다.  
  
```sql  
CREATE RESOURCE POOL Pool_IMOLTP WITH (MAX_MEMORY_PERCENT = 50);  
ALTER RESOURCE GOVERNOR RECONFIGURE;  
GO  
```  
  
###  <a name="bind-the-database-and-resource-pool"></a><a name="bkmk_bind"></a> 데이터베이스와 리소스 풀 바인딩  
 시스템 함수 `sp_xtp_bind_db_resource_pool` 을 사용하여 리소스 풀에 데이터베이스를 바인딩합니다. 이 함수는 데이터베이스 이름과 리소스 풀 이름의 2개의 매개 변수를 사용합니다.  
  
 다음 [!INCLUDE[tsql](../../includes/tsql-md.md)] 에서는 리소스 풀 Pool_IMOLTP와 데이터베이스 IMOLTP_DB의 바인딩을 정의합니다. 다음 단계를 완료해야 바인딩이 유효해집니다.  
  
```sql  
EXEC sp_xtp_bind_db_resource_pool 'IMOLTP_DB', 'Pool_IMOLTP'  
GO  
```  
  
###  <a name="restore-with-recovery"></a><a name="bkmk_RECOVERY"></a> RECOVERY를 사용하여 복원  
 복구를 사용하여 데이터베이스를 복원하면 데이터베이스가 온라인 상태가 되고 모든 데이터가 복원됩니다.  
  
```sql  
RESTORE DATABASE IMOLTP_DB   
   WITH RECOVERY  
```  
  
###  <a name="monitor-the-resource-pool-performance"></a><a name="bkmk_Monitor"></a> 리소스 풀 성능 모니터링  
 데이터베이스가 명명된 리소스 풀에 바인딩되고 복구를 통해 복원되면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], Resource Pool Stats 개체를 모니터링합니다. 자세한 내용은 [SQL Server, Resource Pool Stats 개체](../../relational-databases/performance-monitor/sql-server-resource-pool-stats-object.md)를 참조하세요.  
  
## <a name="see-also"></a>참고 항목  
 [데이터베이스를 리소스 풀에 바인딩하는 방법에 대한 지침은](../../relational-databases/in-memory-oltp/bind-a-database-with-memory-optimized-tables-to-a-resource-pool.md)   
 [sys.sp_xtp_bind_db_resource_pool&#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sys-sp-xtp-bind-db-resource-pool-transact-sql.md)   
 [SQLServer, Resource Pool Stats 개체](../../relational-databases/performance-monitor/sql-server-resource-pool-stats-object.md)   
 [sys.dm_resource_governor_resource_pools](../../relational-databases/system-stored-procedures/sys-sp-xtp-unbind-db-resource-pool-transact-sql.md)  
  
  
