---
title: 사용자 지정 보고서 항목 구현 요구 사항 | Microsoft Docs
ms.date: 03/14/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: custom-report-items
ms.topic: reference
helpviewer_keywords:
- custom report items
ms.assetid: cfacd816-00d6-4a3d-be72-1bba6f7f6886
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: e25938d690d6e1046d1d0e75ae5a4952b05d4615
ms.sourcegitcommit: 312b961cfe3a540d8f304962909cd93d0a9c330b
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 11/05/2019
ms.locfileid: "73594519"
---
# <a name="custom-report-item-implementation-requirements"></a>사용자 지정 보고서 항목 구현 요구 사항
  이 항목에서는 사용자 지정 보고서 항목을 개발하고 배포하기 위한 선행 조건에 대해 설명합니다.  
  
## <a name="development-and-deployment-requirements"></a>개발 및 배포 요구 사항  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]에 대한 사용자 지정 보고서 항목을 개발하려면 다음이 필요합니다.  
  
-   [!INCLUDE[msCoName](../../includes/msconame-md.md)] 및 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]와 함께 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]를 실행하는 서버에 대한 관리 액세스  
  
-   [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK(소프트웨어 개발 키트)가 설치된 [!INCLUDE[vsprvsext](../../includes/vsprvsext-md.md)] 이상  
  
-   [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK 설명서에 대한 액세스  
  
-   구성 요소 제작 및 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]의 구성 요소 모델 네임스페이스에 대한 지식.  
  
## <a name="language-and-namespace-requirements"></a>언어 및 네임스페이스 요구 사항  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 사용자 지정 보고서 항목은 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]를 완벽하게 지원합니다. 원하는 .NET 호환 언어를 사용하여 사용자 지정 보고서 항목을 개발할 수 있습니다.  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]에서는 코딩, 디버깅, 테스트 등의 반복되는 주기를 단순화 및 가속화하고 쉽게 배포할 수 있도록 다양한 도구와 기능을 개발자에게 제공합니다. [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK에는 [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] 과 C# 컴파일러 및 관련 도구가 포함되어 있습니다.  
  
-   사용자 지정 보고서 항목은 **Microsoft.ReportDesigner** 및 <xref:Microsoft.ReportingServices.Interfaces> 네임스페이스를 사용합니다. 이 네임스페이스는 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]의 일부로 설치되는 Microsoft.ReportingServices.Designer.DLL 및 Microsoft.ReportingServices.Interfaces.DLL 어셈블리에 저장됩니다.  
  
-   사용자 지정 보고서 항목 디자인 타임 구성 요소는 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]의 <xref:System.ComponentModel> 네임스페이스에서 인터페이스를 구현해야 합니다. <xref:System.ComponentModel>은 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK 설명서를 참조하십시오.  

## <a name="see-also"></a>참고 항목  
 [사용자 지정 보고서 항목 런타임 구성 요소 만들기](../../reporting-services/custom-report-items/creating-a-custom-report-item-run-time-component.md)   
 [사용자 지정 보고서 항목 디자인 타임 구성 요소 만들기](../../reporting-services/custom-report-items/creating-a-custom-report-item-design-time-component.md)   
 [방법: 사용자 지정 보고서 항목 배포](../../reporting-services/custom-report-items/how-to-deploy-a-custom-report-item.md)   
 [사용자 지정 보고서 항목 클래스 라이브러리](../../reporting-services/custom-report-items/custom-report-item-class-libraries.md)  
  
  
