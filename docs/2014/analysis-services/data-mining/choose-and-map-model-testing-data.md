---
title: 모델 테스트 데이터 선택 및 매핑 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- columns [data mining], mining accuracy charts
- Mining Accuracy Chart [Analysis Services], column mappings
- input column mapping [Analysis Services]
- mapping input columns [Analysis Services]
ms.assetid: be0d9f20-40c3-4dac-81da-281cfe724126
author: minewiskan
ms.author: owend
ms.openlocfilehash: 88e109a3ee51360edf85547a92254f6015168243
ms.sourcegitcommit: 2f166e139f637d6edfb5731510d632a13205eb25
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84524901"
---
# <a name="choose-and-map-model-testing-data"></a>모델 테스트 데이터 선택 및 매핑
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]에서 정확도 차트를 만들려면 모델을 테스트하는 데 사용할 데이터를 선택하고 데이터를 모델에 매핑해야 합니다.  
  
 마이닝 구조를 작성할 때 홀드아웃 데이터 집합을 만든 경우 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 에서는 기본적으로 마이닝 모델 테스트 데이터가 사용됩니다. 홀드아웃 테스트 집합은 열 이름 및 데이터 형식이 항상 모델과 일치하고 데이터 분포도 유사하므로 홀드아웃 테스트 집합을 만드는 것은 동일한 마이닝 구조를 기반으로 하는 모델을 테스트하는 가장 쉬운 방법입니다. 또한 디자이너에서는 입력 열과 모델 열 간의 관계를 자동으로 만듭니다.  
  
 사용자가 외부 데이터 원본을 지정할 수도 있습니다. 외부 데이터의 경우 다음과 같은 몇 가지 추가 요구 사항이 있습니다.  
  
-   외부 데이터 집합은 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]인스턴스에서 데이터 원본 뷰로 정의되어야 합니다.  
  
-   외부 데이터 집합에는 마이닝 모델의 예측 가능한 열에 매핑할 수 있는 열이 하나 이상 포함되어야 합니다. 일부 열은 무시할 수 있습니다.  
  
-   새 열을 추가하거나 다른 데이터 원본 뷰의 열을 매핑할 수 없습니다. 선택하는 데이터 원본 뷰에는 예측 쿼리에 필요한 모든 열이 포함되어야 합니다.  
  
-   외부 열 이름이 모델의 열 이름과 정확하게 일치하는 경우 디자이너에서는 외부 열 이름을 자동으로 매핑합니다. 매핑이 잘못된 경우 매핑을 변경 또는 삭제하거나 기존 열에 대한 새 매핑을 만들 수 있습니다.  
  
-   외부 데이터 원본을 사용하는 경우 필터를 적용하여 테스트 데이터를 관련된 사례 하위 집합으로 제한할 수 있습니다.  
  
