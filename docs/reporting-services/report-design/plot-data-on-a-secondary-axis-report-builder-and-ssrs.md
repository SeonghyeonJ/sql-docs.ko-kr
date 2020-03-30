---
title: 보조 축에 데이터 표시(보고서 작성기) | Microsoft Docs
ms.date: 05/30/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-design
ms.topic: conceptual
ms.assetid: 094f39bf-3634-4852-9fc3-3adec4b266e5
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: b53f514104032f55dcdbc88986f8e2679ecd5700
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/29/2020
ms.locfileid: "77082367"
---
# <a name="plot-data-on-a-secondary-axis-report-builder-and-ssrs"></a>보조 축에 데이터 표시(보고서 작성기 및 SSRS)

차트는 기본 및 보조라는 두 가지 축 유형이 있습니다. 보조 축은 공통 범주를 공유하는 두 개의 개별 데이터 범위를 사용하여 두 개의 값 집합을 비교할 때 유용합니다.  
  
 예를 들어 2008년에 대한 수익과 세금을 계산하는 차트가 있다고 가정해 보십시오. 이 경우 2008년이라는 기간은 두 값 집합에 대한 공통 요소입니다. 하지만 두 계열을 동일한 y축에 표시할 경우 y축 눈금은 데이터 세트의 가장 큰 값에 최적화되기 때문에 제대로 된 비교를 할 수 없습니다. 수익을 기본 축에 표시하고 세금을 보조 축에 표시하면 고유한 값 눈금이 있는 y축에 각 계열을 표시할 수 있습니다. 계열은 여전히 공통 x축을 공유합니다.  
  
 비교할 계열이 3개 이상인 경우에는 차트의 여러 계열을 비교 및 표시하기 위한 다른 방법을 고려해야 합니다. 자세한 내용은 [차트의 여러 계열](../../reporting-services/report-design/multiple-series-on-a-chart-report-builder-and-ssrs.md)을 참조하세요.  
  
 이 차트의 예는 예제 보고서로 제공됩니다. 이 샘플 보고서 및 기타 보고서를 다운로드하는 방법은 [보고서 작성기 및 보고서 디자이너 샘플 보고서](https://go.microsoft.com/fwlink/?LinkId=198283).  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-plot-a-series-on-the-secondary-axis"></a>보조 축에 계열을 표시하려면  
  
1.  차트에서 계열을 마우스 오른쪽 단추로 클릭하거나 **값** 영역에서 보조 축에 표시하려는 필드를 마우스 오른쪽 단추로 클릭하고 **계열 속성**을 클릭합니다. **계열 속성** 대화 상자가 표시됩니다.  
  
2.  **축 및 차트 영역**을 클릭하고 설정하려는 보조 축, 값 축 또는 범주 축을 선택합니다.  

## <a name="next-steps"></a>다음 단계

[차트의 축 레이블 서식 지정](../../reporting-services/report-design/formatting-axis-labels-on-a-chart-report-builder-and-ssrs.md)   
[축 간격 지정](../../reporting-services/report-design/specify-an-axis-interval-report-builder-and-ssrs.md)  

추가 질문이 있으신가요? [Reporting Services 포럼에서 질문하기](https://go.microsoft.com/fwlink/?LinkId=620231)
