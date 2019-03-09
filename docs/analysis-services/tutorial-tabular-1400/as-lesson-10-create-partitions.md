---
title: 'Analysis Services 자습서 단원 10: 파티션을 만들 | Microsoft Docs'
ms.date: 03/08/2019
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: tutorial
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile"
monikerRange: '>= sql-server-2017 || = sqlallproducts-allversions'
ms.openlocfilehash: 705705410a69c4fa0eff507c97747f55b72b1250
ms.sourcegitcommit: 0a7beb2f51e48889b4a85f7c896fb650b208eb36
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57685700"
---
# <a name="create-partitions"></a>파티션 만들기

[!INCLUDE[ssas-appliesto-sql2017-later-aas](../../includes/ssas-appliesto-sql2017-later-aas.md)]

이 단원에서는 만든 FactInternetSales 테이블을 처리할 수 있는 더 작은 논리적 부분으로 나누는 데 (새로 고침) 하는 파티션을 다른 파티션과 독립적으로 합니다. 기본적으로 모델에 포함 된 모든 테이블에는 모든 테이블의 열과 행을 포함 하는 하나의 파티션이 있습니다. FactInternetSales 테이블에 대 한 연도별; 데이터를 분할 하려는 각 테이블의 5 년에 대해 하나의 파티션을 합니다. 이렇게 하면 각 파티션을 독립적으로 처리할 수 있습니다. 자세한 내용은 [파티션](../tabular-models/partitions-ssas-tabular.md)을 참조하세요. 
  
이 단원에 소요되는 예상 시간: **15 분**  
  
## <a name="prerequisites"></a>사전 요구 사항  

이 문서는 순서 대로 완료 해야 하는 테이블 형식 모델링 자습서의 일부입니다. 이 단원의 태스크를 수행하려면 이전 단원을 완료해야 합니다. [9 단원: 계층 구조를 만들](../tutorial-tabular-1400/as-lesson-9-create-hierarchies.md)합니다.  
  
## <a name="create-partitions"></a>파티션 만들기  
  
#### <a name="to-create-partitions-in-the-factinternetsales-table"></a>FactInternetSales 테이블에서 파티션을 만들려면  
  
1.  테이블 형식 모델 탐색기에서 확장 **테이블**를 마우스 오른쪽 단추로 클릭 한 다음 **FactInternetSales** > **파티션을**합니다.  
  
2.  파티션 관리자에서 클릭 **복사본**, 변경한 다음 이름을 **FactInternetSales2010**합니다.
  
    파티션에 2010 년에 대 한 특정 기간 내 행만 포함 되도록 할 것 이므로 쿼리 식을 수정 해야 합니다.
  
4.  클릭 **디자인** 쿼리 편집기를 열고 다음을 클릭 합니다 **FactInternetSales2010** 쿼리 합니다.

5.  미리 보기 상태에서에서 아래쪽 화살표를 클릭 합니다 **OrderDate** 열 머리글을 클릭 한 다음 **날짜/시간 필터** > **간의**합니다.

    ![as-lesson10-query-editor](../tutorial-tabular-1400/media/as-lesson10-query-editor.png)

6.  행 필터 대화 상자에서에서 **조건인 행 표시: OrderDate**를 그대로 **이후 또는 같음**, 날짜 필드에 입력 한 다음 **2010 년 1 월 1 일**합니다. 유지 합니다 **및** 연산자를 선택 하면 선택한 **앞**, 날짜 필드에 입력 한 다음 **2011 년 1 월 1**, 클릭 하 고 **확인**합니다.

    ![as-lesson10-filter-rows](../tutorial-tabular-1400/media/as-lesson10-filter-rows.png)
    
    알림 필터링 된 행 이라는 다른 단계가 표시 쿼리 편집기에서 적용 된 단계에 있습니다. 이 필터는 2010에서 주문 날짜만 선택 하는 것입니다.

8.  **가져오기**를 클릭합니다.

    파티션 관리자에서 이제 쿼리 식에는 추가 필터링 된 행 절을 확인 합니다.

    ![as-lesson10-query](../tutorial-tabular-1400/media/as-lesson10-query.png)
  
    이 문은이 파티션에 2010 년의 필터링된 된 행 절에 지정 된 대로 OrderDate가 있는 행에서 데이터만 포함 하도록 지정 합니다.  
  
  
#### <a name="to-create-a-partition-for-the-2011-year"></a>2011년에 대한 파티션을 만들려면  
  
