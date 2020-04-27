---
title: 멤버 속성 사용 (MDX) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- DIMENSION PROPERTIES keyword
- Properties function
- member properties [MDX]
- members [MDX], properties
ms.assetid: 26b5ad08-3799-4a5e-89f3-dca25e637d45
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 8c0326d45af68db966f120fa12e35eb59f30becc
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/26/2020
ms.locfileid: "66074158"
---
# <a name="using-member-properties-mdx"></a>멤버 속성 사용(MDX)
  멤버 속성은 각 튜플에 있는 각 멤버에 대한 기본 정보를 설명합니다. 이 기본 정보에는 멤버 이름, 부모 수준 및 자식의 수 등이 포함됩니다. 해당 수준의 모든 멤버에 대해 멤버 속성을 사용할 수 있습니다. 조직의 측면에서 볼 때 멤버 속성은 단일 차원에 저장되어 있고 차원에 따라 조직된 데이터로 취급됩니다.  
  
> [!NOTE]  
>  [!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]에서는 멤버 속성을 특성 관계라고 합니다. 자세한 내용은 [특성 관계](../../multidimensional-models-olap-logical-dimension-objects/attribute-relationships.md)를 참조하세요.  
  
 멤버 속성은 *기본* 또는 *사용자 지정*중 하나입니다.  
  
 기본 멤버 속성  
 모든 멤버는 멤버의 서식 값과 같은 기본 멤버 속성을 지원하고 차원과 수준은 멤버 ID와 같은 기본 차원 및 수준 멤버 속성을 추가로 제공합니다.  
  
 자세한 내용은 [기본 멤버 속성&#40;MDX&#41;](mdx-member-properties-intrinsic-member-properties.md)을 참조하세요.  
  
 사용자 정의 멤버 속성  
 멤버가 자신과 관련된 추가 속성을 가진 경우가 있습니다. 예를 들어 제품 수준은 각 제품에 대한 SKU, SRP, 무게 및 부피 속성을 제공할 수 있을 것입니다. 이런 속성이 멤버는 아니지만 제품 수준의 멤버에 대한 추가 정보를 포함합니다.  
  
 자세한 내용은 [사용자 정의 멤버 속성&#40;MDX&#41;](mdx-member-properties-user-defined-member-properties.md)을 참조하세요.  
  
 `PROPERTIES` 키워드 또는 [properties](/sql/mdx/properties-mdx) 함수를 사용 하 여 기본 및 사용자 정의 멤버 속성을 모두 검색할 수 있습니다.  
  
## <a name="using-the-properties-keyword"></a>PROPERTIES 키워드 사용  
 `PROPERTIES` 키워드는 지정된 축 차원에 사용할 멤버 속성을 지정합니다. 키워드 `PROPERTIES` 는 MDX `<axis specification>` [SELECT](/sql/mdx/mdx-data-manipulation-select) 문의 절에 포함 되어 있습니다.  
  
```  
SELECT [<axis_specification>  
       [, <axis_specification>...]]  
  FROM [<cube_specification>]  
[WHERE [<slicer_specification>]]  
```  
  
 `<axis_specification>` 절은 다음 구문에 나타낸 것과 같이 `<dim_props>` 절(옵션)을 포함합니다.  
  
```  
<axis_specification> ::= <set> [<dim_props>] ON <axis_name>  
```  
  
> [!NOTE]  
>  `<set>` 및 `<axis_name>` 값에 대한 자세한 내용은 [쿼리 축의 내용 지정&#40;MDX&#41;](mdx-query-and-slicer-axes-specify-the-contents-of-a-query-axis.md)을 참조하세요.  
  
 `<dim_props>` 절에서는 `PROPERTIES` 키워드를 사용하여 차원, 수준 및 멤버 속성을 쿼리할 수 있습니다. 다음 구문은 `<dim_props>` 절의 서식을 표시합니다.  
  
```  
<dim_props> ::= [DIMENSION] PROPERTIES <property> [,<property>...]  
```  
  
 `<property>` 구문의 분석은 쿼리하는 속성에 따라 다릅니다.  
  
-   차원 또는 수준 이름에 앞서 상황에 맞는 기본 멤버 속성이 선행되어야 합니다. 하지만 상황에 맞지 않는 기본 멤버 속성을 차원 또는 수준 이름으로 정규화할 수 없습니다. 키워드를 `PROPERTIES` 기본 멤버 속성과 함께 사용 하는 방법에 대 한 자세한 내용은 [기본 멤버 속성 &#40;MDX&#41;](mdx-member-properties-intrinsic-member-properties.md)를 참조 하세요.  
  
-   사용자 정의 멤버 속성은 자신이 상주하는 수준 이름보다 선행되어야 합니다. 키워드를 `PROPERTIES` 사용자 정의 멤버 속성과 함께 사용 하는 방법에 대 한 자세한 내용은 [사용자 정의 멤버 속성 &#40;MDX&#41;](mdx-member-properties-user-defined-member-properties.md)를 참조 하세요.  
  
## <a name="see-also"></a>참고 항목  
 [속성 값 만들기 및 사용&#40;MDX&#41;](../../creating-and-using-property-values-mdx.md)  
  
  
