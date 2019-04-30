---
title: Mtd (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 74c8748ae02df8747be5670f09ec11c7dfa8e882
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63278092"
---
# <a name="mtd-mdx"></a>Mtd(MDX)


  지정한 멤버와 동일한 수준의 형제 멤버 집합을 반환합니다. 이 집합은 첫 번째 형제 멤버부터 시작하여 지정된 멤버에서 끝나며 Time 차원의 Year 수준에 따라 제한됩니다.  
  
## <a name="syntax"></a>구문  
  
```  
  
Mtd( [ Member_Expression ] )  
```  
  
## <a name="arguments"></a>인수  
 *Member_Expression*  
 멤버를 반환하는 유효한 MDX 식입니다.  
  
## <a name="remarks"></a>Remarks  
 멤버 식을 지정 하지 않으면 기본값이 있으며 수준 유형이 인 첫 번째 계층의 현재 멤버 *개월* 형식의 첫 번째 차원의 *시간* 측정값 그룹에 있습니다.  
  
 합니다 **Mtd** 함수는에 대 한 바로 가기 함수는 [PeriodsToDate](../mdx/periodstodate-mdx.md) 수준을 기준으로 하는 특성 계층의 Type 속성 설정 된 경우 함수 *개월*합니다. 즉, `Mtd(Member_Expression)`은 `PeriodsToDate(Month_Level_Expression,Member_Expression)`과 동일합니다.  
  
## <a name="example"></a>예제  
 다음 예에서는 2002년 7월 중 7월 20일까지의 일별 인터넷 판매 운송 비용의 합계를 반환합니다.  
  
```  
WITH MEMBER Measures.x AS SUM   
   (  
      MTD([Date].[Calendar].[Date].[July 20, 2002])  
     , [Measures].[Internet Freight Cost]  
     )  
SELECT Measures.x ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>관련 항목  
 [Sum &#40;MDX&#41;](../mdx/sum-mdx.md)   
 [MDX 함수 참조&#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
