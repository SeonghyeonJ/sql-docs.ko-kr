---
title: 보고서에 다중 값 매개 변수 추가 | Microsoft Docs
ms.date: 03/07/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-design
ms.topic: conceptual
ms.assetid: 12ad0e77-4c28-4bbb-ab11-473ae89ec9f1
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: ac257b63b3cd36cc789a842c87aff9d5186f1206
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/29/2020
ms.locfileid: "65575415"
---
# <a name="add-a-multi-value-parameter-to-a-report"></a>보고서에 다중 값 매개 변수 추가
  사용자가 매개 변수에 둘 이상의 값을 선택할 수 있는 보고서에 매개 변수를 추가할 수 있습니다.  
  
 여러 매개 변수 값을 보고서 URL 내의 보고서에 전달할 수 있습니다. 다중 값 매개 변수를 포함하는 URL 예제는 [URL에 보고서 매개 변수 전달](../../reporting-services/pass-a-report-parameter-within-a-url.md)을 참조하세요.  
  
 여러 매개 변수 값을 저장 프로시저에 전달하는 방법에 대한 자세한 내용은 mssqltips.com의 [SSRS 보고서에 다중 선택 매개 변수로 작업](https://go.microsoft.com/fwlink/?LinkId=321529) 을 참조하세요.  
  
## <a name="to-add-a-multi-value-parameter"></a>다중 값 매개 변수를 추가하려면  
  
1.  보고서 작성기에서 다중 값 매개 변수를 추가하려는 보고서를 엽니다.  
  
2.  보고서 데이터 세트를 마우스 오른쪽 단추로 클릭한 다음, **데이터 세트 속성**을 클릭합니다.  
  
3.  **쿼리** 상자에서 쿼리 텍스트를 편집하거나 쿼리 디자이너를 사용하여 필터를 추가하여 변수를 데이터 세트에 추가합니다. 자세한 내용은 [관계형 쿼리 디자이너에서 쿼리 빌드&#40;보고서 작성기 및 SSRS&#41;](../../reporting-services/report-data/build-a-query-in-the-relational-query-designer-report-builder-and-ssrs.md)를 참조하세요.  
  
    ```  
    WHERE  
      Production.ProductInventory.ProductID IN (@ProductID)  
    ```  
  
    > [!IMPORTANT]  
    > *  쿼리 텍스트는 쿼리 변수에 대한 DECLARE 문을 포함하지 않아야 합니다.  
    > *  쿼리 변수의 텍스트에는 위의 예와 같이 **IN** 연산자가 포함되어야 합니다.  
    > *  위와 같이 변수를 괄호로 묶어야 합니다. 그러지 않으면 보고서가 렌더링되지 않고 "스칼라 변수를 선언해야 합니다."라는 오류가 표시됩니다.  
  
    포함된 데이터 세트나 공유 데이터 세트에 대한 데이터 세트 매개 변수는 쿼리 변수에 대해 자동으로 만들어집니다. 데이터 세트 매개 변수에 대해 보고서 매개 변수가 자동으로 만들어집니다.  
  
4.  **보고서 데이터** 창에서 **매개 변수** 노드를 확장하고 데이터 세트 매개 변수에 대해 자동으로 생성된 보고서 매개 변수를 마우스 오른쪽 단추로 클릭한 다음, **매개 변수 속성**을 클릭합니다.  
  
5.  **일반** 탭에서 **다중 값 허용** 을 선택하여 매개 변수에 둘 이상의 값을 선택할 수 있도록 합니다.  
  
6.  (옵션) **사용 가능** 값 탭에서 사용자에게 표시할 사용 가능한 값 목록을 지정합니다.  
  
     사용 가능한 값 목록은 사용자가 매개 변수에 적합한 값만 선택할 수 있도록 제한합니다. 여러 값의 경우 목록 맨 위가 **모두 선택** 기능으로 시작되어 사용자가 클릭 한 번으로 모든 값을 선택하거나 선택 취소할 수 있습니다. 데이터 세트 쿼리에서 보고서 매개 변수에 사용 가능한 값을 가져오도록 선택하는 경우 동일한 보고서 매개 변수와 관련된 쿼리 변수를 포함하지 않는 데이터 세트를 선택해야 합니다.  
  
     자세한 내용은 [보고서 매개 변수의 사용 가능한 값 추가, 변경 또는 삭제&#40;보고서 작성기 및 SSRS&#41;](../../reporting-services/report-design/add-change-or-delete-available-values-for-a-report-parameter.md)를 참조하세요.  

## <a name="see-also"></a>참고 항목  
 [보고서에 연계 매개 변수 추가&#40;보고서 작성기 및 SSRS&#41;](../../reporting-services/report-design/add-cascading-parameters-to-a-report-report-builder-and-ssrs.md)   
 [보고서 매개 변수 추가, 변경 또는 삭제&#40;보고서 작성기 및 SSRS&#41;](../../reporting-services/report-design/add-change-or-delete-a-report-parameter-report-builder-and-ssrs.md)  
  
  
