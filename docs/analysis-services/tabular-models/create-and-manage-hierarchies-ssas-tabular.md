---
title: Analysis Services 테이블 형식 모델에서 계층 만들기 및 관리 | Microsoft Docs
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 5e9e5fc942aa7b03cd4cb9a15d8b474a12f12a8d
ms.sourcegitcommit: 8a64c59c5d84150659a015e54f8937673cab87a0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/08/2018
ms.locfileid: "53072600"
---
# <a name="create-and-manage-hierarchies"></a>계층 만들기 및 관리 
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  모델 디자이너(다이어그램 뷰)에서 계층을 만들고 관리할 수 있습니다. 모델 디자이너(다이어그램 뷰)를 보려면 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]에서 **모델** 메뉴를 클릭하고 **모델 뷰**를 가리킨 다음 **다이어그램 뷰**를 클릭합니다.  
  
 이 문서에는 다음 작업이 포함 됩니다.  
  
-   [계층 만들기](#bkmk_create)  
  
-   [계층 편집](#bkmk_edit)  
  
-   [계층 삭제](#bkmk_delete)  
  
##  <a name="bkmk_create"></a> 계층 만들기  
 열 및 테이블의 상황에 맞는 메뉴를 사용하여 계층을 만들 수 있습니다. 계층을 만들면 새 부모 수준이 자식 수준으로 선택한 열과 함께 나타납니다.  
  
#### <a name="to-create-a-hierarchy-from-the-context-menu"></a>상황에 맞는 메뉴에서 계층을 만들려면  
  
1.  모델 디자이너(다이어그램 뷰)의 테이블 창에서 열을 마우스 오른쪽 단추로 클릭한 다음 **계층 만들기**를 클릭합니다.  
  
     여러 열을 선택하려면 각 열을 클릭한 다음 마우스 오른쪽 단추를 클릭하여 상황에 맞는 메뉴를 열고 **계층 만들기**를 클릭합니다.  
  
     부모 계층 수준이 테이블 창의 맨 아래에 만들어지고 선택한 열이 계층 아래에 자식 수준으로 복사됩니다.  
  
2.  계층의 이름을 입력합니다.  
  
 열을 복사 하는 계층의 부모 수준에 추가 열을 끌 수 있습니다. 끈 열을 계층에서 해당 열을 표시하려는 위치의 자식 수준에 놓습니다.  
  
> [!NOTE]  
>  하나 이상의 열과 함께 측정값을 여러 개 선택하거나 여러 테이블의 열을 선택할 경우 계층 만들기 명령이 비활성화됩니다.  
  
##  <a name="bkmk_edit"></a> 계층 편집  
 계층 이름 바꾸기, 자식 수준 이름 바꾸기, 자식 수준 순서 변경, 다른 열을 자식 수준으로 추가, 계층에서 자식 수준 제거, 자식 수준의 원본 이름(열 이름) 표시, 계층 부모 수준과 이름이 동일한 자식 수준 숨기기 등의 편집 작업을 수행할 수 있습니다.  
  
#### <a name="to-change-the-name-of-a-hierarchy-or-child-level"></a>계층 또는 자식 수준의 이름을 변경하려면  
  
1.  계층 부모 수준 또는 자식 수준을 마우스 오른쪽 단추로 클릭하고 **이름 바꾸기**를 클릭합니다.  
  
2.  새 이름을 입력하거나 기존 이름을 편집합니다.  
  
#### <a name="to-change-the-order-of-a-child-level-in-a-hierarchy"></a>계층의 자식 수준 순서를 변경하려면  
  
-   자식 수준을 클릭하여 계층의 새 위치로 끕니다.  
  
-   또는 계층의 자식 수준을 마우스 오른쪽 단추로 클릭하고, 위로 이동을 클릭하여 목록의 위쪽 수준으로 이동하거나 아래로 이동을 클릭하여 목록의 아래쪽 수준으로 이동합니다.  
  
-   또는 자식 수준을 클릭하여 선택한 다음 Alt + 위쪽 화살표를 클릭하여 목록에서 상위 수준으로 이동하거나, Alt + 아래쪽 화살표를 클릭하여 하위 수준으로 이동합니다.  
  
#### <a name="to-add-another-child-level-to-a-hierarchy"></a>계층에 다른 자식 수준을 추가하려면  
  
-   열을 클릭하고 부모 수준으로 끌거나 계층의 특정 위치로 끕니다. 그러면 해당 열이 계층의 자식 수준으로 복사됩니다.  
  
-   또는 열을 마우스 오른쪽 단추로 클릭하고 **계층에 추가**를 가리킨 다음 계층을 클릭합니다.  
  
> [!NOTE]  
>  보고서에서 숨겨진 열을 계층에 자식 수준으로 추가할 수 있습니다. 자식 수준은 숨겨지지 않습니다.  
  
#### <a name="to-remove-a-child-level-from-a-hierarchy"></a>계층에서 자식 수준을 제거하려면  
  
-   자식 수준을 마우스 오른쪽 단추로 클릭하고 **계층에서 제거**를 클릭합니다.  
  
-   또는 계층의 자식 수준을 클릭하고 **Delete**키를 누릅니다.  
  
> [!NOTE]  
>  계층 자식 수준의 이름을 바꿀 경우 해당 자식 수준은 더 이상 자식 수준을 복사하는 데 사용된 열과 동일한 이름을 공유하지 않습니다. **원본 열 이름 표시** 명령을 사용하여 복사해 온 원본 열을 표시합니다.  
  
#### <a name="to-show-a-source-name"></a>원본 이름을 표시하려면  
  
-   계층 자식 수준을 마우스 오른쪽 단추로 클릭하고 **원본 이름 표시**를 클릭합니다. 복사해 온 원본 열의 이름이 표시됩니다.  
  
##  <a name="bkmk_delete"></a> 계층 삭제  
  
#### <a name="to-delete-a-hierarchy-and-remove-its-child-levels"></a>계층을 삭제하고 자식 수준을 제거하려면  
  
-   부모 계층 수준을 마우스 오른쪽 단추로 클릭하고 계층 삭제를 클릭합니다.  
  
-   또는 부모 계층 수준을 클릭하고 Delete 키를 누릅니다. 이 경우 모든 자식 수준도 제거됩니다.  
  
## <a name="see-also"></a>관련 항목  
 [테이블 형식 모델 디자이너 ](../../analysis-services/tabular-models/tabular-model-designer-ssas.md)   
 [계층 구조](../../analysis-services/tabular-models/hierarchies-ssas-tabular.md)   
 [측정값](../../analysis-services/tabular-models/measures-ssas-tabular.md)  
  
  
