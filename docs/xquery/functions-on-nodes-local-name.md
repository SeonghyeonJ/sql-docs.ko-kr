---
title: local-name 함수 (XQuery) | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: sql
ms.reviewer: ''
ms.technology: xml
ms.topic: language-reference
dev_langs:
- XML
helpviewer_keywords:
- fn:local-name function
- local-name function
ms.assetid: c901ef5d-89c5-482a-bf64-3eefbcf3098d
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 93f289ed165742ae8fdf8d49732186161a4a8b5d
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62936521"
---
# <a name="functions-on-nodes---local-name"></a>노드 함수 - local-name
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  이름의 로컬 부분을 반환 *$arg* 길이가 0 인 문자열을 갖게 됩니다 또는 ncname 어휘 형식이 xs: string을으로 합니다. 인수를 제공하지 않으면 기본값은 컨텍스트 노드입니다.  
  
## <a name="syntax"></a>구문  
  
```  
fn:local-name() as xs:string  
fn:local-name($arg as node()?) as xs:string  
```  
  
## <a name="arguments"></a>인수  
 *$arg*  
 로컬 이름 부분이 검색될 노드 이름입니다.  
  
## <a name="remarks"></a>Remarks  
  
-   SQL server에서 **fn:local-name()** 없이 상황별 조건자의 컨텍스트에서 인수로 사용할 수 있습니다. 특히 사용 시 대괄호(`[ ]`)로 묶어야 합니다.  
  
-   인수가 제공되었지만 빈 시퀀스인 경우 함수는 길이가 0인 문자열을 반환합니다.  
  
-   대상 노드가 문서 노드이거나 설명이거나 텍스트 노드이기 때문에 대상 노드의 이름이 없는 경우 함수는 길이가 0인 문자열을 반환합니다.  
  
## <a name="examples"></a>예  
 이 항목에서는 다양 한 저장 된 XML 인스턴스에 대 한 XQuery 예를 제공 **xml** AdventureWorks 데이터베이스의 열을 입력 합니다.  
  
### <a name="a-retrieve-local-name-of-a-specific-node"></a>1\. 특정 노드의 로컬 이름 검색  
 다음은 형식화되지 않은 XML 인스턴스에 대해 지정된 쿼리입니다. `local-name(/ROOT[1])` 쿼리 식은 지정한 노드의 로컬 이름 부분을 검색합니다.  
  
```  
declare @x xml  
set @x='<ROOT><a>111</a></ROOT>'  
SELECT @x.query('local-name(/ROOT[1])')  
-- result = ROOT  
```  
  
 다음은 ProductModel 테이블의 형식화된 xml 열인 Instructions 열에 대해 지정된 쿼리입니다. `local-name(/AWMI:root[1]/AWMI:Location[1])` 식은 지정된 노드의 로컬 이름 `Location`을 반환합니다.  
  
```  
SELECT Instructions.query('  
declare namespace AWMI="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions" ;  
     local-name(/AWMI:root[1]/AWMI:Location[1])') as Result  
FROM Production.ProductModel  
WHERE ProductModelID=7  
-- result = Location  
```  
  
### <a name="b-using-local-name-without-argument-in-a-predicate"></a>2\. 조건자에서 인수가 없는 로컬 이름 사용  
 형식화 된 Instructions 열에 대해 다음 쿼리를 지정 **xml** ProductModel 테이블의 열입니다. 식의 모든 요소 자식을 반환 합니다 <`root`> QName의 로컬 이름 부분이 "Location" 인 요소입니다. 합니다 **local-name ()** 함수는 지정 된 조건자 및 함수에 의해 컨텍스트 노드를 사용 하는 인수가 없습니다.  
  
```  
SELECT Instructions.query('  
declare namespace AWMI="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions" ;  
  /AWMI:root//*[local-name() = "Location"]') as Result  
FROM Production.ProductModel  
WHERE ProductModelID=7  
```  
  
 모든 쿼리에서 반환 된 <`Location`> 요소 자식을 <`root`> 요소.  
  
## <a name="see-also"></a>관련 항목  
 [노드 함수](https://msdn.microsoft.com/library/09a8affa-3341-4f50-aebc-fdf529e00c08)   
 [namespace-uri 함수 &#40;XQuery&#41;](../xquery/functions-on-nodes-namespace-uri.md)  
  
  
