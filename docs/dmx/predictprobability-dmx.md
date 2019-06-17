---
title: PredictProbability (DMX) | Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 4f2a01e2cfd460d503e4326c44eaf356b8a5ecb4
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62659166"
---
# <a name="predictprobability-dmx"></a>PredictProbability(DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  지정한 상태에 대한 확률을 반환합니다.  
  
## <a name="syntax"></a>구문  
  
```  
  
PredictProbability(<scalar column reference>, [<predicted state>])  
```  
  
## <a name="applies-to"></a>적용 대상  
 스칼라 열  
  
## <a name="return-type"></a>반환 형식  
 스칼라 값입니다.  
  
## <a name="remarks"></a>Remarks  
 예측 상태를 생략하면 누락된 상태 버킷을 제외하고 확률이 가장 높은 상태가 사용됩니다. 누락 된 상태 버킷을 포함 하려면 설정 합니다 \<예측 상태별 > 하 **INCLUDE_NULL**합니다. 누락 된 상태에 대 한 확률을 반환 하려면 설정의 \<예측 상태별 > NULL로 합니다.  
  
> [!NOTE]  
>  일부 마이닝 모델은 확률 값을 제공하지 않으므로 이 함수를 사용할 수 없습니다. 또한 쿼리하는 모델 유형에 따라 특정 대상 값에 대한 확률 값이 다르게 계산되거나 다르게 해석될 수 있습니다. 특정 모델 유형에 대 한 확률은 계산 하는 방법에 대 한 자세한 내용은에서 개별 알고리즘 항목을 참조 하세요 [마이닝 모델 콘텐츠 &#40;Analysis Services-데이터 마이닝&#41;](../analysis-services/data-mining/mining-model-content-analysis-services-data-mining.md)합니다.  
  
## <a name="examples"></a>예  
 다음 예에서는 자연 예측 조인을 사용하여 TM Decision Tree 마이닝 모델을 기반으로 개별 고객이 자전거를 구입할 가능성이 있는지 여부를 확인하고 예측의 확률도 확인합니다. 예에는 가능한 각 값에 대해 하나씩 두 개의 PredictProbability 함수가 있습니다. 이 인수를 생략하면 함수에서 가장 가능성 있는 값의 확률을 반환합니다.  
  
```  
SELECT  
  [Bike Buyer],  
  PredictProbability([Bike Buyer], 1) AS [Bike Buyer = Yes],  
  PredictProbability([Bike Buyer], 0) AS [Bike Buyer = No]  
FROM [TM Decision Tree]  
NATURAL PREDICTION JOIN  
(SELECT 28 AS [Age],  
  '2-5 Miles' AS [Commute Distance],  
  'Graduate Degree' AS [Education],  
  0 AS [Number Cars Owned],  
  0 AS [Number Children At Home]) AS t  
```  
  
 예제 결과:  
  
|Bike Buyer|Bike Buyer = Yes|Bike Buyer = No|  
|----------------|-----------------------|----------------------|  
|1|0.867074195848097|0.132755556974282|  
  
## <a name="see-also"></a>관련 항목  
 [Data Mining Extensions &#40;DMX&#41; 함수 참조](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [함수 &#40;DMX&#41;](../dmx/functions-dmx.md)   
 [일반 예측 함수 &#40;DMX&#41;](../dmx/general-prediction-functions-dmx.md)  
  
  
