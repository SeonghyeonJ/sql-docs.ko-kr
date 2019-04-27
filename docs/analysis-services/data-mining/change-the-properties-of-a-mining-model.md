---
title: 마이닝 모델의 속성 변경 | Microsoft Docs
ms.date: 05/01/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: data-mining
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: a3650b284e8817c2b7f8aee6a0beca71c275d6a1
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62670383"
---
# <a name="change-the-properties-of-a-mining-model"></a>마이닝 모델의 속성 변경
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  일부 마이닝 모델 속성은 모델 전체에 적용되고 다른 모델 속성은 개별 열에 적용됩니다. 모델 전체에 적용되는 속성의 예로는 사례 데이터를 쿼리에 사용할지 여부를 지정하는 **Drillthrough** 속성과 **Description** 속성이 있습니다. 열에 적용되는 속성으로는 모델 내에서 열의 데이터가 사용되는 방식을 제어하는 **Usage** 및 **ModelingFlags**가 있습니다.  
  
 다음 모델 속성의 경우 식을 만들거나 복잡한 모델 속성을 구성하는 데 사용할 수 있는 고급 편집기가 제공됩니다.  
  
-   **필터** 속성: 열립니다는 [데이터 집합 필터 또는 모델 필터 대화 상자](http://msdn.microsoft.com/library/a9602174-b7e2-4e16-8ded-dfd8eb9264d7)합니다.  
  
-   **AlgorithmParameters** 속성: 열립니다는 [알고리즘 매개 변수 대화 상자 &#40;마이닝 모델 뷰&#41;](http://msdn.microsoft.com/library/57f9f6f8-8ca4-4a6e-8f18-85f0571b7060)합니다.  
  
 마이닝 모델의 속성을 설정하는 방법은 [마이닝 모델 열](../../analysis-services/data-mining/mining-model-columns.md)을 참조하세요.  
  
### <a name="to-change-the-properties-of-a-mining-model"></a>마이닝 모델의 속성을 변경하려면  
  
1.  데이터 마이닝 디자이너의 **마이닝 모델** 탭에서 마이닝 모델의 이름이 포함된 열 머리글 또는 마이닝 알고리즘의 이름이 포함된 표의 행을 마우스 오른쪽 단추로 클릭한 다음 **속성**을 선택합니다.  
  
2.  화면 오른쪽에 있는 **속성** 창에서 변경할 속성에 해당하는 값을 강조 표시하고 새 값을 입력합니다.  
  
     디자이너에서 다른 요소를 선택하면 새 값이 적용됩니다.  
  
### <a name="to-change-the-properties-of-a-mining-model-column"></a>마이닝 모델 열의 속성을 변경하려면  
  
1.  데이터 마이닝 디자이너의 **마이닝 모델** 탭에서 마이닝 구조 열과 마이닝 모델이 교차하는 지점에 있는 표의 셀을 마우스 오른쪽 단추로 클릭한 다음 **속성**을 선택합니다.  
  
2.  화면 오른쪽에 있는 **속성** 창에서 변경할 속성에 해당하는 값을 강조 표시하고 새 값을 입력합니다.  
  
    > [!NOTE]  
    >  열 사용법이 **Ignore**로 설정되어 있을 경우 해당 열의 **속성** 창은 비어 있습니다.  
  
     디자이너에서 다른 요소를 선택하면 새 값이 적용됩니다.  
  
## <a name="see-also"></a>관련 항목  
 [마이닝 모델 태스크 및 방법](../../analysis-services/data-mining/mining-model-tasks-and-how-tos.md)  
  
  
