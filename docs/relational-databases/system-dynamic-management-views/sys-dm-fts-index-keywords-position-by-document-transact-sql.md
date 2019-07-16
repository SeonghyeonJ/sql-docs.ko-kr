---
title: sys.dm_fts_index_keywords_position_by_document (TRANSACT-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_fts_index_keywords_position_by_document_TSQL
- dm_fts_index_keywords_position_by_document_TSQL
- dm_fts_index_keywords_position_by_document
- sys.dm_fts_index_keywords_position_by_document
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_fts_index_keywords_position_by_document dynamic management view
ms.assetid: 0d70184f-baa2-411b-a32d-a4c5af890edd
author: pmasl
ms.author: pelopes
ms.openlocfilehash: feaf2a222df364a41e51969a2c95a978f2d0a289
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67900952"
---
# <a name="sysdmftsindexkeywordspositionbydocument-transact-sql"></a>sys.dm_fts_index_keywords_position_by_document (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  인덱싱된 문서에서 키워드 위치 정보를 반환합니다.  
  
## <a name="syntax"></a>구문  
  
```  
sys.dm_fts_index_keywords_position_by_document  
(   
    DB_ID('database_name'),   
OBJECT_ID('table_name')   
)  
```  
  
## <a name="arguments"></a>인수  
 db_id('*database_name*')  
 에 대 한 호출을 [db_id ()](../../t-sql/functions/db-id-transact-sql.md) 함수입니다. 이 함수는 데이터베이스 이름을 받아서 및 지정된 된 데이터베이스를 찾는 데 사용 하는 sys.dm_fts_index_keywords_position_by_document 데이터베이스 ID를 반환 합니다.  
  
 object_id('*table_name*')  
 에 대 한 호출을 [object_id ()](../../t-sql/functions/object-id-transact-sql.md) 함수입니다. 이 함수는 테이블 이름을 받아서 검사할 전체 텍스트 인덱스가 들어 있는 테이블의 테이블 ID를 반환합니다.  
  
## <a name="table-returned"></a>반환된 테이블  
  
|Column|데이터 형식|설명|  
|------------|---------------|-----------------|  
|키워드(keyword)|**varbinary(128)**|키워드를 나타내는 이진 문자열입니다.|  
|display_term|**nvarchar(4000)**|사람이 인식할 수 있는 키워드 형식입니다. 이 형식은 전체 텍스트 인덱스에 저장되는 내부 형식에서 파생됩니다.|  
|column_id|**int**|현재 키워드가 전체 텍스트 인덱싱된 열의 ID입니다.|  
|document_id|**bigint**|현재 단어가 전체 텍스트 인덱싱된 문서 또는 행의 ID입니다. 이 ID는 해당 문서 또는 행의 전체 텍스트 키 값과 일치합니다.|  
|position|**int**|문서에서 키워드의 위치입니다.|  
  
## <a name="remarks"></a>설명  
 DMV를 사용 하 여 인덱싱된 문서의 인덱싱된 단어의 위치를 식별 합니다. 문제를 해결 하는이 DMV를 사용할 수 있습니다 때 문제가 **sys.dm_fts_index_keywords_by_document** 단어는 전체 텍스트 인덱스를 나타내지만 이러한 단어를 사용 하 여 쿼리를 실행 하는 경우 문서가 반환 되지 않습니다.  
  
## <a name="permissions"></a>사용 권한  
 전체 텍스트 인덱스가 적용되는 열에 대한 SELECT 권한 및 CREATE FULLTEXT CATALOG 권한이 필요합니다.  
  
## <a name="examples"></a>예  
 전체 텍스트 인덱스에서 키워드를 반환 하는 다음 예제는 `Production.Document` 목차는 `AdventureWorks` 샘플 데이터베이스.  
  
```  
USE AdventureWorks2012;  
GO   
  
SELECT * FROM sys.dm_fts_index_keywords_position_by_document  
(   
    DB_ID('AdventureWorks2012'),  
    OBJECT_ID('AdventureWorks2012.Production.Document')   
);   
GO  
```  
  
 다음 예제 쿼리에서 위치를 추가로 격리 하려면와 같이 다른 columns_id에 조건자를 추가할 수 있습니다.  
  
```  
SELECT * FROM sys.dm_fts_index_keywords_position_by_document  
(   
    DB_ID('AdventureWorks2012'),  
    OBJECT_ID('AdventureWorks2012.Production.Document')   
)  
WHERE document_id = 7 AND display_term = 'performance';  
```  
  
## <a name="see-also"></a>관련 항목  
 [전체 텍스트 검색](../../relational-databases/search/full-text-search.md)   
 [전체 텍스트 인덱스 성능 향상](../../relational-databases/search/improve-the-performance-of-full-text-indexes.md)   
 [전체 텍스트 검색과 의미 체계 Search 함수 &#40;TRANSACT-SQL&#41;](../../relational-databases/system-functions/full-text-search-and-semantic-search-functions-transact-sql.md)   
 [전체 텍스트 검색 및 의미 체계 검색 동적 관리 뷰 및 함수 &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/full-text-and-semantic-search-dynamic-management-views-functions.md)   
 [전체 텍스트 검색과 의미 체계 검색 저장 프로시저 &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/full-text-search-and-semantic-search-stored-procedures-transact-sql.md)   
 [검색 속성 목록을 사용하여 문서 속성 검색](../../relational-databases/search/search-document-properties-with-search-property-lists.md)   
 [sys.dm_fts_index_keywords_by_document&#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-fts-index-keywords-by-document-transact-sql.md)  
  
  
