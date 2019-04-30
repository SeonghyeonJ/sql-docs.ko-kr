---
title: 계산 열에 XML 사용 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- computed columns, XML
- XML [SQL Server], computed columns
ms.assetid: 1313b889-69b4-4018-9868-0496dd83bf44
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f9bfa88e56e5f914afd4f027634d0f069406c009
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63193230"
---
# <a name="use-xml-in-computed-columns"></a>계산 열에 XML 사용
  XML 인스턴스는 계산 열의 원본이나 계산 열의 유형으로 표시될 수 있습니다. 이 항목의 예에서는 계산 열이 있는 XML을 사용하는 방법을 보여 줍니다.  
  
## <a name="creating-computed-columns-from-xml-columns"></a>XML 열에서 계산 열 만들기  
 다음 `CREATE TABLE` 문에서 `xml` 유형 열(`col2`)은 `col1`에서 계산됩니다.  
  
```  
CREATE TABLE T(col1 varchar(max), col2 AS CAST(col1 AS xml) )    
```  
  
 다음 `xml` 문에서와 같이 계산 열을 만들 때도 `CREATE TABLE` 데이터 형식이 원본으로 표시될 수 있습니다.  
  
```  
CREATE TABLE T (col1 xml, col2 as cast(col1 as varchar(1000) ))   
```  
  
 다음 예에서와 같이 `xml` 유형 열에서 값을 추출하여 계산 열을 만들 수 있습니다. 계산 열을 만들 때는 `xml` 데이터 형식 메서드를 직접 사용할 수 없으므로 이 예에서는 XML 인스턴스에서 값을 반환하는 함수(`my_udf`)를 먼저 정의합니다. 이 함수는 `value()` 유형의 `xml` 메서드를 래핑합니다. 그러면 함수 이름이 계산 열의 `CREATE TABLE` 문에 지정됩니다.  
  
```  
CREATE FUNCTION my_udf(@var xml) returns int  
AS BEGIN   
RETURN @var.value('(/ProductDescription/@ProductModelID)[1]' , 'int')  
END  
GO  
-- Use the function in CREATE TABLE.  
CREATE TABLE T (col1 xml, col2 as dbo.my_udf(col1) )  
GO  
-- Try adding a row.   
INSERT INTO T values('<ProductDescription ProductModelID="1" />')  
GO  
-- Verify results.  
SELECT col2, col1  
FROM T  
  
```  
  
 이전 예에서와 같이 다음 예에서는 계산 열에 대해 `xml` 유형 인스턴스를 반환하도록 함수를 정의합니다. 함수 내에서 `query()` 데이터 형식의 `xml` 메서드는 `xml` 유형 매개 변수에서 값을 검색합니다.  
  
```  
CREATE FUNCTION my_udf(@var xml)   
  RETURNS xml AS   
BEGIN   
   RETURN @var.query('ProductDescription/Features')  
END  
```  
  
 다음 `CREATE TABLE` 문에서 `Col2` 는 함수에서 반환된 XML 데이터(`<Features>` 요소)를 사용하는 계산 열입니다.  
  
```  
CREATE TABLE T (Col1 xml, Col2 as dbo.my_udf(Col1) )  
-- Insert a row in table T.  
INSERT INTO T VALUES('  
<ProductDescription ProductModelID="1" >  
  <Features>  
    <Feature1>description</Feature1>  
    <Feature2>description</Feature2>  
  </Features>  
</ProductDescription>')  
-- Verify the results.  
SELECT *  
FROM T  
```  
  
### <a name="in-this-section"></a>섹션 내용  
  
|항목|Description|  
|-----------|-----------------|  
|[계산 열을 사용하여 자주 사용되는 XML 값 승격](promote-frequently-used-xml-values-with-computed-columns.md)|속성 테이블 및 계산 열이 있는 속성 승격을 사용하는 방법을 설명합니다.|  
  
  
