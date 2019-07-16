---
title: Analysis Services 테이블 형식 모델 테이블에 열을 추가 합니다. | Microsoft Docs
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: a726f7dd8ef72ad30bd055d2f76cc58c7db6183d
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/15/2019
ms.locfileid: "68163114"
---
# <a name="add-columns-to-a-table"></a>테이블에 열 추가
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  이 문서에서는 기존 테이블에 열을 추가 하는 방법을 설명 합니다.  
  
## <a name="add-columns-from-the-datasource"></a>데이터 원본에서 열을 추가 합니다.  
 데이터 원본 테이블에서 데이터를 가져오기 위해 테이블 가져오기 마법사를 사용할 경우 원본 테이블의 모든 열을 포함하거나 미리 보기 및 필터 기능을 사용하여 특정 열을 필터링하여 제외하도록 선택한 경우 해당 열 및 선택한 필터링된 데이터를 포함하는 새 테이블이 모델에서 만들어집니다. 가져올 특정 열만 지정하는 SQL 쿼리를 작성할 수도 있습니다. 그러나 나중에 추가로 원본 테이블의 다른 열을 모델 테이블에 가져오거나 DAX 수식에서 값을 유추하는 계산 열을 추가할 수 있습니다.  
  
 예를 들어 먼저 테이블 가져오기 마법사에서 미리 보기 및 필터 기능을 사용하여 데이터 원본의 일부 열만 선택하여 데이터를 가져온 다음, 나중에 원본 테이블에는 존재하지만 모델 테이블에 없는 다른 열을 추가해야 할 수 있습니다. 또는 데이터 원본의 FactSales 테이블에 새 AdjustedProfit 열을 추가한 다음 동일한 AdjustedProfit 열과 데이터를 모델의 Sales 테이블에 추가해야 할 수 있습니다.  
  
 이러한 경우 테이블 속성 편집 대화 상자를 사용하여 원본 테이블의 열을 선택한 후 모델 테이블에 추가할 수 있습니다. 테이블 속성 편집 대화 상자에는 테이블 미리 보기 창이 있습니다. 이 테이블 미리 보기 창에 원본의 테이블이 표시됩니다. 모델 테이블 정의에 이미 포함된 열은 확인란이 선택되어 있습니다. 모델 테이블 정의에 아직 포함되지 않은 열은 선택이 해제되어 있습니다. 열을 선택한 후 확인을 클릭하여 원본의 열을 모델 테이블 정의에 추가할 수 있습니다. 테이블 속성 편집 대화 상자의 테이블 미리 보기 창은 테이블 가져오기 마법사의 미리 보기 및 필터 페이지에 있는 테이블 미리 보기 창과 동일한 보기와 기능을 제공합니다.  
  
> [!IMPORTANT]  
>  두 개 이상의 파티션이 포함된 테이블에 열을 추가하려면 먼저 파티션 관리자를 사용하여 정의된 모든 파티션에 열을 추가한 후, 테이블 속성 편집 대화 상자를 사용하여 테이블 정의에 열을 추가해야 합니다. 정의된 파티션에 열을 추가한 후 테이블 속성 편집 대화 상자를 사용하여 테이블 정의에 동일한 열을 추가할 수 있습니다.  
  
> [!NOTE]  
>  처음에 테이블 가져오기 마법사를 사용하여 데이터를 가져올 때 SQL 쿼리를 사용하여 테이블 및 열을 선택한 경우에는 나중에 테이블 속성 편집 대화 상자에서 모델 테이블에 열을 추가할 때에도 SQL 쿼리를 사용해야 합니다.  
  
#### <a name="to-add-a-column-from-the-data-source-by-using-the-edit-table-properties-dialog-box"></a>테이블 속성 편집 대화 상자를 사용하여 데이터 원본의 열을 추가하려면  
  
1.  모델 디자이너에서 열을 추가할 테이블을 클릭한 다음 **테이블** 메뉴를 클릭하고  **테이블 속성**을 클릭합니다.  
  
2.  **테이블 속성 편집** 대화 상자의 테이블 미리 보기 창에서 추가할 원본 열을 선택한 다음 확인을 클릭합니다. 이때 모델 테이블 정의에 이미 포함된 열은 확인란이 선택되어 있습니다.  
  
## <a name="add-a-calculated-column"></a>계산된 열 추가  
 계산 열에서는 DAX 수식에 따라 각 행의 값이 정해집니다. 예를 들어 각 행에 값으로 1을 추가하는 간단한 수식(=1)으로 계산된 열을 만들 수 있습니다. 또는 모델의 다른 데이터를 바탕으로 값을 계산하는 좀 더 복잡한 수식의 계산된 열을 만들 수도 있습니다. 계산 열은 다른 항목에서 더 자세히 다룹니다. 자세한 내용은 [계산 열](../../analysis-services/tabular-models/ssas-calculated-columns.md)에서 작성된 테이블 형식 모델 프로젝트에 대해 설명합니다.  
  
#### <a name="to-create-a-calculated-column"></a>계산 열을 만들려면  
  
1.  모델 디자이너의 데이터 뷰에서 새로운 빈 계산 열을 추가하려는 테이블을 선택한 다음 맨 오른쪽 열로 스크롤하거나 **열** 메뉴를 클릭한 다음 **열 추가**를 클릭합니다.  
  
     기존의 두 열 사이에 새 열을 만들려면 기존 열을 마우스 오른쪽 단추로 클릭하고 **열 삽입**을 클릭합니다.  
  
2.  수식 입력줄에 DAX 수식을 입력하여 각 행에 대한 특성을 추가합니다.  
  
## <a name="add-a-blank-column"></a>빈 열 추가  
 모델 테이블에서 명명된 빈 열을 만들 수 있습니다. 빈 열은 다른 원본에서 데이터를 가져와서 붙여넣을 경우에 유용하게 사용됩니다. 붙여넣은 데이터는 가져올 때와 다르게 저장됩니다. 자세한 내용은 [데이터 복사 및 붙여넣기](../../analysis-services/tabular-models/ssas-import-data-copy-and-paste-data.md)합니다.  
  
#### <a name="to-create-a-named-blank-column"></a>명명된 빈 열을 만들려면  
  
1.  모델 디자이너의 데이터 뷰에서 빈 열을 추가하려는 테이블을 선택한 다음 맨 오른쪽 열로 스크롤하거나 **열** 메뉴를 클릭한 다음 **열 추가**를 클릭합니다.  
  
     기존의 두 열 사이에 새 열을 만들려면 기존 열을 마우스 오른쪽 단추로 클릭하고 **열 삽입**을 클릭합니다.  
  
2.  맨 위 셀을 클릭하고 이름을 입력한 다음 Enter 키를 누릅니다.  
  
## <a name="see-also"></a>참조  
 [테이블 속성 편집 대화 상자](http://msdn.microsoft.com/library/8d913e83-7246-44cc-8fc7-31729023c0d8)   
 [테이블, 열 또는 행 필터 매핑 변경](../../analysis-services/tabular-models/change-table-column-or-row-filter-mappings-ssas-tabular.md)  
  
  
