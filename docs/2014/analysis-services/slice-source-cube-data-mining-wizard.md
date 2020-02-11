---
title: 원본 큐브 조각화 (데이터 마이닝 마법사) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.dmwizard.slicesourcecube.f1
ms.assetid: 16485608-d3b9-49ee-8baa-948038cdd7ec
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: bcb156d5c0a3c1332e748878ddebda1772b80696
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66068601"
---
# <a name="slice-source-cube-data-mining-wizard"></a>원본 큐브 조각화(데이터 마이닝 마법사)
  
  **원본 큐브 조각화** 대화 상자를 사용하여 모델의 학습에 사용되는 데이터를 제한할 수 있습니다. 일반적으로 큐브는 모든 상점, 모든 지역 및 모든 제품 등 여러 다른 차원 및 특성과 관련된 데이터를 포함합니다. 제한 없는 특성 조합의 모델 학습은 실용적이지 않으므로 이 대화 상자를 사용하여 모델 학습에 사용할 특정 집합을 선택하십시오.  
  
 예를 들어 AdventureWorks 큐브에서 특정 제품 라인, 지역 또는 연도별로 조각화하여 일부 데이터를 가져올 수 있습니다.  
  
 조각과 큐브에 대해 잘 모르는 경우 다음 문서를 검토하는 것이 좋습니다.  
  
-   [파티션 조각 속성 &#40;Analysis Services 설정&#41;](multidimensional-models/set-the-partition-slice-property-analysis-services.md)  
  
-   [Analysis Services&#41;&#40;로컬 파티션 만들기 및 관리](multidimensional-models/create-and-manage-a-local-partition-analysis-services.md)  
  
> [!NOTE]  
>  동적 MDX 함수(예: [Generate&#40;MDX&#41;](/sql/mdx/generate-mdx) 또는 [Except&#40;MDX&#41;](/sql/mdx/except-mdx-function))는 파티션에 대한 Slice 속성에서 지원되지 않습니다. 명시적 튜플 또는 멤버 참조를 사용하여 조각을 정의해야 합니다.  
>   
>  예를 들어 &#40;범위를 사용 하 여 범위를 정의 하는 대신, 범위를 정의 하는 데 [&#41; &#40;MDX&#41;](/sql/mdx/range-mdx) 를 사용 하는 대신 각 멤버를 특정 연도로 열거 해야 합니다.  
>   
>  복잡한 조각을 정의해야 하는 경우 XMLA Alter 스크립트를 사용하여 조각에서 튜플을 정의하는 것이 좋습니다. 그런 다음 ascmd 명령줄 도구 또는 SSIS [Analysis Services Execute DDL Task](../integration-services/control-flow/analysis-services-execute-ddl-task.md) 를 사용하여 스크립트를 실행하고 지정된 멤버 집합을 만든 후 곧바로 파티션을 처리할 수 있습니다.  
  
 **자세한 내용:** [데이터 마이닝 마법사 &#40;Analysis Services 데이터 마이닝&#41;](data-mining/data-mining-wizard-analysis-services-data-mining.md), [관계형 마이닝 구조 만들기](data-mining/create-a-relational-mining-structure.md)  
  
## <a name="options"></a>옵션  
 **차원**  
 조각화하려는 차원을 선택합니다.  
  
 **계층**  
 조각화하려는 계층을 선택합니다. 계층의 모든 수준을 선택할 수 있지만 모델에 사용되는 특성은 선택한 수준에만 있어야 합니다.  
  
 예를 들어 Geography 계층을 선택하고 Country를 수준으로 선택하는 경우 City를 특성으로 사용하는 모델을 작성할 수 없습니다. 반대로 City를 조각화할 계층의 수준으로 선택하는 경우 Country를 기준으로 마이닝 모델을 만들 수 없습니다.  
  
 **연산자**  
 조각화 식을 작성하는 데 사용할 연산자를 선택합니다.  
  
 예를 들어 Geography를 계층으로 선택한 경우 연산자 =를 선택한 다음 "유럽"을 필터로 입력 하 여 유럽의 큐브 데이터만 가져올 수 있습니다.  
  
 **필터 식**  
 선택한 차원의 큐브를 필터링할 때 조건 유형으로 사용할 식을 입력합니다.  
  
 **매개 변수**  
 이 옵션은 데이터 마이닝 모델에는 사용되지 않습니다.  
  
## <a name="see-also"></a>참고 항목  
 [마법사 완료 &#40;데이터 마이닝 마법사&#41;](completing-the-wizard-data-mining-wizard.md)   
 [데이터 마이닝 마법사 F1 도움말 &#40;Analysis Services 데이터 마이닝&#41;](data-mining-wizard-f1-help-analysis-services-data-mining.md)   
 [데이터 마이닝 마법사 &#40;마이닝 모델 열 사용법 지정&#41;](specify-mining-model-column-usage-data-mining-wizard.md)  
  
  
