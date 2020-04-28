---
title: 식별자 (DMX) | Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 1f72832fd684dd59e27ce58576a7f65fa8796347
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/27/2020
ms.locfileid: "68074812"
---
# <a name="identifiers-dmx"></a>식별자(DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  의 모든 개체 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 에는 식별자가 있어야 합니다. 개체의 이름은 해당 개체의 식별자입니다. 데이터 원본, 데이터 원본 뷰, 큐브, 차원 및 마이닝 모델과 같은 데이터베이스 개체, 서버 및 데이터베이스에는 식별자가 있습니다.  
  
 DMX(데이터 마이닝 확장)에는 다음과 같은 두 가지 식별자 클래스가 있습니다.  
  
-   [일반 식별자](#RegularIdentifiers)  
  
-   [구분 식별자](#DelimitedIdentifiers)  
  
 개체 식별자는 개체를 정의할 때 생성됩니다. 그런 다음 이 식별자를 사용하여 개체를 참조할 수 있습니다. 식별자 길이는 100자로 제한됩니다.  
  
##  <a name="regular-identifiers"></a><a name="RegularIdentifiers"></a>일반 식별자  
 DMX의 일반 식별자는 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]의 식별자 형식 규칙을 따릅니다. DMX의 일반 식별자에는 구분 기호가 필요하지 않습니다. 다음은 구분 기호를 사용하지 않는 일반 식별자를 사용하는 DMX 문의 예입니다.  
  
```  
SELECT * FROM Clustering.CONTENT;  
```  
  
### <a name="rules-for-regular-identifiers"></a>일반 식별자 규칙  
 다음은 일반 식별자 형식에 대한 규칙입니다.  
  
1.  일반 식별자의 첫 번째 문자는 다음 중 하나로 지정해야 합니다.  
  
    -   유니코드 표준 2.0에 정의 된 문자입니다. 여기에는 a~z 및 A~Z의 라틴어 문자와 기타 언어의 문자가 포함됩니다.  
  
    -   밑줄(_)  
  
2.  그 다음 문자에는 다음과 같은 문자를 사용할 수 있습니다.  
  
    -   유니코드 표준 2.0에 정의 된 문자입니다.  
  
    -   기본 라틴 또는 기타 국가 스크립트의 10진수  
  
    -   밑줄(_)  
  
3.  DMX 예약어는 식별자로 사용할 수 없습니다. DMX에서 예약어는 대/소문자를 구분하지 않습니다. 자세한 내용은 [DMX&#41;&#40;예약 된 키워드 ](../dmx/reserved-keywords-dmx.md)를 참조 하세요.  
  
4.  식별자에는 중간 공백 또는 특수 문자가 포함될 수 없습니다.  
  
 DMX 문에서 이러한 규칙을 따르지 않는 식별자를 사용하려면 대괄호로 구분해야 합니다.  
  
##  <a name="delimited-identifiers"></a><a name="DelimitedIdentifiers"></a>구분 식별자  
 구분 식별자는 대괄호([ ])로 묶입니다.  다음은 이 규칙을 따르는 구분 식별자가 있는 DMX 문의 예입니다.  
  
```  
SELECT * FROM [Marketing_Clusters].CONTENT;  
```  
  
 일반 식별자의 형식 규칙에 맞지 않는 식별자는 항상 구분 기호로 분리되어야 합니다. 다음은 공백이 포함된 구분 식별자가 있는 DMX 문의 예입니다.  
  
```  
SELECT * FROM [Targeted Mailing].CONTENT;  
```  
  
 다음과 같은 경우 구분 식별자를 사용합니다.  
  
-   개체 이름 또는 개체 이름의 일부로 예약어를 사용하는 경우  
  
     예약된 키워드는 개체 이름에 사용하지 않는 것이 좋습니다. 이전 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 버전의에서 업그레이드 하는 데이터베이스에는 이전 버전의에서는 예약 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 되지 않았지만에[!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]는 예약어 인 단어가 포함 된 식별자가 포함 될 수 있습니다. 개체 이름을 변경할 때까지 구분 식별자를 사용하여 이러한 개체를 참조할 수 있습니다.  
  
-   정규화된 식별자가 아닌 문자를 사용하는 경우  
  
     [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]에서는 현재 코드 페이지에 있는 문자를 구분 식별자로 사용할 수 있지만 개체 이름에 특수 문자를 무분별하게 사용하면 DMX 문을 읽고 유지 관리하기 어려워집니다.  
  
### <a name="rules-for-delimited-identifiers"></a>구분 식별자 규칙  
 다음은 구분 식별자 형식에 대한 규칙입니다.  
  
1.  구분 식별자에는 일반 식별자와 동일한 수의 문자(구분 기호를 제외한 1~100개의 문자)를 포함할 수 있습니다.  
  
2.  식별자에는 구분 기호 자체를 포함하여 현재 코드 페이지에 사용된 문자의 모든 조합을 사용할 수 있습니다. 식별자에 구분 기호가 포함되는 경우에는 특수하게 처리해야 합니다.  
  
    -   식별자에 왼쪽 대괄호([)가 포함된 경우에는 추가로 처리하지 않아도 됩니다.  
  
    -   식별자에 오른쪽 대괄호(])가 포함된 경우에는 코드 페이지 안에서 표시되도록 두 개의 오른쪽 대괄호(]])를 지정해야 합니다.  
  
### <a name="delimiting-identifiers-with-multiple-parts"></a>여러 부분으로 식별자 구분  
 정규화된 개체 이름을 사용할 때는 개체 이름을 구성하는 식별자 중 둘 이상을 구분해야 합니다. 각 식별자를 개별적으로 구분해야 합니다.  
  
## <a name="see-also"></a>참고 항목  
 [DMX&#41; 참조 &#40;데이터 마이닝 확장](../dmx/data-mining-extensions-dmx-reference.md)   
 [데이터 마이닝 확장 &#40;DMX&#41; 구문 요소](../dmx/data-mining-extensions-dmx-syntax-elements.md)   
 [데이터 마이닝 확장 &#40;DMX&#41; 함수 참조](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [데이터 마이닝 확장 &#40;DMX&#41; 연산자 참조](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [데이터 마이닝 확장 &#40;DMX&#41; 문 참조](../dmx/data-mining-extensions-dmx-statements.md)   
 [데이터 마이닝 확장 &#40;DMX&#41; 구문 규칙](../dmx/data-mining-extensions-dmx-syntax-conventions.md)   
 [DMX&#41;일반 예측 함수 &#40;](../dmx/general-prediction-functions-dmx.md)   
 [DMX 예측 쿼리의 구조 및 사용법](../dmx/structure-and-usage-of-dmx-prediction-queries.md)   
 [DMX Select 문 이해](../dmx/understanding-the-dmx-select-statement.md)  
  
  
