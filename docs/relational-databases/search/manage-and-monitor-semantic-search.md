---
title: 의미 체계 검색 관리 및 모니터링 | Microsoft 문서
ms.date: 03/20/2017
ms.prod: sql
ms.prod_service: search, sql-database
ms.technology: search
ms.topic: conceptual
helpviewer_keywords:
- semantic search [SQL Server], managing
- semantic search [SQL Server], monitoring
ms.assetid: eb5c3b29-da70-42aa-aa97-7d35a3f1eb98
author: pmasl
ms.author: pelopes
ms.reviewer: mikeray
ms.openlocfilehash: a7cd3bb6fd625b588624d38b777788a2f84c814f
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85629260"
---
# <a name="manage-and-monitor-semantic-search"></a>의미 체계 검색 관리 및 모니터링
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  의미 체계 인덱싱의 과정과 인덱스를 모니터링하고 관리하는 데 관련된 태스크에 대해 설명합니다.  
  
##  <a name="check-the-status-of-semantic-indexing"></a><a name="HowToMonitorStatus"></a> 의미 체계 인덱싱의 상태 확인  
### <a name="is-the-first-phase-of-semantic-indexing-complete"></a>의미 체계 인덱싱의 첫 번째 단계가 완료되었는지 확인
 동적 관리 뷰 [sys.dm_fts_index_population&#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-fts-index-population-transact-sql.md)을 쿼리하고 **status** 및 **status_description** 열을 확인합니다.  
  
 인덱싱의 첫 번째 단계에는 문서 유사성 데이터의 추출뿐만 아니라 전체 텍스트 키워드 인덱스와 의미 체계 키 구 인덱스의 채우기도 포함됩니다.  
  
```sql  
USE database_name  
GO  
  
SELECT * FROM sys.dm_fts_index_population WHERE table_id = OBJECT_ID('table_name')  
GO  
```  
  
### <a name="is-the-second-phase-of-semantic-indexing-complete"></a>의미 체계 인덱싱의 두 번째 단계가 완료되었는지 확인
 동적 관리 뷰 [sys.dm_fts_semantic_similarity_population&#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-fts-semantic-similarity-population-transact-sql.md)을 쿼리하고 **status** 및 **status_description** 열을 확인합니다.  
  
 인덱싱의 두 번째 단계에는 의미 체계적 문서 유사성 인덱스의 채우기가 포함됩니다.  
  
```wql  
USE database_name  
GO  
  
SELECT * FROM sys.dm_fts_semantic_similarity_population WHERE table_id = OBJECT_ID('table_name')  
GO  
```  
  
##  <a name="check-the-size-of-the-semantic-indexes"></a><a name="HowToCheckSize"></a> 의미 체계 인덱스의 크기 확인  
### <a name="what-is-the-logical-size-of-a-semantic-key-phrase-index-or-a-semantic-document-similarity-index"></a>의미 체계 키 구 인덱스 또는 의미 체계 문서 유사성 인덱스의 논리적 크기 확인
 동적 관리 뷰 [sys.dm_db_fts_index_physical_stats&#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-fts-index-physical-stats-transact-sql.md)를 쿼리합니다.  
  
 논리적 크기는 인덱스 페이지의 수로 표시됩니다.  
  
```sql  
USE database_name  
GO  
  
SELECT * FROM sys.dm_db_fts_index_physical_stats WHERE object_id = OBJECT_ID('table_name')  
GO  
```  
  
### <a name="what-is-the-total-size-of-the-full-text-and-semantic-indexes-for-a-full-text-catalog"></a>전체 텍스트 카탈로그에 대한 전체 텍스트 및 의미 체계 인덱스의 총 크기 확인  
 [FULLTEXTCATALOGPROPERTY &#40;Transact-SQL&#41;](../../t-sql/functions/fulltextcatalogproperty-transact-sql.md) 메타데이터 함수의 **IndexSize** 속성을 쿼리합니다.  
  
```sql  
SELECT FULLTEXTCATALOGPROPERTY('catalog_name', 'IndexSize')  
GO  
```  
  
### <a name="how-many-items-are-indexed-in-the-full-text-and-semantic-indexes-for-a-full-text-catalog"></a>전체 텍스트 카탈로그에 대한 전체 텍스트 및 의미 체계 인덱스에서 인덱싱된 항목 수 확인  
 [FULLTEXTCATALOGPROPERTY &#40;Transact-SQL&#41;](../../t-sql/functions/fulltextcatalogproperty-transact-sql.md) 메타데이터 함수의 **ItemCount** 속성을 쿼리합니다.  
  
```sql  
SELECT FULLTEXTCATALOGPROPERTY('catalog_name', 'ItemCount')  
GO  
```  
  
##  <a name="force-the-population-of-the-semantic-indexes"></a><a name="HowToForcePopulation"></a> 의미 체계 인덱스의 채우기 적용  
 전체 텍스트 인덱스에 대해 설명한 것과 구문 및 동작이 동일한 START/STOP/PAUSE 또는 RESUME POPULATION 절을 사용하여 전체 텍스트 및 의미 체계 인덱스의 채우기를 적용할 수 있습니다. 자세한 내용은 [ALTER FULLTEXT INDEX&#40;Transact-SQL&#41;](../../t-sql/statements/alter-fulltext-index-transact-sql.md) 및 [전체 텍스트 인덱스 채우기](../../relational-databases/search/populate-full-text-indexes.md)를 참조하세요.  
  
 의미 체계 인덱싱은 전체 텍스트 인덱싱에 따라 달라지므로 의미 체계 인덱스는 연결된 전체 텍스트 인덱스가 채워진 경우에만 채워집니다.  
  
 **예: 전체 텍스트 및 의미 체계 인덱스의 전체 채우기 시작**  
  
 다음 예에서는 AdventureWorks2012 예제 데이터베이스의 **Production.Document** 테이블에 대한 기존의 전체 텍스트 인덱스를 변경하여 전체 텍스트 및 의미 체계 인덱스 모두에 대한 전체 채우기를 시작합니다.  
  
```vb  
USE AdventureWorks2012  
GO  
  
ALTER FULLTEXT INDEX ON Production.Document  
    START FULL POPULATION  
GO  
```  
  
##  <a name="disable-or-re-enable-semantic-indexing"></a><a name="HowToDisableIndexing"></a> 의미 체계 인덱싱 해제 또는 다시 설정  
 전체 텍스트 인덱스에 대해 설명한 것과 구문 및 동작이 동일한 ENABLE/DISABLE 절을 사용하여 전체 텍스트 또는 의미 체계 인덱싱을 사용하거나 사용하지 않도록 설정할 수 있습니다. 자세한 내용은 [ALTER FULLTEXT INDEX&#40;Transact-SQL&#41;](../../t-sql/statements/alter-fulltext-index-transact-sql.md)를 참조하세요.  
  
 의미 체계 인덱싱이 사용하지 않도록 설정되거나 일시 중지된 경우에도 의미 체계 데이터에 대한 쿼리는 계속 작동하여 이전에 인덱싱된 데이터를 반환합니다. 이 동작은 전체 텍스트 검색의 동작과 같지 않습니다.  
  
```sql  
-- To disable semantic indexing on a table  
USE database_name  
GO  
  
ALTER FULLTEXT INDEX ON table_name DISABLE  
GO  
  
-- To re-enable semantic indexing on a table  
USE database_name  
GO  
  
ALTER FULLTEXT INDEX ON table_name ENABLE  
GO  
```  
  
##  <a name="about-the-phases-of-semantic-indexing"></a><a name="SemanticIndexing"></a> 의미 체계 인덱싱의 단계  
 의미 체계 검색에서는 의미 체계 검색을 사용하도록 설정된 각 열에 대해 다음 두 종류의 데이터를 인덱싱합니다.  
  
1.  **핵심 구**  
  
2.  **문서 유사성**  
  
 의미 체계 인덱싱은 전체 텍스트 인덱싱과 함께 다음 두 단계로 수행됩니다.  
  
1.  **단계 1** 전체 텍스트 키워드 인덱스와 의미 체계 키 구 인덱스가 동시에 병렬로 채워집니다. 이때 문서 유사성을 인덱싱하는 데 필요한 데이터도 추출됩니다.  
  
2.  **단계 2**: 그런 다음 의미 체계 문서 유사성 인덱스가 채워집니다. 이 인덱스는 이전 단계에서 채워진 두 인덱스에 따라 달라집니다.  
  
##  <a name="BestPracticeUnderstand"></a>   
##  <a name="issue-semantic-indexes-are-not-populated"></a><a name="ProblemNotPopulated"></a> 문제: 의미 체계 인덱스가 채워지지 않음  
### <a name="are-the-associated-full-text-indexes-populated"></a>연결된 전체 텍스트 인덱스가 채워졌습니까?  
 의미 체계 인덱싱은 전체 텍스트 인덱싱에 따라 달라지므로 의미 체계 인덱스는 연결된 전체 텍스트 인덱스가 채워진 경우에만 채워집니다.  
  
### <a name="are-full-text-search-and-semantic-search-properly-installed-and-configured"></a>전체 텍스트 검색 및 의미 체계 검색이 올바르게 설치 및 구성되어 있습니까?  
 자세한 내용은 [의미 체계 검색 설치 및 구성](../../relational-databases/search/install-and-configure-semantic-search.md)을 참조하세요.  
  
### <a name="is-the-fdhost-service-not-available-or-is-there-another-condition-that-would-cause-full-text-indexing-to-fail"></a>FDHOST 서비스를 사용할 수 없거나 전체 텍스트 인덱싱이 실패할 만한 다른 조건이 있습니까?  
 자세한 내용은 [전체 텍스트 인덱싱 문제 해결](../../relational-databases/search/troubleshoot-full-text-indexing.md)을 참조하세요.  
  
  
