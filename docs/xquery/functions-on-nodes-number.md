---
title: 숫자 함수 (XQuery) | Microsoft Docs
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
- number function
- fn:number function
ms.assetid: dff6d19b-765c-4df9-afff-9a0e7be9b91b
author: rothja
ms.author: jroth
ms.openlocfilehash: 31a52f86692d5769fe22f4cf0b5a04ad324c3ac0
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67930112"
---
# <a name="functions-on-nodes---number"></a>노드 함수 - number
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  표시 된 노드의 숫자 값을 반환 *$arg*합니다.  
  
## <a name="syntax"></a>구문  
  
```  
  
fn:number() as xs:double?   
fn:number($arg as node()?) as xs:double?  
```  
  
## <a name="arguments"></a>인수  
 *$arg*  
 값이 숫자로 반환되는 노드입니다.  
  
## <a name="remarks"></a>설명  
 하는 경우 *$arg* 은 지정 하지 않으면 double로 변환 하는 컨텍스트 노드의 숫자 값 반환 됩니다. SQL server에서 **fn:number()** 없이 상황별 조건자의 컨텍스트에서 인수로 사용할 수 있습니다. 특히 사용 시 대괄호([])로 묶어야 합니다. 예를 들어 다음 식은 반환 된 <`ROOT`> 요소입니다.  
  
```  
declare @x xml  
set @x='<ROOT>111</ROOT>'  
select @x.query('/ROOT[number()=111]')  
```  
  
 에 정의 된 노드의 값이 숫자 단순 유형의 올바른 어휘 표현이 없습니다 **XML Schema Part 2: datatypes, W3C Recommendation**, 빈 시퀀스를 반환 합니다. NaN은 지원되지 않습니다.  
  
## <a name="examples"></a>예  
 이 항목에서는 다양 한 저장 된 XML 인스턴스에 대 한 XQuery 예를 제공 **xml** AdventureWorks 데이터베이스의 열을 입력 합니다.  
  
### <a name="a-using-the-number-xquery-function-to-retrieve-the-numeric-value-of-an-attribute"></a>A. number() XQuery 함수를 사용하여 특성의 숫자 값 검색  
 다음 쿼리는 제품 모델 7의 제조 과정에 있는 첫 번째 업무 센터 위치에서 부지 크기 특성의 숫자 값을 검색합니다.  
  
```  
SELECT ProductModelID, Instructions.query('  
declare namespace AWMI="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions" ;  
     for $i in (//AWMI:root//AWMI:Location)[1]  
     return   
       <Location LocationID="{ ($i/@LocationID) }"   
                   LotSizeA="{  $i/@LotSize }"  
                   LotSizeB="{  number($i/@LotSize) }"  
                   LotSizeC="{ number($i/@LotSize) + 1 }" >  
  
       </Location>  
') as Result  
FROM Production.ProductModel  
WHERE ProductModelID=7  
```  
  
 이전 쿼리에서 다음을 유의하세요.  
  
-   합니다 **number ()** 에 대 한 쿼리에 의해 표시 된 것 처럼이 함수는 필요 하지는 **LotSizeA** 특성입니다. 이 함수는 XPath 1.0 함수이며 주로 이전 버전과의 호환성을 위해 사용됩니다.  
  
-   에 대 한 XQuery **LotSizeB** 숫자 함수를 지정 하 고 중복 됩니다.  
  
-   에 대 한 쿼리 **LotSizeD** 산술 연산에서 숫자 값의 사용을 보여 줍니다.  
  
 다음은 결과입니다.  
  
```  
ProductModelID   Result  
----------------------------------------------  
7              <Location LocationID="10"   
                         LotSizeA="100"   
                         LotSizeB="100"   
                         LotSizeC="101" />  
```  
  
### <a name="implementation-limitations"></a>구현 시 제한 사항  
 제한 사항은 다음과 같습니다.  
  
-   합니다 **number ()** 함수는 노드만 있습니다. 원자 값을 사용하지 않습니다.  
  
-   값을 숫자로 반환할 수 없는 경우는 **number ()** 함수는 NaN 대신 빈 시퀀스를 반환 합니다.  
  
## <a name="see-also"></a>관련 항목  
 [xml 데이터 형식에 대한 XQuery 함수](../xquery/xquery-functions-against-the-xml-data-type.md)  
  
  
