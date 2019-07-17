---
title: Data Mining Extensions (DMX) 참조 | Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 29454fefde7850e5e45ca6a916540e7d38e2b286
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68070904"
---
# <a name="data-mining-extensions-dmx-reference"></a>DMX(Data Mining Extensions) 참조
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  만들기 및 데이터 마이닝 모델의 작업에 사용할 수 있는 언어가 확장 DMX (data Mining) [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]합니다. DMX를 사용하여 새 데이터 마이닝 모델의 구조를 만들고 이 모델을 학습하고 이 모델을 검색, 관리 및 예측할 수 있습니다. DMX는 DDL(데이터 정의 언어) 문, DML(데이터 조작 언어) 문, 함수 및 연산자로 구성됩니다.  
  
## <a name="microsoft-ole-db-for-data-mining-specification"></a>Microsoft OLE DB for Data Mining 사양  
 데이터 마이닝 기능은 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 준수 하기 위해 빌드됩니다는 [!INCLUDE[msCoName](../includes/msconame-md.md)] OLE DB for Data Mining 사양 합니다.  
  
 [!INCLUDE[msCoName](../includes/msconame-md.md)] OLE DB for Data Mining 사양 다음을 정의 합니다.  
  
-   데이터 마이닝 모델을 정의하는 정보를 유지하기 위한 구조  
  
