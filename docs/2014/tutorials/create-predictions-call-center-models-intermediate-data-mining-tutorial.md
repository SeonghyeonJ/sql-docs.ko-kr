---
title: 콜 센터 모델 (중급 데이터 마이닝 자습서)에 대 한 예측 만들기 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 5be0cec7-f639-4eeb-835e-e3204ae619e9
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 30f24ab457669f572189d2eb13deca3f672f5e18
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/11/2019
ms.locfileid: "56025414"
---
# <a name="creating-predictions-for-the-call-center-models-intermediate-data-mining-tutorial"></a>콜 센터 모델에 대한 예측 만들기(중급 데이터 마이닝 자습서)
  교대조, 전화 상담원 수, 호출 및 서비스 등급에 대한 몇 가지 사항을 배웠으므로 이제 비즈니스 분석 및 계획에 사용할 수 있는 일부 예측 쿼리를 만들 준비가 되었습니다. 먼저 탐구 모델에서 일부 예측을 만들어 몇 가지 가정을 테스트합니다. 다음으로 로지스틱 회귀 모델을 사용하여 대량 예측을 만듭니다.  
  
 이 단원에서는 사용자가 예측 쿼리의 개념에 대해 이미 잘 알고 있다고 가정합니다.  
  
## <a name="creating-predictions-using-the-neural-network-model"></a>신경망 모델을 사용하여 예측 만들기  
 다음 예에서는 탐색을 위해 만든 신경망 모델을 사용하여 단일 예측을 만드는 방법을 보여 줍니다. 단일 예측은 모델에서 서로 다른 값을 사용하여 결과를 살펴볼 수 있는 좋은 방법입니다. 이 시나리오에서는 6명의 경력 전화 상담원이 근무하는 경우 요일을 지정하지 않고 자정 교대조에 대한 서비스 등급을 예측합니다.  
  
#### <a name="to-create-a-singleton-query-by-using-the-neural-network-model"></a>신경망 모델을 사용하여 단일 쿼리를 만들려면  
  
1.  [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]에서 사용할 모델이 들어 있는 솔루션을 엽니다.  
  
2.  데이터 마이닝 디자이너에서을 클릭 합니다 **마이닝 모델 예측** 탭 합니다.  
  
3.  에 **마이닝 모델** 창 클릭 **모델 선택**합니다.  
  
4.  합니다 **마이닝 모델 선택** 대화 상자에는 마이닝 구조 목록을 보여 줍니다. 마이닝 구조를 확장하여 해당 구조와 연결된 마이닝 모델 목록을 봅니다.  
  
5.  Call Center Default 마이닝 구조를 확장하고 신경망 모델 Call Center - LR을 선택합니다.  
  
6.  **마이닝 모델** 메뉴에서 **단일 쿼리**를 선택합니다.  
  
     합니다 **단일 쿼리 입력** 마이닝 모델의 열에 매핑할 열을 사용 하 여 대화 상자가 나타납니다.  
  
7.  에 **단일 쿼리 입력** 대화 상자에서 Shift에 대 한 행을 클릭 한 다음 선택 *자정*합니다.  
  
8.  Lvl 2 Operators 및 유형에 대 한 행을 클릭 합니다. `6`합니다.  
  
9. 아래에 있는 절반을 **마이닝 모델 예측** 탭에서 표의 첫 번째 행을 클릭 합니다.  
  
10. 에 **소스** 열에서 아래쪽 화살표를 클릭 하 고 선택 **예측 함수**합니다. 에 **필드** 열 선택 **PredictHistogram**합니다.  
  
     이 예측 함수를 사용 하 여 자동으로 사용할 수 있는 인수 목록에 표시 합니다 **조건/인수** 상자입니다.  
  
11. 열 목록에서 ServiceGrade 열을 끌어 합니다 **마이닝 모델** 창 합니다 **조건/인수** 상자.  
  
     열 이름이 자동으로 인수로 삽입됩니다. 이 입력란으로 끌어다 놓을 임의의 예측 가능한 특성 열을 선택할 수 있습니다.  
  
12. 단추를 클릭 **스위치를 쿼리 결과 보기**, 예측 쿼리 작성기의 위쪽 모서리에 있습니다.  
  
 예상 결과에는 각 예측에 대한 지지도 및 확률 값과 함께 이 입력에 따라 각 서비스 등급에 대해 가능한 예측 값이 포함됩니다. 언제든지 디자인 뷰로 돌아가 입력을 변경하거나 더 많은 입력을 추가할 수 있습니다.  
  
