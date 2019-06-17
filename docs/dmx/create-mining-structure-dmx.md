---
title: MINING STRUCTURE (DMX) 만들기 | Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: ea04b08f98385755f006c1a67125a87dc71e41f1
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62854335"
---
# <a name="create-mining-structure-dmx"></a>CREATE MINING STRUCTURE(DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  데이터베이스에 새 마이닝 구조를 만들고 필요에 따라 학습 및 테스트 파티션을 정의합니다. 마이닝 구조를 만든 후 사용할 수 있습니다 합니다 [ALTER MINING STRUCTURE &#40;DMX&#41; ](../dmx/alter-mining-structure-dmx.md) 마이닝 구조에 모델을 추가 하는 문입니다.  
  
## <a name="syntax"></a>구문  
  
```  
  
CREATE [SESSION] MINING STRUCTURE <structure>  
(  
    [(<column definition list>)]  
)  
[WITH HOLDOUT (<holdout-specifier> [OR <holdout-specifier>])]  
[REPEATABLE(<holdout seed>)]  
<holdout-specifier>::=  <holdout-maxpercent> PERCENT | <holdout-maxcases> CASES  
```  
  
## <a name="arguments"></a>인수  
 *structure*  
 구조의 고유한 이름입니다.  
  
 *열 정의 목록*  
 쉼표로 구분된 열 정의 목록입니다.  
  
 *holdout-maxpercent*  
 테스트용으로 따로 보관하는 데이터의 비율을 나타내는 1에서 100 사이의 정수입니다.  
  
 *holdout-maxcases*  
 테스트에 사용할 사례의 최대 수를 나타내는 정수입니다.  
  
 최대 사례에 지정된 값이 입력 사례 수보다 크면 모든 입력 사례가 테스트에 사용되며 경고가 발생합니다.  
  
> [!NOTE]  
>  사례의 비율과 최대 수가 모두 지정되면 둘 중 작은 값이 사용됩니다.  
  
 *홀드 아웃 초기값*  
 데이터 분할을 시작하기 위한 초기값으로 사용되는 정수입니다.  
  
 0으로 설정하면 마이닝 구조 ID의 해시가 초기값으로 사용됩니다.  
  
> [!NOTE]  
>  파티션을 다시 만들 수 있도록 하려면 초기값을 지정해야 합니다.  
  
 기본값: REPEATABLE(0)  
  
## <a name="remarks"></a>Remarks  
 마이닝 구조 정의는 열 목록을 지정하고 필요에 따라 열 간의 계층 관계를 지정한 다음 역시 필요에 따라 마이닝 구조를 학습 및 테스트 데이터 집합으로 분할하는 작업으로 구성됩니다.  
  
 선택적인 SESSION 키워드는 구조가 현재 세션 기간에만 사용할 수 있는 임시 구조임을 나타냅니다. 세션이 종료될 때 구조 및 구조를 기반으로 하는 모든 모델이 삭제됩니다. 임시 마이닝 구조 및 모델을 만들려면 먼저 데이터베이스 속성인 AllowSessionMiningModels를 설정 해야 합니다. 자세한 내용은 [Data Mining Properties](../analysis-services/server-properties/data-mining-properties.md)을 참조하세요.  
  
## <a name="column-definition-list"></a>열 정의 목록  
 열 정의 목록에서 각 열에 대해 다음과 같은 정보를 포함하여 마이닝 구조를 정의합니다.  
  
-   이름(필수)  
  
-   데이터 형식(필수)  
  
-   배포  
  
-   모델링 플래그 목록  
  
-   내용 유형(필수)  
  
-   RELATED TO 절로 표시되는 특성 열과의 관계(적용되는 경우에만 필수)  
  
 열 정의 목록에 대해 다음 구문을 사용하여 단일 열을 정의합니다.  
  
```  
<column name>    <data type>    [<Distribution>]    [<Modeling Flags>]    <Content Type>    [<column relationship>]  
```  
  
 열 정의 목록에 대해 다음 구문을 사용하여 중첩 테이블 열을 정의합니다.  
  
```  
<column name>    TABLE    ( <column definition list> )  
```  
  
 구조 열을 정의하는 데 사용할 수 있는 데이터 형식, 내용 유형, 열 배포 및 모델링 플래그의 목록은 다음 항목을 참조하십시오.  
  
