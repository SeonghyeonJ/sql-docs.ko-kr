---
title: 유효한 부울 값 (XQuery) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: sql
ms.reviewer: ''
ms.technology: xml
ms.topic: language-reference
dev_langs:
- XML
helpviewer_keywords:
- effective Boolean value [XQuery]
- Boolean values
- XQuery, effective Boolean values
- EBV
ms.assetid: 506682b1-b6c9-45e2-aa54-7abd5844c3f1
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 685c5a6290f9f6b51321c8d730b60614dc0f5fa7
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62934537"
---
# <a name="effective-boolean-value-xquery"></a>유효한 부울 값(XQuery)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  다음은 유효한 부울 값입니다.  
  
-   피연산자가 빈 시퀀스이거나 부울이 거짓인 경우 False입니다.  
  
-   그렇지 않으면 값이 True입니다.  
  
 유효한 부울 값은 단일 부울 값, 노드 시퀀스 또는 빈 시퀀스를 반환하는 식에 대해 계산될 수 있습니다. 다음 유형의 식을 처리할 때는 부울 값이 암시적으로 계산됩니다.  
  
-   논리 식  
  
-   [작동 하지](../xquery/functions-on-boolean-values-not-function.md)  
  
-   FLWOR 식의 WHERE 절  
  
-   [조건식](../xquery/conditional-expressions-xquery.md)  
  
-   [QuantifiedeExpressions](../xquery/quantified-expressions-xquery.md)  
  
 다음은 유효한 부울 값 예입니다. 경우는 **경우** 식을 처리 하는 조건의 유효한 부울 값이 결정 됩니다. `/a[1]`은 빈 시퀀스를 반환하기 때문에 유효한 부울 값은 False입니다. 결과는 하나의 텍스트 노드(False)가 포함된 XML로 반환됩니다.  
  
```  
value is false  
DECLARE @x XML  
SET @x = '<b/>'  
SELECT @x.query('if (/a[1]) then "true" else "false"')  
go  
```  
  
 다음 예에서는 식이 비어 있지 않은 시퀀스를 반환하기 때문에 유효한 부울 값이 True입니다.  
  
```  
DECLARE @x XML  
SET @x = '<a/>'  
SELECT @x.query('if (/a[1]) then "true" else "false"')  
go  
```  
  
 쿼리를 입력 하면 **xml** 열 이나 변수를 부울 유형의 노드를 가질 수 있습니다. 합니다 **data ()** 이 경우 부울 값을 반환 합니다. 쿼리 식이 부울 값 True를 반환하는 경우 유효한 부울 값은 다음 예에서와 같이 True입니다. 이 예에는 다음 내용에 대해서도 설명됩니다.  
  
-   XML 스키마 컬렉션이 생성됩니다. 요소 \<b > 컬렉션은 부울 형식입니다.  
  
-   형식화 된 **xml** 변수 생성 및 쿼리 됩니다.  
  
-   `data(/b[1])` 식은 부울 값 True를 반환합니다. 따라서 이 경우 유효한 부울 값은 True입니다.  
  
-   식 `data(/b[2])` 부울 값 false를 반환 합니다. 따라서 이 경우 유효한 부울 값은 False입니다.  
  
```  
CREATE XML SCHEMA COLLECTION SC AS '  
<schema xmlns="http://www.w3.org/2001/XMLSchema">  
      <element name="s" type="string"/>  
      <element name="b" type="boolean"/>  
</schema>'  
go  
DECLARE @x XML(SC)  
SET @x = '<b>true</b><b>false</b>'  
SELECT @x.query('if (data(/b[1])) then "true" else "false"')  
SELECT @x.query('if (data(/b[2])) then "true" else "false"')  
go  
```  
  
## <a name="see-also"></a>관련 항목  
 [XQuery 기초](../xquery/xquery-basics.md)   
 [FLWOR 문 및 반복 &#40;XQuery&#41;](../xquery/flwor-statement-and-iteration-xquery.md)  
  
  
