---
title: 마이닝 모델에 필터 적용 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- model filter [data mining]
- filters [data mining]
- filtering input rows [Analysis Services]
- filtering data [Analysis Services]
ms.assetid: 4d0abeb5-e939-46d3-9097-6e0358244300
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 0370d4fceada5c0a287c4a071691ea20d5a28f6c
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66086219"
---
# <a name="apply-a-filter-to-a-mining-model"></a>마이닝 모델에 필터 적용
  마이닝 구조에 중첩 테이블이 포함된 경우 사례 테이블, 중첩 테이블 또는 두 테이블 모두에 필터를 적용할 수 있습니다.  
  
 다음 절차에서는 사례 필터 및 중첩 테이블 행의 필터와 같은 두 종류의 필터를 만드는 방법을 보여 줍니다.  
  
 사례 테이블의 조건은 수입이 30000 ~ 40000인 고객으로 제한합니다. 중첩 테이블의 조건은 특정 항목을 구입하지 않은 고객으로 제한합니다.  
  
 이 예에서 만든 전체 필터 조건은 다음과 같습니다.  
  
```  
[Income] > '30000'   
AND  [Income] < '40000'   
AND EXISTS (SELECT * FROM [<nested table name>]   
WHERE [Model] <> 'Water Bottle' )   
```  
  
### <a name="to-create-a-case-filter-on-a-mining-model"></a>마이닝 모델에 사례 필터를 만들려면  
  
1.  
  [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]의 솔루션 탐색기에서 필터링할 마이닝 모델이 포함된 마이닝 구조를 클릭합니다.  
  
2.  
  **마이닝 모델** 탭을 클릭합니다.  
  
3.  모델을 선택하고 마우스 오른쪽 단추를 클릭하여 바로 가기 메뉴를 엽니다.  
  
     또는  
  
     모델을 선택합니다. 
  **마이닝 모델** 메뉴에서 **모델 필터 설정**을 선택합니다.  
  
4.  
  **모델 필터** 대화 상자의 **마이닝 구조 열** 입력란에서 표의 첫 행을 클릭합니다.  
  
5.  데이터 원본에 단일 플랫 테이블이 포함된 경우 드롭다운 목록에 해당 테이블의 열 이름만 표시됩니다.  
  
     마이닝 구조에 여러 테이블이 포함된 경우 목록에 원본 테이블 이름이 표시됩니다. 열 이름은 테이블을 선택한 후에 표시됩니다.  
  
     마이닝 구조에 사례 테이블과 중첩 테이블이 포함된 경우 드롭다운 목록에 사례 테이블의 열과 중첩 테이블의 이름이 표시됩니다.  
  
6.  드롭다운 목록에서 열을 선택합니다.  
  
     입력란의 왼쪽에 있는 아이콘이 변경되어 선택한 항목이 테이블인지 또는 열인지를 나타냅니다.  
  
7.  
  **연산자** 입력란을 클릭하고 목록에서 연산자를 선택합니다. 선택한 열의 데이터 형식에 따라 유효한 연산자가 변경됩니다.  
  
8.  
  **값** 입력란을 클릭하고 상자에 값을 입력합니다.  
  
     예를 들어을 `Income` 열로 선택 하 고 보다 큼 연산자 (>)를 선택한 다음을 입력 `30000`합니다.  
  
9. 표에서 다음 행을 클릭합니다.  
  
     이전에 만든 필터 조건이 식 입력란에 자동으로 추가됩니다. 예를 들어 `[Income] > '30000'`  
  
10. 표의 다음 행에서 **AND/OR** 입력란을 클릭하여 조건을 추가합니다.  
  
     예를 들어 BETWEEN 조건을 만들려면 논리 피연산자의 드롭다운 `AND` 목록에서를 선택 합니다.  
  
11. 7-8단계의 설명에 따라 연산자를 선택하고 값을 입력합니다.  
  
     예를 들어를 `Income` 열로 다시 선택 하 고 보다 작음 연산자 (<)를 선택한 다음을 입력 `40000`합니다.  
  
