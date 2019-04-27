---
title: (사용 빈도 기반 최적화 마법사) 쿼리 조건 지정 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.usagebasedoptimizationwizard.specifyquerycriteria.f1
ms.assetid: 3193adc2-af9f-4234-a4cc-dea0c280a724
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 088d53d1257c4b0d4b141b1e090ab1174416d397
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62746147"
---
# <a name="specify-query-criteria-usage-based-optimization-wizard"></a>쿼리 조건 지정(사용 빈도 기반 최적화 마법사)
  최적화할 쿼리를 식별하기 위해 **쿼리 조건 지정** 페이지를 사용하여 하나 이상의 필터 옵션을 선택할 수 있습니다.  
  
> [!NOTE]  
>  [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 에서 쿼리 로그에 연결할 수 없는 경우에는 이 페이지를 사용할 수 없습니다.  
  
## <a name="options"></a>변수  
 **쿼리 로그 통계**  
 선택한 파티션에 대한 쿼리 로그에 저장된 쿼리 정보를 표시합니다. 다음 항목이 표시됩니다.  
  
|용어|정의|  
|----------|----------------|  
|**총 쿼리 수**|선택한 파티션에 대한 쿼리 로그에 저장된 총 쿼리 수를 표시합니다.|  
|**고유한 쿼리**|선택한 파티션에 대한 쿼리 로그에 저장된 고유한 쿼리 수를 표시합니다.|  
|**고유 사용자**|선택한 파티션에 대한 쿼리 로그에 저장된 쿼리와 연결된 고유한 사용자의 총 수를 표시합니다.|  
|**평균 응답 시간**|선택한 파티션에 대한 쿼리 로그에 저장된 쿼리의 평균 응답 시간을 표시합니다.|  
  
 **시작 날짜**  
 시작 날짜와 시간을 기준으로 쿼리 로그의 쿼리를 필터링합니다. 드롭다운 목록에서 날짜를 선택하거나 입력합니다.  
  
> [!NOTE]  
>  **종료 날짜** 를 선택하지 않으면 쿼리 로그에서 이 옵션에 대해 지정한 날짜와 시간 이후의 모든 쿼리를 고려합니다.  
  
 **종료 날짜**  
 종료 날짜와 시간을 기준으로 쿼리 로그의 쿼리를 필터링합니다. 드롭다운 목록에서 날짜를 선택하거나 입력합니다.  
  
> [!NOTE]  
>  **시작 날짜** 를 선택하지 않으면 쿼리 로그에서 이 옵션에 대해 지정한 날짜와 시간 이전의 모든 쿼리를 고려합니다.  
  
 **사용자**  
 지정한 사용자 집합을 기준으로 쿼리 로그의 쿼리를 필터링합니다. 줄임표(**...**) 단추를 클릭하여 **사용자 선택** 대화 상자를 표시하고 쿼리 필터링 기준으로 사용할 사용자를 선택할 수 있습니다. **사용자 선택** 대화 상자에 대한 자세한 내용은 [사용자 선택 대화 상자&#40;Analysis Services - 다차원 데이터&#41;](user-selection-dialog-box-analysis-services-multidimensional-data.md)를 참조하세요.  
  
 **가장 자주 쿼리**  
 선택한 파티션에 대해 가장 자주 실행한 고유한 쿼리의 최상위 백분율을 기준으로 쿼리 로그의 쿼리를 필터링합니다. 입력란에서 백분율 값을 선택하거나 입력합니다.  
  
## <a name="see-also"></a>관련 항목  
 [사용 빈도 기반 최적화 마법사 F1 도움말](usage-based-optimization-wizard-f1-help.md)   
 [Analysis Services 마법사 &#40;다차원 데이터&#41;](analysis-services-wizards-multidimensional-data.md)  
  
  
