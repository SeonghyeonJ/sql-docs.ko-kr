---
title: Analysis Services에서의 번역 지원 | Microsoft Docs
ms.date: 01/09/2019
ms.prod: sql
ms.technology: analysis-services
ms.custom: ''
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: bd727b56649ce9ffc237575b0311db256ec9b2fc
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/15/2019
ms.locfileid: "68207423"
---
# <a name="translation-support-in-analysis-services"></a>Analysis Services에서의 번역 지원
[!INCLUDE[ssas-appliesto-sqlas-aas](../includes/ssas-appliesto-sqlas-aas.md)]

  [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 데이터 모델, 캡션 또는 로캘 식별자 (LCID)를 기반으로 하는 culture 별 문자열을 제공할 설명의 여러 번역을 포함할 수 있습니다. 다차원 모델의 경우 데이터베이스 이름, 큐브 개체 및 데이터베이스 차원 개체에 대한 번역을 추가할 수 있습니다. 테이블 형식 모델의 경우 테이블 및 열 캡션 및 설명을 번역할 수 있습니다.  
  
 번역을 정의하면 모델 내부에 메타데이터와 번역된 캡션이 생성되지만 클라이언트 애플리케이션에서 지역화된 문자열을 렌더링하려면 개체에서 **Language** 속성을 설정하거나 연결 문자열에서 **Culture** 또는 **Locale Identifier** 매개 변수를 전달해야 합니다(예를 들어 프랑스어 문자열을 반환하려면 `LocaleIdentifier=1036` 설정).  
  
 동일한 개체에 대한 여러 개의 동시 번역을 서로 다른 언어로 지원하려면 **Locale Identifier** 사용을 계획합니다. **Language** 속성 설정은 작동하지만, 처리 및 쿼리에 영향을 주므로 의도하지 않은 결과를 초래할 수 있습니다. 반면에 **Locale Identifier** 를 설정하면 번역된 문자열을 반환하는 데에만 사용되므로 이렇게 하는 것이 좋습니다.  
  
 번역은 LCID(로캘 식별자) 및 개체에 대한 번역된 캡션(예: 차원 또는 특성 이름)과 (원할 경우) 데이터 값을 대상 언어로 제공하는 열에 대한 바인딩으로 구성됩니다. 여러 번역이 있을 수 있지만 지정된 연결에 대해 하나씩만 사용할 수 있습니다. 모델에 포함할 수 있는 번역의 수에 이론적인 제한은 없지만 각 번역은 테스트를 더 복잡하게 하고 모든 번역은 동일한 데이터 정렬을 공유해야 하므로 솔루션을 디자인할 때에는 이러한 기본적인 제약 조건을 염두에 두어야 합니다.  
  
> [!TIP]  
>  번역 된 문자열을 반환 하려면 Excel, SQL Server Management Studio 및 SQL Server Profiler와 같은 클라이언트 응용 프로그램을 사용할 수 있습니다. 자세한 내용은 [세계화 팁과 모범 사례&#40;Analysis Services&#41;](../analysis-services/globalization-tips-and-best-practices-analysis-services.md)를 참조하세요.  
  
## <a name="how-to-add-translated-metadata-to-model-in-analysis-services"></a>Analysis Services에서 모델에 번역된 메타데이터를 추가하는 방법  
 단계별 지침은 다음 링크를 방문하세요.  
  
-   [테이블 형식 모델 번역](../analysis-services/tabular-models/translations-in-tabular-models-analysis-services.md)  
  
-   [다차원 모델의 번역](../analysis-services/multidimensional-models/translations-in-multidimensional-models-analysis-services.md)  
  
## <a name="see-also"></a>참조  
 [Analysis Services의 세계화 시나리오](../analysis-services/globalization-scenarios-for-analysis-services.md)   
 [언어 및 데이터 정렬 & #40; Analysis Services & #41;](../analysis-services/languages-and-collations-analysis-services.md)   
 [열 데이터 정렬 설정 또는 변경](../relational-databases/collations/set-or-change-the-column-collation.md)   
 [세계화 팁과 모범 사례&#40;Analysis Services&#41;](../analysis-services/globalization-tips-and-best-practices-analysis-services.md)  
  
  
