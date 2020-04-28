---
title: IsGeneration (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 401a11a10f190cda8efeaffa04e1025ef7f4e681
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/27/2020
ms.locfileid: "68105232"
---
# <a name="isgeneration-mdx"></a>IsGeneration(MDX)


  지정한 멤버가 지정한 세대에 속하는지 여부를 반환합니다.  
  
## <a name="syntax"></a>구문  
  
```  
  
IsGeneration(Member_Expression, Generation_Number)   
```  
  
## <a name="arguments"></a>인수  
 *Member_Expression*  
 멤버를 반환하는 유효한 MDX 식입니다.  
  
 *Generation_Number*  
 지정된 멤버가 평가되는 기준 세대를 지정하는 유효한 숫자 식입니다.  
  
## <a name="remarks"></a>설명  
 **Isgeneration** 함수는 지정 된 멤버가 지정 된 세대 번호에 있으면 **true** 를 반환 합니다. 그렇지 않으면 함수는 **false**를 반환 합니다. 또한 지정 된 멤버가 빈 멤버로 평가 되는 경우 **Isgeneration** 함수는 **false**를 반환 합니다.  
  
 세대 인덱싱을 위해 리프 멤버는 세대 인덱스 0입니다. 리프가 아닌 멤버의 세대 인덱스는 지정된 멤버에 대한 모든 자식 멤버의 합집합에서 가장 높은 세대 인덱스를 가져와서 1을 더하는 방식으로 결정됩니다. 리프가 아닌 멤버의 세대 인덱스의 결정 방법으로 인해 리프가 아닌 특정 멤버는 둘 이상의 세대에 속할 수 있습니다.  
  
## <a name="example"></a>예제  
 다음 예에서는 [Date].[Fiscal].CurrentMember가 두 번째 세대에 속하는 경우 TRUE를 반환합니다.  
  
 `WITH MEMBER MEASURES.ISGENERATIONDEMO AS`  
  
 `IsGeneration([Date].[Fiscal].CURRENTMEMBER, 2)`  
  
 `SELECT {MEASURES.ISGENERATIONDEMO} ON 0,`  
  
 `[Date].[Fiscal].MEMBERS ON 1`  
  
 `FROM [Adventure Works]`  
  
## <a name="see-also"></a>참고 항목  
 [MDX 함수 참조&#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
