---
description: 의미 체계 검색을 사용하여 문서에서 키 구 찾기
title: 의미 체계 검색을 사용하여 문서에서 키 구 찾기
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: search, sql-database
ms.technology: search
ms.topic: conceptual
helpviewer_keywords:
- semantic search [SQL Server], key phrase queries
ms.assetid: 6ee3676e-ed5d-43ec-aeca-1eed78967111
author: pmasl
ms.author: pelopes
ms.reviewer: mikeray
ms.custom: seo-lt-2019
ms.openlocfilehash: 62a0ba559733c42ddf25b5d40896c4e53bdcf7b7
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88490583"
---
# <a name="find-key-phrases-in-documents-with-semantic-search"></a>의미 체계 검색을 사용하여 문서에서 키 구 찾기
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  통계 의미 체계 인덱싱을 위해 구성된 문서 또는 텍스트 열의 키 구를 찾는 방법에 대해 설명합니다.  

##  <a name="find-the-key-phrases-in-documents-with-semantickeyphrasetable"></a><a name="howtofind"></a> SEMANTICKEYPHRASETABLE을 사용하여 문서의 키 구 찾기  
 특정 문서에서 키 구를 식별하거나 특정 키 구가 포함된 문서를 식별하려면 [semantickeyphrasetable &#40;Transact-SQL&#41;](../../relational-databases/system-functions/semantickeyphrasetable-transact-sql.md) 함수를 쿼리합니다.  
  
 SEMANTICKEYPHRASETABLE은 지정된 테이블의 열과 관련된 키 구가 있는 0개 이상의 행으로 구성된 테이블을 반환합니다. SELECT 문의 FROM 절에서 이 행 집합 함수를 일반 테이블 이름과 마찬가지로 참조할 수 있습니다.  
  
> [!NOTE]  
>  이 릴리스에서는 단일 단어만 의미 체계 검색을 위해 인덱싱되며 여러 단어로 된 구(ngrams)는 인덱싱되지 않습니다. 또한 동일한 단어의 다양한 형태가 개별적으로 인덱싱됩니다. 예를 들어 "computer"와 "computers"는 개별적으로 인덱싱됩니다.  
  
 SEMANTICKEYPHRASETABLE 함수에 필요한 매개 변수와 이 함수에서 반환되는 결과 테이블에 대한 자세한 내용은 [semantickeyphrasetable&#40;Transact-SQL&#41;](../../relational-databases/system-functions/semantickeyphrasetable-transact-sql.md)을 참조하세요.  
  
> [!IMPORTANT]  
>  대상 열에는 전체 텍스트 및 의미 체계 인덱싱이 사용하도록 설정되어 있어야 합니다.  
  
###  <a name="example-1-find-the-top-key-phrases-in-a-specific-document"></a><a name="HowToTopPhrases"></a> 예제 1: 특정 문서에서 상위 키 구 찾기  
 다음 예제에서는 AdventureWorks 예제 데이터베이스에 있는 Production.Document 테이블의 Document 열에서 @DocumentId 변수를 통해 지정된 문서에서 상위 10개의 키 구를 검색합니다. @DocumentId 변수는 전체 텍스트 인덱스의 키 열에 있는 값을 나타냅니다.  
  
```sql  
SELECT TOP(10) KEYP_TBL.keyphrase  
FROM SEMANTICKEYPHRASETABLE  
    (  
    Production.Document,  
    Document,  
    @DocumentId  
    ) AS KEYP_TBL  
ORDER BY KEYP_TBL.score DESC;  
GO  
```  
  
 **SEMANTICKEYPHRASETABLE** 함수는 테이블 검색 대신 인덱스 검색을 사용하여 이러한 결과를 효율적으로 검색합니다.  
  
###  <a name="example-2-find-the-top-documents-that-contain-a-specific-key-phrase"></a><a name="HowToTopDocuments"></a> Example 2: Find the top documents that contain a specific key phrase  
 다음 예제에서는 AdventureWorks 예제 데이터베이스에 있는 Production.Document 테이블의 Document 열에서 "Bracket" 키 구가 포함된 상위 25개의 문서를 검색합니다.  
  
```sql  
SELECT TOP (25) DOC_TBL.DocumentID, DOC_TBL.DocumentSummary  
FROM Production.Document AS DOC_TBL  
    INNER JOIN SEMANTICKEYPHRASETABLE  
    (  
    Production.Document,  
    Document  
    ) AS KEYP_TBL  
ON DOC_TBL.DocumentID = KEYP_TBL.document_key  
WHERE KEYP_TBL.keyphrase = 'Bracket'  
ORDER BY KEYP_TBL.Score DESC;  
GO  
```  
  
  
