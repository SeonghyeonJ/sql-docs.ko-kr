---
title: 마이닝 모델 만들기 (DMX) | Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: e7215f50705b593130a69cfe076f0878b0ac03d6
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68889075"
---
# <a name="create-mining-model-dmx"></a>CREATE MINING MODEL(DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  데이터베이스에 새 마이닝 모델과 마이닝 구조를 만듭니다. 이 문에서 새 모델을 정의하거나 PMML(Predictive Model Markup Language)을 사용하여 모델을 만들 수 있습니다. 두 번째 옵션은 고급 사용자만 사용해야 합니다.  
  
 모델 이름에 "_structure"가 추가되어 마이닝 구조의 이름이 정해지므로 구조 이름이 모델 이름과 달리 고유합니다.  
  
 기존 마이닝 구조에 대 한 마이닝 모델을 만들려면 [ALTER 마이닝 structure &#40;DMX&#41;](../dmx/alter-mining-structure-dmx.md) 문을 사용 합니다.  
  
## <a name="syntax"></a>구문  
  
```  
  
CREATE [SESSION] MINING MODEL <model>  
(  
    [(<column definition list>)]  
)  
USING <algorithm> [(<parameter list>)] [WITH DRILLTHROUGH]  
CREATE MINING MODEL <model> FROM PMML <xml string>  
```  
  
## <a name="arguments"></a>인수  
 *model*  
 모델의 고유 이름입니다.  
  
 *열 정의 목록*  
 쉼표로 구분된 열 정의 목록입니다.  
  
 *알고리즘과*  
 현재 공급자가 정의한 데이터 마이닝 알고리즘 이름입니다.  
  
> [!NOTE]  
>  [DMSCHEMA_MINING_SERVICES 행 집합](https://docs.microsoft.com/bi-reference/schema-rowsets/data-mining/dmschema-mining-services-rowset)을 사용 하 여 현재 공급자가 지 원하는 알고리즘 목록을 검색할 수 있습니다. 현재 인스턴스에서 지원 되는 알고리즘을 보려면 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] [데이터 마이닝 속성](https://docs.microsoft.com/analysis-services/server-properties/data-mining-properties)을 참조 하세요.  
  
 *매개 변수 목록*  
 (선택 사항) 알고리즘에 대해 공급자가 정의한 매개 변수의 쉼표로 구분된 목록입니다.  
  
 *XML 문자열*  
 (고급 사용에만 해당) XML로 인코딩된 모델 (PMML)입니다. 문자열을 작은따옴표(')로 묶어야 합니다.  
  
 **Session** 절을 사용 하면 연결이 닫히거나 세션 시간이 초과 될 때 서버에서 자동으로 제거 되는 마이닝 모델을 만들 수 있습니다. **세션** 마이닝 모델은 사용자를 데이터베이스 관리자로 요구 하지 않고 연결이 열려 있는 동안에만 디스크 공간을 사용 하므로 유용 합니다.  
  
 **WITH DRILLTHROUGH** 절을 사용 하면 새 마이닝 모델에서 드릴스루를 사용할 수 있습니다. 드릴스루는 모델을 만들 때만 사용할 수 있습니다. 일부 모델 유형의 경우 사용자 지정 뷰어에서 모델을 찾아보는 데 드릴스루가 필요합니다. 드릴스루는 예측 또는 Microsoft 일반 콘텐츠 트리 뷰어를 사용하여 모델을 찾는 데 필요하지 않습니다.  
  
 **CREATE 마이닝 model** 문은 열 정의 목록, 알고리즘 및 알고리즘 매개 변수 목록을 기반으로 하는 새 마이닝 모델을 만듭니다.  
  
### <a name="column-definition-list"></a>열 정의 목록  
 각 열에 대해 다음 정보를 포함하여 열 정의 목록을 사용하는 모델 구조를 정의합니다.  
  
-   이름(필수)  
  
-   데이터 형식(필수)  
  
-   배포  
  
-   모델링 플래그 목록  
  
-   내용 유형(필수)  
  
-   **예측 요청-예측 또는** **PREDICT_ONLY** 절로 표시 되는이 열을 예측 하는 알고리즘을 나타냅니다.  
  
-   **관련 to** 절로 표시 되는 특성 열과의 관계 (적용 되는 경우에만 필수)  
  
 열 정의 목록에 대해 다음 구문을 사용하여 단일 열을 정의합니다.  
  
```  
<column name>    <data type>    [<Distribution>]    [<Modeling Flags>]    <Content Type>    [<prediction>]    [<column relationship>]   
```  
  
 열 정의 목록에 대해 다음 구문을 사용하여 중첩 테이블 열을 정의합니다.  
  
```  
<column name>    TABLE    [<prediction>] ( <non-table column definition list> )  
```  
  
 모델링 플래그를 제외하고 특정 그룹에서 하나의 절만 사용하여 열을 정의할 수 있습니다. 열 하나에 대해 여러 개의 모델링 플래그를 정의할 수 있습니다.  
  
 열을 정의하는 데 사용할 수 있는 데이터 형식, 내용 유형, 열 배포 및 모델링 플래그 목록은 다음 항목을 참조하십시오.  
  
-   [데이터 마이닝 &#40;데이터 형식&#41;](https://docs.microsoft.com/analysis-services/data-mining/data-types-data-mining)  
  
-   [데이터 마이닝&#41;&#40;내용 유형](https://docs.microsoft.com/analysis-services/data-mining/content-types-data-mining)  
  
-   [데이터 마이닝&#41;&#40;열 배포](https://docs.microsoft.com/analysis-services/data-mining/column-distributions-data-mining)  
  
-   [데이터 마이닝&#41;&#40;모델링 플래그](https://docs.microsoft.com/analysis-services/data-mining/modeling-flags-data-mining)  
  
 문에 절을 추가하여 두 열 간의 관계를 설명할 수 있습니다. [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]에서는 다음과 같은 \<열 관계> 절을 사용할 수 있습니다.  
  
 **관련 항목**  
 이 형식은 값 계층 구조를 나타냅니다. RELATED TO 열의 대상은 중첩 테이블의 키 열, 사례 행의 불연속 값 열 또는 RELATED TO 절이 있는 다른 열(중첩된 열을 나타냄)일 수 있습니다.  
  
 예측 절을 사용하여 예측 열의 사용 방법을 설명합니다. 다음 표에서는 사용 가능한 두 가지 절을 설명합니다.  
  
|\<예측> 절|Description|  
|---------------------------|-----------------|  
|**PREDICT**|이 열은 모델에 의해 예측될 수 있으며 다른 예측 가능 열 값을 예측하기 위해 입력 사례에 제공될 수 있습니다.|  
|**PREDICT_ONLY**|이 열은 모델에 의해 예측될 수 있지만 이 열의 값을 입력 사례에 사용하여 다른 예측 가능 열 값을 예측할 수는 없습니다.|  
  
### <a name="parameter-definition-list"></a>매개 변수 정의 목록  
 매개 변수 목록을 사용하여 마이닝 모델의 성능과 기능을 조정할 수 있습니다. 매개 변수 목록의 구문은 다음과 같습니다.  
  
```  
[<parameter> = <value>, <parameter> = <value>,...]  
```  
  
 각 알고리즘과 연결 된 매개 변수 목록은 [데이터 마이닝 알고리즘 &#40;Analysis Services 데이터 마이닝&#41;](https://docs.microsoft.com/analysis-services/data-mining/data-mining-algorithms-analysis-services-data-mining)를 참조 하세요.  
  
## <a name="remarks"></a>설명  
 기본 제공 테스트 데이터 집합이 있는 모델을 만들려는 경우 CREATE MINING STRUCTURE 문과 ALTER MINING STRUCTURE 문을 차례로 사용해야 합니다. 그러나 모든 모델 유형이 홀드아웃 데이터 집합을 지원하는 것은 아닙니다. 자세한 내용은 [CREATE MINING STRUCTURE&#40;DMX&#41;](../dmx/create-mining-structure-dmx.md)를 참조하세요.  
  
 CREATEMODEL 문을 사용 하 여 마이닝 모델을 만드는 방법에 대 한 연습은 [시계열 예측 DMX 자습서](https://msdn.microsoft.com/library/38ea7c03-4754-4e71-896a-f68cc2c98ce2)를 참조 하세요.  
  
## <a name="naive-bayes-example"></a>Naive Bayes 예  
 다음 예에서는 [!INCLUDE[msCoName](../includes/msconame-md.md)] Naive Bayes 알고리즘을 사용하여 새 마이닝 모델을 만듭니다. Bike Buyer 열은 예측 가능한 특성으로 정의됩니다.  
  
```  
CREATE MINING MODEL [NBSample]  
(  
    CustomerKey LONG KEY,   
    Gender TEXT DISCRETE,  
    [Number Cars Owned] LONG DISCRETE,  
    [Bike Buyer] LONG DISCRETE PREDICT  
)  
USING Microsoft_Naive_Bayes  
```  
  
## <a name="association-model-example"></a>연결 모델의 예  
 다음 예에서는 [!INCLUDE[msCoName](../includes/msconame-md.md)] 연결 알고리즘을 사용하여 새 마이닝 모델을 만듭니다. 이 문은 테이블 열을 사용하여 모델 정의 안에 테이블을 중첩하는 기능을 사용합니다. 모델은 *MINIMUM_PROBABILITY* 및 *MINIMUM_SUPPORT* 매개 변수를 사용 하 여 수정 됩니다.  
  
```  
CREATE MINING MODEL MyAssociationModel (  
    OrderNumber TEXT KEY,  
    [Products] TABLE PREDICT (  
        [Model] TEXT KEY  
    )  
)  
USING Microsoft_Association_Rules (Minimum_Probability = 0.1, MINIMUM_SUPPORT = 0.01)  
```  
  
## <a name="sequence-clustering-example"></a>시퀀스 클러스터링의 예  
 다음 예에서는 [!INCLUDE[msCoName](../includes/msconame-md.md)] 시퀀스 클러스터링 알고리즘을 사용하여 새 마이닝 모델을 만듭니다. 두 개의 키를 사용하여 모델을 정의합니다. OrderNumber 열은 사례 키로 사용되며 주문 순서를 지정합니다. LineNumber 열은 중첩된 테이블 키로 사용되며 항목이 주문에 추가된 시퀀스를 지정합니다.  
  
```  
CREATE MINING MODEL BuyingSequence (  
    [Order Number] TEXT KEY,  
    [Products] TABLE   
     (  
        [Line Number] LONG KEY SEQUENCE,  
        [Model] TEXT DISCRETE PREDICT  
    )  
)  
USING Microsoft_Sequence_Clustering  
```  
  
## <a name="time-series-example"></a>시계열 예  
 다음 예에서는 [!INCLUDE[msCoName](../includes/msconame-md.md)] 시계열 알고리즘을 사용하여 ARTxp 알고리즘을 사용함으로써 새 마이닝 모델을 만듭니다. ReportingDate는 시계열의 키 열이고 ModelRegion은 데이터 계열의 키 열입니다. 이 예에서는 데이터 주기를 매 12개월로 가정하므로 따라서 *PERIODICITY_HINT* 매개 변수는 12로 설정 됩니다.  
  
> [!NOTE]  
>  중괄호 문자를 사용 하 여 *PERIODICITY_HINT* 매개 변수를 지정 해야 합니다. 또한 값이 문자열 이기 때문에 "{\<numeric value>}" 작은따옴표로 묶어야 합니다.  
  
```  
CREATE MINING MODEL SalesForecast (  
        ReportingDate DATE KEY TIME,  
        ModelRegion TEXT KEY,  
        Amount LONG CONTINUOUS PREDICT,  
        Quantity LONG CONTINUOUS PREDICT  
)  
USING Microsoft_Time_Series (PERIODICITY_HINT = '{12}', FORECAST_METHOD = 'ARTXP')  
```  
  
## <a name="see-also"></a>참고 항목  
 [데이터 마이닝 확장 &#40;DMX&#41; 데이터 정의 문](../dmx/dmx-statements-data-definition.md)   
 [데이터 마이닝 확장 &#40;DMX&#41; 데이터 조작 문](../dmx/dmx-statements-data-manipulation.md)   
 [데이터 마이닝 확장 &#40;DMX&#41; 문 참조](../dmx/data-mining-extensions-dmx-statements.md)  
  
  
