---
title: Microsoft 신경망 알고리즘 | Microsoft Docs
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: data-mining
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 54896093b887985fc658e823f7d277347a70f0ea
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62724997"
---
# <a name="microsoft-neural-network-algorithm"></a>Microsoft Neural Network Algorithm
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] 신경망 알고리즘은 기계 학습을 위해 널리 사용되고 조정 가능한 신경망 아키텍처의 구현입니다.  이 알고리즘은 예측 가능한 특성의 가능한 각 상태에 대해 입력 특성의 가능한 각 상태를 테스트하고 학습 데이터를 기반으로 각 조합의 확률을 계산합니다. 이러한 확률을 분류 또는 회귀 작업에 사용하여 일부 입력 특성을 기반으로 결과를 예측할 수 있습니다. 신경망은 연결 분석에도 사용할 수 있습니다.  
  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 신경망 알고리즘을 사용하여 마이닝 모델을 만들 때 여러 출력을 포함할 수 있으며 알고리즘은 여러 네트워크를 만듭니다. 단일 마이닝 모델에 포함된 네트워크의 수는 입력 열의 상태(또는 특성 값) 수뿐만 아니라 마이닝 모델에서 사용하는 예측 가능한 열의 수와 해당 열에 있는 상태 수에 따라 달라집니다.  
  
## <a name="example"></a>예제  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 신경망 알고리즘은 제조 또는 상업 프로세스와 같은 프로세스에서 사용되는 복잡한 입력 데이터를 분석하거나 상당한 양의 학습 데이터가 있지만 다른 알고리즘으로 쉽게 규칙을 이끌어 낼 수 없는 비즈니스 문제를 분석하는 데 유용합니다.  
  
 다음과 같은 시나리오에서 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 신경망 알고리즘을 사용할 수 있습니다.  
  
-   홍보 메일 행사나 라디오 광고 캠페인의 성공 정도 측정과 같은 마케팅 및 홍보 행사 분석  
  
-   기록 데이터를 사용하여 주식 이동, 통화 변동 또는 유동성이 큰 기타 재무 정보 예측  
  
-   제조 및 공업 프로세스 분석  
  
-   텍스트 마이닝  
  
-   많은 입력과 비교적 적은 출력 간의 복잡한 관계를 분석하는 모든 예측 모델  
  
## <a name="how-the-algorithm-works"></a>알고리즘 작동 방법  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 신경망 알고리즘은 최대 3개의 노드( *뉴런*이라고도 함) 계층으로 구성된 신경망을 만듭니다. 이러한 계층은 *입력 계층*, *숨겨진 계층*및 *출력 계층*입니다.  
  
 **입력된 계층:** 입력된 노드 데이터 마이닝 모델 및 해당 확률에 대 한 모든 입력된 특성 값을 정의 합니다.  
  
 **숨겨진된 계층:** 숨겨진된 노드는 입력 노드에서 입력을 수신 하 고 출력 노드에 출력을 제공 합니다. 숨겨진 뉴런은 입력의 다양한 확률에 가중치가 할당되는 위치입니다. 가중치는 숨겨진 노드에 대한 특정 입력의 관련성 또는 중요도를 설명합니다. 입력에 할당된 가중치가 클수록 해당 입력 값의 중요도도 큽니다. 가중치는 음수가 될 수 있으며 이 경우 입력이 특정 결과를 지지하는 것이 아니라 제한할 수 있음을 의미합니다.  
  
 **출력 계층:** 출력 노드는 데이터 마이닝 모델에 대 한 예측 가능한 특성 값을 나타냅니다.  
  
 입력 계층, 숨겨진 계층 및 출력 계층이 생성되고 점수가 매겨지는 방법에 대한 자세한 내용은 [Microsoft 신경망 알고리즘 기술 참조](../../analysis-services/data-mining/microsoft-neural-network-algorithm-technical-reference.md)를 참조하세요.  
  
