---
title: Columnstore 인덱스 - 조각 모음 | Microsoft 문서
ms.custom: ''
ms.date: 01/27/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
ms.assetid: d3efda1a-7bdb-47f5-80bf-f075329edee5
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 67131c083966244db252c047b200c2a6d979aadb
ms.sourcegitcommit: ce5770d8b91c18ba5ad031e1a96a657bde4cae55
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/25/2019
ms.locfileid: "67388143"
---
# <a name="columnstore-indexes---defragmentation"></a>Columnstore 인덱스 - 조각 모음
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Columnstore 인덱스에 대한 조각 모음 작업입니다.  
  
## <a name="use-alter-index-reorganize-to-defragment-a-columnstore-index-online"></a>Columnstore 인덱스에 대한 조각 모음을 온라인에서 수행하기 위해 ALTER INDEX REORGANIZE 사용  
 **적용 대상:** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]부터), [!INCLUDE[ssSDS](../../includes/sssds-md.md)]  
  
모든 종류의 로드를 수행하면 deltastore에서 여러 개의 작은 rowgroup을 사용할 수 있습니다. `ALTER INDEX REORGANIZE`를 사용하여 모든 rowgroup을 columnstore로 강제한 후 rowgroup을 열이 더 많은 소수의 rowgroup으로 결합합니다.  또한, 재구성 작업은 columnstore에서 삭제된 행도 제거합니다.  
  
