---
title: 보고서 매개 변수의 사용 가능한 값 추가, 변경 또는 삭제 | Microsoft Docs
description: 사용자에게 표시할 사용 가능한 값 목록을 지정하여 보고서 작성기에서 매개 변수에 대해 수행할 수 있는 선택 목록을 사용자 지정합니다.
ms.date: 03/07/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-design
ms.topic: conceptual
f1_keywords:
- sql13.rtp.rptdesigner.reportparameters.availablevalues.f1
- "10455"
- "10071"
ms.assetid: 0e03264c-523f-4c59-b71b-ceef600f75f6
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: b9d826682f2bcb742ab4ba7ae9e2b6fba33600c0
ms.sourcegitcommit: 02b22274da4a103760a376c4ddf26c4829018454
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/11/2020
ms.locfileid: "84681332"
---
# <a name="add-change-or-delete-available-values-for-a-report-parameter"></a>보고서 매개 변수의 사용 가능한 값 추가, 변경 또는 삭제
  보고서 매개 변수를 만든 다음에는 사용자에게 표시할 사용 가능한 값 목록을 지정할 수 있습니다. 사용 가능한 값 목록은 사용자가 매개 변수에 적합한 값만 선택할 수 있도록 제한합니다.  
  
 사용 가능한 값은 보고서를 실행할 때 도구 모음의 보고서 매개 변수 옆에 있는 드롭다운 목록에 나타납니다. 보고서 매개 변수는 단일 값이나 여러 값을 나타낼 수 있습니다. 여러 값의 경우 목록 맨 위가 **모두 선택** 기능으로 시작되어 사용자가 클릭 한 번으로 모든 값을 선택하거나 선택 취소할 수 있습니다.  
  
 정적 값 목록 또는 보고서 데이터 세트에서 가져온 목록을 제공할 수 있습니다. 필요에 따라 레이블 필드를 지정하여 값에 대한 이름을 제공할 수 있습니다. 예를 들어 `ProductID` 필드를 기반으로 하는 매개 변수의 경우 매개 변수 레이블에 `ProductName` 필드를 표시할 수 있습니다. 보고서를 실행할 때 사용자는 제품 이름에서 선택할 수 있지만 실제 선택된 값은 해당 `ProductID`입니다.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
 보고서를 게시한 후에는 보고서 서버에서 매개 변수 속성 값을 설정하여 보고서 제작 도구에서 보고서에 정의한 사용 가능한 값을 재정의할 수 있습니다. 자세한 내용은 [보고서 매개 변수&#40;보고서 작성기 및 보고서 디자이너&#41;](../../reporting-services/report-design/report-parameters-report-builder-and-report-designer.md)에 대해 자세히 알아봅니다.  
  
### <a name="to-add-or-change-the-available-values-for-a-report-parameter"></a>보고서 매개 변수에 대한 사용 가능한 값을 추가 또는 변경하려면  
  
1.  보고서 데이터 창에서 매개 변수 노드를 확장합니다. 매개 변수를 마우스 오른쪽 단추로 클릭하고 **매개 변수 속성**을 클릭합니다. **보고서 매개 변수 속성** 대화 상자가 열립니다.  
  
    > [!NOTE]  
    >  보고서 데이터 창이 표시되지 않는 경우 **보기** , **보고서 데이터**를 차례로 클릭합니다.  
  
2.  **사용 가능한 값**을 클릭합니다. 사용 가능한 값 옵션을 선택합니다.  
  
    -   **값 지정** 을 클릭하여 직접 값 목록과 필요에 따라 값에 대한 이름(레이블)을 제공합니다.  
  
         **추가** 를 클릭한 다음 **값** 입력란에 값을 입력하고 필요에 따라 **레이블** 입력란에 레이블을 입력합니다. 레이블을 제공하지 않으면 값이 사용됩니다. 값에 대한 식을 작성할 수 있습니다. 데이터 형식은 매개 변수의 데이터 형식과 일치해야 합니다. 필드 이름은 매개 변수의 식에 사용할 수 없습니다. 예를 보려면 [일반적으로 사용되는 필터&#40;보고서 작성기 및 SSRS&#41;](../../reporting-services/report-design/commonly-used-filters-report-builder-and-ssrs.md)를 참조하세요.  
  
         제공할 값 개수만큼 이 단계를 반복합니다. 이 목록에 표시되는 항목의 순서에 따라 드롭다운 목록에 표시되는 항목의 순서가 결정됩니다. 목록에서 항목의 순서를 변경하려면 **값** 또는 **레이블** 입력란을 클릭하여 항목을 선택한 다음 위쪽 및 아래쪽 화살표 단추를 사용하여 항목을 목록의 위나 아래로 이동합니다.  
  
    -   **쿼리에서 값 가져오기**를 클릭하여 이 매개 변수에 대한 값과 필요에 따라 이름을 검색하는 기존 데이터 세트의 이름을 제공합니다.  
  
        > [!IMPORTANT]  
        >  동일한 데이터 세트에 보고서 매개 변수에 대한 해당 쿼리 매개 변수가 있는 경우 보고서를 실행하려고 하면 보고서에서 오류 메시지를 표시합니다. 다른 데이터 세트를 사용하여 값을 검색하면 이 오류를 해결할 수 있습니다.  
  
         **데이터 세트**에서 데이터 세트의 이름을 선택합니다.  
  
         **값 필드**에서 매개 변수 값을 제공하는 필드의 이름을 선택합니다.  
  
         **레이블 필드**에서 매개 변수에 대한 이름을 제공하는 필드의 이름을 선택합니다. 이름에 대한 개별 필드가 없으면 **값** 필드에 대해 선택한 동일한 필드를 선택합니다.  
  
3.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
     보고서를 미리 볼 때 매개 변수에 대한 사용 가능한 값의 드롭다운 목록이 나타납니다.  
  
### <a name="to-remove-the-available-values-for-a-report-parameter"></a>보고서 매개 변수에 대한 사용 가능한 값을 제거하려면  
  
1.  보고서 데이터 창에서 매개 변수 노드를 확장합니다. 매개 변수를 마우스 오른쪽 단추로 클릭하고 **매개 변수 속성**을 클릭합니다. **보고서 매개 변수** 대화 상자가 열립니다.  
  
2.  **사용 가능한 값**을 클릭합니다.  
  
3.  **다음 옵션 중 하나 선택**에서 **없음**을 클릭합니다.  
  
4.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
     보고서를 미리 볼 때 매개 변수에 대한 사용 가능한 값의 드롭다운 목록이 더 이상 나타나지 않습니다.  
  
## <a name="see-also"></a>참고 항목  
 [보고서 매개 변수의 순서 변경&#40;보고서 작성기 및 SSRS&#41;](../../reporting-services/report-design/change-the-order-of-a-report-parameter-report-builder-and-ssrs.md)   
 [보고서 매개 변수 추가, 변경 또는 삭제&#40;보고서 작성기 및 SSRS&#41;](../../reporting-services/report-design/add-change-or-delete-a-report-parameter-report-builder-and-ssrs.md)   
 [보고서에 연계 매개 변수 추가&#40;보고서 작성기 및 SSRS&#41;](../../reporting-services/report-design/add-cascading-parameters-to-a-report-report-builder-and-ssrs.md)   
 [보고서 매개 변수의 기본값 추가, 변경 또는 삭제&#40;보고서 작성기 및 SSRS&#41;](../../reporting-services/report-design/add-change-or-delete-default-values-for-a-report-parameter.md)   
 [매개 변수 컬렉션 참조&#40;보고서 작성기 및 SSRS&#41;](../../reporting-services/report-design/built-in-collections-parameters-collection-references-report-builder.md)   
 [자습서: 보고서에 매개 변수 추가&#40;보고서 작성기&#41;](../../reporting-services/tutorial-add-a-parameter-to-your-report-report-builder.md)   
 [식&#40;보고서 작성기 및 SSRS&#41;](../../reporting-services/report-design/expressions-report-builder-and-ssrs.md)  
  
  
