---
title: Analysis Services 테이블 형식 모델의 계산 | Microsoft Docs
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 53455f542e10e816aa55272026a875cf3cf87107
ms.sourcegitcommit: 38076f423663bdbb42f325e3d0624264e05beda1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/06/2018
ms.locfileid: "52984074"
---
# <a name="calculations-in-tabular-models"></a>테이블 형식 모델의 계산
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  데이터를 모델로 가져온 후에는 계산을 추가하여 해당 데이터를 집계, 필터링, 확장, 결합 및 보호할 수 있습니다. 테이블 형식 모델에서는 사용자 지정 계산을 만들기 위한 수식 언어인 DAX(Data Analysis Expressions)가 사용됩니다. 테이블 형식 모델에서 DAX 수식을 사용하여 만드는 계산은 *계산 열*, *측정값*및 *행 필터*에 사용됩니다.  
  
## <a name="in-this-section"></a>단원 내용  
  
|항목|Description|  
|-----------|-----------------|  
|[테이블 형식 모델의 DAX 이해](../../analysis-services/tabular-models/understanding-dax-in-tabular-models-ssas-tabular.md)|테이블 형식 모델에서 계산 열, 측정값 및 행 필터에 대한 계산을 만드는 데 사용되는 DAX(Data Analysis Expressions) 수식 언어에 대해 설명합니다.|  
|[DirectQuery 모드에서의 DAX 수식 호환성](http://msdn.microsoft.com/981b6a68-434d-4db6-964e-d92f8eb3ee3e)|차이점을 설명하고, DirectQuery 모드에서 지원되지 않는 함수와 지원은 되지만 다른 결과를 반환할 수 있는 함수의 목록을 제공합니다.|  
|[DAX(Data Analysis Expressions) 참조](http://msdn.microsoft.com/70a82136-0926-4a91-bcb3-e18e82593b0d)|이 섹션에서는 DAX 구문, 연산자 및 함수에 대해 자세히 설명합니다.|  
  
> [!NOTE]  
>  이 섹션에서는 계산을 만드는 단계별 태스크는 제공되지 않습니다. 계산은 계산 열, 측정값 및 역할의 행 필터에 지정되기 때문에 DAX 수식을 만드는 장소에 대한 지침은 해당 기능과 관련된 태스크에서 제공합니다. 자세한 내용은 [계산 열을 만듭니다](../../analysis-services/tabular-models/ssas-calculated-columns-create-a-calculated-column.md)를 [만들기 및 관리 하는 측정값](../../analysis-services/tabular-models/create-and-manage-measures-ssas-tabular.md), 및 [만들기 및 관리 역할](../../analysis-services/tabular-models/create-and-manage-roles-ssas-tabular.md)입니다.  
  
> [!NOTE]  
>  DAX를 사용하여 테이블 형식 모델을 쿼리할 수도 있지만 이 섹션에서는 DAX 수식을 사용하여 계산을 만드는 과정에 대해서만 설명합니다.  
  
  
