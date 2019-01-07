---
title: 보고서 데이터 창에서 필드 추가, 편집, 새로 고침(보고서 작성기 및 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
ms.assetid: 2e36f0fe-8100-4513-b169-14d611646f81
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 6ffceeae13889bc616be63fbc23838dd75029c4d
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48102983"
---
# <a name="add-edit-refresh-fields-in-the-report-data-pane-report-builder-and-ssrs"></a>보고서 데이터 창에서 필드 추가, 편집, 새로 고침(보고서 작성기 및 SSRS)
  데이터 세트 필드는 외부 데이터 원본에서 데이터 세트 쿼리를 실행할 때 반환되는 데이터를 나타내는 기본 제공 필드 이름 컬렉션입니다.  
  
 포함된 데이터 세트의 경우 데이터 세트 필드는 쿼리 작성을 마치고 쿼리 디자이너 창을 닫은 후 만들어지는 필드와 사용자가 만드는 계산 필드입니다.  
  
 공유 데이터 세트의 경우 데이터 세트 필드는 보고서에 해당 데이터 세트를 추가했을 때 공유 데이터 세트 정의에 있는 필드입니다. 보고서 서버의 공유 데이터 세트 쿼리가 보고서를 실행할 때 항상 사용되지만 보고서의 데이터 세트 필드 목록은 고정되어 있습니다.  
  
 **필드 새로 고침** 을 사용하여 보고서의 필드 목록을 공유 데이터 집합 쿼리에서의 현재 필드 목록과 일치하도록 업데이트할 수 있습니다. 필드 목록을 새로 고치는 경우 보고서에서 정의하는 계산 필드는 영향을 받지 않습니다.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-a-query-field"></a>쿼리 필드를 추가하려면  
  
1.  보고서 데이터 창에서 데이터 세트를 마우스 오른쪽 단추로 클릭한 다음, **쿼리 필드 추가**를 클릭합니다.  
  
    > [!NOTE]  
    >  보고서 데이터 창을 볼 수 없는 경우 **보기** 메뉴에서 **보고서 데이터**를 클릭합니다.  
  
2.  **데이터 집합 속성** 대화 상자의 **필드** 페이지에서 **추가**를 클릭한 다음 **쿼리 필드**를 클릭합니다. 표 아래쪽에 새 행이 추가됩니다.  
  
3.  **필드 이름** 입력란에 필드 이름을 입력합니다.  
  
    > [!NOTE]  
    >  이름은 데이터 세트에서 고유해야 합니다.  
  
4.  **필드 원본** 입력란에 데이터 원본의 기존 필드 이름을 입력합니다.  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-add-a-calculated-field"></a>계산 필드를 추가하려면  
  
1.  보고서 데이터 창에서 데이터 세트를 마우스 오른쪽 단추로 클릭한 다음, **계산 필드 추가**를 클릭합니다.  
  
2.  **데이터 집합 속성** 대화 상자의 **필드** 페이지에서 **추가**를 클릭한 다음 **계산 필드**를 클릭합니다. 표 아래쪽에 새 행이 추가됩니다.  
  
3.  **필드 이름** 입력란에 필드 이름을 입력합니다.  
  
    > [!NOTE]  
    >  이름은 데이터 세트에서 고유해야 합니다.  
  
4.  **필드 원본** 입력란에 필드의 식을 입력합니다. 식을 작성하려면 식 단추(**fx**)를 클릭합니다.  
  
    > [!NOTE]  
    >  계산 필드의 식은 보고서 항목에 대한 참조나 집계를 포함할 수 없습니다.  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-edit-a-query-field-or-a-dataset-field"></a>쿼리 필드 또는 데이터 세트 필드를 편집하려면  
  
1.  보고서 데이터 창에서 필드를 마우스 오른쪽 단추로 클릭한 다음 **필드 속성**을 클릭합니다.  
  
2.  **데이터 집합 속성** 대화 상자의 **필드** 페이지에서 기존 필드를 클릭하여 행을 선택합니다.  
  
3.  필드 이름 또는 필드 값을 변경합니다.  
  
4.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-delete-a-query-field-or-a-calculated-field"></a>쿼리 필드 또는 계산 필드를 삭제하려면  
  
1.  보고서 데이터 창에서 데이터 세트를 확장하여 필드 컬렉션을 표시합니다.  
  
2.  제거할 필드를 마우스 오른쪽 단추로 클릭한 다음 **삭제**를 클릭합니다.  
  
### <a name="to-refresh-the-field-collection-in-the-report-data-pane-for-a-shared-dataset"></a>보고서 데이터 창에서 공유 데이터 세트에 대한 필드 컬렉션을 새로 고치려면  
  
1.  보고서 데이터 창에서 데이터 세트를 마우스 오른쪽 단추로 클릭한 다음, **쿼리**를 클릭합니다.  
  
2.  **필드 새로 고침**을 클릭합니다.  
  
     보고서 서버에서 공유 데이터 세트 쿼리가 실행되고 현재 필드 컬렉션을 반환합니다.  
  
## <a name="see-also"></a>관련 항목  
 [데이터 집합 필드 컬렉션&#40;보고서 작성기 및 SSRS&#41;](dataset-fields-collection-report-builder-and-ssrs.md)   
 [보고서에 데이터 추가 &#40;보고서 작성기 및 SSRS&#41;](report-datasets-ssrs.md)   
 [보고서 포함된 데이터 집합 및 공유 데이터 집합&#40;보고서 작성기 및 SSRS&#41;](report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)   
 [Reporting Services 쿼리 디자이너](../reporting-services-query-designers.md)   
 [쿼리 디자이너&#40;보고서 작성기&#41;](../query-designers-report-builder.md)  
  
  
