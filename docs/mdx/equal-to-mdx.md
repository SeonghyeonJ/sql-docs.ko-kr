---
title: = (같음) (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 1fac06690d811c3ae3d4b00a82ad9088b2df4aae
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62690920"
---
# <a name="-equal-to-mdx"></a>=(같음)(MDX)


  하나의 MDX 식의 값이 다른 MDX 식의 값과 같은지 확인하는 비교 연산을 수행합니다.  
  
> [!NOTE]  
>  개체 비교를 사용 합니다 [IS &#40;MDX&#41; ](../mdx/is-mdx.md) 연산자입니다. 예를 들어 쿼리 축에 있는 현재 멤버가 특정 멤버인지 확인할 때 IS 연산자를 사용합니다.  
  
## <a name="syntax"></a>구문  
  
```  
  
MDX_Expression = MDX_Expression   
```  
  
#### <a name="parameters"></a>매개 변수  
 *MDX_Expression*  
 유효한 MDX 식입니다.  
  
## <a name="return-value"></a>반환 값  
 다음 조건을 기반으로 하는 부울 값입니다.  
  
-   **true** 경우 첫 번째 매개 변수의 값은 두 번째 매개 변수의 값과 같습니다.  
  
-   **false** 첫 번째 매개 변수의 두 번째 매개 변수의 값과 같지 않으면.  
  
-   **true** 경우 매개 변수가 모두 null이 또는 하나의 매개 변수가 null 및 다른 매개 변수는 0입니다.  
  
## <a name="examples"></a>예  
 다음 쿼리에서는 이러한 조건의 예를 보여 줍니다.  
  
 `With`  
  
 `--Returns true`  
  
 `Member [Measures].bool1 as 1=1`  
  
 `--Returns false`  
  
 `Member [Measures].bool2 as 1=0`  
  
 `--Returns true`  
  
 `Member [Measures].bool3 as null=null`  
  
 `--Returns true`  
  
 `Member [Measures].bool4 as 0=null`  
  
 `--Returns false`  
  
 `Member [Measures].bool5 as 1=null`  
  
 `Select {[Measures].bool1,[Measures].bool2,[Measures].bool3,[Measures].bool4,[Measures].bool5}`  
  
 `On 0`  
  
 `From [Adventure Works]`  
  
## <a name="see-also"></a>관련 항목  
 [MDX 연산자 참조 &#40;MDX&#41;](../mdx/mdx-operator-reference-mdx.md)  
  
  
