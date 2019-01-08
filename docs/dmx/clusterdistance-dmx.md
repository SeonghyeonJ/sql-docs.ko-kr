---
title: ClusterDistance (DMX) | Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: ad3d0d06016fe8684cacaf73286b229a423aa7c6
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/28/2018
ms.locfileid: "52533657"
---
# <a name="clusterdistance-dmx"></a>ClusterDistance(DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  합니다 **ClusterDistance** 함수 지정된 된 클러스터에서 입력된 사례 사이의 거리를 반환 합니다. 아니면 클러스터가 지정 되지 않은는 입력된 사례와 가장 가능성 있는 클러스터에서 사이의 거리입니다.  
  
## <a name="syntax"></a>구문  
  
```  
  
ClusterDistance([<ClusterID expression>])  
```  
  
## <a name="applies-to"></a>적용 대상  
 이 함수는 기본 데이터 마이닝 모델이 클러스터링을 지원할 때만 사용할 수 있습니다. 이 함수는 EM과 K-Means를 비롯한 모든 종류의 클러스터링 모델과 함께 사용할 수 있지만 알고리즘에 따라 결과가 달라집니다.  
  
## <a name="return-type"></a>반환 형식  
 스칼라 값입니다.  
  
## <a name="remarks"></a>Remarks  
 합니다 **ClusterDistance** 함수는 입력된 사례와 입력 사례에 대 한 확률이 가장 높은 클러스터 사이의 거리를 반환 합니다.  
  
 K-Means 클러스터링의 경우 모든 사례는 멤버 자격 가중치가 1.0인 하나의 클러스터에만 속할 수 있으므로 클러스터 거리는 항상 0입니다. 그러나 K-Means에서는 각 클러스터에 중심이 있는 것으로 간주됩니다. 마이닝 모델 콘텐츠에서 NODE_DISTRIBUTION 중첩 테이블을 쿼리하거나 탐색하면 중심 값을 가져올 수 있습니다. 자세한 내용은 [클러스터링 모델에 대한 마이닝 모델 콘텐츠&#40;Analysis Services - 데이터 마이닝&#41;](../analysis-services/data-mining/mining-model-content-for-clustering-models-analysis-services-data-mining.md)를 참조하세요.  
  
 기본 EM 클러스터링 모델의 경우 클러스터 내부에 있는 모든 점의 확률이 같은 것으로 간주되므로 클러스터에 중심이 없습니다. 변수의 **ClusterDistance** 특정 사례가 특정 클러스터 사이의 *N* 다음과 같이 계산 됩니다.  
  
 ClusterDistance(N) =1-(membershipWeight(N))  
  
 또는:  
  
 ClusterDistance(N) = 1-ClusterProbability (N))  
  
## <a name="related-prediction-functions"></a>관련 예측 함수  
 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]에서는 클러스터링 모델을 쿼리하는 다음과 같은 함수를 추가로 제공합니다.  
  
-   사용 된 [클러스터 &#40;DMX&#41; ](../dmx/cluster-dmx.md) 가장 가능성이 높은 클러스터를 반환 하는 함수입니다.  
  
-   사용 된 [ClusterProbability &#40;DMX&#41; ](../dmx/clusterprobability-dmx.md) 사례를 특정 클러스터에 속할 확률을 가져오려면 함수를 합니다. 이 값은 클러스터 거리의 역수가 됩니다.  
  
-   사용 된 [PredictHistogram &#40;DMX&#41; ](../dmx/predicthistogram-dmx.md) 입력 사례가 각 모델의 클러스터에 속할 확률의 히스토그램을 반환 하는 함수입니다.  
  
-   사용 된 [PredictCaseLikelihood &#40;DMX&#41; ](../dmx/predictcaselikelihood-dmx.md) 알고리즘을 통해 학습 된 모델을 고려할 때 존재 하는 입력된 사례가 나타날 가능성을 나타내는 1로 0에서 측정값은 반환 하는 함수입니다.  
  
## <a name="example1-obtaining-cluster-distance-to-the-most-likely-cluster"></a>예 1: 가장 가능성 있는 클러스터에 대한 클러스터 거리 가져오기  
 다음 예에서는 지정된 사례와 해당 사례가 속할 가능성이 가장 높은 클러스터 사이의 거리를 반환합니다.  
  
```  
SELECT  
    ClusterDistance()  
FROM  
    [TM Clustering]  
NATURAL PREDICTION JOIN  
(SELECT 28 AS [Age],  
    '2-5 Miles' AS [Commute Distance],  
    'Graduate Degree' AS [Education],  
    0 AS [Number Cars Owned],  
    0 AS [Number Children At Home]) AS t  
```  
  
 예제 결과:  
  
|식|  
|----------------|  
|0.0477390930705145|  
  
 가장 가능성 있는 클러스터를 확인하려면 위 예제에서 `Cluster`를 `ClusterDistance`로 바꿉니다.  
  
 예제 결과:  
  
|$CLUSTER|  
|--------------|  
|클러스터 6|  
  
## <a name="example2-obtaining-distance-to-a-specified-cluster"></a>예 2: 지정된 클러스터까지의 거리 가져오기  
 다음 구문은 마이닝 모델 콘텐츠 스키마 행 집합을 사용하여 마이닝 모델의 클러스터에 대한 노드 ID 및 노드 캡션의 목록을 반환합니다. 노드 캡션의 클러스터 식별자 인수로 사용할 수는 **ClusterDistance** 함수입니다.  
  
```  
SELECT NODE_UNIQUE_NAME, NODE_CAPTION   
FROM <model>.CONTENT   
WHERE NODE_TYPE = 5  
```  
  
 예제 결과:  
  
|NODE_UNIQUE_NAME|NODE_CAPTION|  
|------------------------|-------------------|  
|001|클러스터 1|  
|002|클러스터 2|  
  
 다음 구문 예에서는 지정된 사례와 Cluster 2라는 클러스터 사이의 거리를 반환합니다.  
  
```  
SELECT  
    ClusterDistance('Cluster 2')  
AS [Cluster 2 Distance]  
FROM [TM Clustering]  
NATURAL PREDICTION JOIN  
(SELECT 28 AS [Age],  
    '2-5 Miles' AS [Commute Distance],  
    'Graduate Degree' AS [Education],  
    0 AS [Number Cars Owned],  
    0 AS [Number Children At Home]) AS t  
```  
  
 예제 결과:  
  
|Cluster 2 Distance|  
|------------------------|  
|0.97008209236394|  
  
## <a name="see-also"></a>관련 항목:  
 [클러스터 &#40;DMX&#41;](../dmx/cluster-dmx.md)   
 [Data Mining Extensions &#40;DMX&#41; 함수 참조](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [함수 &#40;DMX&#41;](../dmx/functions-dmx.md)   
 [클러스터링 모델에 대한 마이닝 모델 콘텐츠&#40;Analysis Services - 데이터 마이닝&#41;](../analysis-services/data-mining/mining-model-content-for-clustering-models-analysis-services-data-mining.md)  
  
  