## <a name="creating-predictions-by-using-a-logistic-regression-model"></a>로지스틱 회귀 모델을 사용하여 예측 만들기  
 비즈니스 문제 관련 특성을 이미 알고 있는 경우 로지스틱 회귀 모델을 사용하여 일부 특성을 변경했을 때의 효과를 예측할 수 있습니다. 로지스틱 회귀는 일반적으로 독립 변수의 변경 내용을 기반으로 예측을 수행 하는 데 사용 되는 통계 방법: 예를 들어,이 재무 상태 평가 고객 인구 통계에 따라 고객 행동을 예측할 수 있습니다.  
  
 이 작업에서는 예측에 사용할 데이터 원본을 만든 다음 여러 가지 비즈니스 질문에 대답하는 데 유용한 예측을 만드는 방법을 배웁니다.  
  
### <a name="generating-data-used-for-bulk-prediction"></a>대량 예측에 사용할 데이터 생성  
 입력된 데이터를 제공 하는 방법은 여러 가지: 스프레드시트에서 직원 수준을 가져오고 하 고 다음 달에 대 한 서비스 품질을 예측 하는 모델을 통해 해당 데이터를 실행할 수 있습니다 예를 들어 있습니다.  
  
 이 단원에서는 데이터 원본 뷰 디자이너를 사용하여 명명된 쿼리를 만듭니다. 이 명명된 쿼리는 직원 중 전화 상담원의 최대 수, 받은 최소 전화 수 및 발생한 평균 문제 수를 일정표의 각 교대조에 대해 계산하는 사용자 지정 Transact-SQL 문입니다. 그런 다음 해당 데이터를 마이닝 모델에 조인하여 다가올 날짜의 계열에 대한 예측을 수행합니다.  
  
##### <a name="to-generate-input-data-for-a-bulk-prediction-query"></a>대량 예측 쿼리에 대한 입력 데이터를 생성하려면  
  
1.  솔루션 탐색기에서 마우스 오른쪽 단추로 클릭 **데이터 원본 뷰**를 선택한 후 **새 데이터 원본 뷰**합니다.  
  
2.  데이터 원본 뷰 마법사에서 선택 [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)] 데이터 원본 및 클릭 **다음**합니다.  
  
3.  에 **테이블 및 뷰 선택** 페이지에서 **다음** 테이블을 선택 하지 않고 있습니다.  
  
4.  에 **마법사 완료** 페이지에서 이름을 입력 하 고 `Shifts`입니다.  
  
     이 이름은 솔루션 탐색기에서 데이터 원본 뷰의 이름으로 나타납니다.  
  
5.  빈 디자인 창을 마우스 오른쪽 단추로 클릭 한 다음 선택 **새 명명 된 쿼리**합니다.  
  
6.  에 **명명 된 쿼리 만들기** 대화 상자에 대 한 **이름**, 형식 `Shifts for Call Center`합니다.  
  
     이 이름은 데이터 원본 뷰 디자이너에 명명된 쿼리의 이름으로만 나타납니다.  
  
7.  다음 쿼리 문을 대화 상자의 아래쪽 중간에 있는 SQL 텍스트 창에 붙여 넣습니다.  
  
    ```  
    SELECT DISTINCT WageType, Shift,   
    AVG(Orders) as AvgOrders, MIN(Orders) as MinOrders, MAX(Orders) as MaxOrders,  
    AVG(Calls) as AvgCalls, MIN(Calls) as MinCalls, MAX(Calls) as MaxCalls,  
    AVG(LevelTwoOperators) as AvgOperators, MIN(LevelTwoOperators) as MinOperators, MAX(LevelTwoOperators) as MaxOperators,  
    AVG(IssuesRaised) as AvgIssues, MIN(IssuesRaised) as MinIssues, MAX(IssuesRaised) as MaxIssues  
    FROM dbo.FactCallCenter  
    GROUP BY Shift, WageType  
    ```  
  
8.  디자인 창에서 Shifts for Call Center 테이블을 마우스 오른쪽 단추로 누르고 **데이터 탐색** T-SQL 쿼리가 반환한 데이터를 미리 보려면.  
  
9. 탭을 마우스 오른쪽 단추로 클릭 **Shifts.dsv (디자인)** 을 클릭 한 다음 **저장** 새 데이터 원본 뷰 정의 저장 합니다.  
  
### <a name="predicting-service-metrics-for-each-shift"></a>각 교대조에 대한 서비스 메트릭 예측  
 지금까지 각 교대조에 대한 일부 값을 생성했으므로 이제는 이러한 값을 작성한 로지스틱 회귀 모델의 입력으로 사용하여 비즈니스 계획에 사용할 수 있는 일부 예측을 생성합니다.  
  
##### <a name="to-use-the-new-dsv-as-input-to-a-prediction-query"></a>새 DSV를 예측 쿼리에 대한 입력으로 사용하려면  
  
1.  데이터 마이닝 디자이너에서을 클릭 합니다 **마이닝 모델 예측** 탭 합니다.  
  