-   데이터 마이닝 모델을 만들고 사용하기 위한 언어  
  
 이 사양에서는 데이터 마이닝의 기초를 데이터 마이닝 모델 가상 개체로 정의합니다. 데이터 마이닝 모델 개체에는 특정 마이닝 모델에 대해 알려진 모든 내용이 포함됩니다. 데이터 마이닝 모델 개체는 모델을 설명하는 열, 데이터 형식 및 메타 정보가 포함된 SQL 테이블과 같은 구조로 구성됩니다. 이 구조에서는 SQL의 확장 기능인 DMX 언어를 사용하여 모델을 만들고 사용할 수 있습니다.  
  
 **참조 항목:** [마이닝 구조&#40;Analysis Services - 데이터 마이닝&#41;](../analysis-services/data-mining/mining-structures-analysis-services-data-mining.md)  
  
##  <a name="BKMK_DMXStatements"></a> DMX 문  
 DMX 문을 사용하여 데이터 마이닝 모델을 작성, 처리, 삭제, 복사, 검색 및 예측할 수 있습니다. DMX에는 두 가지 유형의 문인 데이터 정의 문과 데이터 조작 문이 있습니다. 이 두 가지 유형의 문을 사용하여 다양한 태스크를 수행할 수 있습니다.  
  
 다음 섹션에서는 DMX 문을 사용하는 방법에 대해 설명합니다.  
  
-   [데이터 정의 문](#BKMK_DDL)  
  
-   [데이터 조작 문](#BKMK_DML)  
  
-   [쿼리 기본 사항](#BKMK_Queries)  
  
###  <a name="BKMK_DDL"></a> 데이터 정의 문  
 DMX의 데이터 정의 문을 사용하여 새 마이닝 구조 및 모델을 만들거나 정의하고 마이닝 모델과 마이닝 구조를 가져오거나 내보내고 데이터베이스의 기존 모델을 삭제할 수 있습니다. DMX의 데이터 정의 문은 DDL(데이터 정의 언어)의 일부입니다.  
  
 DMX의 데이터 정의 문을 사용하여 다음과 같은 태스크를 수행할 수 있습니다.  
  
-   사용 하 여 마이닝 구조를 만들를 [CREATE MINING STRUCTURE](../dmx/create-mining-structure-dmx.md) 문을 사용 하 여 마이닝 구조에 마이닝 모델을 추가 합니다 [ALTER MINING STRUCTURE](../dmx/alter-mining-structure-dmx.md) 문.  
  
-   마이닝 모델 및 연결 된 마이닝 구조를 사용 하 여 동시에 만들 합니다 [CREATE MINING MODEL](../dmx/create-mining-model-dmx.md) 빈 데이터 마이닝 모델 개체를 작성 하는 문입니다.  
  
-   파일에는 마이닝 모델과 연결 된 마이닝 구조를 사용 하 여 내보낼 합니다 [내보내기](../dmx/export-dmx.md) 문입니다. 마이닝 모델 및 연결 된 마이닝 구조를 사용 하 여 내보내기 문에 의해 생성 되는 파일에서 가져오기 합니다 [가져오기](../dmx/import-dmx.md) 문입니다.  
  
-   기존 마이닝 모델의 구조를 새 모델로 복사 하 고 사용 하 여 동일한 데이터를 사용 하 여 학습 합니다 [SELECT INTO](../dmx/select-into-dmx.md) 문.  
  
-   사용 하 여 데이터베이스에서 마이닝 모델을 완전히 제거 합니다 [DROP MINING MODEL](../dmx/drop-mining-model-dmx.md) 문입니다. 완전히 마이닝 구조와 모든 관련된 마이닝 모델 데이터베이스에서 사용 하 여 제거 합니다 [DROP MINING STRUCTURE](../dmx/drop-mining-structure-dmx.md) 문입니다.  
  
 DMX 문을 사용 하 여 수행할 수 있는 데이터 마이닝 태스크에 대 한 자세한 내용은 참조 하세요 [Data Mining Extensions &#40;DMX&#41; 문 참조](../dmx/data-mining-extensions-dmx-statements.md)합니다.  
  
 [DMX 문을 돌아가기](#BKMK_DMXStatements)  
  
###  <a name="BKMK_DML"></a> 데이터 조작 문  
 DMX의 데이터 조작 문을 사용하여 기존 마이닝 모델로 작업하고 모델을 검색하고 모델에 대한 예측을 만들 수 있습니다. DMX의 데이터 조작 문은 DML(데이터 조작 언어)의 일부입니다.  
  
 DMX의 데이터 조작 문을 사용하여 다음과 같은 태스크를 수행할 수 있습니다.  
  
-   사용 하 여 마이닝 모델을 학습 합니다 [INSERT INTO](../dmx/insert-into-dmx.md) 문입니다. 마이닝 모델의 학습을 수행하면 실제 원본 데이터가 데이터 마이닝 모델 개체에 삽입되지 않는 대신에 알고리즘에서 만드는 마이닝 모델을 설명하는 추상화가 수행됩니다. INSERT INTO 문의 원본 쿼리는에 설명 되어 [ \<원본 데이터 쿼리와 >](../dmx/source-data-query.md)합니다.  
  
-   모델 학습 중에 계산 되며 원본 데이터의 통계와 같은 데이터 마이닝 모델에 저장 된 정보를 찾아보려면 SELECT 문의 확장 합니다. 다음은 다양 한 절을 SELECT 문의 기능 확장을 위해 포함 될 수 있습니다.  
  
    -   [SELECT DISTINCT FROM &#60;모델 &#62; &#40;DMX&#41;](../dmx/select-distinct-from-model-dmx.md)  
  
    -   [SELECT FROM &#60;모델&#62;합니다. 콘텐츠 &#40;DMX&#41;](../dmx/select-from-model-content-dmx.md)  
  
    -   [SELECT FROM &#60;모델&#62;합니다. 경우 &#40;DMX&#41;](../dmx/select-from-model-cases-dmx.md)  
  
    -   [SELECT FROM &#60;모델&#62;합니다. SAMPLE_CASES &#40;DMX&#41;](../dmx/select-from-model-sample-cases-dmx.md)  
  
    -   [SELECT FROM &#60;모델&#62;합니다. DIMENSION_CONTENT &#40;DMX&#41;](../dmx/select-from-model-dimension-content-dmx.md)  
  
-   사용 하 여 기존 마이닝 모델을 기반으로 하는 예측을 만들 합니다 [PREDICTION JOIN](../dmx/select-from-model-prediction-join-dmx.md) SELECT 문의 절. PREDICTION JOIN 문에 대 한 원본 쿼리는에 설명 되어 [ \<원본 데이터 쿼리와 >](../dmx/source-data-query.md)합니다.  
  
-   사용 하 여 모델 또는 구조에서 학습된 된 모든 데이터를 제거 합니다 [삭제 &#40;DMX&#41; ](../dmx/delete-dmx.md) 문입니다.  
  
 DMX 문을 사용 하 여 수행할 수 있는 데이터 마이닝 태스크에 대 한 자세한 내용은 참조 하세요 [Data Mining Extensions &#40;DMX&#41; 문 참조](../dmx/data-mining-extensions-dmx-statements.md)합니다.  
  
 [DMX 문을 돌아가기](#BKMK_DMXStatements)  
  
###  <a name="BKMK_Queries"></a> DMX 쿼리 기본 사항  
 SELECT 문에 대부분의 DMX 쿼리에 대 한 기반이 됩니다. 이 문과 함께 다양한 절을 사용하여 마이닝 모델을 검색하거나 복사하거나 예측할 수 있습니다. 예측 쿼리는 기존 마이닝 모델을 기반으로 예측을 만드는 선택의 형태를 사용 합니다. 함수를 통해 데이터 마이닝 모델의 내재된 기능을 확장하여 마이닝 모델을 다양하게 검색 및 쿼리할 수 있습니다.  
  
 DMX 함수를 사용하여 모델 학습 중에 발견한 정보를 가져오고 새 정보를 계산할 수 있습니다. 기본 데이터 또는 예측 정확성을 설명하는 통계를 반환하거나 예측에 대한 상세한 설명을 반환하는 등의 여러 가지 용도로 함수를 사용할 수 있습니다.  
  
 **자세한 내용은** **정보:**  [Select 문 이해 DMX](../dmx/understanding-the-dmx-select-statement.md), [일반 예측 함수 &#40;DMX&#41;](../dmx/general-prediction-functions-dmx.md)에 [구조 및 사용법 DMX 예측 쿼리의](../dmx/structure-and-usage-of-dmx-prediction-queries.md)를 [데이터 마이닝 확장 &#40;DMX&#41; 함수 참조](../dmx/data-mining-extensions-dmx-function-reference.md)  
  
 [DMX 문을 돌아가기](#BKMK_DMXStatements)  
  
## <a name="see-also"></a>관련 항목  
 [Data Mining Extensions &#40;DMX&#41; 함수 참조](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Data Mining Extensions &#40;DMX&#41; 연산자 참조](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [Data Mining Extensions &#40;DMX&#41; 문 참조](../dmx/data-mining-extensions-dmx-statements.md)   
 [Data Mining Extensions &#40;DMX&#41; 구문 표기 규칙](../dmx/data-mining-extensions-dmx-syntax-conventions.md)   
 [Data Mining Extensions &#40;DMX&#41; 구문 요소](../dmx/data-mining-extensions-dmx-syntax-elements.md)   
 [일반 예측 함수 &#40;DMX&#41;](../dmx/general-prediction-functions-dmx.md)   
 [DMX 예측 쿼리의 구조 및 사용법](../dmx/structure-and-usage-of-dmx-prediction-queries.md)   
 [DMX Select 문 이해](../dmx/understanding-the-dmx-select-statement.md)  
  
  
