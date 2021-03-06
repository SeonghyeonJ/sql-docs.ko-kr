---
description: StripCalculatedMembers(MDX)
title: StripCalculatedMembers (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 7567ad9b8a69f1d83b9c16dd7bf4046b813292c0
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88386839"
---
# <a name="stripcalculatedmembers-mdx"></a>StripCalculatedMembers(MDX)


  지정한 집합에서 계산 멤버를 제거하여 생성된 집합을 반환합니다.  
  
## <a name="syntax"></a>구문  
  
```  
  
StripCalculatedMembers(Set_Expression)   
```  
  
## <a name="arguments"></a>인수  
 *Set_Expression*  
 집합을 반환하는 유효한 MDX 식입니다.  
  
## <a name="remarks"></a>설명  
 **StripCalculatedMembers** 함수는 집합에서 계산 멤버를 제거 합니다. [AddCalculatedMembers](../mdx/addcalculatedmembers-mdx.md) 함수를 사용 하 여 집합에 계산 멤버를 추가할 수 있습니다 .이 함수는 서버에 정의 된 계산 멤버 또는 WITH MEMBER 구문을 사용 하 여 쿼리 자체 내에 추가 된 계산 멤버를 반환 합니다.  
  
## <a name="example"></a>예제  
 다음 예에서는 쿼리에서 모든 계산 멤버를 제거합니다.  
  
```  
WITH MEMBER Measures.MemberName AS   
   [Date].[Calendar].[July 1, 2003].Properties('Name')  
MEMBER Measures.MemberVal AS   
   [Date].[Calendar].[July 1, 2003].Properties('Member_Value')  
MEMBER Measures.MemberKey AS   
   [Date].[Calendar].[July 1, 2003].Properties('Key')  
MEMBER Measures.MemberID AS   
   [Date].[Calendar].[July 1, 2003].Properties('ID')  
MEMBER Measures.MemberCaption AS   
   [Date].[Calendar].[July 1, 2003].Properties('Caption')  
MEMBER Measures.DayName AS   
   [Date].[Calendar].[July 1, 2003].Properties('Day Name', TYPED)  
MEMBER Measures.DayNameTyped AS   
   [Date].[Calendar].[July 1, 2003].Properties('Day Name')  
MEMBER Measures.DayofWeek AS   
   [Date].[Calendar].[July 1, 2003].Properties('Day of Week')  
MEMBER Measures.DayofMonth AS   
   [Date].[Calendar].[July 1, 2003].Properties('Day of Month')  
MEMBER Measures.DayofYear AS   
   [Date].[Calendar].[July 1, 2003].Properties('Day of Year')  
  
SELECT StripCalculatedMembers(  
   { Measures.DefaultMember  
   , Measures.MemberName  
   , Measures.MemberVal  
   , Measures.MemberKey  
   , Measures.MemberID  
   , Measures.MemberCaption  
   , Measures.DayName  
   , Measures.DayNameTyped  
   , Measures.DayofWeek  
   , Measures.DayofMonth  
   , Measures.DayofYear  
   }  
   )  ON 0  
FROM [Adventure Works]  
  
```  
  
## <a name="see-also"></a>참고 항목  
 [MDX 함수 참조&#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
