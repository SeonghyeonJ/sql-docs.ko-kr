---
title: MDX 쿼리에 큐브 컨텍스트 설정 | Microsoft Docs
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 2efdfc74bf45f4e8e6b913e651b0be5fa4511034
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62807608"
---
# <a name="establishing-cube-context-in-a-query-mdx"></a>쿼리에 큐브 컨텍스트 설정(MDX)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  모든 MDX 쿼리는 지정된 큐브 컨텍스트 내에서 실행됩니다. 이 컨텍스트는 쿼리 내의 식에 의해 계산되는 멤버를 정의합니다.  
  
 SELECT 문에서 FROM 절은 큐브 컨텍스트를 결정합니다. 이 컨텍스트는 전체 큐브이거나 해당 큐브의 하위 큐브일 수 있습니다. FROM 절을 통해 큐브 컨텍스트를 지정한 경우 추가 함수를 사용하여 해당 큐브를 확장하거나 제한할 수 있습니다.  
  
> [!NOTE]  
>  SCOPE 및 CALCULATE 문을 사용하면 MDX 스크립트 내에서 큐브 컨텍스트를 관리할 수 있습니다. 자세한 내용은 [MDX 스크립팅 기본 사항&#40;Analysis Services&#41;](../../../analysis-services/multidimensional-models/mdx/mdx-scripting-fundamentals-analysis-services.md)을 참조하세요.  
  
## <a name="from-clause-syntax"></a>FROM 절 구문  
 다음 구문은 FROM 절에 대한 설명입니다.  
  
```  
<SELECT subcube clause> ::=  
   Cube_Identifier |   
   (SELECT [  
      * |   
      ( <SELECT query axis clause> [ , <SELECT query axis clause> ... ] ) ]   
   FROM <SELECT subcube clause> <SELECT slicer axis clause> )  
```  
  
 이 구문에서 `<SELECT subcube clause>` 절은 SELECT 문이 실행되는 큐브 또는 하위 큐브를 설명합니다.  
  
 FROM 절의 간단한 예로는 전체 Adventure Works 예제 큐브에 대해 실행되는 절을 들 수 있습니다. 이러한 FROM 절의 형식은 다음과 같습니다.  
  
```  
FROM [Adventure Works]  
```  
  
 MDX SELECT 문의 FROM 절에 대한 자세한 내용은 [SELECT 문&#40;MDX&#41;](../../../mdx/mdx-data-manipulation-select.md)을 참조하세요.  
  
## <a name="refining-the-context"></a>컨텍스트 구체화  
 FROM 절은 단일 큐브 내의 큐브 컨텍스트를 지정하지만 한 번에 하나 이상의 데이터를 사용하는 경우도 있습니다.  
  
 MDX [LookupCube](../../../mdx/lookupcube-mdx.md) 함수를 사용하면 큐브 컨텍스트 외부의 다른 큐브에서 데이터를 검색할 수 있습니다. 또한 [Filter](../../../mdx/filter-mdx.md) 함수 등을 사용하여 쿼리를 계산할 때 컨텍스트를 임시적으로 제한할 수도 있습니다.  
  
## <a name="see-also"></a>관련 항목  
 [MDX 쿼리 기본 사항&#40;Analysis Services&#41;](../../../analysis-services/multidimensional-models/mdx/mdx-query-fundamentals-analysis-services.md)  
  
  
