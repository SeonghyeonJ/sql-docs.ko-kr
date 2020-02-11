---
title: '1 단원: 자전거 구매자 마이닝 구조 만들기 | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: a73ac60b-660f-458a-bd2f-993fbeba7226
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: d6384910858d87a80aa3c8f897bc88e45f4504fb
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2020
ms.locfileid: "62678497"
---
# <a name="lesson-1-creating-the-bike-buyer-mining-structure"></a>1단원: Bike Buyer 마이닝 구조 만들기
  이 단원에서는 [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)]의 잠재 고객이 자전거를 구입할 것인지 여부를 예측할 수 있는 마이닝 구조를 만듭니다. 마이닝 구조 및 데이터 마이닝의 해당 역할에 익숙하지 않은 경우 [마이닝 구조 &#40;Analysis Services 데이터 마이닝&#41;](../../2014/analysis-services/data-mining/mining-structures-analysis-services-data-mining.md)를 참조 하세요.  
  
 이 단원에서 만들 자전거 구매자 마이닝 구조는 [Microsoft 클러스터링 알고리즘](../../2014/analysis-services/data-mining/microsoft-clustering-algorithm.md)[Microsoft 의사 결정 트리 알고리즘](../../2014/analysis-services/data-mining/microsoft-decision-trees-algorithm.md)을 기반으로 마이닝 모델을 추가 하는 것을 지원 합니다. 이후 단원에서는 클러스터링 마이닝 모델을 사용하여 고객을 그룹화할 수 있는 다양한 방법을 탐색하고 의사 결정 트리 마이닝 모델을 사용하여 잠재 고객이 자전거를 구입할 것인지 여부를 예측합니다.  
  
## <a name="create-mining-structure-statement"></a>CREATE MINING STRUCTURE 문  
 마이닝 구조를 만들려면 [CREATE 마이닝 structure &#40;DMX&#41;](/sql/dmx/create-mining-structure-dmx) 문을 사용 합니다. 이 문의 코드는 다음 부분으로 나눌 수 있습니다.  
  
-   구조 이름을 지정합니다.  
  
-   키 열을 정의합니다.  
  
-   마이닝 열을 정의합니다.  
  
-   선택적 테스트 데이터 집합을 정의합니다.  
  
 다음은 CREATE MINING STRUCTURE 문의 일반적인 예입니다.  
  
```  
CREATE MINING STRUCTURE [<mining structure name>]  
(  
    <key column>,  
    <mining structure columns>  
)   
WITH HOLDOUT (<holdout specifier>)  
```  
  
 코드의 첫 번째 줄에서는 구조의 이름을 정의합니다.  
  
```  
CREATE MINING STRUCTURE [<mining structure name>]  
```  
  
 DMX (데이터 마이닝 확장)에서 개체의 이름을 지정 하는 방법에 대 한 자세한 내용은 [id &#40;dmx&#41;](/sql/dmx/identifiers-dmx)를 참조 하세요.  
  
 코드의 다음 줄에서는 원본 데이터의 엔터티를 고유하게 식별하는 마이닝 구조에 대한 키 열을 정의합니다.  
  
```  
<key column>,  
```  
  
 마이닝 구조에서 원본 데이터의 엔터티를 정의하는 고객 식별자(`CustomerKey`)를 만듭니다.  
  
 코드의 다음 줄은 마이닝 구조와 연결된 마이닝 모델에서 사용할 마이닝 열을 정의하는 데 사용됩니다.  
  
```  
<mining structure columns>  
```  
  
 다음 구문을 사용 하 여> 마이닝 \<구조 열에서 불연속화 함수를 사용 하 여 연속 열을 불연속화 수 있습니다.  
  
 `DISCRETIZE(<method>,<number of buckets>)`  
  
 분할 열에 대 한 자세한 내용은 [데이터 마이닝&#41;&#40;분할 방법 ](../../2014/analysis-services/data-mining/discretization-methods-data-mining.md)을 참조 하세요. 정의할 수 있는 마이닝 구조 열 유형에 대 한 자세한 내용은 [마이닝 구조 열](../../2014/analysis-services/data-mining/mining-structure-columns.md)을 참조 하세요.  
  
 코드의 마지막 줄에서는 마이닝 구조의 선택적 파티션을 정의합니다.  
  
```  
WITH HOLDOUT (<holdout specifier>)  
```  
  
 구조와 관련된 테스트 마이닝 모델에 사용할 일부 데이터를 지정하면 나머지 데이터는 모델 학습에 사용됩니다. 기본적으로 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]는 모든 사례 데이터의 30%를 포함하는 테스트 데이터 집합을 만듭니다. 테스트 데이터 집합이 사례의 30%(최대 1000개의 사례)를 포함해야 하는 사양을 추가합니다. 사례의 30%가 1000개보다 작으면 테스트 데이터 집합에 보다 적은 양이 포함됩니다.  
  
## <a name="lesson-tasks"></a>단원 태스크  
 이 단원에서는 다음 태스크를 수행합니다.  
  
-   비어 있는 새 쿼리를 만듭니다.  
  
-   마이닝 구조를 만들기 위해 쿼리를 변경합니다.  
  
-   쿼리를 실행합니다.  
  
## <a name="creating-the-query"></a>쿼리 만들기  
 첫 번째 단계는 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 인스턴스에 연결하고 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]에서 새 DNX 쿼리를 만드는 것입니다.  
  
#### <a name="to-create-a-new-dmx-query-in-sql-server-management-studio"></a>SQL Server Management Studio에서 새 DMX 쿼리를 만들려면  
  
1.  [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]를 엽니다.  
  
2.  
  **서버에 연결** 대화 상자에서 **서버 유형**으로 **Analysis Services**를 선택합니다. **서버 이름**에을 입력 `LocalHost`하거나이 단원에서 연결할 인스턴스의 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 이름을 입력 합니다. **연결**을 클릭합니다.  
  
3.  **개체 탐색기**에서 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]인스턴스를 마우스 오른쪽 단추로 클릭 하 고 **새 쿼리**를 가리킨 다음 **DMX** 를 클릭 하 여 **쿼리 편집기** 와 비어 있는 새 쿼리를 엽니다.  
  
## <a name="altering-the-query"></a>쿼리 변경  
 다음 단계는 Bike Buyer 마이닝 구조를 만들기 위해 위에서 설명한 CREATE MINING STRUCTURE 문을 수정하는 것입니다.  
  
#### <a name="to-customize-the-create-mining-structure-statement"></a>CREATE MINING STRUCTURE 문을 사용자 지정하려면  
  
1.  쿼리 편집기에서 CREATE MINING STRUCTURE 문의 일반적인 예를 빈 쿼리에 복사합니다.  
  
2.  다음 내용을  
  
    ```  
    [<mining structure>]   
    ```  
  
     다음으로 바꿀 수 있습니다.  
  
    ```  
    [Bike Buyer]  
    ```  
  
3.  다음 내용을  
  
    ```  
    <key column>   
    ```  
  
     다음으로 바꿀 수 있습니다.  
  
    ```  
    CustomerKey LONG KEY  
    ```  
  
4.  다음 내용을  
  
    ```  
    <mining structure columns>   
    ```  
  
     다음으로 바꿀 수 있습니다.  
  
    ```  
    [Age] LONG DISCRETIZED(Automatic,10),  
    [Bike Buyer] LONG DISCRETE,  
    [Commute Distance] TEXT DISCRETE,  
    [Education] TEXT DISCRETE,  
    [Gender] TEXT DISCRETE,  
    [House Owner Flag] TEXT DISCRETE,  
    [Marital Status] TEXT DISCRETE,  
    [Number Cars Owned] LONG DISCRETE,  
    [Number Children At Home] LONG DISCRETE,  
    [Occupation] TEXT DISCRETE,  
    [Region] TEXT DISCRETE,  
    [Total Children]LONG DISCRETE,  
    [Yearly Income] DOUBLE CONTINUOUS  
    ```  
  
5.  다음 내용을  
  
    ```  
    WITH HOLDOUT (holdout specifier>)  
    ```  
  
     다음으로 바꿀 수 있습니다.  
  
    ```  
    WITH HOLDOUT (30 PERCENT or 1000 CASES)  
    ```  
  
     이제 전체 문이 다음과 같아야 합니다.  
  
    ```  
    CREATE MINING STRUCTURE [Bike Buyer]  
    (  
       [Customer Key] LONG KEY,  
       [Age]LONG DISCRETIZED(Automatic,10),  
       [Bike Buyer] LONG DISCRETE,  
       [Commute Distance] TEXT DISCRETE,  
       [Education] TEXT DISCRETE,  
       [Gender] TEXT DISCRETE,  
       [House Owner Flag] TEXT DISCRETE,  
       [Marital Status] TEXT DISCRETE,  
       [Number Cars Owned]LONG DISCRETE,  
       [Number Children At Home]LONG DISCRETE,  
       [Occupation] TEXT DISCRETE,  
       [Region] TEXT DISCRETE,  
       [Total Children]LONG DISCRETE,  
       [Yearly Income] DOUBLE CONTINUOUS  
    )  
    WITH HOLDOUT (30 PERCENT or 1000 CASES)  
  
    ```  
  
6.  
  **파일** 메뉴에서 **다른 이름으로 DMXQuery1.dmx 저장**을 클릭합니다.  
  
7.  다른 이름 **으로 저장** 대화 상자에서 해당 폴더로 이동한 다음 파일 `Bike Buyer Structure.dmx`이름을로 합니다.  
  
## <a name="executing-the-query"></a>쿼리 실행  
 마지막 단계는 쿼리를 실행하는 것입니다. 쿼리를 만들고 저장한 다음에는 해당 쿼리를 실행해야 합니다. 즉, 서버에 마이닝 구조를 만들려면 해당 문을 실행해야 합니다. 쿼리 편집기에서 쿼리를 실행 하는 방법에 대 한 자세한 내용은 [데이터베이스 엔진 쿼리 편집기 &#40;SQL Server Management Studio&#41;](../relational-databases/scripting/database-engine-query-editor-sql-server-management-studio.md)를 참조 하세요.  
  
#### <a name="to-execute-the-query"></a>쿼리를 실행하려면  
  
1.  쿼리 편집기의 도구 모음에서 **실행**을 클릭합니다.  
  
     문의 실행이 끝나면 쿼리 상태가 쿼리 편집기 아래쪽의 **메시지** 탭에 표시됩니다. 메시지는 다음과 같아야 합니다.  
  
    ```  
    Executing the query   
    Execution complete  
    ```  
  
     이제 **자전거 구매자** 라는 새 구조가 서버에 있습니다.  
  
 다음 단원에서는 방금 만든 구조에 마이닝 모델을 추가합니다.  
  
## <a name="next-lesson"></a>다음 단원  
 [2단원: Bike Buyer 마이닝 구조에 마이닝 모델 추가](../../2014/tutorials/lesson-2-adding-mining-models-to-the-bike-buyer-mining-structure.md)  
  
  
