---
title: 안전한 개발(Reporting Services) | Microsoft Docs
description: Reporting Services가 사용하는 코드 액세스 보안 시스템에 대해 알아봅니다. 이 시스템은 엄격하게 제한된 관리자 정의 보안 컨텍스트에서 코드를 실행합니다.
ms.date: 03/14/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: extensions
ms.topic: reference
helpviewer_keywords:
- development security [Reporting Services]
- security [Reporting Services], development
- security [Reporting Services], strategies
ms.assetid: 12161a6c-b93b-4312-9d27-0c922561eb9b
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 69d60e4a68deee28c639cc5e100456ef1c9c3552
ms.sourcegitcommit: 2f166e139f637d6edfb5731510d632a13205eb25
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84529411"
---
# <a name="secure-development-reporting-services"></a>안전한 개발(Reporting Services)
  [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]는 엄격한 제약을 받는 관리자 정의 보안 컨텍스트에서 코드를 실행할 수 있는 강력한 보안 시스템을 제공합니다. [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]에서는 코드 액세스 보안 또는 증명 정보 기반 보안이라고 하는 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 보안 시스템을 사용합니다. 코드 액세스 보안 하에서는 사용자가 안전하게 리소스에 액세스할 수 있지만 사용자가 실행하는 코드를 신뢰할 수 없는 경우 리소스에 대한 액세스가 거부됩니다.  
  
 특정 사용자가 아닌 코드 기반의 보안은 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]용으로 개발하는 사용자 지정 어셈블리나 데이터, 전달, 렌더링 및 보안 확장에 대해 보안을 표시합니다. 확장 코드는 여러 명의 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 사용자가 실행할 수 있으며 전체 사용자 수는 개발 시에 알 수 있습니다. 개발하는 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]의 사용자 지정 어셈블리나 확장에는 특정 보안 정책이 필요합니다. 이러한 보안 정책은 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]의 유형으로 표시됩니다. 코드 액세스 보안에 대한 자세한 내용은 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 설명서에서 "코드 액세스 보안"을 참조하십시오.  
  
## <a name="in-this-section"></a>섹션 내용  
 [Reporting Services의 코드 액세스 보안](../../../reporting-services/extensions/secure-development/code-access-security-in-reporting-services.md)  
 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]의 사용자 지정 어셈블리 및 확장 프로그램에 대해 코드 액세스 보안 및 정책 구성을 소개합니다.  
  
 [보안 정책 이해](../../../reporting-services/extensions/secure-development/understanding-security-policies.md)  
 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]의 다양한 어셈블리 유형 및 코드 액세스 보안이 코드 사용 권한에 미치는 영향에 대해 설명합니다.  
  
 [Reporting Services 보안 정책 파일 사용](../../../reporting-services/extensions/secure-development/using-reporting-services-security-policy-files.md)  
 여러 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 구성 요소 및 해당 정책 구성 파일에 대해 설명합니다.  
  
  
