---
title: 차트의 빈 데이터 요소 및 Null 데이터 요소(보고서 작성기 및 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
ms.assetid: faddd29d-4cc1-4c2c-8e29-d3d9918fe22a
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: f350fed895d039a0d5298832e2cd0437748a0a92
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/11/2019
ms.locfileid: "56016024"
---
# <a name="empty-and-null-data-points-in-charts-report-builder-and-ssrs"></a>차트의 빈 데이터 요소 및 Null 데이터 요소(보고서 작성기 및 SSRS)
  빈 값이나 null 값이 있는 필드를 차트에 표시하면 차트가 제대로 표시되지 않을 수 있습니다. 차트에서 빈 값이 처리되는 방법은 지정된 차트 종류에 따라 다릅니다.  
  
-   차트 종류가 선형 차트 종류(가로 막대형, 세로 막대형, 분산형, 꺾은선형, 영역형, 범위형)인 경우 빈 값은 차트에 빈 공간 또는 "간격"으로 표시됩니다. 빈 요소를 표시하려는 경우에는 빈 요소 자리 표시자를 추가해야 합니다. 자세한 내용은 [차트에 빈 요소 추가 &#40;보고서 작성기 및 SSRS&#41;](add-empty-points-to-a-chart-report-builder-and-ssrs.md)합니다.  
  
-   차트 종류가 연속적 선형 차트 종류(영역형, 가로 막대형, 세로 막대형, 꺾은선형, 분산형)인 경우 계열의 연속성을 유지하기 위해 차트에 빈 데이터 요소가 추가됩니다.  
  
-   비선형 차트 종류(극좌표형, 원형, 도넛형, 깔때기형, 피라미드형)의 경우 빈 값은 차트 표시에서 생략됩니다.  
  
-   셰이프 차트 종류에서는 Null 값이 생략됩니다.  
  
 빈 데이터 요소가 있는 차트의 예는 예제 보고서로 제공됩니다. 이 샘플 보고서 및 기타 보고서를 다운로드하는 방법은 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)][보고서 작성기 및 보고서 디자이너 샘플 보고서](https://go.microsoft.com/fwlink/?LinkId=198283).  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="removing-empty-or-null-values"></a>빈 값 또는 Null 값 제거  
 중요한 데이터가 가려지지 않도록 하려면 데이터 세트에서 빈 값을 제거하는 것이 좋습니다. Null을 필터링하려면 쿼리에 NOT IS NULL 절을 사용합니다. 또는 0이 아닌 값만 표시하도록 지정하는 필터링 식을 추가할 수 있습니다. 자세한 내용은 [데이터 세트 필터, 데이터 영역 필터 및 그룹 필터 추가&amp;#40;보고서 작성기 및 SSRS&amp;#41;](add-dataset-filters-data-region-filters-and-group-filters.md)을 참조하세요.  
  
## <a name="fields-with-no-values-in-a-chart"></a>차트에서 값이 없는 필드  
 반환된 데이터 세트에서 필드에 값이 포함되어 있지 않은 경우 차트는 데이터 요소가 없는 빈 차트를 표시하지만 계열 이름(일반적으로 필드 이름)은 범례 항목으로 추가됩니다.  
  
 이 동작은 보고서에 매개 변수가 있고 선택된 값이 빈 결과 세트를 반환할 때 발생할 수 있는 경우인 반환된 데이터 세트에 데이터 행이 0개인 경우와는 다릅니다. 데이터 세트 쿼리가 0개의 데이터 행을 반환하는 경우 표시할 데이터가 없음을 알리는 메시지가 런타임에 표시됩니다. **속성** 창에서 보고서의 NoDataMessage 캡션을 수정하여 이 메시지를 사용자 지정할 수 있습니다. 자세한 내용은 [보고서 포함된 데이터 집합 및 공유 데이터 집합&#40;보고서 작성기 및 SSRS&#41;](../report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)이라는 데이터 집합이 들어 있습니다.  
  
## <a name="see-also"></a>관련 항목  
 [차트&#40;보고서 작성기 및 SSRS&#41;](charts-report-builder-and-ssrs.md)   
 [차트 서식 지정&#40;보고서 작성기 및 SSRS&#41;](formatting-a-chart-report-builder-and-ssrs.md)   
 [보고서에 차트 추가&#40;보고서 작성기 및 SSRS&#41;](add-a-chart-to-a-report-report-builder-and-ssrs.md)   
 [차트 문제 해결&#40;보고서 작성기 및 SSRS&#41;](troubleshoot-charts-report-builder-and-ssrs.md)  
  
  