1.  파티션 목록에서를 클릭 합니다 **FactInternetSales2010** 파티션 및 클릭 **복사**합니다.  파티션 이름을 **FactInternetSales2011**합니다. 

    쿼리 편집기를 사용 하 여 새 필터링 된 행 절을 만들 필요가 없습니다. 2010에 대 한 쿼리의 복사본을 만들 때 수행 해야 할 모든 이므로 2011 쿼리에서 약간 변경 합니다.
  
2.  **쿼리 식**, 2011 년에 한 행만 포함을 사용 하 여 필터링 된 행 절에서 연도 대체 합니다.이 파티션에 대 한 순서 **2011** 하 고 **2012**, 각각 다음과 같습니다.  
  
    ```  
    let
        Source = #"SQL/localhost;AdventureWorksDW2014",
        dbo_FactInternetSales = Source{[Schema="dbo",Item="FactInternetSales"]}[Data],
        #"Removed Columns" = Table.RemoveColumns(dbo_FactInternetSales,{"OrderDateKey", "DueDateKey", "ShipDateKey"}),
        #"Filtered Rows" = Table.SelectRows(#"Removed Columns", each [OrderDate] >= #datetime(2011, 1, 1, 0, 0, 0) and [OrderDate] < #datetime(2012, 1, 1, 0, 0, 0))
    in
        #"Filtered Rows"
   
    ```  
  
#### <a name="to-create-partitions-for-2012-2013-and-2014"></a>2012, 2013 및 2014에 대 한 파티션을 만들려면 합니다.  
  
- 2012, 2013 및 2014 년 해당 연도 대 한 행만 포함 하도록 필터링 된 행 절에서 연도 변경에 대 한 파티션을 만드는 이전 단계를 따릅니다. 
  

## <a name="delete-the-factinternetsales-partition"></a>FactInternetSales 파티션을 삭제 합니다.

FactInternetSales 파티션을; 각 연도 대 한 파티션이 했으므로 삭제할 수 있습니다. 파티션을 처리할 때 모든 프로세스를 선택할 때 겹침을 방지 합니다.

#### <a name="to-delete-the-factinternetsales-partition"></a>FactInternetSales 파티션을 삭제 하려면

-  클릭 합니다 **FactInternetSales** 파티션하고 클릭 **삭제**합니다.



## <a name="process-partitions"></a>파티션 처리  

파티션 관리자에서 확인 합니다 **마지막 처리** 열 만든 새로운 각 분할에 대 한 표시 이러한 파티션은 처리 되지 않은 합니다. 파티션을 만들 때 해당 파티션에 데이터를 새로 고치려면 파티션 처리 또는 테이블 처리 작업을 실행 해야 합니다.  
  
#### <a name="to-process-the-factinternetsales-partitions"></a>FactInternetSales 파티션을 처리 하려면  
  
1.  클릭 **확인** 파티션 관리자를 닫습니다.  
  
2.  클릭 합니다 **FactInternetSales** 테이블을 클릭 합니다 **모델** 메뉴 > **프로세스** > **파티션 처리**합니다.  
  
3.  파티션 처리 대화 상자에서 확인 **모드** 로 설정 된 **기본값 처리**합니다.  
  
4.  방금 만든 5개의 파티션 각각에 대해 **처리** 열에서 확인란을 선택한 다음 **확인**을 클릭합니다.  

    ![as-lesson10-process-partitions](../tutorial-tabular-1400/media/as-lesson10-process-partitions.png)
  
    가장 자격 증명을 묻는 Windows 사용자 이름 및 2 단원에서에서 지정한 암호를 입력 합니다.  
  
    그러면 **데이터 처리** 대화 상자가 나타나고 각 파티션에 대한 처리 정보가 표시됩니다. 파티션마다 서로 다른 개수의 행이 전송되었음을 확인할 수 있습니다. 각 파티션은 SQL 문의 WHERE 절에 지정 된 연도의 행만을 포함 합니다. 처리가 완료되면 계속해서 데이터 처리 대화 상자를 닫습니다.  
  
    ![as-lesson10-process-complete](../tutorial-tabular-1400/media/as-lesson10-process-complete.png)
  
 ## <a name="whats-next"></a>다음 단계

다음 단원으로 이동 합니다. [11 단원: 역할을 만들](../tutorial-tabular-1400/as-lesson-11-create-roles.md)합니다. 