-   홀드아웃 테스트 집합을 사용하더라도 필터로 인해 마이닝 구조에 연결된 테스트 데이터와 마이닝 모델 테스트 사례 간에 차이가 있을 수 있다는 것을 알고 있어야 합니다.  
  
 이 항목에서는 테스트 데이터를 선택하고 매핑하는 방법에 대해 설명합니다.  
  
 [마이닝 모델의 정확도 테스트에 사용할 입력 테이블 선택](#bkmk_SelectInputs)  
  
 [모델 열을 테스트 데이터의 열에 매핑](#bkmk_MapColumns)  
  
 [테스트 데이터의 열이 모델에 매핑되는 방식 변경](#bkmk_ChangeMappings)  
  
##  <a name="to-select-input-tables-to-test-the-accuracy-of-a-mining-model"></a><a name="bkmk_SelectInputs"></a> 마이닝 모델의 정확도 테스트에 사용할 입력 테이블을 선택하려면  
  
1.  [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]의 데이터 마이닝 디자이너에서 차트로 나타낼 모델을 포함하는 마이닝 구조를 두 번 클릭합니다.  
  
2.  **마이닝 정확도 차트** 탭을 선택합니다.  
  
3.  **마이닝 정확도 차트** 뷰의 **입력 선택** 탭에서 다음 옵션 중 하나를 선택합니다.  
  
     **마이닝 모델 테스트 사례 사용**  
  
     **마이닝 구조 테스트 사례 사용**  
  
     **다른 데이터 집합 지정**  
  
4.  **다른 데이터 집합 지정**을 선택한 경우 **필터 편집기 열기** 를 클릭하여 입력 데이터 집합에 대한 필터 조건을 만들 수 있습니다. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
5.  지정한 테스트 데이터를 사용하여 차트를 자동으로 작성하려면 **리프트 차트** 탭 또는 **분류표** 탭을 클릭합니다.  
  
##  <a name="to-map-model-columns-to-the-columns-in-the-testing-data"></a><a name="bkmk_MapColumns"></a> 모델 열을 테스트 데이터의 열에 매핑하려면  
  
1.  데이터 마이닝 디자이너에서 차트로 나타낼 모델을 포함하는 마이닝 구조를 두 번 클릭하여 해당 구조 및 모델을 엽니다.  
  
2.  **마이닝 정확도 차트** 탭을 선택한 다음 **입력 선택** 탭을 선택합니다.  
  
3.  **입력 선택** 탭의 **정확도 차트에 사용할 데이터 집합을 선택하십시오.** 에서 **다른 데이터 집합 지정**을 선택합니다.  
  
4.  찾아보기 단추 **(...)** 를 클릭 하 여 대화 상자를 열고 외부 데이터 집합의 정의를 작성 합니다.  
  
5.  **마이닝 구조 선택** 대화 상자에서 작업할 모델이 포함된 마이닝 구조를 선택한 다음 **확인**을 클릭합니다.  
  
6.  **마이닝 정확도 차트** 탭의 **입력 테이블 선택** 테이블에서 **사례 테이블 선택** 을 클릭하여 **테이블 선택** 대화 상자를 엽니다.  
  
7.  **테이블 선택** 대화 상자의 **데이터 원본** 목록에서 데이터 원본을 선택합니다. 모델 정확도를 확인하기 위해 예측 쿼리에 사용할 데이터가 포함된 테이블을 선택합니다.  
  
8.  **테이블/뷰 이름** 상자에서 모델 테스트에 사용할 데이터가 포함된 테이블을 선택합니다.  
  
9. 필요한 경우 매핑을 편집합니다. 마이닝 구조의 열이 입력 테이블에 있는 동일한 이름의 열에 자동으로 매핑됩니다. 매핑을 수동으로 만들려면 **입력 테이블 선택** 테이블의 열을 클릭한 다음 **마이닝 구조** 테이블의 해당 열로 끌어 옵니다. 매핑을 삭제하려면 **마이닝 구조** 테이블의 열을 **입력 테이블 선택** 테이블의 매핑된 열에 연결하는 선을 클릭한 다음 Delete 키를 누릅니다.  
  
10. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
##  <a name="to-modify-the-way-input-data-is-mapped-to-the-model"></a><a name="bkmk_ChangeMappings"></a>입력 데이터가 모델에 매핑되는 방식을 수정 하려면  
  
1.  데이터 마이닝 디자이너에서 차트로 나타낼 모델을 포함하는 구조를 두 번 클릭합니다.  
  
2.  **마이닝 정확도 차트** 탭을 선택합니다.  
  
3.  **입력 선택** 탭을 클릭합니다.  
  
4.  **정확도 차트에 사용할 데이터 집합을 선택**하십시오 .에서 **다른 데이터 집합 지정**옵션을 선택 합니다.  
  
5.  찾아보기 단추 **(...)** 를 클릭 하 여 대화 상자를 열고 외부 데이터 원본의 정의를 작성 합니다.  
  
6.  **열 매핑 지정** 대화 상자에서 **사례 테이블 선택**을 클릭합니다.  
  
7.  테이블 선택 대화 상자의 목록에서 데이터 원본 뷰를 선택하고 사례 데이터를 포함하는 테이블을 선택합니다. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
8.  필요한 테이블을 사용할 수 없으면 대화 상자를 닫고 해당 테이블을 포함하는 새 데이터 원본 뷰를 만듭니다. 데이터 원본 뷰를 만드는 방법은 [데이터 원본 뷰 정의&#40;Analysis Services&#41;](../multidimensional-models/defining-a-data-source-view-analysis-services.md)를 참조하세요.  
  
9. 마이닝 모델에 중첩 테이블이 포함되어 있으면 **중첩 테이블 선택**을 클릭하고 데이터 원본 뷰의 테이블 목록에서 중첩 테이블을 선택합니다. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
10. 수정할 매핑의 조인 선을 선택하고 **연결 수정**을 선택합니다.  
  
     **매핑 수정** 대화 상자가 열립니다. 이 대화 상자의 테이블에서 **마이닝 구조 열** 에는 선택한 마이닝 구조에 포함된 각 열이 나열되고 **테이블 열** 에는 마이닝 구조의 열에 매핑되는 입력 테이블의 열이 나열됩니다.  
  
11. **테이블 열**아래에서 관계를 수정할 **마이닝 구조 열** 아래의 행에 해당하는 행을 선택합니다. 목록에서 새 열을 선택하거나 목록에서 빈 항목을 선택하여 열을 삭제합니다.  
  
12. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
     **열 매핑 지정** 대화 상자에 새 열 매핑이 표시됩니다. 열 사이의 선을 선택하고 Delete 키를 눌러 매핑을 제거할 수 있습니다. **마이닝 구조** 테이블의 열을 선택하고 **입력 테이블 선택** 테이블의 해당 열로 끌어 새 연결을 만들 수 있습니다.  
  
## <a name="see-also"></a>참고 항목  
 [테스트 및 유효성 검사 태스크 및 방법&#40;데이터 마이닝&#41;](testing-and-validation-tasks-and-how-tos-data-mining.md)  
  
  
