---
title: 지원 되지 않는 기능
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.prod_service: reporting-services-native, reporting-services-sharepoint
ms.topic: conceptual
ms.custom: seodec18
ms.date: 12/14/2018
ms.openlocfilehash: 14a5a6e38d4c9fcf306436374d80dd1c1c08b27e
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/26/2020
ms.locfileid: "67413048"
---
# <a name="discontinued-functionality-in-sql-server-reporting-services-ssrs"></a>SSRS(SQL Server Reporting Services)에서 지원되지 않는 기능

  이 항목에서는 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 에서 더 이상 사용할 수 없는 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]기능에 대해 설명합니다. 운영 체제 또는 [!INCLUDE[msCoName](../includes/msconame-md.md)] 인터넷 정보 서비스(IIS)의 특정 버전에 대해 더 이상 지원되지 않는 기능에 대해서는 언급하지 않습니다. 시스템 필수 구성 요소에 대 한 자세한 내용은 [SQL Server 2014을 설치 하기 위한 하드웨어 및 소프트웨어 요구 사항](../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md)을 참조 하세요.  
  
 이 항목의 내용:  
  
- [SQL Server 2014 Reporting Services 지원 되지 않는 기능](#bkmk_sql14)  
  
- [SQL Server 2012 Reporting Services에서 지원되지 않는 기능](#bkmk_rc0)  
  
- [SQL Server 2008 R2 Reporting Services에서 지원되지 않는 기능](#bkmk_kj)  
  
##  <a name="sssql14-reporting-services-discontinued-functionality"></a><a name="bkmk_sql14"></a>[!INCLUDE[ssSQL14](../includes/sssql14-md.md)] Reporting Services 지원 되지 않는 기능

 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 기능은 [!INCLUDE[ssSQL14](../includes/sssql14-md.md)]에서 사용됩니다.  
  
##  <a name="sssql11-reporting-services-discontinued-functionality"></a><a name="bkmk_rc0"></a>[!INCLUDE[ssSQL11](../includes/sssql11-md.md)] Reporting Services 지원 되지 않는 기능

 이 섹션에서는 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 에서 지원되지 않는 [!INCLUDE[ssSQL11](../includes/sssql11-md.md)]기능에 대해 설명합니다.  
  
 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 기능은 [!INCLUDE[ssSQL14](../includes/sssql14-md.md)]에서 사용됩니다.  
  
##  <a name="sql-server-2008-r2-reporting-services-discontinued-functionality"></a><a name="bkmk_kj"></a>SQL Server 2008 R2 Reporting Services 지원 되지 않는 기능

 이 섹션에서는에서 [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]중단에 대해 설명 합니다.  
  
> [!NOTE]  
> SQL Server 2008 R2는 SQL Server 2008의 부 버전 업그레이드이므로 SQL Server 2008 섹션의 내용도 검토하는 것이 좋습니다.
  
### <a name="64-bit-platform-support"></a>64비트 플랫폼 지원

 [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)]부터 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 구성 요소는 더 이상 Windows Server 2003 또는 Windows Server 2003 R2를 실행하는 Itanium 기반 서버를 지원하지 않습니다. [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]는 Itanium 기반 시스템용 Windows Server 2008 및 Itanium 기반 시스템용 Windows Server 2008 r 2를 비롯 한 다른 64 비트 운영 체제를 계속 지원 합니다. Itanium 기반 시스템 버전의 Windows Server 2003 또는 Windows Server 2003 R2에서 [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] 를 포함하는 [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] 설치를 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 로 업그레이드하려면 먼저 운영 체제를 업그레이드해야 합니다.  
  
### <a name="data-source-credentials-in-url-access"></a>URL 액세스의 데이터 원본 자격 증명

 URL 액세스 매개 변수 문자열인 *dsu:datasourcename=value* 및 *dsp:datasourcename=value* 는 이제 사용되지 않습니다. 이전 버전에서는 이러한 매개 변수 문자열이 보호되지 않는 일반 텍스트로 브라우저 캐시에 저장되었습니다.  
  
## <a name="next-steps"></a>다음 단계

 - [새로운 기능 &#40;Reporting Services&#41;](what-s-new-reporting-services.md)
 - [SQL Server 2014에서 SQL Server Reporting Services의 동작 변경 내용](behavior-changes-to-sql-server-reporting-services-in-sql-server-2016.md)
 - [SQL Server 2014의 SQL Server Reporting Services에서 지원되지 않는 기능](deprecated-features-in-sql-server-reporting-services-ssrs.md)