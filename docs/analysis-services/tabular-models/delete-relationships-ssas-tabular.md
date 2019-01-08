---
title: Analysis Services 테이블 형식 모델에서 관계를 삭제 합니다. | Microsoft Docs
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 360de0e85048a491f3cfc750ac5288de73c65c95
ms.sourcegitcommit: 8a64c59c5d84150659a015e54f8937673cab87a0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/08/2018
ms.locfileid: "53072777"
---
# <a name="delete-relationships"></a>관계 삭제 
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  다이어그램 뷰의 모델 디자이너나 관계 관리 대화 상자를 사용하여 기존 관계를 삭제할 수 있습니다. 테이블 형식 모델에서 관계가 사용 되는 방법에 대 한 자세한 내용은 [관계](../../analysis-services/tabular-models/relationships-ssas-tabular.md)합니다.  
  
## <a name="considerations-for-deleting-relationships"></a>관계 삭제 시 고려 사항  
 관계를 삭제할지 여부를 결정할 때 다음 사항에 유의하십시오.  
  
-   관계 삭제를 실행 취소할 방법이 없습니다. 관계를 다시 만들 수 있지만 이 동작을 수행하려면 모델의 수식을 완전히 다시 계산해야 합니다. 따라서 관계를 삭제하기 전에 먼저 해당 관계가 수식에 사용되는지 항상 확인하십시오.  
  
-   두 테이블 사이의 관계를 삭제하면 해당 테이블을 참조하는 수식에서 오류가 발생할 수 있습니다.  
  
-   DAX(Data Analysis Expression) RELATED 함수는 테이블 간의 관계를 사용하여 다른 테이블에서 관련 값을 조회합니다. 관계가 삭제된 이후에는 다른 결과가 반환됩니다. RELATED(DAX) 함수에 대한 자세한 내용은 을 참조하십시오.  
  
-   피벗 테이블 및 수식 결과가 변경되는 것 이외에도 관계를 만들거나 삭제하면 통합 문서가 다시 계산되므로 다소 시간이 걸릴 수 있습니다.  
  
## <a name="delete-relationships"></a>관계 삭제  
  
#### <a name="to-delete-a-relationship-by-using-diagram-view"></a>다이어그램 뷰를 사용하여 관계를 삭제하려면  
  
1.  [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]에서 **모델** 메뉴를 클릭하고 **모델 뷰**를 가리킨 다음 **다이어그램 뷰**를 클릭합니다.  
  
2.  두 테이블 간의 관계 선을 마우스 오른쪽 단추로 클릭하고 **삭제**를 클릭합니다.  
  
#### <a name="to-delete-a-relationship-by-using-the-manage-relationships-dialog-box"></a>관계 관리 대화 상자를 사용하여 관계를 삭제하려면  
  
1.  [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]에서 **테이블** 메뉴를 클릭한 다음 **관계 관리**를 클릭합니다.  
  
2.  **관계 관리** 대화 상자의 목록에서 관계를 하나 이상 선택합니다.  
  
     관계를 여러 개 선택하려면 Ctrl 키를 누른 채 각 관계를 클릭합니다.  
  
3.  **관계 삭제**를 클릭합니다.  
  
4.  **관계 관리** 대화 상자에서 **닫기**를 클릭합니다.  
  
## <a name="see-also"></a>관련 항목  
 [관계](../../analysis-services/tabular-models/relationships-ssas-tabular.md)   
 [관계 만들기](../../analysis-services/tabular-models/create-a-relationship-between-two-tables-ssas-tabular.md)  
  
  
