---
title: 구조에 마이닝 모델 추가 (Analysis Services-데이터 마이닝) | Microsoft Docs
ms.date: 05/01/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: data-mining
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: a3647ff06d00aebc4b5feb735d5a69b0b8db79e7
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/15/2019
ms.locfileid: "68210233"
---
# <a name="add-mining-models-to-a-structure-analysis-services---data-mining"></a>구조에 마이닝 모델 추가(Analysis Services - 데이터 마이닝)
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  마이닝 구조는 여러 마이닝 모델을 지원하도록 설계되었습니다. 따라서 마법사를 완료한 후 구조를 열고 새 마이닝 모델을 추가할 수 있습니다. 모델을 만들 때마다 다른 알고리즘을 사용하거나 매개 변수를 변경하거나 필터를 적용하여 다른 데이터 하위 집합을 사용할 수 있습니다.  
  
## <a name="adding-new-mining-models"></a>새 마이닝 모델 추가  
 데이터 마이닝 마법사를 사용하여 새 마이닝 모델을 만드는 경우 항상 기본적으로 먼저 마이닝 구조를 만들어야 합니다. 그러면 마법사에서 구조에 초기 모델을 추가할 수 있는 옵션을 제공합니다. 하지만 모델은 바로 만들 필요가 없습니다. 구조만 만들 경우 예측 가능한 특성으로 사용할 열이나 특정 모델에서 데이터를 사용하는 방법을 결정할 필요가 없습니다. 대신 나중에 사용할 일반 데이터 구조만 설정하고 나중에 [Data Mining Designer](../../analysis-services/data-mining/data-mining-designer.md) 에서 해당 구조를 기반으로 하는 새 마이닝 모델을 추가할 수 있습니다.  
  
> [!NOTE]  
>  DMX에서 CREATE MINING MODEL 문은 마이닝 모델에서 시작됩니다. 즉, 사용자가 선택한 마이닝 모델을 정의하면 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 에서 자동으로 기본 구조를 생성합니다. 나중에 ALTER STRUCTURE를 사용 하 여 해당 구조에 새 마이닝 모델을 추가 할 수 있습니다... ADD MODEL 문입니다.  
  
## <a name="choosing-an-algorithm"></a>알고리즘 선택  
 기존 구조에 새 마이닝 모델을 추가하려면 먼저 해당 모델에서 사용할 데이터 마이닝 알고리즘을 선택해야 합니다. 각 알고리즘에서 서로 다른 유형의 분석을 수행하고 요구 사항이 서로 다르기 때문에 알고리즘의 선택이 중요합니다.  
  
 데이터와 호환되지 않는 알고리즘을 선택하면 경고가 발생합니다. 경우에 따라 알고리즘에서 처리할 수 없는 열을 무시해야 할 수도 있습니다. 그렇지 않은 경우에는 알고리즘에서 자동으로 조정 작업을 실행합니다. 예를 들어 알고리즘에서 불연속 값만 처리할 수 있는 경우 구조에 숫자 데이터가 포함되어 있으면 알고리즘에 의해 숫자 값이 자동으로 불연속 범위로 그룹화됩니다. 하지만 경우에 따라 키 또는 예측 가능한 특성을 선택하여 먼저 데이터를 수동으로 수정해야 할 수도 있습니다.  
  
 새 모델을 만들 때 알고리즘을 변경하지 않아도 됩니다. 동일한 알고리즘을 사용하면서 데이터를 필터링하거나 클러스터링 메서드 또는 최소 항목 집합 크기와 같은 매개 변수를 변경하여 아주 다른 결과를 얻을 수 있는 경우가 많기 때문입니다. 여러 가지 모델을 사용하면서 어떤 매개 변수가 최상의 결과를 제공하는지 확인하는 것이 좋습니다.  
  
 새 모델을 사용하려면 먼저 모델을 처리해야 합니다.  
  
