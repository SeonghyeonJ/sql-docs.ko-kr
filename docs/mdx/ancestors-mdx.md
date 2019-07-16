---
title: Ancestors (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 8551e6fdac54b3eb4c20f13f6722936df1c92feb
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68017106"
---
# <a name="ancestors-mdx"></a>Ancestors(MDX)


  지정된 수준이나 지정된 멤버로부터 지정된 거리만큼 떨어진 수준에서 지정된 멤버의 모든 상위 항목 집합을 반환하는 함수입니다. 사용 하 여 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]에서 반환 된 집합은 항상 단일 멤버로 개로 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 단일 멤버에 대 한 여러 부모를 지원 하지 않습니다.  
  
## <a name="syntax"></a>구문  
  
```  
  
Level syntax  
Ancestors(Member_Expression, Level_Expression)  
  
Numeric syntax  
Ancestors(Member_Expression, Distance)  
```  
  
## <a name="arguments"></a>인수  
 *Member_Expression*  
 멤버를 반환하는 유효한 MDX 식입니다.  
  
 *Level_Expression*  
 수준을 반환하는 유효한 MDX 식입니다.  
  
 *거리*  
 지정된 멤버와의 거리를 지정하는 유효한 숫자 식입니다.  
  
## <a name="remarks"></a>설명  
 사용 하 여 합니다 **상위** 함수를 MDX 멤버 식을 사용 하 여 함수를 제공 및 해당 멤버의 상위 항목인 수준의 MDX 식 이거나 수준의 수를 나타내는 숫자 식 중 하나를 제공 합니다 해당 멤버 위의 합니다. 이 정보를 사용 합니다 **상위** 함수 수준에서 멤버 (될 멤버로 구성 된 집합)의 집합을 반환 합니다.  
  
> [!NOTE]  
>  상위 집합을 것이 아니라 상위 멤버를 사용 하 여 반환 하는 [상위](../mdx/ancestor-mdx.md) 함수입니다.  
  
 수준 식이 지정 되는 **상위** 함수는 지정 된 수준에서 지정된 된 멤버의 모든 상위 항목 집합을 반환 합니다. 지정된 멤버가 지정된 수준과 동일한 계층 내에 없으면 이 함수는 오류를 반환합니다.  
  
 거리를 지정 합니다 **상위** 함수는 멤버 식으로 지정 된 계층에서 지정 된 단계의 수 있는 모든 멤버 집합을 반환 합니다. 멤버는 특성 계층, 사용자 정의 계층 또는 경우에 따라 부모-자식 계층의 멤버로 지정될 수 있습니다. 숫자 1은 부모 수준의 멤버 집합을 반환하고 숫자 2는 최상위 수준의 멤버 집합(있는 경우)을 반환합니다. 숫자 0은 멤버만 포함된 집합을 반환합니다.  
  
> [!NOTE]  
>  이 형식을 사용 하 여 합니다 **상위** 함수 경우은 부모의 수준을 알 수 없는 또는 명명할 수 없습니다.  
  
## <a name="examples"></a>예  
 다음 예제에서는 합니다 **상위** 멤버, 부모 및 최상위 항목에 대 한 Internet Sales Amount 측정값을 반환 하는 함수입니다. 이 예에서는 수준 식을 사용하여 반환할 수준을 지정합니다. 수준은 멤버 식에 지정된 멤버와 동일한 계층에 있습니다.  
  
```  
SELECT {  
    Ancestors([Product].[Product Categories].[Product].[Mountain-100 Silver, 38],[Product].[Product Categories].[Category]),  
    Ancestors([Product].[Product Categories].[Product].[Mountain-100 Silver, 38],[Product].[Product Categories].[Subcategory]),  
    Ancestors([Product].[Product Categories].[Product].[Mountain-100 Silver, 38],[Product].[Product Categories].[Product])  
    } ON 0,  
[Measures].[Internet Sales Amount] ON 1  
FROM [Adventure Works]  
```  
  
 다음 예제에서는 합니다 **상위** 멤버, 부모 및 최상위 항목에 대 한 Internet Sales Amount 측정값을 반환 하는 함수입니다. 이 예에서는 숫자 식을 사용하여 반환할 수준을 지정합니다. 수준은 멤버 식에 지정된 멤버와 동일한 계층에 있습니다.  
  
```  
SELECT {  
   Ancestors(  
      [Product].[Product Categories].[Product].[Mountain-100 Silver, 38],2  
      ),  
   Ancestors(  
      [Product].[Product Categories].[Product].[Mountain-100 Silver, 38],1  
      ),  
   Ancestors(  
      [Product].[Product Categories].[Product].[Mountain-100 Silver, 38],0  
      )  
   } ON 0,  
[Measures].[Internet Sales Amount] ON 1  
FROM  [Adventure Works]  
```  
  
 다음 예제에서는 합니다 **상위** 특성 계층의 멤버의 부모에 대 한 Internet Sales Amount 측정값을 반환 하는 함수입니다. 이 예에서는 숫자 식을 사용하여 반환할 수준을 지정합니다. 멤버 식의 멤버는 특성 계층의 멤버이므로 해당 부모는 [All] 수준입니다.  
  
```  
SELECT {  
   Ancestors(  
      [Product].[Product].[Mountain-100 Silver, 38],1  
      )  
   } ON 0,  
[Measures].[Internet Sales Amount] ON 1  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>관련 항목  
 [MDX 함수 참조&#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