12. 표에서 다음 행을 클릭합니다.  
  
13. 식 입력란의 필터 조건이 새 조건을 포함하도록 자동으로 업데이트됩니다. 전체 식은 `[Income] > '30000'AND [Income] < '40000'`  
  
### <a name="to-add-a-filter-on-the-nested-table-in-a-mining-model"></a>마이닝 모델의 중첩 테이블에 필터를 추가하려면  
  
1.  이름>모델 필터 대화 상자에서 **마이닝 구조 열**아래 표의 빈 행을 클릭 합니다. ** \<**  
  
2.  드롭다운 목록에서 중첩 테이블 이름을 선택합니다.  
  
     입력란의 왼쪽에 있는 아이콘이 변경되어 선택한 항목이 테이블 이름임을 나타냅니다.  
  
3.  
  **연산자** 입력란을 클릭하고 **포함** 또는 **포함하지 않음**을 선택합니다.  
  
     사례 테이블에서 중첩 테이블의 특정 값을 포함하는 사례만 허용하도록 지정했으므로 이러한 조건만 **모델 필터** 대화 상자의 중첩 테이블에서 사용할 수 있습니다. 다음 단계에서는 중첩 테이블의 조건에 대한 값을 설정합니다.  
  
4.  **값** 상자를 클릭 한 다음 **(...)** 단추를 클릭 하 여 식을 작성 합니다.  
  
     ** \<>필터 이름** 대화 상자가 열립니다. 이 대화 상자에서는 현재 테이블의 조건만 설정할 수 있습니다. 이 사례에서 현재 테이블은 중첩 테이블입니다.  
  
5.  
  **마이닝 구조 열** 상자를 클릭하고 중첩 테이블 열의 드롭다운 목록에서 열 이름을 선택합니다.  
  
6.  
  **연산자** 를 클릭하고 열에 대한 올바른 연산자 목록에서 연산자를 선택합니다.  
  
7.  
  **값** 을 클릭한 다음 값을 입력합니다.  
  
     예를 들어 **마이닝 구조 열** 에 대해를 `Model`선택 합니다. **연산자**에 대해를 `<>`선택 하 고 값 `Water Bottle`을 입력 합니다. 이 조건은 다음 필터 식을 만듭니다.  
  
```  
EXISTS (SELECT * FROM [<nested table name>] WHERE [Model] <> 'Water Bottle' )   
```  
  
> [!NOTE]  
>  중첩 테이블 특성의 수는 잠재적으로 제한이 없기 때문에 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 는 선택 가능한 값 목록을 제공하지 않습니다. 정확한 값을 입력해야 합니다. 또한 중첩 테이블에서는 LIKE 연산자를 사용할 수 없습니다.  
  
1.  **조건 표의 왼쪽** 에 있는 **AND/or** 상자에서 또는 `AND` `OR` 를 선택 하 여 조건을 결합 하 여 필요에 따라 조건을 더 추가 합니다. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
2.  
  **모델 필터** 대화 상자에서 **필터** 대화 상자를 사용하여 만든 조건을 검토합니다. 중첩 테이블의 조건이 사례 테이블의 조건에 추가되며 필터 조건의 전체 집합이 **식** 입력란에 표시됩니다.  
  
3.  필요에 따라 **쿼리 편집** 을 클릭하여 필터 식을 수동으로 변경합니다.  
  
    > [!NOTE]  
    >  필터 식의 임의 부분을 수동으로 변경하면 표가 비활성화되어 텍스트 편집 모드에서만 필터 식 작업을 수행할 수 있습니다. 표 편집 모드를 복원하려면 해당 필터 식을 지우고 다시 시작해야 합니다.  
  
  
## <a name="see-also"></a>참고 항목  
 [마이닝 모델 &#40;Analysis Services 데이터 마이닝&#41;필터](mining-models-analysis-services-data-mining.md)   
 [마이닝 모델 태스크 및 방법](mining-model-tasks-and-how-tos.md)   
 [마이닝 모델에서 필터 삭제](delete-a-filter-from-a-mining-model.md)  
  
  