자세한 내용은 SQL Database 엔진 팀 블로그의 다음 게시물을 참조하세요.  
-   [Columnstore 인덱스에서 인덱스 조각화 최소화](https://blogs.msdn.microsoft.com/sqlserverstorageengine/2016/03/07/columnstore-index-defragmentation-using-reorganize-command/)  
-   [Columnstore 인덱스와 rowgroup에 대한 병합 정책](https://blogs.msdn.microsoft.com/sqlserverstorageengine/2016/03/08/columnstore-index-merge-policy-for-reorganize/)  
  
### <a name="recommendations-for-reorganizing"></a>재구성 관련 권장 사항  
하나 이상의 데이터 로드 후에는 최대한 빠르게 쿼리 성능 장점을 얻기 위해 columnstore 인덱스를 다시 구성합니다. 다시 구성하려면 처음에 데이터를 압축하기 위한 추가 CPU 리소스가 필요하므로 전체 시스템 성능이 느려질 수 있습니다. 하지만 데이터가 압축되는 즉시 쿼리 성능을 향상할 수 있습니다.  
  
[sys.dm_db_column_store_row_group_physical_stats&#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-column-store-row-group-physical-stats-transact-sql.md)의 예제를 사용하여 조각화를 컴퓨팅합니다. 이를 통해 REORGANIZE 작업을 수행하는 것이 좋은지를 결정할 수 있습니다.  
  
### <a name="example-how-reorganizing-works"></a>예: 재구성 작동 방식  
 이 예제는 ALTER INDEX REORGANIZE이 모든 deltastore rowgroup을 columnstore로 강제로 적용한 후 rowgroup을 결합하는 방법을 보여줍니다.  
  
1.  이 Transact-SQL을 실행하여 행이 300,000개 포함된 준비 테이블을 생성합니다. 이 테이블을 사용하여 행을 columnstore 인덱스로 대량 로드합니다.  
  
    ```sql  
    USE master;  
    GO  
  
    IF EXISTS (SELECT name FROM sys.databases  
        WHERE name = N'[columnstore]')  
        DROP DATABASE [columnstore];  
    GO  
  
    CREATE DATABASE [columnstore];  
    GO  
  
    USE columnstore;
    GO

    IF EXISTS (SELECT name FROM sys.tables  
        WHERE name = N'staging'  
        AND object_id = OBJECT_ID (N'staging'))  
    DROP TABLE dbo.staging;  
    GO  
  
    CREATE TABLE [staging] (  
         AccountKey int NOT NULL,  
         AccountDescription nvarchar (50),  
         AccountType nvarchar(50),  
         AccountCodeAlternateKey int  
    );  
    GO  
  
    -- Load data  
    DECLARE @loop int;  
    DECLARE @AccountDescription varchar(50);  
    DECLARE @AccountKey int;  
    DECLARE @AccountType varchar(50);  
    DECLARE @AccountCode int;  
  
    SELECT @loop = 0;  
    BEGIN TRAN  
        WHILE (@loop < 300000)   
          BEGIN  
            SELECT @AccountKey = CAST (RAND()*10000000 AS int);  
            SELECT @AccountDescription = 'accountdesc ' + CONVERT(varchar(20), @AccountKey);  
            SELECT @AccountType = 'AccountType ' + CONVERT(varchar(20), @AccountKey);  
            SELECT @AccountCode =  CAST (RAND()*10000000 AS int);  
  
            INSERT INTO staging VALUES (  
               @AccountKey,   
               @AccountDescription,   
               @AccountType,   
               @AccountCode  
            );  
  
            SELECT @loop = @loop + 1;  
          END  
    COMMIT  
    ```  
  
2.  columnstore 인덱스로 저장된 테이블을 만듭니다.  
  
    ```sql  
    IF EXISTS (SELECT name FROM sys.tables  
        WHERE name = N'cci_target'  
        AND object_id = OBJECT_ID (N'cci_target'))  
    DROP TABLE dbo.cci_target;  
    GO  
  
    -- Create a table with a clustered columnstore index  
    -- and the same columns as the rowstore staging table.  
    CREATE TABLE cci_target (  
         AccountKey int NOT NULL,  
         AccountDescription nvarchar (50),  
         AccountType nvarchar(50),  
         AccountCodeAlternateKey int,  
         INDEX idx_cci_target CLUSTERED COLUMNSTORE  
    )  
    GO  
    ```  
  
3.  준비 테이블 행을 columnstore 테이블에 대량 삽입합니다. `INSERT INTO ... SELECT`는 대량 삽입을 수행합니다. `TABLOCK`은 `INSERT`가 병렬 처리로 실행되는 것을 허용합니다.  
  
    ```sql  
    -- Insert rows in parallel  
    INSERT INTO cci_target WITH (TABLOCK)  
    SELECT TOP (300000) * FROM staging;  
    GO  
    ```  
  
4.  *sys.dm_db_column_store_row_group_physical_stats* 동적 관리 뷰(dynamic management view)를 사용하여 rowgroup을 확인합니다.  
  
    ```sql  
    -- Run this dynamic management view (DMV) to see the OPEN rowgroups.   
    -- The number of rowgroups depends on the degree of parallelism.   
    -- You will see multiple OPEN rowgroups depending on the degree of parallelism.   
    -- This is because insert operation can run in parallel in [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)].  
  
    SELECT *   
    FROM sys.dm_db_column_store_row_group_physical_stats   
    WHERE object_id  = object_id('cci_target')  
    ORDER BY row_group_id;  
    ```  
  
     이 예제에서 결과는 각각 37,500개의 행이 있는 8개의 OPEN rowgroup을 보여줍니다. OPEN rowgroup의 수는 *max_degree_of_parallelism* 설정에 따라 달라집니다.  
  
     ![OPEN 행 그룹](../../relational-databases/indexes/media/cci-openrowgroups.png "OPEN 행 그룹")  
  
5.  `COMPRESS_ALL_ROW_GROUPS` 옵션과 함께 `ALTER INDEX REORGANIZE`를 사용하여 모든 rowgroup이 columnstore로 압축되게 합니다.  
  
    ```sql  
    -- This command will force all CLOSED and OPEN rowgroups into the columnstore.  
    ALTER INDEX idx_cci_target ON cci_target   
    REORGANIZE WITH (COMPRESS_ALL_ROW_GROUPS = ON);  
  
    SELECT *   
    FROM sys.dm_db_column_store_row_group_physical_stats   
    WHERE object_id  = object_id('cci_target')  
    ORDER BY row_group_id;  
    ```  
  
     결과는 8개의 rowgroup 및 8개의 삭제 표식 행 rowgroup을 보여줍니다. 각 rowgroup은 크기와 관계 없이 columnstore로 압축됩니다. 삭제 표식 rowgroup은 시스템에서 제거됩니다.  
  
     ![TOMBSTONE 및 COMPRESSED 행 그룹](../../relational-databases/indexes/media/cci-tombstone-compressed-rowgroups.png "TOMBSTONE 및 COMPRESSED 행 그룹")  
  
6.  쿼리 성능을 위해 크기가 작은 rowgroup을 서로 결합하는 것이 좋습니다. `ALTER INDEX REORGANIZE`는 `COMPRESSED` rowgroup을 결합합니다. 이제 델타 rowgroup이 columnstore로 압축되었고 ALTER INDEX REORGANIZE를 실행하여 크기가 작은 압축 rowgroup을 다시 결합합니다. 이번에는 `COMPRESS_ALL_ROW_GROUPS` 옵션이 필요 없습니다.  
  
    ```sql  
    -- Run this again and you will see that smaller rowgroups   
    -- combined into one compressed rowgroup with 300,000 rows  
    ALTER INDEX idx_cci_target ON cci_target REORGANIZE;  
  
    SELECT *   
    FROM sys.dm_db_column_store_row_group_physical_stats   
    WHERE object_id  = object_id('cci_target')  
    ORDER BY row_group_id;  
    ```  
  
     결과는 8개의 압축 rowgroup이 1개의 압축 rowgroup으로 결합되었음을 보여줍니다.  
  
     ![결합된 행 그룹](../../relational-databases/indexes/media/cci-compressed-rowgroups.png "결합된 행 그룹")  
  
## <a name="rebuild"></a> ALTER INDEX REBUILD를 사용하여 오프라인에서 columnstore 인덱스에 대한 조각 모음 수행  
 [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] 이상의 경우 온라인 작업과 같이 `REORGANIZE`가 백그라운드에서 필수 재빌드를 수행하므로 columnstore 인덱스를 다시 빌드할 필요가 없습니다.  
  
 columnstore 인덱스를 다시 작성하면 조각화가 제거되고 모든 행이 columnstore로 이동됩니다. [CREATE COLUMNSTORE INDEX&#40;Transact-SQL&#41;](../../t-sql/statements/create-columnstore-index-transact-sql.md) 또는 [ALTER INDEX&#40;Transact-SQL&#41;](../../t-sql/statements/alter-index-transact-sql.md)를 사용하여 기존 클러스터형 columnstore 인덱스를 완전히 다시 작성할 수 있습니다. 또한 ALTER INDEX ... REBUILD를 사용하여 다시 작성할 수 있습니다.  
  
### <a name="rebuild-process"></a>프로세스 다시 작성  
 columnstore 인덱스를 다시 작성하려면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:  
  
1.  다시 작성 작업이 발생한 동안 테이블 또는 파티션에서 배타적 잠금을 획득합니다. `NOLOCK`, RCSI 또는 SI를 사용하는 경우에도 다시 빌드 중에 데이터는 “오프라인”이며 사용할 수 없습니다.  
  
2.  모든 데이터를 columnstore로 다시 압축합니다. 다시 작성 작업이 발생한 동안에는 columnstore 인덱스의 두 복사본이 존재합니다. 다시 작성 작업이 끝나면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서 원래 columnstore 인덱스를 삭제합니다.  
  
### <a name="recommendations-for-rebuilding-a-columnstore-index"></a>Columnstore 인덱스 다시 작성 관련 권장 사항  
 columnstore 인덱스 다시 작성은 조각화 제거 및 모든 행을 columnstore로 이동하는 데 유용합니다. 다음 권장 사항을 고려할 수 있습니다.  
  
1.  전체 테이블 대신 파티션을 다시 작성합니다.  
    -   인덱스가 큰 경우 전체 테이블을 다시 작성하려면 많은 시간이 소요되고 다시 작성 중에 인덱스의 추가 복사본을 저장할 수 있는 충분한 디스크 공간이 필요합니다. 일반적으로 가장 최근에 사용한 파티션만 다시 작성하면 됩니다.  
    -   분할된 테이블의 경우 최근 수정된 파티션에서만 주로 조각화가 발생하므로 전체 columnstore 인덱스를 다시 작성할 필요는 없습니다. 팩트 테이블 및 대규모 차원 테이블은 일반적으로 테이블 청크에서 백업 및 관리 작업을 수행하기 위해 분할됩니다.  

2.  리소스 사용량이 많은 DML 작업 후 파티션을 다시 작성합니다.  
    -   파티션을 다시 작성하면 파티션을 조각 모음하여 디스크 스토리지를 줄일 수 있습니다. 다시 작성 시 columnstore에서 삭제 표시된 모든 행이 삭제되고 deltastore의 모든 rowgroup이 columnstore로 이동됩니다. 행의 수가 1백만 개 이하인 여러 rowgroup이 deltastore에 있을 수 있습니다.  
  
3.  데이터를 로드한 후 파티션을 다시 작성합니다.  
    -   이렇게 하면 모든 데이터가 columnstore에 저장됩니다. 동시에 동일한 파티션으로 100,000행 이하를 로드하는 각 동시 프로세스의 경우 파티션에는 여러 deltastore가 있을 수 있습니다. 다시 작성 시 deltastore의 모든 행이 columnstore로 이동됩니다.  

## <a name="automatic-index-and-statistics-management"></a>자동 인덱스 및 통계 관리

[Adaptive Index Defrag](https://github.com/Microsoft/tigertoolbox/tree/master/AdaptiveIndexDefrag)와 같은 솔루션을 사용하여 하나 이상의 데이터베이스에 대한 인덱스 조각 모음 및 통계 업데이트를 자동으로 관리합니다. 이 절차는 다른 매개 변수 사이에서 조각화 수준에 따라 인덱스를 다시 작성하거나 다시 구성할지 여부를 자동으로 선택하고 통계를 선형 임계값으로 업데이트합니다.

## <a name="see-also"></a>참고 항목        
[Columnstore 인덱스 - 새로운 기능](../../relational-databases/indexes/columnstore-indexes-what-s-new.md)    
[Columnstore 인덱스 쿼리 성능](../../relational-databases/indexes/columnstore-indexes-query-performance.md)   
[실시간 운영 분석을 위한 Columnstore 시작](../../relational-databases/indexes/get-started-with-columnstore-for-real-time-operational-analytics.md)   
[데이터 웨어하우스용 Columnstore 인덱스](../../relational-databases/indexes/columnstore-indexes-data-warehouse.md)  
[Columnstore 인덱스 아키텍처](../../relational-databases/sql-server-index-design-guide.md#columnstore_index)    
[Adaptive Index Defrag](https://github.com/Microsoft/tigertoolbox/tree/master/AdaptiveIndexDefrag)    
  
  
