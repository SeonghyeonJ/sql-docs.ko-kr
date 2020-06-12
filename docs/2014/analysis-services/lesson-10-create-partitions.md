---
title: '11 단원: 파티션 만들기 | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 92eb21a8-5fc4-4999-ad37-1332ce26431d
author: minewiskan
ms.author: owend
ms.openlocfilehash: 545c6f45339047d3a632f9e18d69108f3c8b5111
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84543585"
---
# <a name="lesson-11-create-partitions"></a>11단원: 파티션 만들기
  이 단원에서는 다른 파티션과 독립적으로 처리(새로 고침)할 수 있도록 파티션을 만들어 Internet Sales 테이블을 더 작은 논리적 부분으로 나눕니다. 기본적으로 모델에 포함 된 모든 테이블에는 테이블의 열과 행이 모두 포함 된 하나의 파티션이 있습니다. Internet Sales 테이블의 경우 데이터를 연도별로 나누려고 합니다. 각 테이블의 5 년에 대해 하나의 파티션입니다.  이렇게 하면 각 파티션을 독립적으로 처리할 수 있습니다. 자세한 내용은 [파티션&#40;SSAS 테이블 형식&#41;](tabular-models/partitions-ssas-tabular.md)을 참조하세요.  
  
 이 단원을 완료하기 위한 예상 시간: **15분**  
  
## <a name="prerequisites"></a>사전 요구 사항  
 이 항목은 테이블 형식 모델링 자습서에 포함되며 순서대로 완료해야 합니다. 이 단원의 태스크를 수행하려면 이전 단원인 [10단원: 계층 만들기](lesson-9-create-hierarchies.md)를 완료해야 합니다.  
  
## <a name="create-partitions"></a>파티션 만들기  
  
#### <a name="to-create-partitions-in-the-internet-sales-table"></a>Internet Sales 테이블에서 파티션을 만들려면  
  
1.  모델 디자이너에서 **Internet Sales** 테이블을 클릭한 다음 **테이블** 메뉴와 **파티션**을 차례로 클릭합니다.  
  
     **파티션 관리자** 대화 상자가 열립니다.  
  
2.  **파티션 관리자** 대화 상자의 **파티션**에서 **Internet Sales** 파티션을 클릭 합니다.  
  
3.  **파티션 이름**에서 이름을로 변경 `Internet Sales 2005` 합니다.  
  
    > [!TIP]  
    >  다음 단계로 진행하기 전에 테이블 미리 보기 창을 보면 열 이름에 모델 테이블(선택됨)에 포함된 열이 원본의 열 이름과 함께 표시되는 것을 확인할 수 있습니다. 이는 테이블 미리 보기 창에 모델 테이블의 열이 아니라 원본 테이블의 열이 표시되기 때문입니다.  
  
4.  미리 보기 창의 오른쪽 바로 위에 있는 **쿼리 편집기** 단추를 선택합니다.  
  
     파티션에 특정 기간에 해당하는 행만 포함하려고 하므로 WHERE 절을 포함해야 합니다. WHERE 절은 SQL 문을 사용해서만 만들 수 있습니다.  
  
5.  **SQL 문** 필드에서 다음 문을 붙여넣어 기존 문을 바꿉니다.  
  
    ```  
    SELECT   
    [dbo].[FactInternetSales].[ProductKey],  
    [dbo].[FactInternetSales].[CustomerKey],  
    [dbo].[FactInternetSales].[PromotionKey],  
    [dbo].[FactInternetSales].[CurrencyKey],  
    [dbo].[FactInternetSales].[SalesTerritoryKey],  
    [dbo].[FactInternetSales].[SalesOrderNumber],  
    [dbo].[FactInternetSales].[SalesOrderLineNumber],  
    [dbo].[FactInternetSales].[RevisionNumber],  
    [dbo].[FactInternetSales].[OrderQuantity],  
    [dbo].[FactInternetSales].[UnitPrice],  
    [dbo].[FactInternetSales].[ExtendedAmount],  
    [dbo].[FactInternetSales].[UnitPriceDiscountPct],  
    [dbo].[FactInternetSales].[DiscountAmount],  
    [dbo].[FactInternetSales].[ProductStandardCost],  
    [dbo].[FactInternetSales].[TotalProductCost],  
    [dbo].[FactInternetSales].[SalesAmount],  
    [dbo].[FactInternetSales].[TaxAmt],  
    [dbo].[FactInternetSales].[Freight],  
    [dbo].[FactInternetSales].[CarrierTrackingNumber],  
    [dbo].[FactInternetSales].[CustomerPONumber],  
    [dbo].[FactInternetSales].[OrderDate],  
    [dbo].[FactInternetSales].[DueDate],  
    [dbo].[FactInternetSales].[ShipDate]   
    FROM [dbo].[FactInternetSales]  
    WHERE (([OrderDate] >= N'2005-01-01 00:00:00') AND ([OrderDate] < N'2006-01-01 00:00:00'))  
    ```  
  
     이 문은 WHERE 절에 지정된 대로 OrderDate가 2005년인 행의 데이터를 모두 파티션에 포함하도록 지정합니다.  
  
6.  **유효성 검사**를 클릭합니다.  
  
     특정 열이 원본에 없음을 나타내는 경고가 표시됩니다. 이는 [3 단원: 열 이름 바꾸기](rename-columns.md)에서 모델의 Internet Sales 테이블에 있는 해당 열의 이름을 원본의 동일한 열과 다른 것 이기 때문입니다.  
  
#### <a name="to-create-a-partition-for-the-2006-year-in-the-internet-sales-table"></a>Internet Sales 테이블에서 2006 년에 대 한 파티션을 만들려면  
  
1.  **파티션 관리자** 대화 상자의 **파티션에서** `Internet Sales 2005` 방금 만든 파티션을 클릭 한 다음 **복사**를 클릭 합니다.  
  
2.  **파티션 이름**에을 입력 `Internet Sales 2006` 합니다.  
  
3.  SQL 문에서 파티션에 2006 년에 해당 하는 행만 포함 하도록 하려면 WHERE 절을 다음과 같이 바꿉니다.  
  
    ```  
    WHERE (([OrderDate] >= N'2006-01-01 00:00:00') AND ([OrderDate] < N'2007-01-01 00:00:00'))  
    ```  
  
#### <a name="to-create-a-partition-for-the-2007-year-in-the-internet-sales-table"></a>Internet Sales 테이블에서 2007 년에 대 한 파티션을 만들려면  
  
1.  **파티션 관리자** 대화 상자에서 **복사**를 클릭합니다.  
  
2.  **파티션 이름**에을 입력 `Internet Sales 2007` 합니다.  
  
3.  **전환 대상**에서 **쿼리 편집기**를 선택 합니다.  
  
4.  SQL 문에서 파티션에 2007 년에 해당 하는 행만 포함 하도록 하려면 WHERE 절을 다음과 같이 바꿉니다.  
  
    ```  
    WHERE (([OrderDate] >= N'2007-01-01 00:00:00') AND ([OrderDate] < N'2008-01-01 00:00:00'))  
    ```  
  
#### <a name="to-create-a-partition-for-the-2008-year-in-the-internet-sales-table"></a>Internet Sales 테이블에서 2008 년에 대 한 파티션을 만들려면  
  
1.  **파티션 관리자** 대화 상자에서 **새로 만들기**를 클릭합니다.  
  
2.  **파티션 이름**에을 입력 `Internet Sales 2008` 합니다.  
  
3.  **전환 대상**에서 **쿼리 편집기**를 선택 합니다.  
  
4.  SQL 문에서 파티션에 2008 년에 해당 하는 행만 포함 하도록 하려면 WHERE 절을 다음과 같이 바꿉니다.  
  
    ```  
    WHERE (([OrderDate] >= N'2008-01-01 00:00:00') AND ([OrderDate] < N'2009-01-01 00:00:00'))  
    ```  
  
#### <a name="to-create-a-partition-for-the-2009-year-in-the-internet-sales-table"></a>Internet Sales 테이블에서 2009년에 대한 파티션을 만들려면  
  
1.  **파티션 관리자** 대화 상자에서 **새로 만들기**를 클릭합니다.  
  
2.  **파티션 이름**에을 입력 `Internet Sales 2009` 합니다.  
  
3.  **전환 대상**에서 **쿼리 편집기**를 선택 합니다.  
  
4.  2009년에 해당하는 행만 파티션에 포함되도록 SQL 문에서 WHERE 절을 다음으로 바꿉니다.  
  
    ```  
    WHERE (([OrderDate] >= N'2009-01-01 00:00:00') AND ([OrderDate] < N'2010-01-01 00:00:00'))  
    ```  
  
## <a name="process-partitions"></a>파티션 처리  
 **파티션 관리자** 대화 상자에서 방금 만든 새 파티션 각각의 파티션 이름 옆에 별표(**\***)가 표시되는 것을 확인할 수 있습니다. 별표는 파티션이 처리되지 않았음을, 즉 새로 고쳐지지 않았음을 나타냅니다. 새 파티션을 만들면 파티션 처리 또는 테이블 처리 작업을 실행하여 해당 파티션의 데이터를 새로 고쳐야 합니다.  
  
#### <a name="to-process-internet-sales-partitions"></a>Internet Sales 파티션을 처리하려면  
  
1.  **확인** 을 클릭하여 **파티션 관리자** 대화 상자를 닫습니다.  
  
2.  모델 디자이너에서 **Internet Sales** 테이블을 클릭하고 **모델** 메뉴를 클릭한 다음 **처리** (새로 고침)를 가리키고 **파티션 처리**를 클릭합니다.  
  
3.  **파티션 처리** 대화 상자에서 **모드** 가 **기본값 처리**로 설정되었는지 확인합니다.  
  
4.  생성한 5개의 파티션 각각에 대한 **처리** 열에서 확인란을 선택한 후 **확인**을 클릭합니다.  
  
     가장 자격 증명을 요청하는 메시지가 표시되면 2단원의 6단계에서 지정한 Windows 사용자 이름 및 암호를 입력합니다.  
  
     그러면 **데이터 처리** 대화 상자가 나타나고 각 파티션에 대 한 처리 정보가 표시 됩니다. 파티션마다 서로 다른 개수의 행이 전송되었음을 확인할 수 있습니다. 이는 각 파티션에 해당 SQL 문의 WHERE 절에 지정된 연도의 행만 포함되어 있기 때문입니다. 2010년에는 해당하는 데이터가 없습니다.  
  
## <a name="next-steps"></a>다음 단계  
 이 자습서를 계속하려면 다음 단원인 [12단원: 역할 만들기](lesson-11-create-roles.md)로 이동하세요.  
  
  