2.  에 **마이닝 모델** 창 클릭 **모델 선택**, Call Center-LR 사용 가능한 모델 목록에서 선택 합니다.  
  
3.  **마이닝 모델** 메뉴 옵션의 선택을 취소 **단일 쿼리**합니다. 단일 쿼리 입력이 손실된다는 경고가 표시됩니다. **확인**을 클릭합니다.  
  
     합니다 **단일 쿼리 입력** 대화 상자를 사용 하 여 바뀝니다 합니다 **입력 테이블 선택** 대화 상자.  
  
4.  **사례 테이블 선택**을 클릭합니다.  
  
5.  에 **테이블 선택** 대화 상자, 데이터 원본 목록에서 selectShifts 합니다. 에 **테이블/뷰 이름** 목록에서 shifts for Call Center (있습니다 수 자동으로 선택) 하 고 클릭 한 다음 **확인 합니다.**  
  
     합니다 **마이닝 모델 예측** 디자인 화면이 입력 데이터에서 및 모델의 열 이름과 데이터 형식을 기반으로 생성 된 매핑을 표시 하도록 업데이트 됩니다.  
  
6.  조인 선을 중 하나를 마우스 오른쪽 단추로 클릭 하 고 선택한 **연결 수정**합니다.  
  
     이 대화 상자에서는 매핑된 열과 매핑되지 않은 열을 정확하게 볼 수 있습니다. 마이닝 모델에는 Calls, Orders, IssuesRaised 및 LvlTwoOperators 열이 포함되어 있으므로 사용자가 원본 데이터의 이 열을 기반으로 만든 집계로 매핑할 수 있습니다. 이 시나리오에서는 평균으로 매핑합니다.  
  
7.  LevelTwoOperators, 옆의 빈 셀을 클릭 하 고 선택 **Shifts for Call Center.AvgOperators**합니다.  
  
8.  선택 Calls 옆의 빈 셀을 클릭 **Shifts for Call Center.AvgCalls**합니다. 클릭 하 고 **확인**합니다.  
  
##### <a name="to-create-the-predictions-for-each-shift"></a>각 교대조에 대한 예측을 만들려면  
  
1.  아래쪽 표에 절반를 **예측 쿼리 작성기**에서 빈 셀을 클릭 **원본** 한 다음 Shifts for Call Center를 선택 합니다.  
  
2.  아래의 빈 셀 **필드**, Shift를 선택 합니다.  
  
3.  표의 다음 빈 줄을 클릭하고 위에 설명한 절차를 반복하여 WageType에 대한 다른 행을 추가합니다.  
  
4.  표에서 다음 빈 줄을 클릭합니다. 에 **원본** 열 선택 **예측 함수**합니다. 에 **필드** 열 선택 **Predict**합니다.  
  
5.  ServiceGrade 열을 끌어서에서 합니다 **마이닝 모델** 표 아래로 창과에 **조건/인수** 셀입니다. 에 **별칭** 필드에 입력 **Predicted Service Grade**합니다.  
  
6.  표에서 다음 빈 줄을 클릭합니다. 에 **원본** 열 선택 **예측 함수**합니다. 에 **필드** 열 선택 **PredictProbability**합니다.  
  
7.  ServiceGrade 열을 끌어서에서 합니다 **마이닝 모델** 표 아래로 창과에 **조건/인수** 셀입니다. 에 **별칭** 필드에 입력 **확률**합니다.  
  
8.  클릭 **쿼리 결과 뷰로 전환** 예측을 봅니다.  
  
 다음 표에서는 각 교대조에 대한 결과 예를 보여 줍니다.  
  
|Shift|WageType|Predicted Service Grade|Probability|  
|-----------|--------------|-----------------------------|-----------------|  
|AM|holiday|0.165|0.377520666|  
|midnight|holiday|0.105|0.364105573|  
|PM1|holiday|0.165|0.40056055|  
|PM2|holiday|0.165|0.338532973|  
|AM|weekday|0.165|0.370847617|  
|midnight|weekday|0.08|0.352999173|  
|PM1|weekday|0.165|0.317419177|  
|PM2|weekday|0.105|0.311672027|  
  
