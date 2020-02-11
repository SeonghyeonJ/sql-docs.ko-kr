---
title: MDX 연산자 참조 (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: c026da3551448faf7cf204dbdde1e794d5b12967
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68033913"
---
# <a name="mdx-operator-reference-mdx"></a>MDX 연산자 참조(MDX)


  MDX 언어는 산술, 논리, 비교, 집합, 문자열 및 단항 연산자를 지원합니다. 다음 표에서는 지원되는 연산자와 해당 설명을 나열합니다.  
  
## <a name="in-this-section"></a>섹션 내용  
  
|항목|Description|  
|-----------|-----------------|  
|[--&#40;주석&#41; &#40;MDX&#41;](../mdx/comment-mdx-operator-reference.md)|사용자가 제공한 주석 텍스트를 나타냅니다.|  
|[-&#40;&#41; &#40;MDX를 제외 하 고&#41;](../mdx/except-mdx-operator.md)|중복된 멤버를 제거하고 두 집합 간의 차집합을 반환하는 집합 연산을 수행합니다.|  
|[-&#40;음수&#41; &#40;MDX&#41;](../mdx/negative-mdx.md)|숫자 식의 음수 값을 반환하는 단항 연산을 수행합니다.|  
|[-&#40;빼기&#41; &#40;MDX&#41;](../mdx/subtract-mdx.md)|한 수에서 다른 수를 빼는 산술 연산을 수행합니다.|  
|[&#42; &#40;Crossjoin&#41; &#40;MDX&#41;](../mdx/crossjoin-mdx-operator-reference.md)|두 집합의 교차곱을 반환하는 집합 연산을 수행합니다.|  
|[MDX&#41; &#40;&#42; &#40;곱하기&#41;](../mdx/multiply-mdx.md)|두 수를 곱하는 산술 연산을 수행합니다.|  
|[&#40;&#41; &#40;MDX&#41;](../mdx/divide-mdx-operator-reference.md)|한 수를 다른 수로 나누는 산술 연산을 수행합니다.|  
|[^ &#40;Power&#41; &#40;MDX&#41;](../mdx/power-mdx.md)|한 수에 다른 수를 제곱하는 산술 연산을 수행합니다.|  
|[MDX &#40;설명&#41;](../mdx/comment-mdx.md)|사용자가 제공한 주석 텍스트를 나타냅니다.|  
|[MDX&#41; &#40;&#40;설명&#41;](../mdx/comment-mdx-double-slash.md)|사용자가 제공하는 텍스트를 나타냅니다.|  
|[: &#40;범위&#41; &#40;MDX&#41;](../mdx/range-mdx.md)|지정한 두 멤버를 엔드포인트로 사용하고 지정한 두 멤버 사이의 모든 멤버를 집합의 멤버로 포함시켜 일반적인 순서로 정렬된 집합을 반환하는 집합 연산을 수행합니다.|  
|[+ &#40;MDX&#41; &#40;추가&#41;](../mdx/add-mdx.md)|두 수를 더하는 산술 연산을 수행합니다.|  
|[+ &#40;긍정&#41; &#40;MDX&#41;](../mdx/positive-mdx.md)|숫자 식의 양수 값을 반환하는 단항 연산을 수행합니다.|  
|[+ &#40;문자열 연결&#41; &#40;MDX&#41;](../mdx/string-concatenation-mdx.md)|둘 이상의 문자열, 튜플 또는 문자열과 튜플의 조합을 연결하는 문자열 연산을 수행합니다.|  
|[+ &#40;Union&#41; &#40;MDX&#41;](../mdx/union-mdx-operator-reference.md)|중복된 요소를 제거하고 두 집합의 합집합을 반환하는 집합 연산을 수행합니다.|  
|[&#60; &#40;MDX&#41; &#40;보다 작음&#41;](../mdx/less-than-mdx.md)|하나의 MDX 식의 값이 다른 MDX 식의 값보다 작은지 확인하는 비교 연산을 수행합니다.|  
|[&#60;= &#40;MDX&#41; &#40;보다 작거나 같음&#41;](../mdx/less-than-or-equal-to-mdx.md)|하나의 MDX 식의 값이 다른 MDX 식의 값보다 작거나 같은지 확인하는 비교 연산을 수행합니다.|  
|[&#41; &#40;MDX와 같지&#60;&#62; &#40;&#41;](../mdx/not-equal-to-mdx.md)|하나의 MDX 식의 값이 다른 MDX 식의 값과 다른지 확인하는 비교 연산을 수행합니다.|  
|[= &#40;&#41; &#40;MDX&#41;](../mdx/equal-to-mdx.md)|하나의 MDX 식의 값이 다른 MDX 식의 값과 동일한지 확인하는 비교 연산을 수행합니다.|  
|[&#62; &#40;&#41; &#40;MDX&#41;](../mdx/greater-than-mdx.md)|하나의 MDX 식의 값이 다른 MDX 식의 값보다 큰지 확인하는 비교 연산을 수행합니다.|  
|[&#62;= &#40;MDX&#41; &#40;보다 크거나 같음&#41;](../mdx/greater-than-or-equal-to-mdx.md)|하나의 MDX 식의 값이 다른 MDX 식의 값보다 크거나 같은지 확인하는 비교 연산을 수행합니다.|  
|[및 &#40;MDX&#41;](../mdx/and-mdx.md)|두 숫자 식에 논리 결합을 수행합니다.|  
|[&#40;MDX&#41;](../mdx/is-mdx.md)|두 개체 식에 대해 논리 비교를 수행합니다.|  
|[&#40;MDX&#41;](../mdx/not-mdx.md)|숫자 식에 논리 부정을 수행합니다.|  
|[또는 MDX&#41;&#40;](../mdx/or-mdx.md)|두 숫자 식에 논리 분리를 수행합니다.|  
|[XOR &#40;MDX&#41;](../mdx/xor-mdx.md)|두 숫자 식에 대해 논리 제외를 수행합니다.|  
  
## <a name="see-also"></a>참고 항목  
 [Mdx 언어 참조 &#40;MDX&#41;](../mdx/mdx-language-reference-mdx.md)  
  
  
