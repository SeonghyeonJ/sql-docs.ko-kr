---
title: 계산 멤버를 MDX로 작성 (MDX) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- MDX [Analysis Services], calculated members
- calculated members [MDX]
- Multidimensional Expressions [Analysis Services], calculated members
- queries [MDX], calculated members
ms.assetid: 9322e8b8-43e1-4e02-a7d1-e41a586a5bb8
author: minewiskan
ms.author: owend
ms.openlocfilehash: 30dc6562ec394065cf2f177608d4e5679cbd7df3
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84546490"
---
# <a name="building-calculated-members-in-mdx-mdx"></a>계산 멤버를 MDX로 작성(MDX)
  MDX에서 계산 멤버는 값을 반환하기 위해 MDX 식을 계산하여 확인되는 멤버입니다. 이러한 정의에는 놀랄 만한 개념이 포함되어 있습니다. MDX 쿼리에서 계산 멤버를 구성하고 사용할 수 있으면 다차원 데이터에 대한 상당한 조작 기능을 활용할 수 있습니다.  
  
 계산 멤버는 계층 구조 안의 어느 지점에나 만들 수 있습니다. 또한, 큐브의 기존 멤버는 물론, 동일한 MDX 식에서 정의된 다른 계산 멤버에도 종속되는 계산 멤버를 만들 수도 있습니다.  
  
 다음 컨텍스트 중 하나가 포함되도록 계산 멤버를 정의할 수 있습니다.  
  
-   **쿼리 범위** MDX 쿼리의 일부로 정의되는 계산 멤버를 만들어서 해당 범위가 쿼리로 제한되도록 하려면 WITH 키워드를 사용합니다. 그런 다음 MDX SELECT 문 내에서 계산 멤버를 사용할 수 있습니다. 이 방식을 사용할 경우 WITH 키워드를 사용하여 만든 계산 멤버는 SELECT 문을 배포하지 않아도 변경할 수 있습니다.  
  
     WITH 키워드를 사용하여 계산 멤버를 만드는 방법은 [쿼리 범위 계산 멤버 만들기&#40;MDX&#41;](mdx-calculated-members-query-scoped-calculated-members.md)를 참조하세요.  
  
-   **세션 범위** 범위가 쿼리 컨텍스트보다 넓은, 즉 범위가 MDX 세션의 수명인 계산 멤버를 만들려면 CREATE MEMBER 문을 사용합니다. CREATE MEMBER 문을 사용하여 정의된 계산 멤버는 해당 세션의 모든 MDX 쿼리에서 사용할 수 있습니다. 예를 들어 CREATE MEMBER 문은 여러 쿼리에서 하나의 동일 집합을 계속적으로 다시 사용하는 클라이언트 애플리케이션에 적합합니다.  
  
     CREATE MEMBER 문을 사용하여 세션에서 계산 멤버를 만드는 방법은 [세션 범위 계산 멤버 만들기&#40;MDX&#41;](mdx-calculated-members-session-scoped-calculated-members.md)를 참조하세요.  
  
## <a name="see-also"></a>참고 항목  
 [CREATE MEMBER 문 &#40;MDX&#41;](/sql/mdx/mdx-data-definition-create-member)   
 [Mdx 함수 참조 &#40;MDX&#41;](/sql/mdx/mdx-function-reference-mdx)   
 [SELECT 문&#40;MDX&#41;](/sql/mdx/mdx-data-manipulation-select)  
  
  
