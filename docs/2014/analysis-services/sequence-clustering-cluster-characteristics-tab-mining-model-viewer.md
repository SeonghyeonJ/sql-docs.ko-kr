---
title: 시퀀스 클러스터링 클러스터 특징 탭 (마이닝 모델 뷰어) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.miningmodeleditor.sequenceclustering.characteristics.f1
ms.assetid: 3a9e8a0c-7d03-47cc-8625-e68d73a8c947
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: a3a9121129ab0f7e4e185e35418132a4f1aa663f
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66069173"
---
# <a name="sequence-clustering-cluster-characteristics-tab-mining-model-viewer"></a>시퀀스 클러스터링 클러스터 특징 탭(마이닝 모델 뷰어)
  **Microsoft 시퀀스 클러스터링 뷰어** 의 **클러스터 특징** 탭에서는 시퀀스 클러스터를 정의하는 특징의 세부 목록을 제공합니다. 이러한 특징에는 간단한 특성-값 쌍뿐만 아니라 상태 간 전환도 포함될 수 있습니다.  
  
 이 시퀀스 클러스터링 모델 뷰를 사용하여 클러스터 콘텐츠로 드릴다운하고 클러스터의 특징을 나타내는 시퀀스를 확인할 수 있습니다.  
  
 **참조 항목:** [Microsoft 시퀀스 클러스터링 알고리즘](data-mining/microsoft-sequence-clustering-algorithm.md), [Microsoft 시퀀스 클러스터 뷰어를 사용 하 여 모델 찾아보기](data-mining/browse-a-model-using-the-microsoft-sequence-cluster-viewer.md)  
  
## <a name="options"></a>변수  
 **뷰어 내용 새로 고침**  
 뷰어에서 마이닝 모델을 다시 로드합니다.  
  
 **마이닝 모델**  
 현재 마이닝 구조에서 볼 마이닝 모델을 선택합니다. 관련 뷰어에서 마이닝 모델이 열립니다.  
  
 **Viewer**  
 선택한 마이닝 모델을 탐색하는 데 사용할 뷰어를 선택합니다. 사용자 지정 뷰어 또는 **Microsoft 일반 콘텐츠 트리 뷰어**를 사용할 수 있습니다. 또한 사용 가능한 경우 플러그 인 뷰어를 사용할 수 있습니다.  
  
 **Cluster**  
 확인할 클러스터를 선택합니다.  
  
 **에 대 한 특성 \<클러스터 >**  
 이 표에서는 확률 기준으로 정렬된 현재 클러스터에 할당된 시퀀스의 목록을 제공합니다. 시퀀스는 기본적으로 하나의 특성-값 쌍이고 그 뒤에 추가 특성-값 쌍이 하나 이상 올 수 있습니다. 시퀀스와 해당 확률의 조합은 각 클러스터의 결정적인 특징입니다.  
  
 예를 들어 시장 바구니 분석 기반의 시퀀스 클러스터링 모델에서 한 클러스터의 최상위 특징은 판매 품목을 선택한 다음 더 이상 구매하지 않고 거래를 끝내는 고객일 수 있습니다. 서버 오류를 분석하려는 시퀀스 클러스터링 모델에서 클러스터의 기본 특징은 너무 자주 발생하는 일련의 오류 이벤트일 수 있습니다.  
  
|값|Description|  
|-----------|-----------------|  
|**변수**|이 열은 특징이 값인지 아니면 전환인지를 나타냅니다.<br /><br /> 특징이 값인 경우 합니다 **변수** 열 특성 이름을 포함 합니다.<br /><br /> 특징이 상태 전환을 나타내는 경우는 **변수** 열에 "transitions 라는" 텍스트가 포함 됩니다.|  
|**값**|이 열의 값은 특징이 간단한 특성-값 쌍인지, 아니면 항목이나 이벤트의 일반 시퀀스를 나타내는 상태 전환인지에 따라 달라집니다.<br /><br /> 특징이 값인 경우 합니다 **값** 열 상태를 포함 합니다.<br /><br /> 특징이 상태 전환을 나타내는 경우는 **값** 열 상태 전환에 대 한 설명을 포함 합니다.|  
|**확률**|이 열에는 이 특징(간단한 특성-값 쌍 또는 상태의 조합)이 현재 클러스터의 멤버일 상대적인 확률을 나타내는 막대가 표시됩니다.<br /><br /> 마우스를 막대 위로 이동하여 특징의 빈도 값을 표시할 수 있습니다.|  
  
## <a name="see-also"></a>관련 항목  
 [데이터 마이닝 알고리즘&#40;Analysis Services - 데이터 마이닝&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md)   
 [마이닝 모델 뷰어&#40;데이터 마이닝 모델 디자이너&#41;](mining-model-viewers-data-mining-model-designer.md)   
 [데이터 마이닝 모델 뷰어](data-mining/data-mining-model-viewers.md)  
  
  
