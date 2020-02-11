---
title: 보고서 뷰어의 로컬 모드 및 연결 된 모드 보고서 (SharePoint 모드의 Reporting Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: a230a9bb-6046-401f-b5e5-53ff6edf2264
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 86cff99688dda7a953a7da1d4104865beed5a98b
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2020
ms.locfileid: "75253175"
---
# <a name="local-mode-vs-connected-mode-reports-in-the-report-viewer-reporting-services-in-sharepoint-mode"></a>보고서 뷰어의 로컬 모드와 연결 모드 보고서 비교(SharePoint 모드의 Reporting Services)
  [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]보고서는 *로컬 모드* 또는 보고서 서버를 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 활용 하는 *연결 된 모드*에서 실행 되도록 구성할 수 있습니다. 데이터 확장 프로그램에서 로컬 모드 보고를 지원하는 경우 이제 보고서 뷰어를 사용하여 SharePoint에서 직접 보고서를 렌더링할 수 있습니다. 이 방법을 *로컬 모드*라고 합니다. 
  [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]의 이전 버전에서는 보고서 뷰어 컨트롤로 보고서를 렌더링하려면 SharePoint 팜을 사용하여 SharePoint 모드로 구성된 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 보고서 서버에 연결해야 했습니다. 이 방법을 *원격 모드* 또는 *연결된 모드*라고 합니다.  
  
 
  *로컬 모드* 에는 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 보고서 서버가 없습니다. SharePoint 제품용 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 추가 기능을 설치해야 하지만 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 보고서 서버는 필요하지 않습니다. 로컬 모드에서는 사용자가 보고서를 볼 수 있지만 구독, 데이터 경고 등과 같은 서버 쪽 기능에 액세스할 수 없습니다.  
  
||  
|-|  
|**[!INCLUDE[applies](../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]SharePoint 모드|  
  
 **항목 내용**  
  
-   [로컬 모드와 연결 된 모드 및 지원 되는 확장](#bkmk_local_vs_connected)  
  
-   [SharePoint 2013를 사용 하 여 로컬 모드 및 Access Services 구성](#bkmk_local_mode_sharepoint2013)  
  
-   [SharePoint 2010를 사용 하 여 로컬 모드 보고 구성](#bkmk_local_mode_sharepoint2010)  
  
##  <a name="bkmk_local_vs_connected"></a>로컬 모드와 연결 된 모드 및 지원 되는 확장  
 **로컬 모드:** 로컬 모드를 지 원하는 데이터 확장 프로그램이 있는 경우 보고서 뷰어는 SharePoint에서 보고서를 직접 렌더링 합니다. 
  *로컬 모드* 에는 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 보고서 서버가 없습니다. SharePoint 제품용 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 추가 기능을 설치해야 하지만 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 보고서 서버는 필요하지 않습니다. 로컬 모드에서는 사용자가 보고서를 볼 수 있지만 구독, 데이터 경고 등과 같은 서버 쪽 기능에 액세스할 수 **없습니다.**  
  
 **연결 된 모드**( *원격 모드* 라고도 함) [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 를 사용 하려면 보고서 뷰어 컨트롤이 보고서를 렌더링할 수 있도록 sharepoint 팜에 연결 된 sharepoint 모드의 보고서 서버가 필요 합니다.  
  
 아래에는 로컬 모드 보고를 지원하는 데이터 처리 확장 프로그램이 나열되어 있습니다.  
  
-   
  [!INCLUDE[msCoName](../includes/msconame-md.md)] Access 2010 보고서 확장 프로그램. Access Services에 대한 자세한 내용은 [SQL Reporting Services와 함께 Access Services 사용: SQL Server 2008 R2 Reporting Services 추가 기능 설치(SharePoint Server 2010)](https://go.microsoft.com/fwlink/?LinkId=192686)를 참조하세요.  
  
-   
  [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] SharePoint 목록 데이터 확장 프로그램. SharePoint 목록 데이터 확장 프로그램에 대한 자세한 내용은 [Data Sources Supported by Reporting Services &#40;SSRS&#41;](create-deploy-and-manage-mobile-and-paginated-reports.md)  
  
 로컬 모드를 지원하는 사용자 지정 데이터 처리 확장 프로그램을 개발할 수도 있습니다. 자세한 내용은 [Implementing a Data Processing Extension](extensions/data-processing/implementing-a-data-processing-extension.md)을 참조하세요.  
  
 로컬 모드에서는 포함된 데이터 원본이나 .rsds 파일의 공유 데이터 원본이 있는 보고서를 렌더링할 수 있습니다. 그러나 보고서나 이와 연결된 데이터 원본을 관리할 수는 없습니다. 관리하려고 하는 경우 로컬 모드에서는 지원되지 않는다는 오류가 발생합니다. SharePoint 사이트에서 데이터 원본을 관리하는 것은 연결된 모드에서만 지원됩니다.  
  
> [!NOTE]  
>  이전 버전과 마찬가지로 사용자 이름 및 암호를 .rsds 파일에 포함할 수 없습니다.  
  
##  <a name="bkmk_local_mode_sharepoint2013"></a>SharePoint 2013를 사용 하 여 로컬 모드 및 Access Services 구성  
 기존 Access 2010 웹 데이터베이스 및 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 로컬 모드를 지원하도록 SharePoint 2013 팜을 구성할 수 있습니다. 자세한 내용은 [SharePoint Server 2013에서 웹 데이터베이스에 대한 Access Services 2010 설정 및 구성](https://technet.microsoft.com/library/ee748653\(office.15\).aspx)을 참조하십시오.  
  
 SharePoint 2013에 대한 새 Access 웹 데이터베이스를 만들 수 없습니다. Access 2013에서는 Access에서 빌드되는 새로운 유형의 데이터베이스인 *Access 웹 앱* 을 사용한 다음 웹 브라우저에서 SharePoint 앱으로 다른 사용자와 공유합니다.  
  
 자세한 내용은 다음 항목을 참조하십시오.  
  
-   [Access 2013의 새로운 기능](https://office.microsoft.com/access-help/what-s-new-in-access-2013-HA102809500.aspx) (https://office.microsoft.com/access-help/what-s-new-in-access-2013-HA102809500.aspx).  
  
-   [액세스 앱에 대 한 기본 작업](https://office.microsoft.com/access-help/basic-tasks-for-an-access-app-HA102840210.aspx?CTT=5&origin=HA102809500) (https://office.microsoft.com/access-help/basic-tasks-for-an-access-app-HA102840210.aspx?CTT=5&origin=HA102809500).  
  
##  <a name="bkmk_local_mode_sharepoint2010"></a>SharePoint 2010를 사용 하 여 로컬 모드 보고 구성  
 로컬 모드를 사용하려면 ASP.NET 세션 상태가 있어야 합니다. Access Services를 설치하면 ASP.NET 세션 상태가 활성화됩니다. PowerShell을 사용하여 활성화할 수도 있습니다.  
  
1.  SharePoint 2010 관리 셸을 엽니다.  
  
2.  다음 명령을 입력합니다.  
  
    ```  
    - Enable-SPSessionStateService  
    ```  
  
3.  메시지가 표시되면 데이터베이스의 이름을 입력합니다.  
  
4.  IIS를 다시 설정합니다.  
  
 자세한 내용은 [SQL Reporting Services와 함께 Access Services 사용: SQL Server 2008 R2 Reporting Services 추가 기능 설치(SharePoint Server 2010)](https://go.microsoft.com/fwlink/?LinkId=192686) 및 [Enable-SPSessionStateService](https://technet.microsoft.com/library/ff607857\(v=office.15\).aspx)를 참조하세요.  
  
## <a name="connected-mode"></a>연결된 모드  
 
  [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 연결된 모드에서 ADS 확장 프로그램 사용에 대한 최신 정보는 [데이터 확장 프로그램 'ADS'의 오류를 표시하는 SharePoint 사이트에서 서비스 보고서에 액세스](https://social.technet.microsoft.com/wiki/contents/articles/25298.access-services-report-in-sharepoint-site-shows-error-in-data-extension-ads.aspx)를 참조하세요.  
  
## <a name="see-also"></a>참고 항목  
 [Reporting Services &#40;SSRS&#41;에서 지 원하는 데이터 원본](create-deploy-and-manage-mobile-and-paginated-reports.md)  
  
