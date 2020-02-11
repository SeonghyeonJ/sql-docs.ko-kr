---
title: Analysis Services 프로젝트 배포 (SSDT) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- deploy [Analysis Services]
- projects [Analysis Services], deploying
- Business Intelligence Development Studio, deploying projects [Analysis Services]
ms.assetid: 29490a5b-1573-4a35-9277-10c6a6e4ef0e
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 5b6c79c2ea4355e9d889e235c8185a2460c0ed8c
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66075384"
---
# <a name="deploy-analysis-services-projects-ssdt"></a>Analysis Services 프로젝트 배포(SSDT)
  
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 에서 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]프로젝트를 개발하는 동안 프로젝트에서 정의된 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 데이터베이스를 만들기 위해 개발 서버에 자주 프로젝트를 배포합니다. 큐브에서 셀을 찾아보거나 차원 멤버를 찾아보거나 KPI(핵심 성과 지표) 수식을 확인하는 등 프로젝트를 테스트하려면 이 작업을 수행해야 합니다.  
  
## <a name="deploying-a-project"></a>프로젝트 배포  
 독립적으로 프로젝트를 배포하거나 솔루션 내의 모든 프로젝트를 배포할 수 있습니다. 프로젝트를 배포하면 여러 작업이 순서대로 수행됩니다. 먼저 프로젝트가 작성됩니다. 이 단계에서는 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 데이터베이스와 해당 요소 개체를 정의하는 출력 파일을 만듭니다. 다음에는 대상 서버의 유효성이 확인됩니다. 마지막으로 대상 데이터베이스와 해당 개체가 대상 서버에 생성됩니다. 배포 중에 배포 엔진은 이전 배포 시 프로젝트에서 해당 개체를 만들지 않은 경우 기존 데이터베이스를 프로젝트의 내용으로 모두 바꿉니다.  
  
 초기 배포 후 Incrementalsnapshot.xml 파일은 \<프로젝트 이름> \obj 폴더에 생성 됩니다. 이 파일은 대상 서버의 데이터베이스나 해당 개체가 프로젝트 외부에서 변경되었는지 여부를 확인하는 데 사용됩니다. 이 경우 대상 데이터베이스의 모든 개체를 덮어쓸 것인지 묻는 메시지가 표시됩니다. 모든 변경이 프로젝트 내에서 수행되었으며 프로젝트에 증분 배포가 구성된 경우에는 변경 내용만 대상 서버로 배포됩니다.  
  
 프로젝트 구성 및 관련 설정에 따라 프로젝트 배포에 사용되는 배포 속성이 결정됩니다. 공유 프로젝트의 경우 각 개발자가 선택한 프로젝트 구성 옵션이 포함된 고유한 구성을 사용할 수 있습니다. 예를 들어 각 개발자는 서로 다른 테스트 서버를 지정하여 다른 개발자와 격리된 상태로 작업할 수 있습니다.  
  
## <a name="see-also"></a>참고 항목  
 [SSDT&#41;&#40;Analysis Services 프로젝트 만들기](create-an-analysis-services-project-ssdt.md)  
  
  
