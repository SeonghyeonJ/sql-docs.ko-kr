---
title: '9 단원: 큐브 뷰 만들기 | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 55b0f0d0-1cdf-4876-9c3d-d0c848be3f5d
author: minewiskan
ms.author: owend
ms.openlocfilehash: 20601a1ece7707e8f798907f21ee5ee7110fe2fe
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84542225"
---
# <a name="lesson-9-create-perspectives"></a>9단원: 큐브 뷰 만들기
  이 단원에서는 Internet Sales 큐브 뷰를 만듭니다. 큐브 뷰는 비즈니스 또는 애플리케이션 중심의 관점에서 파악할 수 있게 해 주는 보기 가능한 모델 하위 집합을 정의합니다. 사용자가 큐브 뷰를 사용하여 모델에 연결하는 경우 해당 모델 개체(테이블, 열, 측정값, 계층 및 KPI)만 해당 큐브 뷰에 정의되어 있는 필드로 볼 수 있습니다.  
  
 이 단원에서 만드는 Internet Sales 큐브 뷰에는 Customer 테이블 개체가 제외됩니다. 뷰에서 특정 개체를 제외하는 큐브 뷰를 만들면 해당 개체가 모델에는 그대로 있지만 보고 클라이언트 필드 목록에서는 보이지 않습니다. 큐브 뷰에 포함되어 있거나 포함되어 있지 않은 계산 열 및 측정값을 계속해서 제외된 개체 데이터에서 계산할 수 있습니다.  
  
 이 단원의 목표는 큐브 뷰를 만드는 방법을 설명하고 테이블 형식 모델 제작 도구를 파악하도록 돕는 데 있습니다. 나중에 추가 테이블을 포함하도록 이 모델을 확장할 경우 큐브 뷰를 추가로 만들어 모델에 대한 다양한 뷰포인트(예: Inventory 및 Sales Force)를 정의할 수 있습니다.  
  
 자세한 내용은 [큐브 뷰&#40;SSAS 테이블 형식&#41;](tabular-models/perspectives-ssas-tabular.md)를 참조하세요.  
  
 이 단원에 소요되는 예상 시간: **5분**  
  
## <a name="prerequisites"></a>사전 요구 사항  
 이 항목은 테이블 형식 모델링 자습서에 포함되며 순서대로 완료해야 합니다. 이 단원의 태스크를 수행하려면 이전 단원인 [8단원: 핵심 성과 지표 만들기](lesson-7-create-key-performance-indicators.md)를 완료해야 합니다.  
  
## <a name="create-perspectives"></a>큐브 뷰 만들기  
  
#### <a name="to-create-an-internet-sales-perspective"></a>Internet Sales 큐브 뷰를 만들려면  
  
1.  모델 디자이너에서 **모델** 메뉴를 클릭 한 다음 **큐브 뷰**를 클릭 합니다.  
  
2.  **큐브 뷰** 대화 상자에서 **새 큐브 뷰**를 클릭합니다.  
  
3.  큐브 뷰의 이름을 바꾸려면 **새 큐브 뷰 1** 열 머리글을 두 번 클릭 한 다음를 입력 `Internet Sales` 합니다.  
  
4.  **필드**에서 **Date**, **Geography**, **Product**, **product Category**, **product 하위 범주**및 테이블을 선택 합니다 `Internet Sales` .  
  
     이 큐브 뷰에서 Customer 테이블과 이 테이블의 모든 열을 제외했습니다. 나중에 12단원에서 Excel에서 분석 기능을 사용하여 이 큐브 뷰를 테스트합니다. Excel 피벗 테이블 필드 목록에는 Customer 테이블을 제외한 각 테이블이 포함됩니다.  
  
5.  선택 항목을 확인하여 **Customer** 테이블이 선택되어 있지 않은지 확인한 다음 **확인**을 클릭합니다.  
  
## <a name="next-steps"></a>다음 단계  
 이 자습서를 계속하려면 다음 단원인 [10단원: 계층 만들기](lesson-9-create-hierarchies.md)로 이동하세요.  
  
  
