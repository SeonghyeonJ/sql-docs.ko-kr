---
title: concat 함수 (XQuery) | Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql
ms.prod_service: sql
ms.reviewer: ''
ms.technology: xml
ms.topic: language-reference
dev_langs:
- XML
helpviewer_keywords:
- fn:concat function
- concat function [XQuery]
ms.assetid: d50afd20-a297-445e-be9e-13b48017e7ca
author: rothja
ms.author: jroth
ms.openlocfilehash: 063eca49a6a4d69e84e8a3d05221b632d0690bef
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68099836"
---
# <a name="functions-on-string-values---concat"></a>문자열 값 함수 - concat
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  0개 이상의 문자열을 인수로 허용하고 이러한 각 인수의 값을 연결하여 만든 문자열을 반환합니다.  
  
## <a name="syntax"></a>구문  
  
```  
  
fn:concat ($string as xs:string?  
           ,$string as xs:string?  
           [, ...]) as xs:string  
```  
  
## <a name="arguments"></a>인수  
 *$string*  
 연결하기 위한 문자열(옵션)입니다.  
  
## <a name="remarks"></a>설명  
 함수에는 최소한 둘 이상의 인수가 필요합니다. 인수가 빈 시퀀스인 경우 길이가 0인 문자열로 처리됩니다.  
  
## <a name="supplementary-characters-surrogate-pairs"></a>보조 문자(서로게이트 쌍)  
 XQuery 함수에서 서로게이트 쌍의 동작은 데이터베이스 호환성 수준과 일부 경우 함수의 기본 네임스페이스 URI에 따라 달라집니다. 자세한 내용은 항목의 "XQuery 함수는 서로게이트 인식" 섹션을 참조 하세요 [SQL Server 2016 데이터베이스 엔진 기능의 주요 변경 내용](../database-engine/breaking-changes-to-database-engine-features-in-sql-server-2016.md)합니다. 도 참조 하세요 [ALTER DATABASE 호환성 수준 &#40;TRANSACT-SQL&#41; ](../t-sql/statements/alter-database-transact-sql-compatibility-level.md) 하 고 [Collation and Unicode Support](../relational-databases/collations/collation-and-unicode-support.md).  
  
## <a name="examples"></a>예  
 이 항목에서는 다양 한 저장 된 XML 인스턴스에 대 한 XQuery 예를 제공 **xml** AdventureWorks 예제 데이터베이스의 열을 입력 합니다.  
  
### <a name="a-using-the-concat-xquery-function-to-concatenate-strings"></a>A. concat() XQuery 함수를 사용하여 문자열 연결  
 이 쿼리는 특정한 제품 모델에 대한 보증 기간과 보증 설명을 연결하여 만든 문자열을 반환합니다. 카탈로그 설명 문서에는 <`Warranty`> 요소는 구성 <`WarrantyPeriod`> 및 <`Description`> 자식 요소입니다.  
  
```  
WITH XMLNAMESPACES (  
'https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription' AS pd,  
'https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelWarrAndMain' AS wm)  
SELECT CatalogDescription.query('  
    <Product   
        ProductModelID= "{ (/pd:ProductDescription/@ProductModelID)[1] }"  
        ProductModelName = "{ sql:column("PD.Name") }" >  
        {   
          concat( string((/pd:ProductDescription/pd:Features/wm:Warranty/wm:WarrantyPeriod)[1]), "-",  
                  string((/pd:ProductDescription/pd:Features/wm:Warranty/wm:Description)[1]))   
         }   
     </Product>  
 ') as Result  
FROM Production.ProductModel PD  
WHERE  PD.ProductModelID=28  
  
```  
  
 이전 쿼리에서 다음을 유의하세요.  
  
-   SELECT 절에서 CatalogDescription은는 **xml** 유형 열입니다. 따라서 합니다 [query () 메서드 (XML 데이터 형식)](../t-sql/xml/query-method-xml-data-type.md), instructions.query 사용 됩니다. XQuery 문은 쿼리 메서드에 대한 인수로 지정됩니다.  
  
-   쿼리가 실행되는 문서는 네임스페이스를 사용합니다. 따라서 합니다 **네임 스페이스** 키워드 네임 스페이스 접두사를 정의 하는 데 사용 됩니다. 자세한 내용은 [XQuery 프롤로그](../xquery/modules-and-prologs-xquery-prolog.md)합니다.  
  
 다음은 결과입니다.  
  
```  
<Product ProductModelID="28" ProductModelName="Road-450">1 year-parts and labor</Product>  
```  
  
 앞의 쿼리는 특정한 제품에 대한 정보를 검색합니다. 다음 쿼리는 XML 카탈로그 설명이 저장된 모든 제품에 대해 동일한 정보를 검색합니다. 합니다 **exist ()** 메서드는 **xml** 데이터 형식을 WHERE 절에서는 XML 문서 행에 있으면 True를 반환 합니다를 <`ProductDescription`> 요소입니다.  
  
```  
WITH XMLNAMESPACES (  
'https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription' AS pd,  
'https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelWarrAndMain' AS wm)  
  
SELECT CatalogDescription.query('  
    <Product   
        ProductModelID= "{ (/pd:ProductDescription/@ProductModelID)[1] }"   
        ProductName = "{ sql:column("PD.Name") }" >  
        {   
          concat( string((/pd:ProductDescription/pd:Features/wm:Warranty/wm:WarrantyPeriod)[1]), "-",  
                  string((/pd:ProductDescription/pd:Features/wm:Warranty/wm:Description)[1]))   
         }   
     </Product>  
 ') as Result  
FROM Production.ProductModel PD  
WHERE CatalogDescription.exist('//pd:ProductDescription ') = 1  
  
```  
  
 반환한 부울 값에 **exist ()** 메서드는 **xml** 유형 1과 비교 됩니다.  
  
### <a name="implementation-limitations"></a>구현 시 제한 사항  
 제한 사항은 다음과 같습니다.  
  
-   합니다 **concat ()** SQL Server의 함수에는 xs: string 유형의 값만 허용 합니다. 그 밖의 다른 값은 명시적으로 xs:string 또는 xdt:untypedAtomic으로 캐스팅되어야 합니다.  
  
## <a name="see-also"></a>관련 항목  
 [xml 데이터 형식에 대한 XQuery 함수](../xquery/xquery-functions-against-the-xml-data-type.md)  
  
  
