---
title: 다차원 모델의 차원 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- OLAP [Analysis Services], dimensions
- dimensions [Analysis Services], about dimensions
- OLAP objects [Analysis Services], dimensions
ms.assetid: 2b62b05c-00fd-4e60-b77f-f707ba83a19b
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 520d6f11e5a472d5337a3747cc73c1d3656171c2
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66075176"
---
# <a name="dimensions-in-multidimensional-models"></a>다차원 모델의 차원
  데이터베이스 차원은 하나 이상의 큐브 내 팩트 데이터에 대한 정보를 제공하는 데 사용할 수 있는 특성이라는 관련 개체의 모음입니다. 예를 들어 제품 차원의 일반적인 특성은 제품 이름, 제품 범주, 제품 라인, 제품 크기 및 제품 가격이 될 수 있습니다. 이러한 개체는 데이터 원본 뷰에 있는 하나 이상의 테이블의 하나 이상의 열에 바인딩됩니다. 기본적으로 이러한 특성은 특성 계층으로 표시되며 큐브의 팩트 데이터를 확인하는 데 사용할 수 있습니다. 특성은 큐브의 데이터를 검색할 때 사용자를 지원할 탐색 경로를 제공하는 사용자 정의 계층으로 구성될 수 있습니다.  
  
 큐브에는 사용자가 팩트 데이터 분석을 기반으로 사용하는 모든 차원이 들어 있습니다. 큐브의 데이터베이스 차원 인스턴스를 큐브 차원이라고 하며 이 인스턴스는 큐브에 있는 하나 이상의 측정값 그룹과 관련되어 있습니다. 데이터베이스 차원은 큐브에서 여러 번 사용될 수 있습니다. 예를 들어 팩트 테이블에 여러 개의 시간 관련 팩트가 있을 수 있고 각 시간 관련 팩트 분석을 지원하기 위해 별도의 큐브 차원을 정의할 수 있습니다. 그러나 시간 관련 데이터베이스 차원은 한 개만 있어야 하므로 여러 개의 시간 기반 큐브 차원을 지원하는 시간 관련 관계형 데이터베이스 테이블도 한 개만 있어야 합니다.  
  
> [!NOTE]  
>  차원 디자인과 관련된 성능 문제에 대한 자세한 내용은 [SQL Server 2008 R2 Analysis Services Performance Guide](https://go.microsoft.com/fwlink/?LinkId=306717)(SQL Server 2008 R2 Analysis Services 성능 가이드)를 참조하세요.  
  
## <a name="defining-dimensions-attributes-and-hierarchies"></a>차원, 특성 및 계층 정의  
 데이터베이스 및 큐브 차원, 특성 및 계층을 정의하는 가장 간단한 방법은 큐브 마법사를 사용하여 큐브를 정의할 때 이러한 차원을 만드는 것입니다. 큐브 마법사는 마법사가 식별하거나 사용자가 큐브에서 사용하도록 지정한 데이터 원본 뷰의 차원 테이블을 기반으로 차원을 만듭니다. 그러면 마법사를 통해 만든 데이터베이스 차원이 새 큐브에 추가되어 큐브 차원이 됩니다.  
  
 큐브를 만들 때 데이터베이스에 이미 있는 차원을 새 큐브에 추가할 수도 있습니다. 이러한 차원은 다른 큐브에 대해 또는 차원 마법사를 통해 이전에 정의된 것일 수 있습니다. 데이터베이스 차원을 정의한 후에는 차원 디자이너에서 해당 데이터베이스 차원을 수정하고 구성할 수 있습니다. 그리고 큐브 디자이너에서 제한된 범위까지 큐브 차원을 사용자 지정할 수 있습니다.  
  
> [!NOTE]  
>  또한 XMLA 또는 AMO(Analysis Management Objects)를 사용하여 차원, 특성 및 계층을 프로그래밍 방식으로 디자인하고 구성할 수 있습니다. 자세한 내용은 [AMO(Analysis Management Object) &#40;AMO&#41;를 사용 하 여 ](https://docs.microsoft.com/bi-reference/amo/developing-with-analysis-management-objects-amo) [Analysis Services 스크립팅 언어 &#40;&#41; 참조](https://docs.microsoft.com/bi-reference/assl/analysis-services-scripting-language-assl-for-xmla) 및 개발을 참조 하세요.  
  
## <a name="in-this-section"></a>섹션 내용  
 다음 표에서는 이 섹션에서 다루는 항목에 대해 설명합니다.  
  
 [데이터베이스 차원 정의](define-database-dimensions.md)  
 차원 디자이너를 사용하여 데이터베이스 차원을 수정하고 구성하는 방법에 대해 설명합니다.  
  
 [차원 특성 속성 참조](dimension-attribute-properties-reference.md)  
 차원 디자이너를 사용하여 데이터베이스 차원 특성을 정의, 수정 및 구성하는 방법에 대해 설명합니다.  
  
 [특성 관계 정의](attribute-relationships-define.md)  
 차원 디자이너를 사용하여 특성 관계를 정의, 수정 및 구성하는 방법에 대해 설명합니다.  
  
 [사용자 정의 계층 만들기](user-defined-hierarchies-create.md)  
 차원 디자이너를 사용하여 차원 특성의 사용자 정의 계층을 정의, 수정 및 구성하는 방법에 대해 설명합니다.  
  
 [비즈니스 인텔리전스 마법사를 사용하여 차원 향상](../use-the-business-intelligence-wizard-to-enhance-dimensions.md)  
 비즈니스 인텔리전스 마법사를 사용하여 데이터베이스 차원을 향상시키는 방법에 대해 설명합니다.  
  
## <a name="see-also"></a>참고 항목  
 [다차원 모델의 큐브](cubes-in-multidimensional-models.md)  
  
  
