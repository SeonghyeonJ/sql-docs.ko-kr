---
title: Dimension 개체 (Analysis Services 다차원 데이터) | Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- dimensions [Analysis Services], objects
ms.assetid: 7f3d55c7-cccb-4ad0-b6cb-3a2c9992dd68
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: c0c64f95b0c366453e1099c80d8e40b217fb7801
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2020
ms.locfileid: "62702457"
---
# <a name="dimension-objects-analysis-services---multidimensional-data"></a>차원 개체(Analysis Services - 다차원 데이터)
  단순 <xref:Microsoft.AnalysisServices.Dimension> 개체는 기본 정보, 특성 및 계층으로 구성되어 있습니다. 기본 정보에는 차원의 이름, 차원의 유형, 데이터 원본, 스토리지 모드 등이 포함됩니다. 특성은 차원의 실제 데이터를 정의합니다. 특성이 반드시 계층에 속할 필요는 없지만 계층은 특성으로 만들어집니다. 계층은 순서가 지정된 수준 목록을 만들고 사용자가 차원을 탐색할 수 있는 방법을 정의합니다.  
  
## <a name="in-this-section"></a>섹션 내용  
 다음 항목에서는 차원 개체를 디자인하고 구현하는 방법에 대해 자세히 설명합니다.  
  
|항목|Description|  
|-----------|-----------------|  
|[차원 &#40;Analysis Services 다차원 데이터&#41;](dimensions-analysis-services-multidimensional-data.md)|[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]차원은 큐브의 기본 구성 요소입니다. 고객, 대리점 또는 직원 등 사용자의 관심 영역과 관련된 데이터를 구성합니다.|  
|[특성 및 특성 계층](attributes-and-attribute-hierarchies.md)|차원은 데이터 원본 뷰의 테이블이나 뷰에 있는 하나 이상의 열에 바인딩되는 특성의 모음입니다.|  
|[의 차원 디자이너에 있는 차원 구조 뷰의](attribute-relationships.md)|[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]차원 내의 특성은 항상 키 특성과 직접 또는 간접적으로 관련이 있습니다. 모든 차원 특성이 동일한 관계형 테이블에서 파생되는 별모양 스키마를 기반으로 차원을 정의할 경우 차원의 키 특성과 각각의 키가 아닌 특성 간에 특성 관계가 자동으로 정의됩니다. 그러나 차원 특성이 관련된 여러 테이블에서 파생되는 눈송이 스키마를 기반으로 차원을 정의하면 다음 사이에서 특성 관계가 자동으로 정의됩니다.<br /><br /> -주 차원 테이블의 열에 바인딩된 키 특성과 키가 아닌 각 특성 사이입니다.<br />-기본 차원 테이블을 연결 하는 보조 테이블의 외래 키에 바인딩된 키 특성과 키 특성 사이입니다.<br />-보조 테이블의 외래 키에 바인딩된 특성과 보조 테이블의 열에 바인딩된 각각의 키가 아닌 특성 사이입니다.|  
  
  
