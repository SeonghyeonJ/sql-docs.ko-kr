---
title: 보고서에 차트 추가(보고서 작성기 및 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: a6b595dc-f775-4a53-8554-74a0bf9335ec
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 257df5742c2f8dec7d48c6d3afb4d6c6373d058c
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66106887"
---
# <a name="add-a-chart-to-a-report-report-builder-and-ssrs"></a>보고서에 차트 추가(보고서 작성기 및 SSRS)
  시각적 형식으로 데이터를 요약하려면 차트 데이터 영역을 사용합니다. 표현하려는 데이터의 형식에 적합한 차트 종류를 선택하는 것이 중요합니다. 선택한 차트 종류에 따라 데이터를 차트 형태로 만들었을 때 해당 데이터를 얼마나 잘 해석할 수 있는지가 결정됩니다. 자세한 내용은 [차트&#40;보고서 작성기 및 SSRS&#41;](charts-report-builder-and-ssrs.md)를 참조하세요.  
  
 보고서에 차트 데이터 영역을 추가하는 가장 간단한 방법은 새 차트 마법사를 실행하는 것입니다. 이 마법사는 세로 막대형 차트, 선형 차트, 원형 차트, 가로 막대형 차트 및 영역형 차트를 제공합니다. 또한 차트를 직접 추가할 수도 있습니다.  
  
 디자인 화면에 차트 데이터 영역을 추가한 후에는 숫자 데이터 및 숫자가 아닌 데이터에 대한 보고서 데이터 세트 필드를 차트의 차트 데이터 창으로 끌 수 있습니다. 차트를 클릭하여 차트 데이터 창을 표시합니다. 이 창에는 계열 그룹, 범주 그룹 및 값의 세 영역이 있습니다.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-a-chart-to-a-report-by-using-the-chart-wizard"></a>차트 마법사를 사용하여 보고서에 차트를 추가하려면  
  
1.  > [!NOTE]  
    >  차트 마법사는 보고서 작성기에서만 사용할 수 있습니다.  
  
     **삽입** 탭에서 **차트**를 클릭한 다음 **차트 마법사**를 클릭합니다.  
  
2.  **새 차트** 마법사의 단계별 지침을 따릅니다.  
  
3.  **홈** 탭에서 **실행** 을 클릭하여 렌더링된 보고서를 표시합니다.  
  
4.  **실행** 탭에서 **디자인** 을 클릭하여 보고서에 대한 작업을 진행합니다.  
  
### <a name="to-add-a-chart-to-a-report"></a>보고서에 차트를 추가하려면  
  
1.  보고서를 만들고 데이터 세트를 정의합니다. 자세한 내용은 [보고서에 데이터 추가 &#40;보고서 작성기 및 SSRS&#41;](../report-data/report-datasets-ssrs.md)를 참조 하세요.  
  
2.  **삽입** 탭에서 **차트**를 클릭한 다음 **차트 삽입**을 클릭합니다.  
  
3.  디자인 화면에서 차트 왼쪽 위 모퉁이를 배치할 위치를 클릭한 다음 차트 오른쪽 아래 모퉁이로 지정할 위치까지 끕니다.  
  
     **차트 종류 선택** 대화 상자가 나타납니다.  
  
4.  추가할 차트 종류를 선택합니다. [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
5.  차트를 클릭하여 **차트 데이터** 창을 표시합니다.  
  
6.  **값** 영역에 하나 이상의 필드를 추가합니다. 이 정보는 값 축에 점으로 표시됩니다.  
  
7.  **범주 그룹** 영역에 그룹화 필드를 추가합니다. **범주 그룹** 영역에 이 필드를 추가하면 그룹화 필드가 자동으로 만들어집니다. 각 그룹은 계열의 데이터 요소를 나타냅니다.  
  
8.  범주별로 데이터를 요약하려면 데이터 필드를 마우스 오른쪽 단추로 클릭하고 **계열 속성**을 클릭합니다. **범주** 상자의 드롭다운 목록에서 범주 필드를 선택합니다. [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
9. **홈** 탭에서 **실행** 을 클릭하여 렌더링된 보고서를 표시합니다.  
  
10. **실행** 탭에서 **디자인** 을 클릭하여 보고서에 대한 작업을 진행합니다.  
  
 가로 막대형 차트 및 세로 막대형 차트와 같이 축이 있는 차트에서 범주 축에는 일부 범주 레이블이 표시되지 않을 수 있습니다. 축 레이블을 변경하는 방법에 대한 자세한 내용은 [축 간격 지정&#40;보고서 작성기 및 SSRS&#41;](specify-an-axis-interval-report-builder-and-ssrs.md)을 참조하세요.  
  
## <a name="see-also"></a>참고 항목  
 [차트&#40;보고서 작성기 및 SSRS&#41;](charts-report-builder-and-ssrs.md)   
 [차트 종류&#40;보고서 작성기 및 SSRS&#41;](chart-types-report-builder-and-ssrs.md)   
 [차트의 빈 데이터 요소 및 Null 데이터 요소&#40;보고서 작성기 및 SSRS&#41;](empty-and-null-data-points-in-charts-report-builder-and-ssrs.md)   
 [자습서: 보고서에 가로 막대형 차트 추가(보고서 작성기)](https://go.microsoft.com/fwlink/?LinkId=198052)   
 [자습서: 보고서에 가로 막대형 차트 추가(보고서 디자이너)](https://go.microsoft.com/fwlink/?LinkId=198042)   
 [자습서: 보고서에 원형 차트 추가(보고서 작성기)](https://go.microsoft.com/fwlink/?LinkId=198051)   
 [자습서: 보고서에 원형 차트 추가(보고서 디자이너)](https://go.microsoft.com/fwlink/?LinkId=198041)  
  
  
