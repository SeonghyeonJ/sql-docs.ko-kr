---
title: AND (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 30cb8be449c58e10da5c2e91ebec936b3547581d
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63249877"
---
# <a name="and-mdx"></a>AND(MDX)


  두 숫자 식에 논리 결합을 수행합니다.  
  
## <a name="syntax"></a>구문  
  
```  
  
Expression1 AND Expression2  
```  
  
#### <a name="parameters"></a>매개 변수  
 *Expression1*  
 숫자 값을 반환하는 유효한 MDX 식입니다.  
  
 *Expression2*  
 숫자 값을 반환하는 유효한 MDX 식입니다.  
  
## <a name="return-value"></a>반환 값  
 두 매개 변수를 평가 하는 경우 true를 반환 하는 부울 값 **true**이 고, 그렇지 않으면 **false**합니다.  
  
## <a name="remarks"></a>Remarks  
 합니다 **AND** 연산자는 두 식이 모두 부울 값으로 처리 (0으로 **false**이 고, 그렇지 않으면 **true**) 연산자는 논리곱 연산을 수행 하기 전에 합니다. 다음 표에서 설명 하는 방법을 **AND** 연산자로 논리 결합을 수행 합니다.  
  
|*Expression1*|*Expression2*|반환 값|  
|-------------------|-------------------|------------------|  
|**true**|**true**|**true**|  
|**true**|**false**|**false**|  
|**false**|**true**|**false**|  
|**false**|**false**|**false**|  
  
## <a name="example"></a>예제  
  
```  
-- This query returns the gross profit margin (GPM)  
-- for clothing sales where the GPM is between 20% and 30%.  
With Member [Measures].[LowGPM] as  
  IIF(  
      [Measures].[Gross Profit Margin] <= .3 AND   
      [Measures].[Gross Profit Margin] >= .2,  
      [Measures].[Gross Profit Margin],  
      null)  
SELECT NON EMPTY  
    [Sales Territory].[Sales Territory Country].Members ON 0,  
    [Product].[Category].[Clothing] ON 1  
FROM  
    [Adventure Works]  
WHERE  
    ([Measures].[LowGPM])  
```  
  
## <a name="see-also"></a>관련 항목  
 [MDX 연산자 참조 &#40;MDX&#41;](../mdx/mdx-operator-reference-mdx.md)  
  
  
