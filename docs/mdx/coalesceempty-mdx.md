---
description: CoalesceEmpty(MDX)
title: CoalesceEmpty (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 4fd02400d6b560e1cc0b21908b788a257f56b26c
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88487586"
---
# <a name="coalesceempty-mdx"></a>CoalesceEmpty(MDX)


  빈 셀 값을 비어 있지 않은 특정 셀 값으로 변환합니다. 지정된 셀 값은 숫자이거나 문자열일 수 있습니다.  
  
## <a name="syntax"></a>구문  
  
```  
  
Numeric syntax  
CoalesceEmpty( Numeric_Expression1 [ ,Numeric_Expression2,...n] )  
  
String syntax  
CoalesceEmpty(String_Expression1 [ ,String_Expression2,...n] )  
```  
  
## <a name="arguments"></a>인수  
 *Numeric_Expression1*  
 숫자를 반환하는 셀 좌표의 유효한 숫자 식으로서, 일반적으로 MDX 식입니다.  
  
 *Numeric_Expression2*  
 유효한 숫자 식으로서, 일반적으로 지정된 숫자 값입니다.  
  
 *String_Expression1*  
 문자열을 반환하는 셀 좌표의 유효한 문자열 식으로서, 일반적으로 MDX 식입니다.  
  
 *String_Expression2*  
 첫 번째 문자열 식에서 반환되는 NULL을 대체하는 유효한 문자열 식으로서, 일반적으로 지정된 문자열 값입니다.  
  
## <a name="remarks"></a>설명  
 하나 이상의 숫자 식이 지정 된 경우 **CoalesceEmpty** 함수는 비어 있지 않은 값으로 확인 될 수 있는 첫 번째 숫자 식 (왼쪽에서 오른쪽)의 숫자 값을 반환 합니다. 모든 지정된 숫자 식이 비어 있지 않은 값으로 확인될 수 없으면 함수가 빈 셀 값을 반환합니다. 일반적으로 두 번째 숫자 식의 값은 첫 번째 숫자 식에서 반환되는 NULL을 대체하는 숫자 값입니다.  
  
 문자열 식이 하나 이상 지정된 경우 이 함수는 비어 있지 않은 값으로 확인될 수 있는 첫 번째 문자열 식(왼쪽에서 오른쪽의 순서로)의 문자열 값을 반환합니다. 모든 지정된 문자열 식이 비어 있지 않은 값으로 확인될 수 없으면 함수가 빈 셀 값을 반환합니다. 일반적으로 두 번째 문자열 식의 값은 첫 번째 문자열 식에서 반환되는 NULL을 대체하는 문자열 값입니다.  
  
 **CoalesceEmpty** 함수는 동일한 형식의 값만 사용할 수 있습니다. 즉, 지정된 모든 값 식이 숫자 데이터 형식이나 빈 셀 값으로 계산되거나 지정된 모든 값 식이 문자열 데이터 형식 또는 빈 셀 값으로 계산되어야 합니다. 이 함수에 대한 단일 셀에는 숫자 및 문자열 식이 모두 포함될 수 없습니다.  
  
 빈 셀에 대한 자세한 내용은 OLE DB 설명서를 참조하십시오.  
  
## <a name="example"></a>예제  
 다음 예에서는 **놀이 Works** 큐브를 쿼리 합니다. 이 예에서는 각 제품의 주문 수량과 범주별 주문 수량의 비율을 반환합니다. **CoalesceEmpty** 함수는 계산 멤버의 서식을 지정할 때 null 값이 0으로 표시 되도록 합니다.  
  
```  
WITH   
   MEMBER [Measures].[Order Percent by Category] AS  
   CoalesceEmpty(   
      ([Product].[Product Categories].CurrentMember,  
        Measures.[Order Quantity]) /   
          (  
           Ancestor  
           ( [Product].[Product Categories].CurrentMember,   
             [Product].[Product Categories].[Category]  
           ), Measures.[Order Quantity]  
       ), 0  
   ), FORMAT_STRING='Percent'  
SELECT   
   {Measures.[Order Quantity],  
      [Measures].[Order Percent by Category]} ON COLUMNS,  
{[Product].[Product].Members} ON ROWS  
FROM [Adventure Works]  
WHERE {[Date].[Calendar Year].[Calendar Year].&[2003]}  
```  
  
## <a name="see-also"></a>참고 항목  
 [MDX 함수 참조&#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
