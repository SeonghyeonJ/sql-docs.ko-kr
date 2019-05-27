---
title: (MDX) Slicer 축의 내용 지정 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- slicer axis
- filtering data [MDX]
ms.assetid: c56b0a70-cdec-427f-990e-425290344e7d
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 12e2d2f543694a1da418f5e8eb4b900eaa123d97
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66074056"
---
# <a name="specifying-the-contents-of-a-slicer-axis-mdx"></a>Slicer 축의 내용 지정(MDX)
  slicer 축은 지정된 멤버와 교차되는 데이터만 반환되도록 반환 데이터를 제한하여 MDX SELECT 문에 의해 반환된 데이터를 필터링합니다. slicer 축은 표시되지 않는 쿼리의 추가 축으로 간주할 수 있으며 MDX에서 SELECT 문의 WHERE 절에 정의됩니다.  
  
## <a name="slicer-axis-syntax"></a>Slicer 축 구문  
 slicer 축을 명시적으로 지정하려면 다음 구문에 설명된 것과 같이 MDX에서 `<SELECT slicer axis clause>` 를 사용합니다.  
  
```  
<SELECT slicer axis clause> ::=  WHERE Set_Expression  
```  
  
 표시된 slicer 축 구문에서 `Set_Expression` 은 절을 계산할 목적의 집합으로 취급되는 튜플 식 또는 집합 식을 사용할 수 있습니다. 집합 식이 지정된 경우 MDX는 집합과 함께 모든 튜플에 있는 결과 셀을 집계하여 집합을 계산하려고 시도합니다. 즉, MDX는 집합에 대해 [Aggregate](/sql/mdx/aggregate-mdx) 함수 사용을 시도하여 각 측정값을 관련 집계 함수로 집계합니다. 또한 집합 식을 특성 계층 멤버의 크로스 조인으로 표현할 수 없는 경우 MDX는 slicer에 대한 집합 식 범위에 속하지 않는 셀을 계산 목적의 Null로 취급합니다.  
  
> [!IMPORTANT]  
>  SQL의 WHERE 절과 달리, MDX SELECT 문의 WHERE 절은 쿼리의 Rows 축에서 반환되는 항목을 직접 필터링하지 않습니다. 쿼리의 Rows 또는 Columns 축에 나타나는 항목을 필터링하는 데 FILTER, NONEMPTY, TOPCOUNT 등의 다양한 MDX 함수를 사용할 수 있습니다.  
  
### <a name="implicit-slicer-axis"></a>암시적 Slicer 축  
 큐브 내에 있는 계층의 멤버가 쿼리 축에 명시적으로 포함되지 않은 경우 해당 계층의 기본 멤버는 slicer 축에 암시적으로 포함됩니다. 기본 멤버에 대한 자세한 내용은 [기본 멤버 정의](../attribute-properties-define-a-default-member.md)를 참조하세요.  
  
## <a name="examples"></a>예  
 다음 쿼리는 WHERE 절을 포함하지 않으며 모든 Calendar Year의 Internet Sales Amount 측정값을 반환합니다.  
  
```  
SELECT {[Measures].[Internet Sales Amount]} ON COLUMNS,  
[Date].[Calendar Year].MEMBERS ON ROWS  
FROM [Adventure Works]  
```  
  
 다음과 같이 WHERE 절을 추가하는 경우  
  
```  
SELECT {[Measures].[Internet Sales Amount]} ON COLUMNS,  
[Date].[Calendar Year].MEMBERS ON ROWS  
FROM [Adventure Works]  
WHERE([Customer].[Customer Geography].[Country].&[United States])  
  
```  
  
 쿼리의 Rows 또는 Columns에서 반환되는 항목은 변경되지 않으며 각 셀에 대해 반환되는 값이 변경됩니다. 이 예제에서 쿼리는 United States에 거주하는 Customer에만 해당하는 모든 Calendar Year의 Internet Sales Amount 값을 반환하도록 조각화됩니다. 서로 다른 계층의 여러 멤버를 WHERE 절에 추가할 수 있습니다. 다음 쿼리는 United States에 거주하며 Category Bikes에서 Product를 구입한 Customer에 해당하는 모든 Calendar Year의 Internet Sales Amount 값을 표시합니다.  
  
```  
SELECT {[Measures].[Internet Sales Amount]} ON COLUMNS,  
[Date].[Calendar Year].MEMBERS ON ROWS  
FROM [Adventure Works]  
WHERE([Customer].[Customer Geography].[Country].&[United States], [Product].[Category].&[1])  
```  
  
 동일한 계층에서 여러 멤버를 사용하려면 WHERE 절에 집합을 포함해야 합니다. 예를 들어 다음 쿼리는 United States 또는 United Kingdom에 거주하며 Category Bikes에서 Product를 구입한 Customer에 해당하는 모든 Calendar Year의 Internet Sales Amount 값을 표시합니다.  
  
```  
SELECT {[Measures].[Internet Sales Amount]} ON COLUMNS,  
[Date].[Calendar Year].MEMBERS ON ROWS  
FROM [Adventure Works]  
WHERE(  
{[Customer].[Customer Geography].[Country].&[United States]  
, [Customer].[Customer Geography].[Country].&[United Kingdom]}  
, [Product].[Category].&[1])  
  
```  
  
 위에서 설명했듯이 WHERE 절에서 집합을 사용하면 해당 집합의 모든 멤버에 대한 값이 암시적으로 집계됩니다. 이 경우 쿼리는 각 셀의 United States 및 United Kingdom에 대한 집계된 값을 표시합니다.  
  
  
