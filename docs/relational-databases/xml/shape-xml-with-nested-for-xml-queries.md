---
title: 중첩 FOR XML 쿼리로 XML 구체화 | Microsoft 문서
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- FOR XML query
- queries [XML in SQL Server], nested FOR XML
- XML [SQL Server], FOR XML queries
ms.assetid: 8dc42c05-16e8-4b7b-a5d3-550b55acae26
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 22522a2bfabc3406e8e3e1331a0518a38b930c8a
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/30/2020
ms.locfileid: "68000669"
---
# <a name="shape-xml-with-nested-for-xml-queries"></a>중첩 FOR XML 쿼리로 XML 구체화
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  다음 예에서는 `Production.Product` 테이블을 쿼리하여 특정 제품의 `ListPrice` 및 `StandardCost` 값을 검색합니다. 쿼리를 효과적으로 만들기 위해 두 가격이 모두 <`Price`> 요소에 반환되고 각 <`Price`> 요소에는 `PriceType` 특성이 포함됩니다.  
  
## <a name="example"></a>예제  
 다음은 XML의 예상 셰이프입니다.  
  
```  
<xsd:schema xmlns:schema="urn:schemas-microsoft-com:sql:SqlRowSet2" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:sqltypes="https://schemas.microsoft.com/sqlserver/2004/sqltypes" targetNamespace="urn:schemas-microsoft-com:sql:SqlRowSet2" elementFormDefault="qualified">  
  <xsd:import namespace="https://schemas.microsoft.com/sqlserver/2004/sqltypes" schemaLocation="https://schemas.microsoft.com/sqlserver/2004/sqltypes/sqltypes.xsd" />  
  <xsd:element name="Production.Product" type="xsd:anyType" />  
</xsd:schema>  
<Production.Product xmlns="urn:schemas-microsoft-com:sql:SqlRowSet2" ProductID="520">  
  <Price xmlns="" PriceType="ListPrice">133.34</Price>  
  <Price xmlns="" PriceType="StandardCost">98.77</Price>  
</Production.Product>  
```  
  
 다음은 중첩된 FOR XML 쿼리입니다.  
  
```  
USE AdventureWorks2012;  
GO  
SELECT Product.ProductID,   
          (SELECT 'ListPrice' as PriceType,   
                   CAST(CAST(ListPrice as NVARCHAR(40)) as XML)   
           FROM    Production.Product Price   
           WHERE   Price.ProductID=Product.ProductID   
           FOR XML AUTO, TYPE),  
          (SELECT  'StandardCost' as PriceType,   
                   CAST(CAST(StandardCost as NVARCHAR(40)) as XML)   
           FROM    Production.Product Price   
           WHERE   Price.ProductID=Product.ProductID   
           FOR XML AUTO, TYPE)  
FROM Production.Product  
WHERE ProductID=520  
for XML AUTO, TYPE, XMLSCHEMA  
```  
  
 이전 쿼리에서 다음을 유의하세요.  
  
-   외부 SELECT 문은 `Product`ProductID **특성과 두 개의 <** > 자식 요소가 있는 <`Price`> 요소를 생성합니다.  
  
-   두 개의 내부 SELECT 문은 각각 `Price`PriceType **특성과 제품 가격을 반환하는 XML이 포함된 두 개의 <** > 요소를 생성합니다.  
  
-   외부 SELECT 문에 있는 XMLSCHEMA 지시어는 결과 XML의 셰이프를 기술하는 인라인 XSD 스키마를 생성합니다.  
  
 쿼리를 효과적으로 만들기 위해 FOR XML 쿼리를 작성한 다음 결과에 대해 XQuery를 작성하여 다음 쿼리에서와 같이 XML 셰이프를 다시 지정할 수 있습니다.  
  
```  
SELECT ProductID,   
 ( SELECT p2.ListPrice, p2.StandardCost  
   FROM Production.Product p2   
   WHERE Product.ProductID = p2.ProductID  
   FOR XML AUTO, ELEMENTS XSINIL, type ).query('  
                                   for $p in /p2/*  
                                   return   
                                    <Price PriceType = "{local-name($p)}">  
                                     { data($p) }  
                                    </Price>  
                                  ')  
FROM Production.Product  
WHERE ProductID = 520  
FOR XML AUTO, TYPE  
```  
  
 이전 예에서는 **xml** 데이터 형식의 **query()** 메서드를 사용하여 내부 FOR XML 쿼리에 의해 반환된 XML을 쿼리하고 예상된 결과를 생성합니다.  
  
 다음은 결과입니다.  
  
```  
<Production.Product ProductID="520">  
  <Price PriceType="ListPrice">133.3400</Price>  
  <Price PriceType="StandardCost">98.7700</Price>  
</Production.Product>  
```  
  
## <a name="see-also"></a>참고 항목  
 [중첩 FOR XML 쿼리 사용](../../relational-databases/xml/use-nested-for-xml-queries.md)  
  
  
