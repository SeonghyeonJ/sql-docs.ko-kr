---
title: 기능 선택 (데이터 마이닝) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining models [Analysis Services], feature selections
- attributes [data mining]
- feature selection algorithms [Analysis Services]
- data mining [Analysis Services], feature selections
- neural network algorithms [Analysis Services]
- naive bayes algorithms [Analysis Services]
- decision tree algorithms [Analysis Services]
- datasets [Analysis Services]
- clustering algorithms [Analysis Services]
- coding [Data Mining]
ms.assetid: b044e785-4875-45ab-8ae4-cd3b4e3033bb
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: a1d79bb3810a56e8a1769845131312eab306f223
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66084423"
---
# <a name="feature-selection-data-mining"></a>기능 선택(데이터 마이닝)
  *기능 선택* 도구와 입력 처리 및 분석을 위해 관리 하기 쉬운 크기로 줄이는 데 사용할 수 있는 기법을 설명 하기 위해 데이터 마이닝에서 일반적으로 사용 하는 용어입니다. 기능 선택은 뿐 아니라 *카디널리티 감소가*, 즉, 모델 뿐만 아니라 특성, 즉 선택 빌드할 때 고려할 수 있는 특성의 수에는 임의의 또는 미리 정의 된 구분 나아가 분석가 또는 모델링 도구가 적극적으로 선택 하거나 분석의 유용성을 기반으로 특성을 삭제 합니다.  
  
 데이터 집합에는 모델을 작성하는 데 필요한 것보다 훨씬 많은 정보가 자주 포함되기 때문에 기능 선택을 적용하는 기능은 효과적인 분석에 중요합니다. 예를 들어, 데이터 집합에 고객의 특성을 설명하는 열이 500개 있지만 일부 열에 데이터가 매우 드물 경우 해당 열을 모델에 추가하여 얻는 이점이 거의 없을 수 있습니다. 모델을 작성하는 동안 불필요한 열을 그대로 둘 경우 학습 프로세스에 더 많은 CPU와 메모리가 필요하고 완료된 모델에 더 많은 저장 공간이 필요합니다.  
  
 리소스가 문제 되지 않는 경우라도 불필요한 열은 다음과 같은 이유로 검색된 패턴의 품질을 떨어뜨리므로 일반적으로 제거하는 것이 좋습니다.  
  
-   일부 열에 잡음이 있거나 중복됩니다. 이러한 잡음이 있으면 데이터에서 의미 있는 패턴을 찾아내기가 더 어려워집니다.  
  
-   양질의 패턴을 찾아내기 위해 대부분의 데이터 마이닝 알고리즘은 고차원 데이터 집합에 대해 훨씬 큰 학습 데이터 집합을 요구합니다. 하지만 일부 데이터 마이닝 응용 프로그램에서는 학습 데이터가 매우 작습니다.  
  
 데이터 원본의 500개 열 중에서 50개 열에만 모델 작성에 유용한 정보가 있을 경우 이러한 열을 모델에 포함하지 않거나, 기능 선택 기술을 사용하여 최상의 기능을 자동으로 검색하고 통계적으로 중요하지 않은 값을 제외할 수 있습니다. 기능 선택은 중요하지 않은 데이터가 너무 많거나, 매우 중요한 데이터가 너무 적은 두 가지 문제를 해결하는 데 도움이 됩니다.  
  
