---
title: 작업할 Analysis Services 프로젝트 및 데이터베이스 개발에서 | Microsoft Docs
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: multidimensional-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 018f937ed07c202aad17d5e7758f41a3082c4870
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62743119"
---
# <a name="work-with-analysis-services-projects-and-databases-in-development"></a>작업할 Analysis Services 프로젝트 및 데이터베이스 개발
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  프로젝트 모드나 온라인 모드로 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 를 사용하여 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 데이터베이스를 개발할 수 있습니다.  
  
## <a name="single-developer"></a>단일 개발자  
 단일 개발자가 전체 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 데이터베이스 및 모든 요소 개체를 개발하는 경우 이 개발자는 비즈니스 인텔리전스 솔루션의 수명 주기 동안 언제든지 프로젝트 모드나 온라인 모드로 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 를 사용할 수 있습니다. 단일 개발자의 경우 모드 선택은 별로 중요하지 않습니다. 원본 제어 시스템과 통합된 상태로 오프라인 프로젝트 파일을 유지 관리하면 보관 및 롤백과 같은 많은 이점이 있습니다. 단일 개발자의 경우에는 다른 개발자와 변경 작업에 관해 통신할 필요가 없습니다.  
  
## <a name="multiple-developers"></a>다중 개발자  
 다중 개발자가 비즈니스 인텔리전스 솔루션에서 작업할 때 개발자가 원본 제어를 포함하는 프로젝트 모드로 작업하지 않으면 항상은 아니지만 대부분의 경우에서 문제가 발생합니다. 원본 제어는 두 명의 개발자가 동시에 같은 개체를 변경하지 않도록 합니다.  
  
 예를 들어 한 개발자가 프로젝트 모드로 작업 중이며 선택한 개체를 변경한다고 가정합니다. 또한 이 개발자가 변경하는 동안 다른 개발자가 온라인 모드로 배포된 데이터베이스를 변경한다고 가정합니다. 첫 번째 개발자가 수정된 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 프로젝트를 배포하려고 하면 문제가 발생합니다. 즉, [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 에서 배포된 데이터베이스 내의 개체가 변경되었음을 감지하고 개발자에게 전체 데이터베이스를 덮어써서 두 번째 개발자의 변경 내용을 덮어쓸 것인지 묻는 메시지를 표시합니다. [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 에는 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 데이터베이스 인스턴스와 덮어쓸 프로젝트 개체 간 변경 내용을 해결할 방법이 없으므로 사실상 첫 번째 개발자는 변경 내용을 모두 삭제하고 현재 버전의 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 데이터베이스를 기반으로 새 프로젝트에서 다시 시작하는 수밖에 없습니다.  
  
  
