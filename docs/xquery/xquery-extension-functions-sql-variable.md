---
title: 'sql: variable 함수 (XQuery) | Microsoft Docs'
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: sql
ms.reviewer: ''
ms.technology: xml
ms.topic: language-reference
dev_langs:
- XML
helpviewer_keywords:
- sql:variable() function
- sql:variable function
ms.assetid: 6e2e5063-c1cf-4b5a-b642-234921e3f4f7
author: rothja
ms.author: jroth
ms.openlocfilehash: 56a8c53a22fefec7fbda4c2ac7476ae46d664199
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67946002"
---
# <a name="xquery-extension-functions---sqlvariable"></a>XQuery 확장 함수 - sql:variable()
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  XQuery 식 내의 SQL 관계형 값을 포함하는 변수를 제공합니다.  
  
## <a name="syntax"></a>구문  
  
```  
  
sql:variable("variableName") as xdt:anyAtomicType?  
```  
  
## <a name="remarks"></a>설명  
 항목에 설명 된 대로 [관계형 데이터 내에서 XML 데이터 바인딩](../t-sql/xml/binding-relational-data-inside-xml-data.md)를 사용 하는 경우이 함수를 사용할 수 있습니다 [XML 데이터 형식 메서드](../t-sql/xml/xml-data-type-methods.md) XQuery 내 관계형 값을 제공할 합니다.  
  
 예를 들어 합니다 [query () 메서드](../t-sql/xml/query-method-xml-data-type.md) 에 저장 된 XML 인스턴스에 대해 쿼리를 지정 하는 데 사용 되는 **xml** 데이터 형식 변수 또는 열입니다. 일부 경우에는 쿼리에서 [!INCLUDE[tsql](../includes/tsql-md.md)] 변수 또는 매개 변수로부터 값을 사용하거나 관계형 및 XML 데이터를 함께 사용할 수 있습니다. 이 작업을 수행 하려면 사용 합니다 **sql: variable** 함수입니다.  
  
 SQL 값을 해당 XQuery 값으로 매핑되고 해당 SQL 형식에 해당 하는 XQuery 기본 유형이 됩니다.  
  
 만 참조할 수 있습니다는 **xml** XML-DML 원본 식의 컨텍스트에서 인스턴스 insert 문 형식의 값을 참조할 수 없습니다이 고, 그렇지 않으면 **xml** 또는 공용 언어 런타임 (CLR) 사용자 정의 형식입니다.  
  
## <a name="examples"></a>예  
  
### <a name="a-using-the-sqlvariable-function-to-bring-a-transact-sql-variable-value-into-xml"></a>A. sql:variable() 함수를 사용하여 Transact-SQL 변수 값을 XML로 가져오기  
 다음 예에서는 다음으로 구성된 XML 인스턴스를 생성합니다.  
  
-   비-XML 열의 값(`ProductID`). 합니다 [1!s!sql:column () 함수](../xquery/xquery-extension-functions-sql-column.md) XML에이 값을 바인딩하는 데 사용 됩니다.  
  
-   다른 테이블에 있는 비-XML 열의 값(`ListPrice`). 여기에서도 XML에서 이 값을 바인딩하는 데 `sql:column()`이 사용됩니다.  
  
-   [!INCLUDE[tsql](../includes/tsql-md.md)] 변수의 값(`DiscountPrice`). XML로 이 값을 바인딩하는 데 `sql:variable()` 메서드가 사용됩니다.  
  
-   값 (`ProductModelName`)에서 **xml** 쿼리를 보다 유용 하도록 유형 열입니다.  
  
 다음은 쿼리입니다.  
  
```sql
DECLARE @price money  
  
SET @price=2500.00  
SELECT ProductID, Production.ProductModel.ProductModelID,CatalogDescription.query('  
declare namespace pd="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
  
       <Product   
           ProductID="{ sql:column("Production.Product.ProductID") }"  
           ProductModelID= "{ sql:column("Production.Product.ProductModelID") }"  
           ProductModelName="{/pd:ProductDescription[1]/@ProductModelName }"  
           ListPrice="{ sql:column("Production.Product.ListPrice") }"  
           DiscountPrice="{ sql:variable("@price") }"  
        />')   
FROM Production.Product   
JOIN Production.ProductModel  
ON Production.Product.ProductModelID = Production.ProductModel.ProductModelID  
WHERE ProductID=771  
```  
  
 이전 쿼리에서 다음을 유의하세요.  
  
-   `query()` 메서드 내부의 XQuery는 XML을 생성합니다.  
  
-   합니다 `namespace` 키워드는 네임 스페이스 접두사를 정의 하는 데 사용 됩니다 합니다 [XQuery 프롤로그](../xquery/modules-and-prologs-xquery-prolog.md)합니다. 이러한 작업은 스키마가 연결되어 있는 `ProductModelName` 유형의 열에서 `CatalogDescription xml` 특성 값이 검색되기 때문에 수행됩니다.  
  
 다음은 결과입니다.  
  
```xml
<Product ProductID="771" ProductModelID="19"   
         ProductModelName="Mountain 100"   
         ListPrice="3399.99" DiscountPrice="2500" />  
```  
  
## <a name="see-also"></a>관련 항목  
 [SQL Server XQuery 확장 함수](https://msdn.microsoft.com/library/4bc5d499-5fec-4c3f-b11e-5ab5ef9d8f97)   
 [형식화된 XML과 형식화되지 않은 XML 비교](../relational-databases/xml/compare-typed-xml-to-untyped-xml.md)   
 [XML 데이터&#40;SQL Server&#41;](../relational-databases/xml/xml-data-sql-server.md)   
 [XML 데이터 인스턴스 만들기](../relational-databases/xml/create-instances-of-xml-data.md)   
 [xml 데이터 형식 메서드](../t-sql/xml/xml-data-type-methods.md)   
 [XML DML&#40;XML 데이터 수정 언어&#41;](../t-sql/xml/xml-data-modification-language-xml-dml.md)  
  
  
