---
title: Analysis Services 테이블 형식 모델에서 관계 만들기 | Microsoft Docs
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 7e9ee96a04aa6b023be51f8e1e8d913e26a7e2a8
ms.sourcegitcommit: 8a64c59c5d84150659a015e54f8937673cab87a0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/08/2018
ms.locfileid: "53072100"
---
# <a name="create-a-relationship"></a>관계 만들기 
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  데이터 원본의 테이블에 기존 관계가 없거나 새 테이블을 추가하는 경우 모델 디자이너의 도구를 사용하여 새 관계를 만들 수 있습니다. 테이블 형식 모델에서 관계가 사용 되는 방법에 대 한 자세한 내용은 [관계](../../analysis-services/tabular-models/relationships-ssas-tabular.md)합니다.  
  
## <a name="create-a-relationship-between-two-tables"></a>두 테이블 간에 관계 만들기  
  
#### <a name="to-create-a-relationship-between-two-tables-in-diagram-view-click-and-drag"></a>다이어그램 뷰에서 두 테이블 간의 관계를 만들려면(클릭하여 끌기)  
  
1.  [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]에서 **모델** 메뉴를 클릭하고 **모델 뷰**를 클릭한 다음 **다이어그램 뷰**를 클릭합니다.  
  
2.  테이블 내의 열을 클릭한 채로 커서를 관련 조회 테이블의 관련 조회 열로 끌어다 놓으면 관계가 올바른 순서로 자동으로 만들어집니다.  
  
#### <a name="to-create-a-relationship-between-two-tables-in-diagram-view-right-click"></a>다이어그램 뷰에서 두 테이블 간의 관계를 만들려면(마우스 오른쪽 단추 클릭)  
  
1.  [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]에서 **모델** 메뉴를 클릭하고 **모델 뷰**를 클릭한 다음 **다이어그램 뷰**를 클릭합니다.  
  
2.  테이블 머리글 또는 열을 마우스 오른쪽 단추로 클릭하고 **관계 만들기**를 클릭합니다.  
  
3.  **관계 만들기** 대화 상자의 **테이블**에서 아래쪽 화살표를 클릭하고 드롭다운 목록에서 테이블을 선택합니다.  
  
     "일 대 다" 관계에서 이 테이블은 "다" 쪽에 있어야 합니다.  
  
4.  **열**에서 **관련 조회 열**과 관련된 데이터가 들어 있는 열을 선택합니다. 관계를 만들기 위해 열을 마우스 오른쪽 단추로 클릭하면 열이 자동으로 선택됩니다.  
  
5.  **테이블**에서 방금 선택한 테이블과 관련된 데이터 열이 하나 이상 있는 테이블을 **관련 조회 테이블**에서 선택합니다.  
  
     "일 대 다" 관계에서 이 테이블은 "일" 쪽에 있어야 하므로 선택한 열에 중복 값이 포함되지 않습니다. 잘못된 순서(다 대 일 대신 일 대 다)로 관계를 만들려고 하면 **관련 조회 열** 필드 옆에 아이콘이 나타납니다. 순서를 반대로 하여 유효한 관계를 만듭니다.  
  
6.  **열**에서 선택한 열의 값과 일치하는 고유 값이 있는 열을 **관련 조회 열**에서 선택합니다.  
  
7.  **만들기**를 클릭합니다.  
  
#### <a name="to-create-a-relationship-between-two-tables-in-data-view"></a>데이터 뷰에서 두 테이블 간의 관계를 만들려면  
  
1.  [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]에서 **테이블** 메뉴를 클릭한 다음 **관계 만들기**를 클릭합니다.  
  
2.  **관계 만들기** 대화 상자의 **테이블**에서 아래쪽 화살표를 클릭하고 드롭다운 목록에서 테이블을 선택합니다.  
  
     "일 대 다" 관계에서 이 테이블은 "다" 쪽에 있어야 합니다.  
  
3.  **열**에서 **관련 조회 열**과 관련된 데이터가 들어 있는 열을 선택합니다.  
  
4.  **테이블**에서 방금 선택한 테이블과 관련된 데이터 열이 하나 이상 있는 테이블을 **관련 조회 테이블**에서 선택합니다.  
  
     "일 대 다" 관계에서 이 테이블은 "일" 쪽에 있어야 하므로 선택한 열에 중복 값이 포함되지 않습니다. 잘못된 순서(다 대 일 대신 일 대 다)로 관계를 만들려고 하면 **관련 조회 열** 필드 옆에 아이콘이 나타납니다. 순서를 반대로 하여 유효한 관계를 만듭니다.  
  
5.  **열**에서 선택한 열의 값과 일치하는 고유 값이 있는 열을 **관련 조회 열**에서 선택합니다.  
  
6.  **만들기**를 클릭합니다.  
  
## <a name="see-also"></a>참고자료  
 [관계 삭제](../../analysis-services/tabular-models/delete-relationships-ssas-tabular.md)   
 [관계](../../analysis-services/tabular-models/relationships-ssas-tabular.md)  
  
  
