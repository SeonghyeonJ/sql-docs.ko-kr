---
title: Members (집합) (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 3bd4fe92c064f4665a4b397e47a45ae5bde50f39
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63048453"
---
# <a name="members-set-mdx"></a>Members(집합)(MDX)


  차원, 수준 또는 계층의 멤버 집합을 반환합니다.  
  
## <a name="syntax"></a>구문  
  
```  
  
Hierarchy expression syntax  
Hierarchy_Expression.Members  
  
Level expression Syntax  
Level_Expression.Members  
```  
  
## <a name="arguments"></a>인수  
 *Hierarchy_Expression*  
 계층을 반환하는 유효한 MDX 식입니다.  
  
 *Level_Expression*  
 수준을 반환하는 유효한 MDX 식입니다.  
  
## <a name="remarks"></a>Remarks  
 계층 식이 지정 하는 경우는 **Members (집합)** 함수 계산된 멤버를 포함 하지 않습니다 지정된 된 계층 내의 모든 멤버 집합을 반환 합니다. 계산 하는 모든 멤버 집합을 구하거 나 그렇지 않은 경우 계층 구조를 사용 하 여 [AllMembers &#40;MDX&#41; ](../mdx/allmembers-mdx.md) 함수  
  
 수준 식이 지정 되는 **Members (집합)** 함수는 지정 된 수준 내의 모든 멤버 집합을 반환 합니다.  
  
> [!IMPORTANT]  
>  차원에 표시 가능한 계층이 하나만 있는 경우 해당 차원 이름은 표시 가능한 유일한 계층으로 확인되므로 해당 계층을 차원 이름이나 계층 이름 중 하나로 참조할 수 있습니다. 예를 들어 Measures.Members는 Measures 차원의 유일한 계층으로 확인되므로 유효한 MDX 식입니다.  
  
## <a name="examples"></a>예  
 다음 예에서는 Adventure Works 큐브에 있는 Calendar Year 계층의 모든 멤버 집합을 반환합니다.  
  
```  
SELECT   
   [Date].[Calendar].[Calendar Year].Members ON 0  
FROM  
   [Adventure Works]  
  
```  
  
 다음 예에서는 `[Product].[Products].[Product Line]` 수준의 각 멤버에 대해 2003년 주문 수량을 반환합니다. 합니다 **멤버** 함수 모든 수준에서 멤버를 나타내는 집합을 반환 합니다.  
  
```  
SELECT   
   {Measures.[Order Quantity]} ON COLUMNS,  
   [Product].[Product Line].[Product Line].Members ON ROWS  
FROM  
   [Adventure Works]  
WHERE  
   {[Date].[Calendar Year].[Calendar Year].&[2003]}  
```  
  
## <a name="see-also"></a>관련 항목  
 [MDX 함수 참조 & #40; Mdx& #41;](../mdx/mdx-function-reference-mdx.md)   
 [MDX 함수 참조&#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