### <a name="predicting-the-effect-of-reduced-response-time-on-service-grade"></a>응답 시간 단축이 서비스 등급에 미치는 영향 예측  
 지금까지 각 교대조에 대한 일부 평균 값을 생성하고 이러한 값을 로지스틱 회귀 모델의 입력으로 사용했습니다. 그러나 중단율을 0.00-0.05 범위 내로 유지하려는 비즈니스 목표에는 이 결과가 충분하지 않습니다.  
  
 따라서 서비스 등급에 대한 응답 시간의 큰 영향력을 보여 준 원래 모델을 기반으로 하여 운영 팀에서는 호출에 응답하는 평균 시간을 줄이면 서비스 품질을 향상시킬 수 있는지를 평가하는 일부 예측을 실행하기로 결정합니다. 예를 들어 현재 통화 응답 시간을 90% 또는 80%까지 줄이면 서비스 등급 값이 어떻게 될지 살펴 봅니다.  
  
 각 교대조의 평균 응답 시간을 계산하는 DSV(데이터 원본 뷰)를 만드는 것은 간단합니다. 그런 다음에는 해당 평균 응답 시간의 80% 또는 90%를 계산하는 열을 추가합니다. 그런 다음 DSV를 모델에 대한 입력으로 사용할 수 있습니다.  
  
 정확한 단계를 여기에서 보여 주지는 않지만 다음 표에서 응답 시간을 현재 응답 시간의 80% 또는 90%까지 줄일 경우 서비스 등급에 대한 영향을 비교해 봅니다.  
  
 이러한 결과를 통해 서비스 품질의 향상을 위해서는 대상 교대조에서 응답 시간을 현재 수준의 90%로 줄여야 한다는 결론을 내릴 수 있습니다.  
  
|교대조, 임금 및 요일|현재 평균 응답 시간으로 예측되는 서비스 품질|응답 시간을 90퍼센트 줄여 예측되는 서비스 품질|응답 시간 80% 감소를 사용 하 여 서비스 품질 예측|  
|--------------------------|------------------------------------------------------------------|--------------------------------------------------------------------------|--------------------------------------------------------------------------|  
|Holiday AM|0.165|0.05|0.05|  
|Holiday PM1|0.05|0.05|0.05|  
|Holiday Midnight|0.165|0.05|0.05|  
  
 모델에서 만들 수 있는 여러 가지 기타 예측 쿼리가 있습니다. 예를 들어 특정 서비스 수준을 만족하기 위해 또는 특정 개수의 들어오는 호출에 응답하기 위해 필요한 전화 상담원 수를 예측할 수 있습니다. 로지스틱 회귀 모델에 여러 출력을 포함할 수 있기 때문에 여러 개별 모델을 만들지 않아도 서로 다른 독립 변수 및 결과를 쉽게 경험할 수 있습니다.  
  
## <a name="remarks"></a>Remarks  
 Excel 2007용 데이터 마이닝 추가 기능에서는 로지스틱 회귀 마법사를 제공하기 때문에 서비스 등급을 특정 교대조에 대한 대상 수준으로 개선하는 데 필요한 두 번째 수준의 전화 상담원의 수와 같은 복잡한 질문에 보다 쉽게 대답할 수 있습니다. 데이터 마이닝 추가 기능은 무료로 다운로드할 수 있으며 신경망 또는 로지스틱 회귀 알고리즘을 기반으로 하는 마법사를 포함합니다. 자세한 내용은 다음 링크를 참조하십시오.  
  
-   [SQL Server 2005 데이터 마이닝 추가 기능 Office 2007 용](https://www.microsoft.com/sql/technologies/dm/addins.mspx): 목표 검색 및 가상 시나리오 분석  
  
-   [SQL Server 2008 데이터 마이닝 추가 기능 Office 2007 용](https://go.microsoft.com/fwlink/?LinkID=117790): 목표 검색 시나리오 분석, 가상 시나리오 분석 및 예측 계산기  
  
## <a name="conclusion"></a>결론  
 이 단원에서는 Microsoft 신경망 알고리즘 및 Microsoft 로지스틱 회귀 알고리즘을 기반으로 하는 마이닝 모델을 생성, 사용자 지정 및 해석하는 방법을 배웠습니다. 이러한 모델 유형은 복잡하고 거의 제한 없이 다양하게 분석될 수 있으므로 복잡하고 마스터하기가 어렵습니다.  
  
 그러나 이러한 알고리즘은 요인의 여러 조합을 통해 반복을 수행하고 가장 강력한 상관 관계를 자동으로 식별할 수 있습니다. 이를 통해 Transact-SQL이나 PowerPivot을 사용한 데이터의 수동 탐색을 통해서는 발견하기가 매우 어려운 통찰력에 대한 통계학적 지원을 제공합니다.  
  
## <a name="see-also"></a>관련 항목  
 [로지스틱 회귀 모델 쿼리 예제](../../2014/analysis-services/data-mining/logistic-regression-model-query-examples.md)   
 [Microsoft 로지스틱 회귀 알고리즘](../../2014/analysis-services/data-mining/microsoft-logistic-regression-algorithm.md)   
 [Microsoft Neural Network Algorithm](../../2014/analysis-services/data-mining/microsoft-neural-network-algorithm.md)   
 [신경망 모델 쿼리 예제](../../2014/analysis-services/data-mining/neural-network-model-query-examples.md)  
  
  
