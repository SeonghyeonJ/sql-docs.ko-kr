---
title: 원형 차트에서 작은 조각 수집(보고서 작성기 및 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
ms.assetid: 21c2b8cb-b9ca-4bc0-bf49-50ba432562f6
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: c85692c3ae50df88c59d2622fc1ca06925413ba2
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63185587"
---
# <a name="collect-small-slices-on-a-pie-chart-report-builder-and-ssrs"></a>원형 차트에서 작은 조각 수집(보고서 작성기 및 SSRS)
  원형 차트에서 너무 많은 데이터 요소를 표시하면 복잡하게 보일 수 있습니다. 이 문제를 해결하기 위해 특정 값 미만의 모든 데이터를 원형 차트의 한 조각으로 표시할 수 있습니다.  
  
 여러 개의 작은 조각을 한 조각으로 수집하려면 먼저 작은 조각을 수집하기 위한 임계값을 원형 차트의 백분율과 고정 값 중 어떤 것으로 측정할지 결정해야 합니다. 그런 다음 CollectedThreshold 및 CollectedThresholdUsePercent 속성을 설정합니다. 데이터를 수집할 차트의 백분율(이 백분율 미만의 데이터가 수집됨) 또는 실제 임계 데이터 값으로 CollectedThreshold 속성을 설정합니다. CollectedThresholdUsePercent 속성을 설정 `True` 백분율을 사용 하도록 또는 `False` 실제 값을 사용 하 합니다.  
  
 첫 번째 원형 차트에서 수집된 조각으로 만든 두 번째 원형 차트에 작은 조각을 수집할 수도 있습니다. 두 번째 원형 차트는 첫 번째 원형 차트의 오른쪽에 그려집니다.  
  
 깔때기형 차트나 피라미드형 차트의 조각은 한 조각으로 결합할 수 없습니다.  
  
 이 차트의 예는 예제 보고서로 제공됩니다. 이 샘플 보고서 및 기타 보고서를 다운로드하는 방법은 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)][보고서 작성기 및 보고서 디자이너 샘플 보고서](https://go.microsoft.com/fwlink/?LinkId=198283).  
  
### <a name="to-collect-small-slices-into-a-single-slice-on-a-pie-chart"></a>작은 조각을 원형 차트의 한 조각으로 수집하려면  
  
1.  속성 창을 엽니다.  
  
2.  디자인 화면에서 원형 차트의 조각을 아무 것이나 클릭합니다. 계열의 속성이 속성 창에 표시됩니다.  
  
3.  **일반** 섹션에서 **CustomAttributes** 노드를 확장합니다.  
  
4.  CollectedStyle 속성을 **SingleSlice**로 설정합니다.  
  
5.  수집된 임계값 및 임계값의 유형을 설정합니다. 다음 예는 수집된 임계값을 설정하는 일반적인 방법입니다.  
  
    -   **백분율로 설정.** 예를 들어 원형 차트에서 10% 미만의 모든 조각을 한 개의 조각으로 수집하려면  
  
         CollectedThresholdUsePercent 속성을 설정 `True`합니다.  
  
         CollectedThreshold 속성을 **10**으로 설정합니다.  
  
        > [!NOTE]  
        >  CollectedStyle을 설정 하면 **SingleSlice**, 보다 큰 값으로 CollectedThreshold **100**, CollectedThresholdUsePercent 이며 `True`, 차트 수 없어서 예외가 throw 됩니다 백분율을 계산 합니다. 이 문제를 해결하려면 CollectedThreshold를 **100**보다 작은 값으로 설정합니다.  
  
    -   **데이터 값으로.** 예를 들어 원형 차트에서 5000개 미만의 모든 조각을 한 개의 조각으로 수집하려면  
  
         CollectedThresholdUsePercent 속성을 설정 `False`합니다.  
  
         CollectedThreshold 속성을 **5000**으로 설정합니다.  
  
6.  CollectedLabel 속성을 수집된 조각에 표시할 텍스트 레이블을 나타내는 문자열로 설정합니다.  
  
7.  (선택 사항) CollectedSliceExploded, CollectedColor, CollectedLegendText 및 CollectedToolTip 속성을 설정합니다. 이러한 속성은 단일 조각의 모양, 색, 레이블 텍스트, 범례 텍스트 및 도구 설명 측면을 변경합니다.  
  
### <a name="to-collect-small-slices-into-a-secondary-callout-pie-chart"></a>작은 조각을 보조 설명선 원형 차트로 수집하려면  
  
1.  위의 1-3단계를 수행합니다.  
  
2.  CollectedStyle 속성을 **CollectedPie**로 설정합니다.  
  
3.  CollectedThreshold 속성을 작은 조각을 한 조각으로 수집할 임계값을 나타내는 값으로 설정합니다. CollectedStyle 속성으로 설정 된 경우 **CollectedPie**을 항상으로 설정 하면 collectedthresholdusepercent 속성 `True`, 수집 된 임계값은 항상 백분율로 측정 및 합니다.  
  
4.  (선택 사항) CollectedColor, CollectedLabel, CollectedLegendText 및 CollectedToolTip 속성을 설정합니다. "Collected"로 명명된 다른 모든 속성은 수집된 원형에 적용되지 않습니다.  
  
> [!NOTE]  
>  보조 원형 차트는 데이터의 작은 조각을 기반으로 계산되므로 미리 보기에만 나타나며 디자인 화면에는 나타나지 않습니다.  
  
> [!NOTE]  
>  보조 원형 차트의 서식은 지정할 수 없습니다. 이러한 이유로 원형 조각을 수집할 때는 첫 번째 방법을 사용하는 것이 좋습니다.  
  
## <a name="see-also"></a>관련 항목  
 [원형 차트&#40;보고서 작성기 및 SSRS&#41;](charts-report-builder-and-ssrs.md)   
 [차트의 데이터 요소에 서식 지정&#40;보고서 작성기 및 SSRS&#41;](formatting-data-points-on-a-chart-report-builder-and-ssrs.md)   
 [원형 차트 외부에 데이터 요소 레이블 표시&#40;보고서 작성기 및 SSRS&#41;](display-data-point-labels-outside-a-pie-chart-report-builder-and-ssrs.md)   
 [원형 차트에서 백분율 값 표시&#40;보고서 작성기 및 SSRS&#41;](display-percentage-values-on-a-pie-chart-report-builder-and-ssrs.md)   
 [차트에 3D 효과 추가&#40;보고서 작성기 및 SSRS&#41;](chart-effects-add-3d-effects-report-builder.md)  
  
  
