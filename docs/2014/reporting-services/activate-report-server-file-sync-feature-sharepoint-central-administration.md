---
title: SharePoint 중앙 관리에서 보고서 서버 파일 동기화 기능 활성화 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
ms.assetid: 32d1988d-07e7-41c2-b636-e65ecfae4677
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: 69d059807b7d48fe71cffb120c73fa9aa004a8bb
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/11/2019
ms.locfileid: "56018005"
---
# <a name="activate-the-report-server-file-sync-feature-in-sharepoint-central-administration"></a>SharePoint 중앙 관리에서 보고서 서버 파일 동기화 기능 활성화
  [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 보고서 서버 파일 동기화 기능은 SharePoint 이벤트 처리기를 활용하여 보고서 서버 카탈로그를 문서 라이브러리의 항목과 동기화합니다. 이 기능은 사용자가 게시된 보고서 항목을 SharePoint 문서 라이브러리에 직접 자주 업로드하는 경우에 유용합니다. 파일 동기화 기능이 활성화되지 않은 경우 내용이 동기화되지만 자주 동기화되지는 않습니다.  
  
 파일 동기화 기능은 SharePoint 제품용 [!INCLUDE[ssRSCurrent](../includes/ssrscurrent-md.md)] 추가 기능을 설치한 후 SharePoint 사이트 관리에서 활성화할 수 있습니다.  
  
 이 기능은 사이트별로 수동으로 활성화하고 비활성화할 수 있으나 사이트 모음 수준에서는 이렇게 할 수 없습니다.  
  
## <a name="prerequisites"></a>사전 요구 사항  
 SharePoint용 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 추가 기능을 설치해야 합니다. 추가 기능이 설치되어 있지 않으면 파일 동기화 기능이 사이트 기능 목록에 표시되지 않습니다.  
  
 설치를 확인하려면 [!INCLUDE[msCoName](../includes/msconame-md.md)] Windows **제어판**에서 설치된 애플리케이션 목록을 확인합니다. [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 추가 기능이 설치되어 있으면 이 항목의 지침에 따라 보고서 서버 파일 동기화 기능을 활성화합니다.  
  
### <a name="to-activate-or-deactivate-the-reporting-services-file-sync-feature-on-a-site"></a>사이트에서 Reporting Services 파일 동기화 기능을 활성화 또는 비활성화하려면  
  
1.  사이트의 주 페이지에서 **사이트 동작** 메뉴를 클릭하고 **사이트 설정**을 클릭합니다.  
  
2.  **사이트 동작** 에서 **사이트 기능 관리**를 클릭합니다.  
  
3.  목록에서 **보고서 서버 파일 동기화** 를 찾습니다.  
  
4.  **활성화**를 클릭합니다.  
  
> [!NOTE]  
>  보고서 서버 파일 동기화 기능을 비활성화하려면 동일한 절차를 따르면서 **비활성화**를 클릭합니다.  
  
## <a name="see-also"></a>관련 항목  
 [보고서 파트 문제 해결 &#40;보고서 작성기 및 SSRS&#41;](report-parts-report-builder-and-ssrs.md)   
 [SharePoint에서 보고서 서버 및 파워 뷰 통합 사이트 모음 기능 활성화](activate-the-report-server-and-power-view-integration-features-in-sharepoint.md)   
 [설치 또는 제거는 Reporting Services 추가-SharePoint 용 &#40;SharePoint 2010 및 SharePoint 2013&#41;](install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md)   
 [설치 또는 제거는 Reporting Services 추가-SharePoint 용 &#40;SharePoint 2010 및 SharePoint 2013&#41;](install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md)  
  
  
