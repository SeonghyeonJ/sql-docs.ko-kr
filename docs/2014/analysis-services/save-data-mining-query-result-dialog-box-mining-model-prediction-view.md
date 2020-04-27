---
title: 데이터 마이닝 쿼리 결과 저장 대화 상자 (마이닝 모델 예측 뷰) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.dm.savedataminingqueryresult.f1
helpviewer_keywords:
- Save Data Mining Query Result dialog box
ms.assetid: 112fb527-7466-4fd4-9cf1-75596135648f
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 97b391e24f98b230dbfe352e0cf1a574c7549984
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/26/2020
ms.locfileid: "66070015"
---
# <a name="save-data-mining-query-result-dialog-box-mining-model-prediction-view"></a>데이터 마이닝 쿼리 결과 저장 대화 상자(마이닝 모델 예측 뷰)
  **데이터 마이닝 쿼리 결과 저장** 대화 상자를 사용하여 데이터 마이닝 쿼리 결과를 새 테이블에 저장할 수 있습니다.  
  
 데이터 원본에서 정의한 데이터베이스에 새 테이블이 생성됩니다.  
  
## <a name="options"></a>옵션  
 **데이터 원본**  
 현재 프로젝트에서 데이터 원본을 선택합니다. 올바른 데이터 원본이 없는 경우 **새로 만들기** 를 클릭하여 새 데이터 원본을 만들 수 있습니다.  
  
 **신규**  
 **데이터 원본 마법사**를 엽니다.  
  
 **표 이름**  
 새 테이블의 이름을 입력합니다.  
  
 **기존 항목 덮어쓰기**  
 기존 테이블을 같은 이름으로 덮어쓰려면 이 옵션을 선택합니다.  
  
 다음 중 하나에 해당할 경우 기존 테이블을 덮어써야 합니다.  
  
-   예측 쿼리에 열을 추가했습니다.  
  
-   예측 쿼리의 열 이름이나 데이터 형식을 변경했습니다.  
  
-   대상 테이블에서 ALTER 문을 실행했습니다.  
  
 여러 열의 이름이 동일한 경우(예: 파생된 여러 열에서 기본 열 이름인 **식**을 사용할 수 있음) 중복된 이름의 각 열에 대해 별칭을 만들어야 합니다. 테이블의 열 이름은 고유해야 하기 때문에 열 이름이 고유하지 않을 경우 디자이너가 SQL Server에 결과를 저장하려고 할 때 오류가 발생합니다.  
  
 **DSV에 추가**  
 테이블을 기존 데이터 원본에 추가하려면 프로젝트에 포함된 데이터 원본 뷰를 선택합니다(옵션).  
  
 이 옵션은 학습 데이터, 예측 원본 데이터 및 쿼리 결과와 같은 모델에 대 한 모든 관련 테이블을 동일한 데이터 원본에 유지 하려는 경우에 유용 합니다.  
  
## <a name="see-also"></a>참고 항목  
 [예측 쿼리 작성기 &#40;데이터 마이닝&#41;](prediction-query-builder-data-mining.md)   
 [데이터 마이닝 쿼리 인터페이스](data-mining/data-mining-query-tools.md)   
 [DMX&#40;Data Mining Extensions&#41; 문 참조](/sql/dmx/data-mining-extensions-dmx-statements)  
  
  
