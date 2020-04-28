---
title: 데이터 원본 뷰에서 명명 된 계산 정의 (Analysis Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- modifying named calculations
- data source views [Analysis Services], named calculations
- named calculations [Analysis Services]
ms.assetid: 729e7b12-6185-4b73-8bcb-cfe459b15355
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 435ef9a3b64b6a2b39a898bb0db0afaa5c79f828
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/27/2020
ms.locfileid: "78175749"
---
# <a name="define-named-calculations-in-a-data-source-view-analysis-services"></a>데이터 원본 뷰에서 명명된 계산 정의(Analysis Services)
  명명된 계산은 계산 열로 표시된 SQL 식입니다. 이 식은 테이블의 열과 같이 나타나고 동작합니다. 명명된 계산을 사용하면 기본 데이터 원본의 테이블이나 뷰를 수정하지 않고 데이터 원본 뷰에 있는 기존 테이블이나 뷰의 관계형 스키마를 확장할 수 있습니다. 다음과 같은 예를 고려할 수 있습니다.

-   팩트 테이블의 여러 열로부터 파생되는 단일 명명된 계산을 만듭니다. 예를 들어 세율에 소매 가격을 곱해서 Tax Amount를 만듭니다.

-   차원 구성원에 대해 알기 쉬운 이름을 생성합니다.

-   쿼리 성능을 향상하기 위해 큐브에 계산 멤버를 만드는 대신 DSV에 명명된 계산을 만듭니다. 명명된 계산은 처리 중에 계산되고 계산 멤버는 쿼리 시에 계산됩니다.

## <a name="creating-named-calculations"></a>명명된 계산 만들기

> [!NOTE]
>  명명된 계산을 명명된 쿼리에 추가할 수 없으며 명명된 계산이 포함된 테이블을 명명된 쿼리의 기반으로 할 수 없습니다.

 명명된 계산을 만들 때는 이름, SQL 식 및 필요에 따라 계산에 대한 설명을 지정합니다. SQL 식은 데이터 원본 뷰에서 다른 테이블을 참조할 수 있습니다. 명명된 계산을 정의하면 명명된 계산의 식이 데이터 원본 공급자에게 전송되고 다음 SQL 문과 같이 유효성 검사가 수행됩니다. 다음 문에서 명명된 계산을 정의하는 식은 `<Expression>` 자리에 포함됩니다.

```
SELECT 
   <Table Name in Data Source>.*, 
   <Expression> AS <Column Name> 
FROM 
   <Table Name in Data Source> AS <Table Name in Data Source View>
```

 열의 데이터 형식은 식에서 반환하는 스칼라 값의 데이터 형식에 의해 결정됩니다. 공급자가 식에서 오류를 찾을 수 없으면 해당 열이 테이블에 추가됩니다.

 식에서 참조되는 열은 한정되어서는 안 되며 한정할 경우 테이블 이름으로만 한정해야 합니다. 예를 들어 테이블의 SaleAmount 열을 참조하려면 `SaleAmount` 나 `Sales.SaleAmount` 는 유효하지만 `dbo.Sales.SaleAmount` 는 오류를 생성합니다.

 식은 자동으로 괄호로 묶이지 않기 때문에 SELECT 문과 같은 식에 괄호가 필요한 경우 **식** 상자에서 괄호를 입력해야 합니다. 예를 들어 다음 식은 괄호를 입력해야만 유효합니다.

```
(SELECT Description FROM Categories WHERE Categories.CategoryID = CategoryID)
```

## <a name="add-or-edit-a-named-calculation"></a>명명된 계산 추가 또는 편집

1.  [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]에서 명명된 계산을 정의할 데이터 원본 뷰가 포함된 프로젝트를 열거나 데이터베이스에 연결합니다.

2.  솔루션 탐색기에서 **데이터 원본 뷰** 폴더를 확장한 다음 해당 데이터 원본 뷰를 두 번 클릭합니다.

3.  **테이블** 또는 **다이어그램** 창에서 명명된 계산을 정의할 테이블을 마우스 오른쪽 단추로 클릭한 다음 **새 명명된 계산**을 클릭합니다. 특성이 아닌 테이블 이름을 마우스 오른쪽 단추로 클릭해야 합니다. 다음과 같은 메뉴가 나타납니다.

     ![다이어그램 작업 영역, 마우스 오른쪽 단추 클릭 메뉴의 스크린 샷](../media/ssas-olapdsv-diagram.gif "다이어그램 작업 영역, 마우스 오른쪽 단추 클릭 메뉴의 스크린 샷")

    > [!NOTE]
    >  테이블이 나 뷰를 찾으려면 **데이터 원본 뷰** 메뉴를 클릭 하거나 **테이블** 또는 **다이어그램** 창의 열린 영역을 마우스 오른쪽 단추로 클릭 하 여 **테이블 찾기** 옵션을 사용할 수 있습니다.

4.  **명명된 계산 만들기** 대화 상자에서 다음을 수행하십시오.

    -   **열 이름** 입력란에 새 열의 이름을 입력합니다.

    -   **설명** 입력란에 새 열에 대한 설명을 입력합니다.

    -   **식** 입력란에 데이터 공급자에 적합한 SQL 언어로 새 열의 내용을 생성하는 식을 입력합니다.

5.  **확인**을 클릭합니다.

     명명된 계산 열이 데이터 원본 뷰 테이블의 마지막 열로 표시됩니다. 계산기 기호는 열에 명명된 계산이 있음을 나타냅니다.

## <a name="delete-a-named-calculation"></a>명명된 계산 삭제
 명명된 계산을 삭제하려고 하면 프로젝트나 데이터베이스에 정의된 개체 중에서 삭제 작업으로 인해 무효화될 개체 목록이 표시됩니다. 계산을 삭제하기 전에 목록을 신중하게 검토합니다.

## <a name="see-also"></a>참고 항목
 [데이터 원본 뷰에서 명명된 쿼리 정의&#40;Analysis Services&#41;](define-named-queries-in-a-data-source-view-analysis-services.md)


