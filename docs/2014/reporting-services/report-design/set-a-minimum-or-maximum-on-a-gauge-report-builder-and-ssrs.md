---
title: 계기의 최소값 또는 최대값 설정(보고서 작성기 및 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: b4c260c0-5a88-4f30-8977-eb5cc78fc146
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 2c7a9ad23124105443349720d2d5769fb9227db2
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66105025"
---
# <a name="set-a-minimum-or-maximum-on-a-gauge-report-builder-and-ssrs"></a>계기의 최소값 또는 최대값 설정(보고서 작성기 및 SSRS)
  여러 그룹이 정의되는 차트와 달리 계기에는 하나의 값만 표시됩니다. 보고서 작성기 및 보고서 디자이너에서 사용자가 계기에 표시하려고 하는 한 값의 컨텍스트 또는 상대적 중요도를 확인하므로 사용자가 눈금의 최소값 및 최대값을 정의해야 합니다. 예를 들어 데이터 값이 0과 10 사이의 순위인 경우에는 대개 최소값과 최대값을 각각 0과 10으로 설정합니다. 간격 수는 최소값과 최대값으로 지정된 값을 기반으로 자동으로 계산됩니다. 기본적으로 최소값과 최대값은 0과 100으로 설정되지만 이러한 값은 임의의 값이므로 사용자가 변경해야 합니다. 애플리케이션에서는 값을 백분율로 계산하지 않습니다.  
  
 0부터 10000까지와 같이 값 범위가 큰 경우에는 승수를 사용하여 계기에서 0의 개수를 줄이는 것이 좋습니다. 승수를 사용하면 계기의 숫자 크기가 줄어들 뿐 값 자체는 줄어들지 않습니다.  
  
 식을 사용하여 **최소값** 및 **최대값** 옵션의 값을 설정할 수 있습니다. 자세한 내용은 [식&#40;보고서 작성기 및 SSRS&#41;](expressions-report-builder-and-ssrs.md)을 참조하세요.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-set-the-minimum-and-maximum-on-the-gauge"></a>계기의 최소값 및 최대값을 설정하려면  
  
1.  눈금을 마우스 오른쪽 단추로 클릭하고 **눈금 속성**을 선택합니다. **눈금 속성** 대화 상자가 나타납니다.  
  
2.  **일반**에서 **최소값**의 값을 지정합니다. 기본적으로 이 값은 0입니다. 필요한 경우 **식** (*fx*) 단추를 클릭하여 이 옵션의 값을 설정하는 식을 편집합니다.  
  
3.  **최대값**의 값을 지정합니다. 기본적으로 이 값은 100입니다. 필요한 경우 **식** (*fx*) 단추를 클릭하여 이 옵션의 값을 설정하는 식을 편집합니다.  
  
4.  (옵션) 최소값 및 최대값이 큰 경우 **눈금 레이블 곱하기** 옵션의 값을 지정합니다. 눈금을 줄이는 승수를 지정하려면 10진수를 사용합니다. 예를 들어 눈금이 0에서 1000 사이인 경우 승수 값을 0.01로 지정하면 눈금이 줄어 0에서 10 사이로 표시됩니다.  
  
## <a name="see-also"></a>관련 항목  
 [계기의 눈금 서식 지정&#40;보고서 작성기 및 SSRS&#41;](formatting-scales-on-a-gauge-report-builder-and-ssrs.md)   
 [계기의 포인터 서식 지정&#40;보고서 작성기 및 SSRS&#41;](formatting-pointers-on-a-gauge-report-builder-and-ssrs.md)   
 [계기&#40;보고서 작성기 및 SSRS&#41;](gauges-report-builder-and-ssrs.md)  
  
  