-   [데이터 형식&#40;데이터 마이닝&#41;](../analysis-services/data-mining/data-types-data-mining.md)  
  
-   [콘텐츠 형식&#40;데이터 마이닝&#41;](../analysis-services/data-mining/content-types-data-mining.md)  
  
-   [열 배포&#40;데이터 마이닝&#41;](../analysis-services/data-mining/column-distributions-data-mining.md)  
  
-   [모델링 플래그&#40;데이터 마이닝&#41;](../analysis-services/data-mining/modeling-flags-data-mining.md)  
  
 열 하나에 대해 여러 개의 모델링 플래그 값을 정의할 수 있습니다. 단, 하나의 열에는 각각 하나의 내용 유형과 데이터 형식만 있을 수 있습니다.  
  
### <a name="column-relationships"></a>열 관계  
 열 정의 문에 절을 추가하여 두 열 간의 관계를 설명할 수 있습니다. [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 다음의 사용을 지원 \<열 관계 > 절.  
  
 **와 관련 된**  
 값 계층 구조를 나타냅니다. RELATED TO 열의 대상은 중첩 테이블의 키 열, 사례 행의 불연속 값 열 또는 RELATED TO 절이 있는 다른 열(중첩된 열을 나타냄)일 수 있습니다.  
  
## <a name="holdout-parameters"></a>홀드아웃 매개 변수  
 홀드아웃 매개 변수를 지정할 때 구조 데이터의 파티션이 만들어집니다. 홀드아웃에 지정하는 크기는 테스트용으로 예약되며 남은 데이터는 학습에 사용됩니다. 기본적으로 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]를 사용하여 마이닝 구조를 만드는 경우 30%의 테스트 데이터와 70%의 학습 데이터를 포함하는 홀드아웃 파티션이 만들어집니다. 자세한 내용은 [Training and Testing Data Sets](../analysis-services/data-mining/training-and-testing-data-sets.md)을 참조하세요.  
  
 DMX(Data Mining Extensions)를 사용하여 마이닝 구조를 만드는 경우에는 홀드아웃 파티션이 만들어지도록 수동으로 지정해야 합니다.  
  
> [!NOTE]  
>  합니다 **ALTER MINING STRUCTURE** 문은 홀드 아웃을 지원 하지 않습니다.  
  
 홀드아웃 매개 변수는 최대 3개까지 지정할 수 있습니다. 최대 홀드아웃 사례 수와 홀드아웃 비율을 모두 지정하면 최대 사례 제한에 도달할 때까지 사례 비율이 예약됩니다. 홀드 아웃 비율은 정수 뒤에 지정할 합니다 **%** 키워드를 뒤에 정수로 사례의 최대 수를 지정 합니다 **사례** 키워드. 다음 예에서 볼 수 있듯이 순서에 관계없이 조건을 결합할 수 있습니다.  
  
```  
WITH HOLDOUT (20 PERCENT)   
WITH HOLDOUT (2000 CASES)   
WITH HOLDOUT (20 PERCENT OR 2000 CASES)   
WITH HOLDOUT (2000 CASES OR 20 PERCENT)  
```  
  
 홀드아웃 초기값은 학습 또는 테스트 데이터 집합에 무작위로 사례를 할당하는 프로세스의 시작 지점을 제어합니다. 홀드아웃 초기값을 설정하면 파티션을 반복할 수 있게 됩니다. 홀드아웃 초기값을 지정하지 않으면 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]는 마이닝 구조의 이름을 사용하여 초기값을 만듭니다. 구조의 이름을 변경하면 초기값이 바뀝니다. 홀드아웃 초기값 매개 변수는 다른 홀드아웃 매개 변수 중 하나 또는 모두와 함께 사용할 수 있습니다.  
  
> [!NOTE]  
>  파티션 정보를 학습 데이터를 사용 하 여 캐시 되므로 홀드 아웃을 사용 해야 하는 합니다 **CacheMode** 마이닝 구조 속성 **KeepTrainingData**합니다. 이는 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]에서 새 마이닝 구조에 대한 기본 설정입니다. 변경 된 **CacheMode** 속성을 **ClearTrainingCases** 홀드 아웃을 포함 하는 기존 마이닝 구조에 파티션을 처리 된 모든 마이닝 모델을 주지 것입니다. 그러나 경우 <xref:Microsoft.AnalysisServices.MiningStructureCacheMode> 로 설정 되어 있지 **KeepTrainingData**, 홀드 아웃 매개 변수는 영향을 주지 것입니다. 이는 모든 원본 데이터가 학습에 사용되며 테스트 집합은 사용할 수 없음을 의미합니다. 파티션의 정의는 구조와 함께 캐시됩니다. 학습 사례의 캐시를 지우면 테스트 데이터의 캐시와 홀드아웃 집합의 정의도 함께 지워집니다.  
  
## <a name="examples"></a>예  
 다음 예에서는 DMX를 사용하여 홀드아웃이 있는 마이닝 구조를 만드는 방법을 보여 줍니다.  
  
### <a name="example-1-adding-a-structure-with-no-training-set"></a>예 1: 없는 학습 집합을 사용 하 여 구조 추가  
 다음 예에서는 연결된 마이닝 모델을 만들지 않고 홀드아웃 사용 없이 `New Mailing`이라는 새 마이닝 구조를 만듭니다. 구조에 마이닝 모델을 추가 하는 방법에 알아보려면 참조 [ALTER MINING STRUCTURE &#40;DMX&#41;](../dmx/alter-mining-structure-dmx.md)합니다.  
  
```  
CREATE MINING STRUCTURE [New Mailing]  
(  
    CustomerKey LONG KEY,   
    Gender TEXT DISCRETE,  
    [Number Cars Owned] LONG DISCRETE,  
    [Bike Buyer] LONG DISCRETE   
)  
```  
  
### <a name="example-2-specifying-holdout-percentage-and-seed"></a>예 2: 홀드 아웃 비율 및 초기값 지정  
 다음 절은 열 정의 목록 이후에 추가되어 마이닝 구조와 관련된 모든 마이닝 모델을 테스트하는 데 사용할 수 있는 데이터 집합을 정의할 수 있습니다. 다음 문은 최대 사례 수에 제한 없이 전체 입력 사례의 25%에 해당하는 테스트 집합을 만듭니다. 파티션을 만드는 초기값으로 5000이 사용됩니다. 초기값을 지정하는 경우 기본 데이터가 변경되지 않으면 마이닝 구조를 처리할 때마다 테스트 집합에 대해 동일한 사례가 선택됩니다.  
  
```  
CREATE MINING STRUCTURE [New Mailing]  
(  
    CustomerKey LONG KEY,   
    Gender TEXT DISCRETE,  
    [Number Cars Owned] LONG DISCRETE,  
    [Bike Buyer] LONG DISCRETE   
)   
WITH HOLDOUT(25 PERCENT) REPEATABLE(5000)  
```  
  
### <a name="example-3-specifying-holdout-percentage-and-max-cases"></a>예제 3: 홀드 아웃 비율 및 최대 사례 지정  
 다음 절은 전체 입력 사례의 25%와 2000개의 사례 중 더 적은 쪽을 포함하는 테스트 집합을 만듭니다. 초기값으로 0이 지정되므로 입력 사례의 샘플링을 시작하는 데 사용되는 초기값은 마이닝 구조의 이름을 사용하여 생성됩니다.  
  
```  
CREATE MINING STRUCTURE [New Mailing]  
(  
    CustomerKey LONG KEY,   
    Gender TEXT DISCRETE,  
    [Number Cars Owned] LONG DISCRETE,  
    [Bike Buyer] LONG DISCRETE   
)   
WITH HOLDOUT(25 PERCENT OR 2000 CASES) REPEATABLE(0)  
```  
  
## <a name="see-also"></a>관련 항목  
 [Data Mining Extensions &#40;DMX&#41; 데이터 정의 문](../dmx/dmx-statements-data-definition.md)   
 [Data Mining Extensions &#40;DMX&#41; 데이터 조작 문](../dmx/dmx-statements-data-manipulation.md)   
 [DMX&#40;Data Mining Extensions&#41; 문 참조](../dmx/data-mining-extensions-dmx-statements.md)  
  
  
