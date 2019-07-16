---
title: 멤버 그룹 정의 | Microsoft Docs
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: multidimensional-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 1da226353847409f1d808472dc155cb2055395cd
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/15/2019
ms.locfileid: "68179596"
---
# <a name="attribute-properties---define-member-groups"></a>특성 속성 - 멤버 그룹 정의
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  특성에 많은 수의 멤버가 있는 경우 해당 멤버를 버킷으로 그룹화하여 계층에서 데이터를 탐색할 때 사용자에게 표시되는 멤버 수를 줄일 수 있습니다. 멤버가 그룹인 버킷 수를 결정하고 버킷의 명명 구성표를 설정할 수도 있습니다. 자세한 내용은 [특성 멤버 그룹화&#40;불연속화&#41;](../../analysis-services/multidimensional-models/attribute-properties-group-attribute-members.md)를 참조하세요.  
  
 **의** 속성 **창을 통해 액세스하는** DiscretizationMethod [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]속성을 설정하여 멤버를 그룹화합니다.  
  
 멤버 그룹을 만드는 경우 차원을 처리할 때까지 변경 내용이 사용자에게 표시되지 않습니다. 자세한 내용은 [다차원 모델 처리&#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/processing-a-multidimensional-model-analysis-services.md)를 참조하세요.  
  
### <a name="to-create-member-groups"></a>멤버 그룹을 만들려면  
  
1.  작업할 차원을 엽니다. 기본적으로 **차원 구조** 탭이 열립니다.  
  
2.  **특성**에서 멤버를 그룹화할 특성을 마우스 오른쪽 단추로 클릭한 다음 **속성**을 클릭합니다.  
  
3.  **DiscretizationMethod** 옆의 드롭다운 목록에서 멤버 그룹화 방법을 선택합니다. **DiscretizationMethod** 설정에 대한 자세한 내용은 [특성 멤버 그룹화&#40;불연속화&#41;](../../analysis-services/multidimensional-models/attribute-properties-group-attribute-members.md)를 참조하세요.  
  
  