## <a name="specifying-the-usage-of-columns-in-a-new-mining-model"></a>새 마이닝 모델의 열 사용법 지정  
 새 마이닝 모델을 기존 마이닝 구조에 추가하는 경우 모델에서 각 데이터 열을 사용할 방법을 지정해야 합니다. 모델에 대해 선택한 알고리즘 유형에 따라 일부 선택 항목이 기본적으로 지정될 수 있습니다. 열에 대한 사용 유형을 지정하지 않으면 해당 열이 마이닝 구조에 포함되지 않습니다. 그러나 열의 데이터는 드릴스루에 계속 사용할 수 있습니다(모델에서 지원하는 경우).  
  
 모델에 사용되는 마이닝 구조의 열(무시로 설정되지 않은 경우)은 키, 입력 열, 예측 가능한 열 또는 해당 값이 모델의 입력으로도 사용되는 예측 가능한 열입니다.  
  
-   키 열은 테이블의 각 행에 대한 고유 식별자를 포함합니다. 시퀀스 클러스터링 또는 시계열 알고리즘을 기반으로 하는 일부 마이닝 모델은 여러 키 열을 포함할 수 있습니다. 그러나 이러한 여러 키는 관계상 복합 키가 아니며 대신 시계열 및 시퀀스 클러스터링 분석을 지원하기 위해 선택되어야 합니다.  
  
-   입력 열은 예측의 기반이 되는 정보를 제공합니다. 데이터 마이닝 마법사에서는 예측 가능한 열을 선택하면 설정되는 **제안** 기능을 사용할 수 있습니다. 이 단추를 클릭하면 마법사에서 예측 가능한 값을 샘플링하여 구조의 다른 열 중 적절한 변수를 만드는 열을 결정합니다. 키 열 또는 고유 값이 많은 다른 열을 거부하고 결과와 상관 관계가 있을 것 같은 열을 제안합니다.  
  
     이 기능은 데이터 세트에 마이닝 모델을 작성하는 데 필요한 것보다 많은 열이 포함되어 있는 경우에 특히 편리합니다. **제안** 기능은 데이터 집합의 각 열과 예측 가능한 열 사이의 관계를 설명하는 0에서 1 사이의 점수를 계산합니다. 제안 기능은 이 점수를 기준으로 마이닝 모델에 대한 입력으로 사용할 열을 제안합니다. **제안** 기능을 사용하는 경우 제안된 열을 사용하거나, 필요에 맞게 선택 사항을 수정하거나, 제안을 무시할 수 있습니다.  
  
-   예측 가능한 열은 마이닝 모델에서 예측하려는 정보를 포함합니다. 여러 열을 예측 가능한 특성으로 선택할 수 있습니다. 클러스터링 모델은 예측 가능한 특성이 선택 사항이므로 예외입니다.  
  
     예측 가능한 열은 모델 유형에 따라 특정 데이터 형식이어야 할 수 있습니다. 예를 들어 선형 회귀 모델에는 예측 값인 숫자 열이 필요하고, Naïve Bayes 알고리즘에는 불연속 값이 필요(모든 입력도 불연속이어야 함)합니다.  
  
## <a name="specifying-column-content"></a>열 내용 지정  
 *열 내용*을 지정해야 하는 열도 있습니다. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터 마이닝에서는 각 데이터 열의 내용 유형 속성을 통해 알고리즘이 해당 열의 데이터를 처리하는 방식을 알 수 있습니다. 예를 들어 데이터에 Income 열이 있는 경우 내용 유형을 Continuous로 설정하여 열이 연속 숫자를 포함하도록 지정해야 합니다. 그러나 내용 유형을 Discretized로 설정하고 선택적으로 정확한 버킷 수를 지정하여 Income 열의 숫자를 버킷으로 그룹화하도록 지정할 수도 있습니다. 고객을 세 개의 연령 그룹으로 버킷팅하는 모델과 고객을 10개의 연령 그룹으로 버킷팅하는 또 다른 모델을 만들려는 경우와 같이 열을 다르게 처리하는 다른 모델을 만들 수 있습니다.  
  
## <a name="see-also"></a>관련 항목  
 [마이닝 구조 & #40; Analysis Services-데이터 마이닝 & #41;](../../analysis-services/data-mining/mining-structures-analysis-services-data-mining.md)   
 [관계형 마이닝 구조 만들기](../../analysis-services/data-mining/create-a-relational-mining-structure.md)   
 [마이닝 모델 속성](../../analysis-services/data-mining/mining-model-properties.md)   
 [마이닝 모델 열](../../analysis-services/data-mining/mining-model-columns.md)  
  
  