## <a name="feature-selection-in-analysis-services-data-mining"></a>Analysis Services 데이터 마이닝의 기능 선택  
 일반적으로 기능 선택은 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]에서 자동으로 수행되며 각 알고리즘에는 기능 축소를 지능형으로 적용하기 위한 기본 기술 집합이 있습니다. 기능 선택은 모델에 사용될 가능성이 가장 높은 특성을 데이터 집합에서 자동으로 선택하기 위해 모델을 학습하기 전에 항상 수행됩니다. 하지만 기능 선택 동작에 영향을 주는 매개 변수를 수동으로 설정할 수도 있습니다.  
  
 일반적으로 기능 선택은 각 특성에 대한 점수를 계산한 다음 점수가 가장 높은 특성만 선택하는 방식으로 작동합니다. 최고 점수에 대한 임계값도 조정할 수 있습니다. [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]에서는 이러한 점수를 계산하기 위한 여러 방법을 제공하며 특정 모델에 적용되는 정확한 방법은 다음 요소에 따라 결정됩니다.  
  
-   모델에 사용되는 알고리즘  
  
-   특성의 데이터 형식  
  
-   모델에 설정할 수 있는 모든 매개 변수  
  
 기능 선택은 열의 입력, 예측 가능한 특성 또는 상태에 적용됩니다. 기능 선택에 대한 평가가 완료되면 알고리즘이 선택한 특성 및 상태만 모델 작성 프로세스에 포함되며 예측에 사용할 수 있습니다. 기능 선택에 대한 임계값과 일치하지 않는 예측 가능한 특성을 선택할 경우 이 특성을 예측에 사용할 수 있지만 예측은 모델에 있는 글로벌 통계만을 기준으로 수행됩니다.  
  
> [!NOTE]  
>  기능 선택은 모델에 사용된 열에만 영향을 미치며 마이닝 구조 스토리지에는 영향을 미치지 않습니다. 마이닝 모델에서 제외된 열은 계속 구조에서 사용할 수 있으며 마이닝 구조 열의 데이터는 캐시됩니다.  
  
### <a name="definition-of-feature-selection-methods"></a>기능 선택 방법 정의  
 기능 선택을 구현하는 방법에는 여러 가지가 있는데 작업 중인 데이터의 형식과 분석을 위해 선택한 알고리즘에 따라 이 방법이 달라집니다. SQL Server Analysis Services는 널리 사용되고 잘 알려진 특성 점수 매기기 메서드를 여러 개 제공합니다. 알고리즘 또는 데이터 집합에 적용되는 방법은 데이터 형식 및 열 사용법에 따라 다릅니다.  
  
 *흥미도* 점수는 이진이 아닌 연속 숫자 데이터를 포함하는 열의 특성에 순위를 매기고 정렬하는 데 사용됩니다.  
  
 불연속 데이터와 분할된 데이터가 들어 있는 열에는*Shannon Entropy* 및 두 가지 *Bayesian* 점수를 사용할 수 있습니다. 하지만 모델에 연속 열이 포함된 경우 일관성을 보장하기 위해 흥미도 점수를 사용하여 모든 입력 열을 평가합니다.  
  
 다음 섹션에서는 기능 선택의 각 방법에 대해 설명합니다.  
  
#### <a name="interestingness-score"></a>흥미도 점수  
 유용한 정보를 제공하는 기능은 흥미롭습니다. 데이터 마이닝 업계 측정 하는 다양 한 방법 개발한 시나리오에 따라 달라 집니다 무엇이 유용한 정의 되므로 *흥미도*합니다. 예를 들어 *새로 움* 이상 값 검색 하지만 밀접 하 게 관련된 항목을 구분 하는 기능이 유용할 수 있습니다 또는 *판별 가중치*에 대 한 흥미로운 수 분류 합니다.  
  
 SQL Server Analysis Services에 사용 되는 흥미도 측정은 *entropy 기반*즉, 분포가 특성 보다 높은 엔트로피 있고 낮은 정보 획득, 따라서 이러한 특성은 작은 된 흥미로운 합니다. 특정 특성에 대한 Entropy는 다음과 같이 다른 모든 특성의 Entropy와 비교됩니다.  
  
 Interestingness(Attribute) = - (m - Entropy(Attribute)) * (m - Entropy(Attribute))  
  
 중앙 Entropy 또는 m은 전체 기능 집합의 Entropy를 의미합니다. 중앙 Entropy에서 대상 특성의 Entropy를 뺀 값으로 특성이 제공하는 정보량을 평가할 수 있습니다.  
  
 이 점수는 기본적으로 이진이 아닌 연속 숫자 데이터가 열에 포함되어 있는 경우 항상 사용됩니다.  
  
