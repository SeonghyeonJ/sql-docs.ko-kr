---
title: 부모-자식 유형 차원의 재무 계정 만들기 | Microsoft Docs
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: multidimensional-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: a9db268d931d46f6254501e95d68739c3e71db3b
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/28/2018
ms.locfileid: "52517227"
---
# <a name="database-dimensions---finance-account-of-parent-child-type"></a>데이터베이스 차원-부모-자식 유형 재무 계정
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
   [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]에서 계정 유형 차원은 재무 보고용 계정 차트를 나타내는 특성이 있는 차원입니다.  
  
 계정 차원을 사용하여 여러 계정에 대한 시간별 집계 동작을 선택적으로 관리할 수 있습니다. 또한 계정 차원을 통해 표준 메커니즘을 사용하여 재무 데이터를 처리하는 비즈니스 인텔리전스 솔루션에서 일반적으로 발생하는 비표준 집계 문제를 대부분 해결할 수 있습니다. 표준 메커니즘이 없는 경우 이러한 비표준 집계 문제를 해결하려면 사용자 지정 롤업 수식, 계산 멤버 또는 MDX(Multidimensional Expressions) 스크립트가 필요합니다.  
  
 차원을 계정 차원으로 식별하려면 차원의 **Type** 속성을 **Accounts**로 설정합니다.  
  
## <a name="dimension-structure"></a>차원 구조  
 계정 차원에는 다음과 같은 두 개의 필수 특성이 있습니다.  
  
-   키 특성을 하는 특성을 계정 차원에 대 한 차원 테이블의 개별 계정을 식별 합니다.  
  
-   계정 차원에서 계정이 계층적으로 정렬 되는 방법을 설명 하는 계정 특성을 부모 특성입니다.  
  
     특성을 계정 특성으로 식별하려면 특성의 **Type** 속성을 **Account** 로 설정하고 **Usage** 속성을 **Parent**로 설정합니다.  
  
 계정 차원에는 다음과 같은 선택적 특성이 있을 수 있습니다.  
  
-   계정 차원의 각 계정에 대 한 계정 유형을 정의 하는 특성을 특성을 입력 합니다. 계정 유형 특성의 멤버 이름은 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 데이터베이스나 프로젝트에 정의된 계정 유형에 매핑되고 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 에서 이러한 계정에 사용되는 집계 함수를 나타냅니다. 단항 연산자나 사용자 지정 롤업 수식을 사용하여 계정 특성에 대한 집계 동작을 결정할 수도 있으나 계정 유형을 사용하면 기본 관계형 데이터베이스를 변경하지 않고도 계정 차트에 일관된 동작을 쉽게 적용할 수 있습니다.  
  
     계정 유형 특성을 식별하려면 특성의 **Type** 속성을 **AccountType**으로 설정합니다.  
  
-   계정 이름 특성을 특성 보고용으로 사용 되는 합니다. 특성의 **Type** 속성을 **AccountName**으로 설정하여 계정 이름 특성을 식별합니다.  
  
-   계정 번호 보고용으로 사용 되는 특성을 특성입니다. 특성의 **Type** 속성을 **AccountNumber**로 설정하여 계정 번호 특성을 식별합니다.  
  
 특성 유형에 대한 자세한 내용은 [특성 유형 구성](../../analysis-services/multidimensional-models/attribute-properties-configure-attribute-types.md)을 참조하세요.  
  
## <a name="adding-account-intelligence-with-the-business-intelligence-wizard"></a>비즈니스 인텔리전스 마법사로 계정 인텔리전스 추가  
 계정 차원을 정의하고 큐브에 추가한 후에는 비즈니스 인텔리전스 마법사를 사용하여 계정 유형을 식별하고 매핑하는 등의 계정 인텔리전스 기능을 차원에 추가할 수 있습니다. 자세한 내용은 [차원에 계정 인텔리전스 추가](../../analysis-services/multidimensional-models/bi-wizard-add-account-intelligence-to-a-dimension.md)를 참조하세요.  
  
## <a name="see-also"></a>관련 항목  
 [특성 및 특성 계층](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/attributes-and-attribute-hierarchies.md)   
 [비즈니스 인텔리전스 마법사 F1 도움말](http://msdn.microsoft.com/library/155ac80c-63ae-47aa-9e86-9396e3d920eb)   
 [차원 유형](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/database-dimension-properties-types.md)  
  
  