## <a name="data-required-for-neural-network-models"></a>신경망 모델에 필요한 데이터  
 신경망 모델은 하나의 키 열, 하나 이상의 입력 열, 하나 이상의 예측 가능한 열을 포함해야 합니다.  
  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 신경망 알고리즘을 사용하는 데이터 마이닝 모델은 알고리즘에 사용 가능한 매개 변수에 대해 사용자가 지정한 값의 영향을 크게 받습니다. 이러한 매개 변수는 데이터가 샘플링되는 방식, 데이터가 각 열에 배포되거나 배포될 것으로 예상되는 방식 및 기능 선택이 실행되어 최종 모델에 사용되는 값을 제한하는 시기를 정의합니다.  
  
 매개 변수를 설정하여 모델의 동작을 사용자 지정하는 방법에 대한 자세한 내용은 [Microsoft 신경망 알고리즘 기술 참조](../../analysis-services/data-mining/microsoft-neural-network-algorithm-technical-reference.md)를 참조하세요.  
  
## <a name="viewing-a-neural-network-model"></a>신경망 모델 보기  
 데이터를 사용하고 모델이 입력과 출력 간의 상관 관계를 찾아내는 방식을 보려면 **Microsoft 신경망 뷰어**를 사용합니다. 이 사용자 지정 뷰어를 사용하면 입력 특성과 해당 값을 필터링하고 이러한 항목이 출력에 주는 영향을 보여 주는 그래프를 볼 수 있습니다. 뷰어의 도구 설명에는 각 입력 및 출력 값 쌍과 연결된 확률 및 리프트가 표시됩니다. 자세한 내용은 [Microsoft 신경망 뷰어를 사용하여 모델 찾아보기](../../analysis-services/data-mining/browse-a-model-using-the-microsoft-neural-network-viewer.md)를 참조하세요.  
  
 모델의 구조를 탐색하는 가장 쉬운 방법은 **Microsoft 일반 콘텐츠 트리 뷰어**를 사용하는 것입니다. 모델에서 만든 입력, 출력 및 네트워크를 볼 수 있을 뿐 아니라, 노드를 클릭하여 확장한 다음 입력 계층, 출력 계층 또는 숨겨진 계층 노드와 관련된 통계를 볼 수 있습니다. 자세한 내용은 [Microsoft 일반 콘텐츠 트리 뷰어를 사용하여 모델 찾아보기](../../analysis-services/data-mining/browse-a-model-using-the-microsoft-generic-content-tree-viewer.md)를 참조하세요.  
  
## <a name="creating-predictions"></a>예측 만들기  
 모델이 처리된 후에는 네트워크와 각 노드 내에 저장된 가중치를 사용하여 예측을 만들 수 있습니다. 신경망 모델에서는 회귀, 연결 및 분류 분석을 지원하므로 각 예측의 의미가 다를 수 있습니다. 모델 자체를 쿼리하여 발견된 상관 관계를 검토하고 관련 통계를 찾을 수도 있습니다. 신경망 모델에 대한 쿼리를 만드는 방법의 예는 [신경망 모델 쿼리 예제](../../analysis-services/data-mining/neural-network-model-query-examples.md)를 참조하세요.  
  
 데이터 마이닝 모델에 대한 쿼리를 만드는 방법은 [데이터 마이닝 쿼리](../../analysis-services/data-mining/data-mining-queries.md)를 참조하세요.  
  
## <a name="remarks"></a>Remarks  
  
-   드릴스루 또는 데이터 마이닝 차원은 지원하지 않습니다. 이는 마이닝 모델의 노드 구조가 기본 데이터와 반드시 일치하지는 않기 때문입니다.  
  
-   PMML(Predictive Model Markup Language) 형식의 모델 생성은 지원하지 않습니다.  
  
-   OLAP 마이닝 모델의 사용을 지원합니다.  
  
-   데이터 마이닝 차원의 생성은 지원하지 않습니다.  
  
## <a name="see-also"></a>관련 항목  
 [Microsoft 신경망 알고리즘 기술 참조](../../analysis-services/data-mining/microsoft-neural-network-algorithm-technical-reference.md)   
 [신경망 모델에 대한 마이닝 모델 콘텐츠&#40;Analysis Services - 데이터 마이닝&#41;](../../analysis-services/data-mining/mining-model-content-for-neural-network-models-analysis-services-data-mining.md)   
 [신경망 모델 쿼리 예제](../../analysis-services/data-mining/neural-network-model-query-examples.md)   
 [Microsoft 로지스틱 회귀 알고리즘](../../analysis-services/data-mining/microsoft-logistic-regression-algorithm.md)  
  
  
