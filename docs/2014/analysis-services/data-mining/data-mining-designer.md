---
title: 데이터 마이닝 디자이너 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- data mining [Analysis Services], structure
- mining structures [Analysis Services], modifying
- data mining editor [Analysis Services]
- Data Mining Designer
- data mining [Analysis Services], modifying
ms.assetid: 2540db5b-2bf3-4b6c-87c8-79c48d71acce
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: b0a54a0ae2bab2c8019b706a51b94f0338dcb3cf
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66085107"
---
# <a name="data-mining-designer"></a>Data Mining Designer
  데이터 마이닝 디자이너는 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]에서 마이닝 모델을 사용하는 기본 환경입니다. 기존 마이닝 구조를 선택하거나 데이터 마이닝 마법사를 사용하여 새 마이닝 구조 및 마이닝 모델을 만들면 데이터 마이닝 디자이너에 액세스할 수 있습니다. 데이터 마이닝 디자이너를 사용하여 다음과 같은 태스크를 수행할 수 있습니다.  
  
-   처음에 데이터 마이닝 마법사에서 생성된 마이닝 구조 및 마이닝 모델 수정  
  
-   기존 마이닝 구조를 기반으로 새 모델 만들기  
  
-   마이닝 모델 학습 및 검색  
  
-   정확도 차트를 사용하여 모델 비교  
  
-   마이닝 모델을 기반으로 예측 쿼리 만들기  
  
## <a name="mining-structure-tab"></a>마이닝 구조 탭  
 **마이닝 구조** 탭을 사용하여 열을 추가하고 기존 마이닝 구조의 속성을 수정할 수 있습니다. 다음 태스크 및 항목에서는 마이닝 구조 작업에 대한 추가 정보를 제공합니다.  
  
 [마이닝 구조&#40;Analysis Services - 데이터 마이닝&#41;](mining-structures-analysis-services-data-mining.md)  
  
 [마이닝 구조 태스크 및 방법](mining-structure-tasks-and-how-tos.md)  
  
## <a name="mining-models-tab"></a>마이닝 모델 탭  
 **마이닝 모델** 탭을 사용하여 기존 마이닝 모델을 관리하고 새 모델을 만들 수 있습니다. 마이닝 모델은 항상 기존 마이닝 구조를 기반으로 합니다.  
  
 **마이닝 모델** 탭에서 알고리즘 유형 변경, 모델 구조와 연결된 열 추가 또는 제거, 알고리즘 특정 열 속성 조정, 마이닝 모델 열 사용 지정, 마이닝 모델과 연결된 알고리즘 매개 변수 조정 등의 작업을 수행할 수 있습니다. 마이닝 구조를 선택한 모델 또는 연결된 모든 모델과 함께 처리할 수도 있습니다.  
  
 마이닝 모델 작업에 대한 자세한 내용은 다음 항목을 참조하십시오.  
  
 [마이닝 모델&#40;Analysis Services - 데이터 마이닝&#41;](mining-models-analysis-services-data-mining.md)  
  
 [마이닝 모델 태스크 및 방법](mining-model-tasks-and-how-tos.md)  
  
## <a name="mining-model-viewer-tab"></a>마이닝 모델 뷰어 탭  
 **마이닝 모델 뷰어** 탭을 사용하여 마이닝 모델을 시각적으로 탐색할 수 있습니다. 각 마이닝 모델은 해당 모델에 고유한 콘텐츠를 표시하는 사용자 지정 뷰어와 연결되어 있습니다. 콘텐츠 뷰어를 사용하여 마이닝 모델 콘텐츠를 볼 수도 있습니다.  
  
 데이터 마이닝 뷰어를 사용하여 마이닝 모델을 탐색하는 방법은 다음 항목을 참조하십시오.  
  
 [데이터 마이닝 모델 뷰어](data-mining-model-viewers.md)  
  
 [마이닝 모델 뷰어 태스크 및 방법](mining-model-viewer-tasks-and-how-tos.md)  
  
## <a name="mining-accuracy-chart-tab"></a>마이닝 정확도 차트 탭  
 **마이닝 정확도 차트** 탭을 사용하여 단일 마이닝 모델의 예측 정확도를 테스트하거나 마이닝 구조에 포함된 여러 마이닝 모델의 효율성을 비교할 수 있습니다. 이 탭에는 데이터를 필터링하고, 마이닝 모델을 선택하고, 리프트 차트, 수익 차트 또는 분류 행렬에 결과를 표시하기 위한 도구가 있습니다.  
  
 마이닝 모델의 테스트 및 유효성 검사에 대한 자세한 내용은 다음 항목을 참조하십시오.  
  
 [테스트 및 유효성 검사&#40;데이터 마이닝&#41;](testing-and-validation-data-mining.md)  
  
 [테스트 및 유효성 검사 태스크 및 방법&#40;데이터 마이닝&#41;](testing-and-validation-tasks-and-how-tos-data-mining.md)  
  
## <a name="mining-model-prediction-tab"></a>마이닝 모델 예측 탭  
 **마이닝 모델 예측** 탭에는 DMX(Data Mining Extensions) 예측 쿼리를 만들 때 사용할 수 있는 예측 쿼리 작성기가 있습니다. 또한 마이닝 모델 및 입력 테이블을 지정하고, 마이닝 모델의 열을 입력 테이블의 열로 매핑하고, 쿼리에 함수를 추가하고, 각 열에 대한 조건을 지정하기 위한 도구가 포함되어 있습니다.  
  
 쿼리를 디자인한 후 이 탭의 여러 보기를 사용하여 쿼리 결과를 표시하고 수동으로 쿼리를 수정할 수 있습니다. 쿼리 결과를 데이터베이스의 테이블에 저장할 수도 있습니다.  
  
 데이터 마이닝 쿼리를 작성하는 방법은 다음 항목을 참조하십시오.  
  
 [데이터 마이닝 쿼리](data-mining-queries.md)  
  
 [데이터 마이닝 쿼리 태스크 및 방법](data-mining-query-tasks-and-how-tos.md)  
  
## <a name="see-also"></a>관련 항목  
 [데이터 마이닝 솔루션](data-mining-solutions.md)  
  
  
