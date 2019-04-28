---
title: 데이터 마이닝 개체 처리 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
helpviewer_keywords:
- processing objects [Analysis Services]
- mining structures [Analysis Services]
- process [Analysis Services]
- mining structures [Analysis Services], creating
- mining structures [Analysis Services], how-to topics
- mining structures [Analysis Services], processing
ms.assetid: 0f6993c0-0917-4935-82f9-7b8a8a7cc627
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: aa4a536a142ae63dd2b028d983f083609ea2e717
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62732935"
---
# <a name="processing-data-mining-objects"></a>데이터 마이닝 개체 처리
  데이터 마이닝 개체는 처리되기 전까지는 단순히 빈 컨테이너입니다. 데이터 마이닝 모델을*처리* 하는 작업을 *학습*이라고도 합니다.  
  
 **마이닝 구조 처리:** 마이닝 구조 열 바인딩 및 사용법 메타 데이터에 의해 정의 된 대로 외부 데이터 원본의 데이터를 가져옵니다 하 고 데이터를 읽습니다. 이 데이터 전체를 읽은 다음 분석하여 다양한 통계를 추출합니다. Analysis Services에서는 데이터 마이닝 알고리즘으로 분석하는 데 적합한 데이터의 압축된 표현을 로컬 캐시에 저장합니다. 이 캐시는 보관하거나 모델 처리 후 제거할 수 있습니다. 기본적으로 캐시는 저장됩니다. 자세한 내용은 [Process a Mining Structure](process-a-mining-structure.md)를 참조하세요.  
  
 **마이닝 모델 처리:** 마이닝 모델은 처리 될 때까지 정의 들어 있는 빈 합니다. 마이닝 모델을 처리하려면 먼저 해당 모델의 기반이 되는 마이닝 구조를 처리해야 합니다. 마이닝 모델은 마이닝 구조 캐시에서 데이터를 가져오고, 모델에 필터가 만들어진 경우 이를 적용한 다음, 알고리즘을 통해 데이터 집합을 전달하여 패턴을 검색합니다. 모델이 처리된 후 모델에는 데이터 자체가 아니라 처리 결과만 저장됩니다. 자세한 내용은 [마이닝 모델 처리](process-a-mining-model.md)를 참조하세요.  
  
 다음 다이어그램에서는 마이닝 구조가 처리될 때와 마이닝 모델이 처리될 때의 데이터 흐름을 보여 줍니다.  
  
 ![데이터 처리: 원본 구조에 모델](../media/dmcon-modelarch.gif "데이터 처리: 원본 구조에 모델")  
  
## <a name="viewing-the-results-of-processing"></a>처리 결과 보기  
 마이닝 구조가 처리된 후 해당 마이닝 구조에는 통계 분석에 사용할 데이터의 압축된 표현이 포함됩니다. 캐시가 지워지지 않은 경우 다음 방법으로 이 캐시의 데이터에 액세스할 수 있습니다.  
  
-   모델에 대한 DMX(Data Mining Extensions) 쿼리를 만들고 구조로 드릴스루합니다. 자세한 내용은 [SELECT FROM &#60;model&#62;.CASES&#40;DMX&#41;](/sql/dmx/select-from-model-content-dmx)를 참조하세요.  
  
-   해당 구조를 기반으로 하는 모델을 찾아보고 사용자 인터페이스의 옵션 중 하나를 사용하여 구조 사례로 드릴스루합니다. 자세한 내용은 [데이터 마이닝 모델 뷰어](data-mining-model-viewers.md)또는 [마이닝 모델에서 사례 데이터로 드릴스루](drill-through-to-case-data-from-a-mining-model.md)를 참조하세요.  
  
-   구조 사례에 대한 DMX 쿼리를 만듭니다. 자세한 내용은 [SELECT FROM &#60;structure&#62;.CASES](/sql/dmx/select-from-structure-cases)를 참조하세요.  
  
 마이닝 모델이 처리된 후 해당 마이닝 모델에는 분석에서 얻은 패턴과 모델 결과에서 캐시된 학습 데이터로의 매핑만 포함됩니다. *모델 콘텐츠*라는 모델 결과를 찾아보거나 쿼리할 수도 있고, 모델 결과가 캐시된 경우 모델 및 구조 사례를 쿼리할 수도 있습니다.  
  
 각 마이닝 모델의 모델 콘텐츠는 마이닝 모델을 만드는 데 사용된 알고리즘에 따라 달라집니다. 예를 들어 한 모델은 클러스터링 모델이고 다른 모델은 의사 결정 트리 모델인 경우 모델이 동일한 데이터를 사용하더라도 모델 콘텐츠는 매우 달라집니다. 자세한 내용은 [마이닝 모델 콘텐츠&#40;Analysis Services - 데이터 마이닝&#41;](mining-model-content-analysis-services-data-mining.md)를 참조하세요.  
  
## <a name="processing-requirements"></a>처리 요구 사항  
 처리 요구 사항은 마이닝 모델이 전적으로 관계형 데이터를 기반으로 하는지 아니면 다차원 데이터 원본을 기반으로 하는지 여부에 따라 달라질 수 있습니다.  
  
 관계형 데이터 원본을 처리하기 위해서는 학습 데이터를 만들고 해당 데이터에 대해 마이닝 알고리즘을 실행하기만 하면 됩니다. 그러나 차원 및 측정값과 같은 OLAP 개체를 기반으로 하는 마이닝 모델의 경우에는 기본 데이터가 처리된 상태에 있어야 합니다. 이를 위해 다차원 개체를 처리하여 마이닝 모델을 채워야 할 수 있습니다.  
  
 자세한 내용은 [처리 요구 사항 및 고려 사항&#40;데이터 마이닝&#41;](processing-requirements-and-considerations-data-mining.md)을 참조하세요.  
  
## <a name="see-also"></a>관련 항목  
 [드릴스루 쿼리&#40;데이터 마이닝&#41;](drillthrough-queries-data-mining.md)   
 [마이닝 구조 & #40; Analysis Services-데이터 마이닝 & #41;](mining-structures-analysis-services-data-mining.md)   
 [마이닝 모델&#40;Analysis Services - 데이터 마이닝&#41;](mining-models-analysis-services-data-mining.md)   
 [논리적 아키텍처&#40;Analysis Services - 데이터 마이닝&#41;](logical-architecture-analysis-services-data-mining.md)  
  
  
