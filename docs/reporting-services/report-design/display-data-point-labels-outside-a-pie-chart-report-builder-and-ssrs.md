---
title: 원형 차트 외부에 데이터 요소 레이블 표시(보고서 작성기) | Microsoft Docs
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-design
ms.topic: conceptual
ms.assetid: 959b7574-cf43-470b-b592-4944d8a9948f
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: bd5607aa5e3d6f93692e251da7c3490d8f62cb86
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2020
ms.locfileid: "77080502"
---
# <a name="display-data-point-labels-outside-a-pie-chart-report-builder-and-ssrs"></a>원형 차트 외부에 데이터 요소 레이블 표시(보고서 작성기 및 SSRS)
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]에서 원형 차트 레이블 지정은 몇 개의 데이터 조각에만 레이블을 표시하도록 최적화되어 있습니다. 원형 차트에 조각이 너무 많을 경우 레이블이 겹쳐서 표시될 수 있습니다. 한 가지 해결 방법은 원형 차트 외부에 레이블을 표시하여 이름이 긴 데이터 레이블에 대한 공간을 더 확보하는 것입니다. 그래도 여전히 레이블이 겹칠 경우 3D를 설정하여 더 많은 공간을 만들 수 있습니다. 이렇게 하면 원형 차트의 지름이 줄어 차트 주위에 더 많은 공간이 확보됩니다.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-display-data-point-labels-inside-a-pie-chart"></a>원형 차트 내부에 데이터 요소 레이블을 표시하려면  
  
1.  보고서에 원형 차트를 추가합니다. 자세한 내용은 [보고서에 차트 추가&#40;보고서 작성기 및 SSRS&#41;](../../reporting-services/report-design/add-a-chart-to-a-report-report-builder-and-ssrs.md)를 참조하세요.  
  
2.  디자인 화면에서 차트를 마우스 오른쪽 단추로 클릭하고 **데이터 레이블 표시**를 선택합니다.  
  
### <a name="to-display-data-point-labels-outside-a-pie-chart"></a>원형 차트 외부에 데이터 요소 레이블을 표시하려면  
  
1.  원형 차트를 만들고 데이터 레이블을 표시합니다.  
  
2.  속성 창을 엽니다.  
  
3.  디자인 화면에서 원형 자체를 클릭하여 속성 창에 **범주** 속성을 표시합니다.  
  
4.  **CustomAttributes** 노드를 확장합니다. 원형 차트에 대한 특성 목록이 표시됩니다.  
  
5.  **PieLabelStyle** 속성을 **Outside**로 설정합니다.  
  
6.  **PieLineColor** 속성을 **Black**으로 설정합니다. PieLineColor 속성은 각 데이터 요소 레이블에 대한 설명선을 정의합니다.  
  
### <a name="to-prevent-overlapping-labels-displayed-outside-a-pie-chart"></a>원형 차트 외부에 표시되는 레이블이 겹쳐지지 않도록 하려면  
  
1.  외부 레이블을 사용하여 원형 차트를 만듭니다.  
  
2.  디자인 화면에서 원형 차트 외부와 차트 테두리 내부 사이를 마우스 오른쪽 단추로 클릭하고 **차트 영역 속성**을 선택합니다. **차트 영역 속성** 대화 상자가 나타납니다.  
  
3.  **3D 옵션** 탭에서 **3D 사용**을 선택합니다.  
  
4.  레이블을 위한 공간을 더 확보하면서 차트를 계속 2차원으로 표시하려면 **회전** 및 **기울기** 속성을 **0**으로 설정합니다.  
  
## <a name="see-also"></a>참고 항목  
 [원형 차트&#40;보고서 작성기 및 SSRS&#41;](../../reporting-services/report-design/pie-charts-report-builder-and-ssrs.md)   
 [원형 차트에서 작은 조각 수집&#40;보고서 작성기 및 SSRS&#41;](../../reporting-services/report-design/collect-small-slices-on-a-pie-chart-report-builder-and-ssrs.md)   
 [원형 차트에서 백분율 값 표시&#40;보고서 작성기 및 SSRS&#41;](../../reporting-services/report-design/display-percentage-values-on-a-pie-chart-report-builder-and-ssrs.md)  
  
  