#### <a name="shannons-entropy"></a>Shannon Entropy  
 Shannon Entropy는 특정 결과에 대한 불규칙 변수의 불확실성을 측정합니다. 예를 들어 동전 던지기에 대한 Entropy는 동전 앞면이 나올 확률에 대한 함수로 표시할 수 있습니다.  
  
 Analysis Services에서는 다음 수식을 사용하여 Shannon Entropy를 계산합니다.  
  
 H(X) = -  P(xi) log(P(xi))  
  
 이 점수 매기기 메서드는 불연속 특성과 불연속화된 특성에 사용할 수 있습니다.  
  
#### <a name="bayesian-with-k2-prior"></a>Bayesian with K2 Prior  
 Analysis Services에서는 Bayesian 네트워크를 기반으로 하는 두 개의 기능 선택 점수를 제공합니다. Bayesian 네트워크는 상태 및 상태 전환에 대한 *방향* 또는 *비순환* 그래프로, 항상 현재 상태 앞에 오는 상태도 있고 현재 상태 뒤에 오는 상태도 있으며 그래프가 반복되거나 순환되지 않음을 의미합니다. 정의에 따라 Bayesian 네트워크에서는 사전 지식을 활용할 수 있습니다. 그러나 이후 상태에 대한 확률을 계산하는 데 사용할 이전 상태가 어떤 것인가는 알고리즘 설계, 성능 및 정확도에 중요합니다.  
  
 Bayesian 네트워크를 통한 학습을 위해 고안된 K2 알고리즘은 Cooper와 Herskovits가 개발하였으며 데이터 마이닝에 자주 사용됩니다. K2 알고리즘은 확장 가능하며 여러 변수를 분석할 수 있지만 입력으로 사용되는 변수의 정렬을 필요로 합니다. 자세한 내용은 [Learning Bayesian Networks](https://go.microsoft.com/fwlink/?LinkId=105885) (Chickering, Geiger 및 Heckerman 공저)를 참조하십시오.  
  
 이 점수 매기기 메서드는 불연속 특성과 불연속화된 특성에 사용할 수 있습니다.  
  
#### <a name="bayesian-dirichlet-equivalent-with-uniform-prior"></a>Bayesian Dirichlet Equivalent with Uniform Prior  
 데이터 세트가 제공된 경우 BDE(Bayesian Dirichlet Equivalent) 점수도 Bayesian 분석을 사용하여 네트워크를 평가합니다. BDE 점수 매기기 메서드는 Heckerman이 개발했으며 Cooper와 Herskovits가 개발한 BD 메트릭을 기반으로 합니다. Dirichlet 분포는 네트워크에 있는 각 변수에 대한 조건부 확률을 설명하는 다차원 분포로 학습에 유용한 속성을 많이 포함합니다.  
  
 BDEU(Bayesian Dirichlet Equivalent with Uniform Prior) 메서드는 이전 상태에 대한 고정 분포 및 균일 분포를 만드는 데 수학 상수가 사용되는 Dirichlet 분포의 특수한 사례를 가정합니다. BDE 점수도 데이터가 등가 구조를 판별할 수 없음을 의미하는 가능성 등가를 가정합니다. 다시 말해서 If A Then B에 대한 점수가 If B Then A에 대한 점수와 동일한 경우 데이터를 기반으로 구조를 구별할 수 없으며 인과 관계를 추론할 수 없습니다.  
  
 Bayesian 네트워크 및 이러한 점수 매기기 메서드의 구현에 대한 자세한 내용은 [Bayesian 네트워크 학습(Learning Bayesian Networks)](https://go.microsoft.com/fwlink/?LinkId=105885)을 참조하십시오.  
  
### <a name="feature-selection-methods-used-by-analysis-services-algorithms"></a>Analysis Services 알고리즘에서 사용하는 기능 선택 방법  
 다음 표에서는 기능 선택을 지원하는 알고리즘, 알고리즘에서 사용하는 기능 선택 방법 및 기능 선택 동작을 제어하기 위해 설정하는 매개 변수를 보여 줍니다.  
  
|알고리즘|분석 방법|주석|  
|---------------|------------------------|--------------|  
|Naive Bayes|Shannon Entropy<br /><br /> Bayesian with K2 Prior<br /><br /> Bayesian Dirichlet with uniform prior(기본값)|Microsoft Naïve Bayes 알고리즘은 불연속 특성 또는 불연속화된 특성을 허용하므로 흥미도 점수를 사용할 수 없습니다.<br /><br /> 이 알고리즘에 대한 자세한 내용은 [Microsoft Naive Bayes Algorithm Technical Reference](microsoft-naive-bayes-algorithm-technical-reference.md)를 참조하십시오.|  
|의사 결정 트리|흥미도 점수<br /><br /> Shannon Entropy<br /><br /> Bayesian with K2 Prior<br /><br /> Bayesian Dirichlet with uniform prior(기본값)|이진이 아닌 연속 값이 열에 포함되어 있는 경우 일관성을 보장하기 위해 모든 열에 흥미도 점수가 사용됩니다. 그렇지 않으면 기본 기능 선택 방법이 사용되거나 모델을 만들 때 지정한 방법이 사용됩니다.<br /><br /> 이 알고리즘에 대한 자세한 내용은 [Microsoft Decision Trees Algorithm Technical Reference](microsoft-decision-trees-algorithm-technical-reference.md)를 참조하십시오.|  
|신경망|흥미도 점수<br /><br /> Shannon Entropy<br /><br /> Bayesian with K2 Prior<br /><br /> Bayesian Dirichlet with uniform prior(기본값)|데이터에 연속 열이 포함된 경우 Microsoft 신경망 알고리즘에서는 Bayesian 및 Entropy 기반 방법을 모두 사용할 수 있습니다.<br /><br /> 이 알고리즘에 대한 자세한 내용은 [Microsoft Neural Network Algorithm Technical Reference](microsoft-neural-network-algorithm-technical-reference.md)를 참조하십시오.|  
|로지스틱 회귀|흥미도 점수<br /><br /> Shannon Entropy<br /><br /> Bayesian with K2 Prior<br /><br /> Bayesian Dirichlet with uniform prior(기본값)|Microsoft 로지스틱 회귀 알고리즘이 Microsoft 신경망 알고리즘을 기반으로 하지만 로지스틱 회귀 모델을 사용자 지정하여 기능 선택 동작을 제어할 수 없습니다. 따라서 기능 선택은 항상 기본적으로 특성에 가장 적합한 방법으로 설정됩니다.<br /><br /> 모든 특성이 불연속 특성 또는 불연속화된 특성인 경우 기본값은 BDEU입니다.<br /><br /> 이 알고리즘에 대한 자세한 내용은 [Microsoft Logistic Regression Algorithm Technical Reference](microsoft-logistic-regression-algorithm-technical-reference.md)를 참조하십시오.|  
|Clustering|흥미도 점수|Microsoft 클러스터링 알고리즘은 불연속 데이터 또는 불연속화된 데이터를 사용할 수 있습니다. 그러나 각 특성의 점수가 거리로 계산되고 연속 숫자로 표현되기 때문에 흥미도 점수를 사용해야 합니다.<br /><br /> 이 알고리즘에 대한 자세한 내용은 [Microsoft Clustering Algorithm Technical Reference](microsoft-clustering-algorithm-technical-reference.md)를 참조하십시오.|  
|선형 회귀|흥미도 점수|Microsoft 선형 회귀 알고리즘은 연속 열만 지원하므로 흥미도 점수만 사용할 수 있습니다.<br /><br /> 이 알고리즘에 대한 자세한 내용은 [Microsoft Linear Regression Algorithm Technical Reference](microsoft-linear-regression-algorithm-technical-reference.md)를 참조하십시오.|  
|연결 규칙<br /><br /> 시퀀스 클러스터링|사용되지 않음|기능 선택은 이러한 알고리즘을 통해 호출되지 않습니다.<br /><br /> 그러나 MINIMUM_SUPPORT 및 MINIMUM_PROBABILIITY 매개 변수의 값을 설정하여 알고리즘의 동작을 제어하고 필요한 경우 입력 데이터의 크기를 줄일 수 있습니다.<br /><br /> 자세한 내용은 [Microsoft Association Algorithm Technical Reference](microsoft-association-algorithm-technical-reference.md) 및 [Microsoft Sequence Clustering Algorithm Technical Reference](microsoft-sequence-clustering-algorithm-technical-reference.md)를 참조하세요.|  
|시계열|사용되지 않음|기능 선택은 시계열 모델에 적용되지 않습니다.<br /><br /> 이 알고리즘에 대한 자세한 내용은 [Microsoft Time Series Algorithm Technical Reference](microsoft-time-series-algorithm-technical-reference.md)를 참조하십시오.|  
  
## <a name="feature-selection-parameters"></a>기능 선택 매개 변수  
 기능 선택을 지원하는 알고리즘에서 다음 매개 변수를 사용하여 기능 선택 사용 시기를 제어할 수 있습니다. 각 알고리즘에는 허용되는 입력 수에 대한 기본값이 있지만, 이 기본값을 재정의하거나 특성 수를 지정할 수 있습니다. 이 섹션에서는 기능 선택을 관리하기 위해 제공되는 매개 변수를 나열합니다.  
  
#### <a name="maximuminputattributes"></a>MAXIMUM_INPUT_ATTRIBUTES  
 *MAXIMUM_INPUT_ATTRIBUTES* 매개 변수에서 지정한 수보다 더 많은 열이 모델에 있는 경우 알고리즘은 필요 없다고 판단되는 모든 열을 무시합니다.  
  
#### <a name="maximumoutputattributes"></a>MAXIMUM_OUTPUT_ATTRIBUTES  
 마찬가지로 *MAXIMUM_OUTPUT_ATTRIBUTES* 매개 변수에서 지정한 수보다 더 많은 예측 가능한 열이 모델에 있는 경우 알고리즘은 필요 없다고 판단되는 모든 열을 무시합니다.  
  
#### <a name="maximumstates"></a>MAXIMUM_STATES  
 *MAXIMUM_STATES* 매개 변수에서 지정한 수보다 더 많은 사례가 모델에 있으면 가장 인기가 없는 상태를 함께 그룹화하여 없는 것으로 처리합니다. 이러한 매개 변수 중 하나를 0으로 설정할 경우 기능 선택이 해제되고 처리 시간 및 성능에 영향을 미칩니다.  
  
 기능 선택에 대한 이러한 방법 외에도, 모델에 *모델링 플래그* 를 설정하거나 구조에 *분산 플래그* 를 설정함으로써 의미 있는 특성을 식별하거나 승격시키는 알고리즘 기능을 강화할 수 있습니다. 이러한 개념에 대한 자세한 내용은 [모델링 플래그&#40;데이터 마이닝&#41;](modeling-flags-data-mining.md) 및 [열 배포&#40;데이터 마이닝&#41;](column-distributions-data-mining.md)를 참조하세요.  
  
## <a name="see-also"></a>관련 항목  
 [마이닝 모델 및 구조 사용자 지정](customize-mining-models-and-structure.md)  
  
  
