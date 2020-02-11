---
title: 시퀀스 클러스터링 모델에 대 한 예측 만들기 (중급 데이터 마이닝 자습서) | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 94a8d4f9-a76a-49c5-9785-917010359511
author: minewiskan
ms.author: owend
manager: kfilee
ms.openlocfilehash: 893067e234d868ae6dde2f93d93bfd50458bfeb2
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2020
ms.locfileid: "63217738"
---
# <a name="creating-predictions-on-a-sequence-clustering-model-intermediate-data-mining-tutorial"></a>시퀀스 클러스터링 모델에서 예측 만들기(중급 데이터 마이닝 자습서)
  뷰어에서 시퀀스 클러스터링 모델을 탐색 하 여 더 잘 이해 한 후에는 데이터 마이닝 디자이너의 **마이닝 모델 예측** 탭에서 예측 쿼리 작성기를 사용 하 여 예측 쿼리를 만들 수 있습니다. 예측을 만들려면 먼저 시퀀스 클러스터링 모델을 선택한 다음 입력 데이터를 선택합니다. 입력의 경우 외부 데이터 원본을 사용하거나 단일 쿼리를 작성하고 대화 상자에 값을 제공할 수 있습니다.  
  
 이 단원에서는 사용자가 예측 쿼리 작성기를 사용하는 방법에 이미 익숙하고 시퀀스 클러스터링 모델과 관련된 쿼리를 작성하는 방법을 알아보려고 한다고 가정합니다. 예측 쿼리 작성기를 사용 하는 방법에 대 한 일반적인 내용은 [데이터 마이닝 쿼리 인터페이스](../../2014/analysis-services/data-mining/data-mining-query-tools.md) 또는 기본 데이터 마이닝 자습서, [예측 만들기 &#40;기본 데이터 마이닝 자습서 ](../../2014/tutorials/creating-predictions-basic-data-mining-tutorial.md)의 섹션을 참조 하세요&#41;.  
  
## <a name="creating-predictions-on-the-regional-model"></a>지역 모델에서 예측 만들기  
 이 시나리오의 경우 지역별로 예측이 어떻게 다른지를 알아보기 위해 먼저 몇 가지 단일 예측 쿼리를 만듭니다.  
  
#### <a name="to-create-a-singleton-query-on-a-sequence-clustering-model"></a>시퀀스 클러스터링 모델에서 단일 쿼리를 만들려면  
  
1.  데이터 마이닝 디자이너의 **마이닝 모델 예측** 탭을 클릭 합니다.  
  
2.  **마이닝 모델** 열 메뉴에서 **단일 쿼리**를 선택 합니다.  
  
     **마이닝 모델** 창과 **단일 쿼리 입력** 창이 나타납니다.  
  
3.  **마이닝 모델** 창에서 **모델 선택**을 클릭 합니다. 시퀀스 클러스터링 모드가 이미 선택되어 있는 경우 이 단계를 건너뛸 수 있습니다.  
  
     **마이닝 모델 선택** 대화 상자가 열립니다.  
  
4.  영역을 사용 하 여 마이닝 구조 **시퀀스 클러스터링**을 나타내는 노드를 확장 하 고 영역을 사용 하 여 모델 **시퀀스 클러스터링**을 선택 합니다. **확인**을 클릭합니다. 여기서는 입력 창을 무시하겠습니다. 예측 함수를 설정한 후 입력을 지정할 것입니다.  
  
5.  표에서 **원본** 아래의 빈 셀을 클릭 하 고 **예측 함수를 선택 합니다.** **필드**아래의 셀에서 **PredictSequence**를 선택 합니다.  
  
    > [!NOTE]  
    >  **Predict** 함수를 사용할 수도 있습니다. 이 경우 테이블 열을 인수로 사용 하는 **Predict** 함수 버전을 선택 해야 합니다.  
  
6.  **마이닝 모델** 창에서 중첩 테이블 `v Assoc Seq Line Items`을 선택 하 고 표 형태의 **PredictSequence** 함수에 대 한 **조건/인수** 상자로 끌어다 놓습니다.  
  
     테이블 및 열 이름을 끌어서 놓으면 구문 오류 없이 복잡한 문을 작성할 수 있습니다. 그러나 **PredictSequence** 함수에 대 한 다른 선택적 인수를 포함 하는 셀의 현재 내용을 대체 합니다. 다른 인수를 보려면 참조를 위해 임시로 함수의 두 번째 인스턴스를 표에 추가합니다.  
  
7.  예측 쿼리 작성기 위쪽 모퉁이에 있는 **결과** 단추를 클릭 합니다.  
  
 예상 결과에는 머리글 **식이**포함 된 단일 열이 포함 됩니다. **식** 열에는 다음과 같은 세 개의 열이 있는 중첩 테이블이 포함 됩니다.  
  
|$SEQUENCE|Line Number|모델|  
|---------------|-----------------|-----------|  
|1||Mountain-200|  
  
 이러한 결과의 의미는 무엇입니까? 어떤 입력도 지정하지 않았으므로 사례의 전체 모집단에 대한 예측이 수행되고 Analysis Services에서 가능성이 가장 높은 전체 예측을 반환합니다.  
  
### <a name="adding-inputs-to-a-singleton-prediction-query"></a>단일 예측 쿼리에 입력 추가  
 지금까지 어떤 입력도 지정하지 않았습니다. 다음 태스크에서는 **단일 쿼리 입력** 창을 사용 하 여 쿼리에 대 한 일부 입력을 지정 합니다. 먼저 [Region]을 지역별 시퀀스 클러스터링 모델에 대한 입력으로 사용하여 예측된 시퀀스가 모든 지역에 대해 동일한지 여부를 확인합니다. 그리고 나서 쿼리를 수정하여 각 예측에 대한 확률을 추가하고 결과를 보다 쉽게 볼 수 있도록 평면화하는 방법을 배웁니다.  
  
##### <a name="to-generate-predictions-for-a-specific-customer-group"></a>특정 고객 그룹에 대한 예측을 생성하려면  
  
1.  예측 쿼리 작성기의 왼쪽 위 모서리에 있는 **디자인** 단추를 클릭 하 여 쿼리 작성 표로 다시 전환 합니다.  
  
2.  **단일 쿼리 입력** 대화 상자에서 `Region`의 **값** 상자를 클릭 하 고 **유럽**을 선택 합니다.  
  
3.  **결과** 단추를 클릭 하 여 유럽 고객에 대 한 예측을 봅니다.  
  
4.  예측 쿼리 작성기의 왼쪽 위 모서리에 있는 **디자인** 단추를 클릭 하 여 쿼리 작성 표로 다시 전환 합니다.  
  
5.  **단일 쿼리 입력** 대화 상자에서 `Region`의 **값** 상자를 클릭 하 고 **북아메리카**를 선택 합니다.  
  
6.  **결과** 단추를 클릭 하 여 북아메리카 고객에 대 한 예측을 봅니다.  
  
### <a name="adding-probabilities-by-using-a-custom-expression"></a>사용자 지정 식을 사용하여 확률 추가  
 확률은 예측의 특성이며 중첩 테이블로 출력되기 때문에 각 예측에 대한 확률을 출력하는 작업은 다소 복잡합니다. DMX(Data Mining Extensions)에 익숙하면 중첩 테이블에 하위 SELECT 문을 추가하도록 쿼리를 쉽게 변경할 수 있습니다. 그러나 사용자 지정 식을 추가하여 예측 쿼리 작성기에서 하위 SELECT 문을 만들 수도 있습니다.  
  
##### <a name="to-output-probabilities-for-a-predicted-sequence-by-using-a-custom-expression"></a>사용자 지정 식을 사용하여 예측된 시퀀스에 대한 확률을 출력하려면  
  
1.  예측 쿼리 작성기의 왼쪽 위 모서리에 있는 **디자인** 단추를 클릭 하 여 쿼리 작성 표로 다시 전환 합니다.  
  
2.  표의 **원본**에서 새 행을 클릭 하 고 **사용자 지정 식**을 선택 합니다.  
  
3.  **필드** 아래에 있는 상자를 비워 둡니다.  
  
4.  **별칭**에를 입력 `t`합니다.  
  
5.  **조건/인수** 상자에 다음 코드 샘플과 같이 전체 하위 select 문을 입력 합니다. 시작 괄호와 끝 괄호를 포함해야 합니다.  
  
    ```  
    (SELECT PredictProbability([Model]) FROM PredictSequence([Sequence Clustering with Region].[v Assoc Seq Line Items]))  
    ```  
  
6.  **결과** 단추를 클릭 하 여 유럽 고객에 대 한 예측을 봅니다.  
  
 이제 결과에 두 개의 중첩 테이블인 예측이 있는 테이블과 예측에 대한 확률이 있는 테이블이 포함됩니다. 쿼리가 작동하지 않는 경우 쿼리 디자인 뷰로 전환하고 다음과 같은 전체 쿼리 문을 검토할 수 있습니다.  
  
```  
SELECT  
  PredictSequence([Sequence Clustering with Region].[v Assoc Seq Line Items]),  
  ( (SELECT PredictProbability([Model]) FROM PredictSequence([Sequence Clustering with Region].[v Assoc Seq Line Items]))) as [t]  
FROM  
  [Sequence Clustering with Region]  
NATURAL PREDICTION JOIN  
(SELECT 'Europe' AS [Region]) AS t  
```  
  
### <a name="working-with-results"></a>결과 작업  
 결과에 중첩 테이블이 많이 있는 경우 결과를 보다 쉽게 볼 수 있도록 평면화할 수 있습니다. 이렇게 하려면 수동으로 쿼리를 수정하고 `FLATTENED` 키워드를 추가합니다.  
  
##### <a name="to-flatten-nested-rowsets-in-a-prediction-query"></a>예측 쿼리에서 중첩 행 집합을 평면화하려면  
  
1.  예측 쿼리 작성기의 모서리에 있는 **쿼리** 단추를 클릭 합니다.  
  
     표가 열린 창으로 변경됩니다. 이 창에서는 예측 쿼리 작성기에서 만든 DMX 문을 보고 수정할 수 있습니다.  
  
2.  
  `SELECT` 키워드 다음에 `FLATTENED`를 입력합니다.  
  
     쿼리의 전체 텍스트는 다음과 같은 형태가 됩니다.  
  
    ```  
    SELECT FLATTENED  
      PredictSequence([Sequence Clustering with Region].[v Assoc Seq Line Items]),  
      ( (SELECT PredictProbability([Model]) FROM PredictSequence([Sequence Clustering with Region].[v Assoc Seq Line Items]))) as [t]  
    FROM  
      [Sequence Clustering with Region]  
    NATURAL PREDICTION JOIN  
    (SELECT 'Europe' AS [Region]) AS t  
    ```  
  
3.  예측 쿼리 작성기 위쪽 모퉁이에 있는 **결과** 단추를 클릭 합니다.  
  
 쿼리를 수동으로 편집한 경우에는 변경 내용 손실 없이 디자인 뷰로 다시 전환할 수 없습니다. 그러나 수동으로 만든 DMX 문을 텍스트 파일로 저장한 다음 디자인 뷰로 다시 전환할 수 있습니다. 이렇게 하면 쿼리가 디자인 뷰에서 유효했던 마지막 버전으로 되돌려집니다.  
  
## <a name="creating-predictions-on-the-related-model"></a>관련 모델에서 예측 만들기  
 이전 예에서는 사용자가 모델에서 지역 간의 차이점을 발견했는지 여부를 알려고 했으므로 Region이라고 하는 사례 테이블 열을 단일 예측 쿼리에 대한 입력으로 사용했습니다. 그러나 모델을 탐색한 결과 차이점이 그리 크지 않아 지역별 제품 권장 사항의 사용자 지정을 정당화하기 어렵다고 판단했습니다. 실제로 예측하려고 하는 것은 고객이 선택하는 항목입니다. 따라서 다음 쿼리에서는 Region을 포함하지 않는 시퀀스 클러스터링 모델을 사용하여 모든 고객에 대한 권장 사항을 생성합니다.  
  
### <a name="using-nested-table-columns-as-input"></a>중첩 테이블 열을 입력으로 사용  
 먼저 단일 항목을 입력으로 사용하고 다음으로 가능성이 가장 높은 항목을 반환하는 단일 예측 쿼리를 만듭니다. 이러한 종류의 예측을 가져오려면 중첩 테이블 열을 입력 값으로 사용해야 합니다. 이는 예측하는 특성인 Model이 중첩 테이블의 일부분이기 때문입니다. Analysis Services는 예측 쿼리 작성기를 사용 하 여 중첩 테이블 특성에 대 한 예측 쿼리를 쉽게 만들 수 있도록 하는 **중첩 테이블 입력** 대화 상자를 제공 합니다.  
  
##### <a name="to-use-a-nested-table-as-input-to-a-prediction"></a>중첩 테이블을 예측에 대한 입력으로 사용하려면  
  
1.  예측 쿼리 작성기의 왼쪽 위 모서리에 있는 **디자인** 단추를 클릭 하 여 쿼리 작성 표로 다시 전환 합니다.  
  
2.  **단일 쿼리 입력** 대화 상자에서의 `Region` **값** 상자를 클릭 하 고 빈 행을 선택 하 여이 필드에 대 한 입력을 지웁니다.  
  
3.  **단일 쿼리 입력** 대화 상자에서의 `vAssocSeqLineItems` **값** 상자를 클릭 한 다음 (...) 단추를 클릭 합니다.  
  
4.  **중첩 테이블 입력** 대화 상자에서 **추가**를 클릭 합니다.  
  
5.  새 행에서 아래의 `Model`상자를 클릭 하 고 목록에서 여행용 타이어를 선택 합니다. **확인**을 클릭합니다.  
  
6.  **결과** 단추를 클릭 하 여 예측을 봅니다.  
  
 모델은 Touring Tire를 첫 번째 항목으로 선택한 모든 고객에 대해 아래와 같이 다음 항목을 권장합니다. 모델을 탐색한 결과 고객이 Touring Tire 제품과 Touring Tire Tube 제품을 함께 구매하는 경우가 많음을 알게되었으므로 이러한 권장 사항은 적합한 것 같습니다.  
  
|$SEQUENCE|Line Number|모델|  
|---------------|-----------------|-----------|  
|1||Touring Tire Tube|  
|2||Sport-100|  
|3||Long-Sleeve Logo Jersey|  
  
### <a name="creating-a-bulk-prediction-query-using-nested-table-inputs"></a>중첩 테이블 입력을 사용하여 대량 예측 쿼리 만들기  
 이제 권장 사항을 만들 때 사용할 수 있는 예측 종류를 모델에서 만들 수 있음을 확인했으므로 외부 데이터 원본에 매핑되는 예측 쿼리를 만듭니다. 해당 데이터 원본은 현재 제품을 나타내는 값을 제공합니다. 고객 ID 및 제품 목록을 입력으로 제공하는 예측 쿼리를 만들려고 하기 때문에 고객 테이블을 사례 테이블로 추가하고 구매 테이블은 중첩 테이블로 추가합니다. 그리고 나서 권장 사항을 만들기 위해 이전에 한 대로 예측 함수를 추가합니다.  
  
 이는 3단원에서 시장 바구니 시나리오에 대한 예측을 만드는 데 사용하는 절차와 동일하지만 시퀀스 클러스터링 모델에서는 예측도 주문을 입력해야 합니다.  
  
##### <a name="to-create-a-prediction-query-using-nested-table-inputs"></a>중첩 테이블 입력을 사용하여 예측 쿼리를 만들려면  
  
1.  **마이닝 모델** 창에서 시퀀스 클러스터링 모델을 선택 합니다 (아직 선택 하지 않은 경우).  
  
2.  **입력 테이블 선택** 대화 상자에서 **사례 테이블 선택**을 클릭 합니다.  
  
3.  **테이블 선택** 대화 상자에서 데이터 원본에 대해 Orders를 선택 합니다. **테이블/뷰 이름** 목록에서 vAssocSeqOrders를 선택 하 고 **확인**을 클릭 합니다.  
  
4.  **입력 테이블 선택** 대화 상자에서 **중첩 테이블 선택**을 클릭 합니다.  
  
5.  **테이블 선택** 대화 상자에서 **데이터 원본**에 대해 Orders를 선택 합니다. **테이블/뷰 이름** 목록에서 vAssocSeqLineItems를 선택 하 고 **확인**을 클릭 합니다.  
  
     Analysis Services에서는 데이터 형식이 일치하고 열 이름이 유사한 경우 자동으로 관계를 검색하고 만들려고 합니다. 만든 관계가 잘못 된 경우 조인 선을 마우스 오른쪽 단추로 클릭 하 고 **연결 수정** 을 선택 하 여 열 매핑을 편집 하거나 조인 선을 마우스 오른쪽 단추로 클릭 하 고 **삭제** 를 선택 하 여 관계를 완전히 제거할 수 있습니다. 이 경우 테이블 원본 뷰에 테이블이 이미 조인되어 있기 때문에 이러한 관계는 자동으로 디자인 창에 추가됩니다.  
  
6.  표에 새 행을 추가합니다. **원본**에 대해 vAssocSeqOrders를 선택 하 고 **필드**에 대해 customerkey를 선택 합니다.  
  
7.  표에 새 행을 추가합니다. **원본**에 대해 **예측 함수**를 선택 하 고 **필드**에 대해 **PredictSequence**를 선택 합니다.  
  
8.  VAssocSeqLineItems을 **조건/인수** 상자로 끌어다 놓습니다. **조건/인수** 상자의 끝을 클릭 하 고 다음 인수를 입력 `2`합니다.  
  
     **조건/인수** 상자의 전체 텍스트는 다음과 같아야 합니다.`[Sequence Clustering].[v Assoc Seq Line Items],2`  
  
9. **결과** 단추를 클릭 하 여 각 고객에 대 한 예측을 봅니다.  
  
 시퀀스 클러스터링 모델에 대한 자습서를 완료했습니다.  
  
## <a name="next-steps"></a>다음 단계  
 중간 데이터 마이닝 자습서의 모든 섹션을 완료 하 여 [Analysis Services 데이터 마이닝&#41;&#40;](../../2014/tutorials/intermediate-data-mining-tutorial-analysis-services-data-mining.md)하는 경우 다음 단계를 통해 DMX (Data 마이닝 확장) 문을 사용 하 여 모델을 작성 하 고 예측을 생성 하는 방법을 배울 수 있습니다. 자세한 내용은 [DMX를 사용 하 여 데이터 마이닝 모델 만들기 및 쿼리: 자습서 &#40;Analysis Services 데이터 마이닝&#41;](../../2014/tutorials/create-query-data-mining-models-dmx-tutorials.md)를 참조 하세요.  
  
 프로그래밍 개념에 익숙한 경우 AMO(Analysis Management Objects)를 사용하여 프로그래밍 방식으로 데이터 마이닝 개체를 사용할 수도 있습니다. 자세한 내용은 [AMO 데이터 마이닝 클래스](https://docs.microsoft.com/bi-reference/amo/amo-data-mining-classes)를 참조하세요.  
  
## <a name="see-also"></a>참고 항목  
 [시퀀스 클러스터링 모델 쿼리 예제](../../2014/analysis-services/data-mining/sequence-clustering-model-query-examples.md)   
 [시퀀스 클러스터링 모델에 대 한 마이닝 모델 콘텐츠 &#40;Analysis Services 데이터 마이닝&#41;](../../2014/analysis-services/data-mining/mining-model-content-for-sequence-clustering-models.md)  
  
  
