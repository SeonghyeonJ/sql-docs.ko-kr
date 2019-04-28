---
title: 마이닝 모델의 복사본 | Microsoft Docs
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: data-mining
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 7c5479a43a07a6398ff45635828a2a9c88b7cb11
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62679468"
---
# <a name="make-a-copy-of-a-mining-model"></a>마이닝 모델 복사본 만들기
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  마이닝 모델의 복사본을 만들면 동일한 데이터를 기반으로 여러 마이닝 모델을 빠르게 만들 때 유용합니다. 모델을 복사한 후 매개 변수를 변경하거나 필터를 추가하여 새 복사본을 편집할 수도 있습니다.  
  
 예를 들어 구매 테이블에 연결된 Customers 테이블이 있는 경우 나이 또는 지역과 같은 특성을 기준으로 필터링하여 각 고객 인구 통계에 대한 별도의 마이닝 모델을 생성하도록 복사본을 만들 수 있습니다.  
  
 다른 프로그램에서 사용할 수 있도록 그래픽 표현 또는 모델 패턴과 같은 모델 내용을 클립보드에 복사하는 방법에 대한 자세한 내용은 [마이닝 모델의 뷰 복사](../../analysis-services/data-mining/copy-a-view-of-a-mining-model.md)를 참조하세요.  
  
### <a name="to-create-a-related-mining-model"></a>관련 마이닝 모델을 만들려면  
  
1.  [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]의 솔루션 탐색기에서 마이닝 모델이 포함된 마이닝 구조를 클릭합니다.  
  
2.  **마이닝 모델** 탭을 클릭합니다.  
  
3.  모델을 선택하고 마우스 오른쪽 단추를 클릭하여 바로 가기 메뉴를 엽니다.  
  
     -또는-  
  
     모델을 선택합니다. **마이닝 모델** 메뉴에서 **새 마이닝 모델**을 선택합니다.  
  
4.  새 마이닝 모델의 이름을 입력하고 알고리즘을 선택합니다. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-edit-the-filter-on-the-copied-mining-model"></a>복사된 마이닝 모델에서 필터를 편집하려면  
  
1.  마이닝 모델을 선택합니다.  
  
2.  에 **속성** 창에 대 한 입력란을 클릭 합니다 **필터** 속성 및 빌드를 클릭 하 **(...)**  단추입니다.  
  
3.  필터 조건을 변경합니다.  
  
     필터 편집기 대화 상자를 사용하는 방법에 대한 자세한 내용은 [마이닝 모델에 필터 적용](../../analysis-services/data-mining/apply-a-filter-to-a-mining-model.md)을 참조하세요.  
  
4.  **속성** 창의 **AlgorithmParameters** 입력란에서 **알고리즘 매개 변수 설정**을 클릭하고 필요한 경우 알고리즘 매개 변수를 변경합니다.  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a>관련 항목  
 [마이닝 모델에 대한 필터&#40;Analysis Services - 데이터 마이닝&#41;](../../analysis-services/data-mining/filters-for-mining-models-analysis-services-data-mining.md)   
 [마이닝 모델 태스크 및 방법](../../analysis-services/data-mining/mining-model-tasks-and-how-tos.md)   
 [마이닝 모델에서 필터 삭제](../../analysis-services/data-mining/delete-a-filter-from-a-mining-model.md)  
  
  
