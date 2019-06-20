---
title: 기본 테이블 이름 수정 | Microsoft Docs
ms.date: 05/06/2019
ms.prod: sql
ms.technology: analysis-services
ms.custom: multidimensional-models
ms.topic: tutorial
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: cbb8490c7b60a65e909ed6905003a4ec61f80e59
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/15/2019
ms.locfileid: "65403855"
---
# <a name="lesson-1-4---modifying-default-table-names"></a>단원 1-4-기본 테이블 이름 수정
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]

데이터 원본 뷰에서 개체에 대한 **FriendlyName** 속성의 값을 변경하여 알아보기 쉽고 사용이 간편한 이름을 지정할 수 있습니다.  
  
아래의 태스크에서 데이터 원본 뷰에 있는 각 테이블의 이름에서 "**Dim**" 및 "**Fact**" 접두사를 제거하여 테이블의 이름을 변경합니다. 이렇게 하면 다음 단원에서 정의하게 될 큐브 및 차원 개체를 알아보기 쉽고 사용이 간편하게 만들 수 있습니다.  
  
> [!NOTE]  
> 또한 열의 이름을 변경하고, 계산 열을 정의하고, 데이터 원본 뷰에 있는 테이블이나 뷰를 조인하여 사용하기 쉽게 만들 수 있습니다.  
  
### <a name="to-modify-the-default-name-of-a-table"></a>테이블의 기본 이름을 수정하려면  
  
1.  **데이터 원본 뷰 디자이너** 의 **테이블**창에서 **FactInternetSales** 테이블을 마우스 오른쪽 단추로 클릭한 다음 **속성**을 클릭합니다.  
  
2.  Microsoft Visual Studio 창의 오른쪽에 속성 창이 표시되지 않으면 속성 창의 제목 표시줄에서 **자동 숨기기** 를 클릭하여 속성 창이 계속 표시되도록 합니다.  
  
    속성 창이 계속 열려 있으면 데이터 원본 뷰에 있는 각 테이블에 대한 속성을 보다 쉽게 변경할 수 있습니다. **자동 숨기기** 단추를 사용하여 속성 창을 계속 열어 놓지 않으면 **다이어그램** 창에서 다른 개체를 클릭할 때 창이 닫힙니다.  
  
3.  **FactInternetSales** 개체에 대한 **FriendlyName** 속성을 ***InternetSales***로 변경합니다.  
  
    **FriendlyName** 속성의 셀에서 떨어진 곳을 클릭하면 변경 내용이 적용됩니다. 다음 단원에서는 이 팩트 테이블을 기반으로 하는 측정값 그룹을 정의합니다. 이 단원에서 수행한 변경 작업으로 인해 팩트 테이블의 이름은 FactInternetSales가 아닌 InternetSales가 됩니다.  
  
4.  **테이블** 창에서 **DimProduct** 를 클릭합니다. 속성 창에서 **FriendlyName** 속성을 ***Product***로 변경합니다.  
  
5.  데이터 원본 뷰에 있는 나머지 테이블 각각의 **FriendlyName** 속성도 같은 방법으로 변경합니다. 즉 "**Dim**" 접두사를 제거합니다.  
  
6.  다 변경했으면 **자동 숨기기** 단추를 클릭하여 속성 창을 다시 숨깁니다.  
  
7.  **파일** 메뉴 또는 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]의 도구 모음에서 **모두 저장** 을 클릭하여 지금까지의 변경 내용을 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Tutorial 프로젝트에 저장합니다. 원할 경우 여기에서 자습서를 중지했다가 나중에 계속 진행할 수 있습니다.  
  
## <a name="next-lesson"></a>다음 단원  
[2단원: 정의 및 큐브를 배포 합니다.](lesson-2-defining-and-deploying-a-cube.md)  
  
## <a name="see-also"></a>관련 항목  
[다차원 모델의 데이터 원본 뷰](../multidimensional-models/data-source-views-in-multidimensional-models.md)  
[데이터 원본 뷰에서 속성 변경&#40;Analysis Services&#41;](../multidimensional-models/change-properties-in-a-data-source-view-analysis-services.md)  
  
  
  
