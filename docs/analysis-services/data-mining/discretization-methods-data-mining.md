---
title: 분할 메서드 (데이터 마이닝) | Microsoft Docs
ms.date: 05/01/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: data-mining
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 610108ce4edb6e3beb5c13398d0a79eca200bdba
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62467764"
---
# <a name="discretization-methods-data-mining"></a>분할 방법(데이터 마이닝)
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 에서 데이터 마이닝 모델을 만드는 데 사용되는 일부 알고리즘은 특정 내용 유형이 있어야만 올바로 실행될 수 있습니다. 예를 들어 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Naive Bayes 알고리즘은 연속 열을 입력으로 사용할 수 없고 연속 값을 예측할 수 없습니다. 또한 일부 열에는 포함된 값이 너무 많아 알고리즘에서 모델을 만들기 위한 데이터 패턴을 쉽게 식별할 수 없습니다.  
  
 이 경우 알고리즘을 사용하여 마이닝 모델을 생성할 수 있도록 열의 데이터를 분할할 수 있습니다. *분할* 은 가능한 상태의 수를 제한하기 위해 값을 버킷에 넣는 프로세스로서, 버킷 자체는 정렬된 불연속 값으로 처리됩니다. 숫자 및 문자열 열을 모두 분할할 수 있습니다.  
  
 데이터를 분할하는 데 사용할 수 있는 여러 가지 방법이 있습니다. 데이터 마이닝 솔루션에서 관계형 데이터를 사용하는 경우 <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn.DiscretizationBucketCount%2A> 속성 값을 설정하여 데이터를 그룹화하는 데 사용할 버킷 수를 제어할 수 있습니다. 기본 버킷 수는 5개입니다.  
  
 데이터 마이닝 솔루션에서 OLAP(온라인 분석 처리) 큐브의 데이터를 사용하는 경우 데이터 마이닝 알고리즘은 다음 수식을 사용하여 생성할 버킷 수를 계산합니다. 여기서 n은 열에 있는 데이터의 고유 값 수입니다.  
  
 `Number of Buckets = sqrt(n)`  
  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]에서 버킷 수를 계산하지 않으려는 경우 <xref:Microsoft.AnalysisServices.DimensionAttribute.DiscretizationBucketCount%2A> 속성을 사용하여 버킷 수를 수동으로 지정할 수 있습니다.  
  
 다음 표에서는 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]에서 데이터를 분할하는 데 사용할 수 있는 방법을 설명합니다.  
  
|분할 방법|Description|  
|---------------------------|-----------------|  
|**AUTOMATIC**|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 에서 사용할 분할 방법을 결정합니다.|  
|**CLUSTERS**|이 알고리즘은 학습 데이터를 샘플링하여 임의의 지점 수로 초기화하고 EM(Expectation Maximization) 클러스터링 방법으로 Microsoft 클러스터링 알고리즘을 여러 번 반복 실행하여 데이터를 그룹으로 나눕니다. **CLUSTERS** 방법은 모든 분포 곡선에서 실행되기 때문에 유용합니다. 그러나 다른 분할 방법보다 처리 시간이 오래 걸립니다.<br /><br /> 이 방법은 숫자 열에만 사용할 수 있습니다.|  
|**EQUAL_AREAS**|이 알고리즘은 각 그룹에 동일한 수의 값이 포함되도록 데이터를 그룹으로 나눕니다. 이 방법은 정규 분포 곡선에 가장 효과적이며 연속 데이터의 제한된 그룹에 많은 값이 포함된 분포에서는 제대로 실행되지 않습니다. 예를 들어 항목의 절반에 대한 비용이 0인 경우 해당 데이터의 절반이 곡선의 단일 지점에서 발생합니다. 이러한 분포에서 이 방법은 여러 영역에 같은 분할을 설정하기 위해 데이터를 분리하므로 데이터가 잘못 표현됩니다.|  
  
## <a name="remarks"></a>Remarks  
  
-   **EQUAL_AREAS** 메서드를 사용하여 문자열을 불연속화할 수 있습니다.  
  
-   **CLUSTERS** 방법은 1000개 레코드의 무작위 샘플링을 사용하여 데이터를 분할합니다. 알고리즘에서 데이터를 샘플링하지 않으려면 **EQUAL_AREAS** 메서드를 사용합니다.  
  
  
  
## <a name="see-also"></a>관련 항목  
 [콘텐츠 형식&#40;데이터 마이닝&#41;](../../analysis-services/data-mining/content-types-data-mining.md)   
 [콘텐츠 형식&#40;DMX&#41;](../../dmx/content-types-dmx.md)   
 [데이터 마이닝 알고리즘&#40;Analysis Services - 데이터 마이닝&#41;](../../analysis-services/data-mining/data-mining-algorithms-analysis-services-data-mining.md)   
 [마이닝 구조 & #40; Analysis Services-데이터 마이닝 & #41;](../../analysis-services/data-mining/mining-structures-analysis-services-data-mining.md)   
 [데이터 형식&#40;데이터 마이닝&#41;](../../analysis-services/data-mining/data-types-data-mining.md)   
 [마이닝 구조 열](../../analysis-services/data-mining/mining-structure-columns.md)   
 [열 배포&#40;데이터 마이닝&#41;](../../analysis-services/data-mining/column-distributions-data-mining.md)  
  
  
