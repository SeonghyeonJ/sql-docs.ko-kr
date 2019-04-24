---
title: Reporting Services 설치 문제 해결 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
ms.assetid: e2536f7f-d90c-4571-9ffd-6bbfe69018d6
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: c923a239ad0eeb677b476665a4c99b45d430b421
ms.sourcegitcommit: 8d6fb6bbe3491925909b83103c409effa006df88
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/22/2019
ms.locfileid: "59954209"
---
# <a name="troubleshoot-a-reporting-services-installation"></a>Reporting Services 설치 문제 해결
  설치 중에 오류가 발생하여 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 를 설치할 수 없는 경우 이 항목에 설명된 지침에 따라 설치 오류가 발생할 가능성이 가장 높은 상황을 처리하세요.  
  
  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]의 문제에 대한 최신 정보는 [Reporting Services SQL Server 2012 질문과 대답, 팁과 요령 및 문제 해결](https://go.microsoft.com/fwlink/?LinkId=221297)을 참조하십시오.  
  
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 와 관련된 기타 오류 및 문제에 대한 자세한 내용은 [SSRS 문제 및 오류 문제 해결](https://social.technet.microsoft.com/wiki/contents/articles/ssrs-troubleshooting-issues-and-errors.aspx)을 참조하세요.  
  
 릴리스 정보에 설명되어 있는 문제가 발생하는 경우 [온라인 릴리스 정보](https://go.microsoft.com/fwlink/?linkid=236893) 를 검토하십시오.  
  
 이 항목에는 다음과 같은 정보가 포함되어 있습니다.  
  
-   [설치 로그 확인](#bkmk_setuplogs)  
  
-   [필수 구성 요소 확인](#bkmk_prereq)  
  
-   [SharePoint 모드 설치 관련 문제 해결](#bkmk_tshoot_sharepoint)  
  
-   [기본 모드 설치 관련 문제 해결](#bkmk_tshoot_native)  
  
-   [추가 리소스](#bkmk_additional)  
  
##  <a name="bkmk_setuplogs"></a> 설치 로그 확인  
 설치 오류는 **Program Files\Microsoft SQL Server\110\Setup Bootstrap\Log** 폴더의 로그 파일에 기록됩니다. 설치 프로그램을 실행할 때마다 하위 폴더가 만들어지는데 하위 폴더의 이름은 설치 프로그램을 실행한 시간과 날짜입니다. 설치 로그 파일을 확인하는 방법에 대한 지침은 [SQL Server 설치 로그 파일 보기 및 읽기](../../database-engine/install-windows/view-and-read-sql-server-setup-log-files.md)를 참조하세요.  
  
-   로그 파일에는 파일 모음이 포함되어 있습니다.  
  
-   제품, 구성 요소 및 인스턴스 정보를 확인하려면 *_summary.txt 파일을 엽니다.  
  
-   설치 중에 생성된 오류 정보를 확인하려면 *_errorlog.txt 파일을 엽니다.  
  
-   \_\*설치 정보를 보려면 *_RS [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] _ComponentUpdateSetup.log를 엽니다.  
  
##  <a name="bkmk_prereq"></a> 필수 구성 요소 확인  
 필수 구성 요소는 설치 프로그램에서 자동으로 확인합니다. 그러나 설치 문제를 해결하는 경우 설치 프로그램에서 확인하는 요구 사항을 알고 있으면 도움이 됩니다.  
  
-   설치 프로그램을 실행하기 위해서는 계정이 로컬 Administrators 그룹의 멤버여야 합니다. 설치 프로그램은 파일 및 레지스트리 설정 추가, 로컬 보안 그룹 만들기 및 사용 권한 설정 등을 수행할 수 있는 권한을 갖고 있어야 합니다. 기본 구성을 설치하는 경우 설치 프로그램은 사용자가 설치 중인 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스에 보고서 서버 데이터베이스를 만들 권한을 갖고 있어야 합니다.  
  
-   운영 체제가 HTTP.SYS 1.1을 지원해야 합니다.  
  
-   HTTP 서비스가 활성화되어 실행 중이어야 합니다.  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 서비스도 설치할 경우 DTC(Distributed Transaction Coordinator)가 실행 중이어야 합니다.  
  
-   System32 폴더에 Authz.dll이 있어야 합니다.  
  
 설치 프로그램은 더 이상 인터넷 정보 서비스(IIS) 또는 [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)]이 설치되어 있는지 확인하지 않습니다. [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 에는 MDAC 2.0 및 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 버전 2.0이 필요하므로 이들이 설치되어 있지 않은 경우 설치 프로그램에서 설치합니다.  
  
##  <a name="bkmk_tshoot_sharepoint"></a> SharePoint 모드 설치 관련 문제 해결  
  
-   [Reporting Services 구성 관리자 시작 안 함](#bkmk_configmanager_notstart)  
  
-   [SharePoint 모드의 SQL Server 2012 SSRS를 설치한 후 SharePoint 중앙 관리에 SQL Server Reporting Services 서비스가 나타나지 않습니다](#bkmk_no_ssrs_service)  
  
-   [Reporting Services PowerShell cmdlet을 사용할 수 없으며 명령이 인식되지 않습니다.](#bkmk_cmdlets_not_recognized)  
  
-   [URL이 구성되지 않았음을 나타내는 오류 메시지가 표시됩니다.](#bkmk_URL_not_configured)  
  
-   [컴퓨터에 SharePoint가 설치됐지만 구성되지 않은 경우 설치 프로그램이 실패합니다.](#bkmk_sharepoint_not_confiugred)  
  
-   [SharePoint 중앙 관리 페이지 비어 있음](#bkmk_central_admin_blank)  
  
-   [새 보고서 작성기 보고서를 만들려고 할 때 오류 메시지가 표시됩니다.](#bkmk_reportbuilder_newreport_error)  
  
-   [PREPAREIMAGE에는 RS_SHP가 지원되지 않는다는 오류 메시지가 표시됩니다.](#bkmk_RS_SHP_notsupported)  
  
###  <a name="bkmk_configmanager_notstart"></a> Reporting Services 구성 관리자 시작 안 함  
 **설명:** 이 문제는에서 의도 된 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]합니다. [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]는 이제 SharePoint 서비스 아키텍처에 맞게 구축됐습니다. 구성 관리자는 더 이상 SharePoint 모드에서 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 를 구성 및 관리하지 않아도 됩니다.  
  
 **해결 방법:** SharePoint 중앙 관리를 사용하여 SharePoint 모드에서 보고서 서버를 구성합니다. 자세한 내용은 [Reporting Services SharePoint 서비스 애플리케이션 관리](../../../2014/reporting-services/manage-a-reporting-services-sharepoint-service-application.md)를 참조하세요.  
  
###  <a name="bkmk_no_ssrs_service"></a> SharePoint 모드의 SQL Server 2012 SSRS를 설치한 후 SharePoint 중앙 관리에 SQL Server Reporting Services 서비스가 나타나지 않습니다  
 **설명:** 성공적으로 설치한 후 경우 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint 모드에서와 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] add-in SharePoint 2010에 대 한 표시 되지 않습니다 "SQL Server Reporting Services"는 다음 두 메뉴에 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 서비스에 등록 되지 않았습니다.  
  
-   SharePoint 2010 중앙 관리 -> "응용 프로그램 관리" -> "서버의 서비스 관리" 페이지  
  
-   SharePoint 2010 중앙 관리 -> "응용 프로그램 관리" -> "서비스 응용 프로그램 관리" ->"새로 만들기" 메뉴  
  
 **해결 방법:** 등록 및 시작 하는 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint Services의 경우 다음 단계를 완료 합니다.  
  
1.  SharePoint 2010 중앙 관리를 실행하는 컴퓨터에서  
  
    1.  관리자 권한으로 SharePoint 2010 관리 셸을 엽니다. 아이콘을 마우스 오른쪽 단추로 클릭하고 "관리자 권한으로 실행"을 클릭합니다. 셸에서 다음 세 cmdlet을 실행합니다.  
  
    2.  ```  
        Install-SPRSService  
        ```  
  
    3.  ```  
        Install-SPRSServiceProxy  
        ```  
  
    4.  ```  
        Get-SPServiceInstance -all |where {$_.TypeName -like "SQL Server Reporting*"} | Start-SPServiceInstance  
        ```  
  
2.  확인 합니다 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 서비스 상태를 보여 줍니다. "**시작**" 페이지에서: SharePoint 2010 중앙 관리-> "**응용 프로그램 관리**"->"**서버의 서비스 관리**"  
  
###  <a name="bkmk_cmdlets_not_recognized"></a> Reporting Services PowerShell cmdlet을 사용할 수 없으며 명령이 인식되지 않습니다.  
 **설명:** 실행 하려는 경우는 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 다음과 비슷한 오류 메시지가 나타나면 PowerShell cmdlet:  
  
-   'Install-SPRSServiceInstall-SPRSService' 용어는 cmdlet, 함수, 스크립트 파일 또는 실행 프로그램의 이름으로 **인식되지 않습니다** . 이름의 철자를 확인 하거나 경로 포함 하는 경우 경로가 올바른지 확인 하 고 다시 시도 합니다. 줄: 1 문자: 39 + SPRSServiceInstall-Install-sprsservice에서 <<<< + CategoryInfo: ObjectNotFound: (Install-SPRSServiceInstall-SPRSService:String) [], CommandNotFoundExcep  
  
 **해결 방법:** 다음 중 하나를 수행 합니다.  
  
-   SharePoint 제품의 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 추가 기능인 **rssharepoint.msi**를 실행합니다.  
  
-   SQL Server 2005 설치 미디어에서 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint 모드를 설치합니다.  
  
 **참고:** 경우는 **SharePoint 2013 관리 셸** 해결 방법 중 하나를 완료, 닫기 및 관리 셸을 다시 열 때 열려 있습니다.  
  
 자세한 내용은 다음 항목을 참조하세요.  
  
-   [SharePoint 제품용 Reporting Services 추가 기능 검색 위치](../../reporting-services/install-windows/where-to-find-the-reporting-services-add-in-for-sharepoint-products.md)  
  
-   [SharePoint 2010용 Reporting Services SharePoint 모드 설치](../../../2014/sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2010.md)  
  
-   [SharePoint 2013 용 Reporting Services SharePoint 모드 설치](../../../2014/sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2013.md)  
  
###  <a name="bkmk_URL_not_configured"></a> URL이 구성되지 않았음을 나타내는 오류 메시지가 표시됩니다.  
 **설명:** 오류 메시지가 표시는 다음과 유사 합니다.  
  
 이 SQL Server Reporting Services(SSRS) 기능은 지원되지 않습니다. 중앙 관리를 사용하여 하나 이상의 다음 문제를 확인하고 해결합니다.•보고서 서버 URL이 구성되지 않았습니다. SSRS 통합 페이지를 사용하여 설정합니다.•SSRS 서비스 애플리케이션 프록시가 구성되지 않았습니다. SSRS 서비스 애플리케이션 페이지를 사용하여 프록시를 구성합니다.•SSRS 서비스 애플리케이션이 이 웹 애플리케이션에 매핑되지 않았습니다. SSRS 서비스 애플리케이션 페이지를 사용하여 SSRS 서비스 애플리케이션 프록시를 이 웹 애플리케이션의 애플리케이션 프록시 그룹에 연결합니다.  
  
 **해결 방법:** 오류 메시지는이 문제를 해결 하는 세 가지 제안 된 단계를 포함 합니다. 보고서 서버 URL 구성 되지 않았습니다...' 메시지의 첫 번째 제안 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]이전의 보고서 서버 버전과 통합하는 경우 관련됩니다. 이전 보고서 서버 버전의 SharePoint 구성은 **SQL Server Reporting Services(2008 및 2008 R2)** 를 사용하여 **일반 애플리케이션 설정**페이지에서 완료됩니다.  
  
 **추가 정보:** 중 하나를 사용 하려고 할 때이 오류 메시지가 표시 됩니다는 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 에 대 한 연결을 필요로 하는 기능을 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 서비스입니다. 다음을 포함합니다.  
  
-   SharePoint 문서 라이브러리에서 SQL Server 보고서 작성기 열기  
  
-   구독 관리  
  
-   서비스 애플리케이션 관리  
  
###  <a name="bkmk_sharepoint_not_confiugred"></a> 컴퓨터에 SharePoint가 설치됐지만 구성되지 않은 경우 설치 프로그램이 실패합니다.  
 **설명:** 선택 하는 경우 sharepoint 컴퓨터에서 Reporting Services SharePoint 모드를 설치 하려면 설치 하지만 SharePoint 구성 되어 있지 않습니다를 살펴보면, 설치 확인 하 고 다음과 비슷한 오류 메시지가 중지 됩니다.  
  
 SQL Server 설치 작업이 중단됐습니다.  
  
 **해결 방법:** SharePoint를 구성 하 고 SQL Server 설치를 실행 합니다.  
  
 **추가 정보:** 설치할 때 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 에 기존 SharePoint 설치로 설치 하 고 시작을 시도 설치는 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint 서비스입니다. SharePoint가 구성되지 않은 경우 서비스 설치가 실패하므로 설치 프로그램이 실패합니다.  
  
###  <a name="bkmk_central_admin_blank"></a> SharePoint 중앙 관리 페이지 비어 있음  
 **설명:** 설치 오류 없이 SharePoint 2010을 설치할 수 있었습니다. 그러나 중앙 관리를 탐색할 때 빈 페이지만 표시됩니다.  
  
 **해결 방법:** 이 문제에 한정 되지 않습니다. [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 아니라 전체 SharePoint 설치에서 권한의 구성에 관련 되어 있습니다. 다음은 제안된 목록입니다.  
  
-   개발 환경에서 SharePoint 항목을 검토합니다. [7 및 Windows Server 2008 Windows Vista, Windows에서 SharePoint 2010 용 개발 환경 설정](https://msdn.microsoft.com/library/ee554869\(office.14\).aspx)  
  
-   포럼 포스트 검토: [중앙 관리에서 빈 페이지 반환 설치 후 Windows 7에서](https://social.technet.microsoft.com/Forums/en/sharepoint2010setup/thread/a422a3c8-39f6-4b9e-988a-4c4d1e745694)  
  
-   SharePoint 2010 중앙 관리 서비스와 같은 SharePoint 서비스를 위해 사용 중인 서비스 계정은 로컬 운영 체제에 관리 권한이 있어야 합니다.  
  
###  <a name="bkmk_reportbuilder_newreport_error"></a> 새 보고서 작성기 보고서를 만들려고 할 때 오류 메시지가 표시됩니다.  
 **설명:** 문서 라이브러리 내에서 보고서 작성기 보고서를 만들려고 할 때 다음과 유사한 오류 메시지가 표시:  
  
 이 기능은 SQL Server Reporting Services 서비스 애플리케이션이 없거나 보고서 서버 URL이 중앙 관리에 구성되지 않았기 때문에 지원되지 않습니다.  
  
 **해결 방법:** 확인을 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 서비스 응용 프로그램이 있고 올바르게 구성 합니다. 자세한 내용은 섹션 '만들기'는 Reporting Services 서비스 응용 프로그램에서 [Reporting Services SharePoint 모드 설치 SharePoint 2010 용](../../../2014/sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2010.md)  
  
###  <a name="bkmk_RS_SHP_notsupported"></a> PREPAREIMAGE에는 RS_SHP가 지원되지 않는다는 오류 메시지가 표시됩니다.  
 **설명:** 에 대 한 PREPAREIMAGE를 실행 하려고 하면 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 다음과 유사한 오류 메시지가 표시:  
  
 "SysPrep이 지원되지 않으므로 PREPAREIMAGE 동작을 실행할 때 지정된 'RS_SHP' 기능이 지원되지 않습니다. SysPrep과 호환되지 않는 기능을 제거하고 설치 프로그램을 다시 실행합니다."  
  
 **해결 방법:** 관련 작업이 있습니다. [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 는 SYSPREP(PREPAREIMAGE)를 지원하지 않습니다. [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 기본 모드는 SYSPREP을 지원하지 않습니다.  
  
##  <a name="bkmk_tshoot_native"></a> 기본 모드 설치 관련 문제 해결  
  
###  <a name="PerfCounters"></a> Windows Vista 또는 Windows Server 2008로 업그레이드한 후 성능 카운터가 표시되지 않는 경우  
 [!INCLUDE[wiprlhext](../../includes/wiprlhext-md.md)] 를 실행하는 컴퓨터에서 운영 체제를 [!INCLUDE[firstref_longhorn](../../includes/firstref-longhorn-md.md)] 또는 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]로 업그레이드하면 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 성능 카운터가 설정되지 않습니다.  
  
#### <a name="to-reinstate-reporting-services-performance-counters"></a>Reporting Services 성능 카운터를 다시 시작하려면  
  
1.  다음 레지스트리 키를 삭제합니다.  
  
    -   **HKLM\SYSTEM\CurrentControlSet\Services\MSRS 2011 Web Service**  
  
    -   **HKLM\SYSTEM\CurrentControlSet\Services\MSRS 2011 Windows Service**  
  
2.  명령 창을 열고 프롬프트에 다음 명령을 입력합니다.  
  
    -   **run \<** *.NET 2.0 Framework directory* **>\InstallUtil.exe \<** *Report Server Bin directory* **>\ReportingServicesLibrary.dll**  
  
        > [!NOTE]  
        >  바꿉니다 \< *.NET 2.0 Framework directory*> 파일은.NET Framework 2.0의 실제 경로로 바꾸고 \< *Report Server Bin directory*> 실제 경로 사용 하 여 보고서 서버 bin 파일입니다.  
  
3.  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 서비스를 다시 시작합니다.  
  
 위 단계가 제대로 수행되었는지 확인하기 위해 웹 브라우저를 열어 보고서 관리자 URL 또는 보고서 서버 URL로 이동합니다. 그런 다음 성능 모니터를 열어 카운터가 작동하고 있는지 확인합니다.  
  
#### <a name="to-re-add-the-performance-registry-keys-by-using-registry-editor"></a>레지스트리 편집기를 사용하여 성능 레지스트리 키를 다시 추가하려면  
  
1.  레지스트리 편집기를 엽니다.  
  
    1.  **시작**을 클릭한 다음 **실행**을 클릭합니다.  
  
    2.  에 **실행** 대화 상자의 합니다 **열려** 상자에 입력 `regedit`.  
  
2.  레지스트리 편집기에서 레지스트리 키를 선택합니다. `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\MSRS 2011 Web Service\Performance`  
  
3.  **Performance** 노드를 마우스 오른쪽 단추로 클릭하고 **새로 만들기**를 가리킨 다음 **다중 문자열 값**을 클릭합니다.  
  
4.  `Counter Names`를 입력한 다음 Enter 키를 누릅니다.  
  
5.  이 작업을 반복하여 이 노드에 `Counter Types` 레지스트리 키를 추가합니다.  
  
6.  레지스트리 키로 이동합니다. `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\MSRS 2011 Web Service\Performance`  
  
7.  **Performance** 노드를 마우스 오른쪽 단추로 클릭하고 **새로 만들기**를 가리킨 다음 **다중 문자열 값**을 클릭합니다.  
  
8.  `Counter Names`를 입력한 다음 Enter 키를 누릅니다.  
  
9. 이 작업을 반복하여 이 노드에 `Counter Types` 레지스트리 키를 추가합니다.  
  
 64비트 인스턴스를 복구하거나 레지스트리 키를 수동으로 다시 추가하면 성능 모니터를 사용하여 모니터링하려는 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 성능 개체를 구성할 수 있습니다.  
  
###  <a name="ConfigPropsMissing"></a> SQL Server 2005에서 업그레이드한 후 ReportServerExternalURL 및 PassThroughCookies 구성 속성이 구성되지 않는 경우  
 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]를 [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)]로 업그레이드할 때 `ReportServerExternalURL` 및 `PassThroughCookies` 구성 속성은 업그레이드 프로세스에서 구성되지 않습니다. `ReportServerExternalURL` 선택적 속성 이며 SharePoint 2.0 웹 파트를 사용 하 고 사용자가 보고서를 검색 하는 새 브라우저 창에서 열 수 있도록 하려는 경우에 설정 해야 합니다. 에 대 한 자세한 내용은 `ReportServerExternalURL`를 참조 하세요 [구성 파일의 Url &#40;SSRS 구성 관리자&#41;](../../reporting-services/install-windows/urls-in-configuration-files-ssrs-configuration-manager.md)합니다. `PassThroughCookies` 사용자 지정 인증 방법을 사용할 때에 필요 합니다. 에 대 한 자세한 내용은 `PassThroughCookies`를 참조 하세요 [사용자 지정 인증 쿠키를 전달 하도록 보고서 관리자 구성](../security/configure-the-web-portal-to-pass-custom-authentication-cookies.md)합니다.  
  
> [!NOTE]  
>  사용자 지정 인증을 사용할 때는 업그레이드를 수행하는 대신 설치를 마이그레이션하는 것이 좋습니다. [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 마이그레이션에 대한 자세한 내용은 [Reporting Services 설치 마이그레이션&#40;기본 모드&#41;](../../reporting-services/install-windows/migrate-a-reporting-services-installation-native-mode.md)을 참조하세요.  
  
 기본적으로 이러한 속성은 [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)] 구성에 존재하지 않습니다. [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 에서 이러한 속성을 구성했고 해당 기능을 계속 사용해야 하는 경우 업그레이드 프로세스 후에 **RSReportServer.config** 파일에 이러한 속성을 수동으로 추가해야 합니다. 자세한 내용은 [Reporting Services 구성 파일 수정&#40;RSreportserver.config&#41;](../report-server/modify-a-reporting-services-configuration-file-rsreportserver-config.md)을 참조하세요.  
  
###  <a name="Default2005InstallBreaks2008"></a> SQL Server 2012Reporting 서비스를 실행 하는 컴퓨터의 SQL Server 2005 Reporting Services의 기본 인스턴스에 대해 설치 실패  
  [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)]로 업그레이드할 때 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 인스턴스 설치가 실패합니다.  
  
 "이름이 같은 인스턴스가 이 컴퓨터에 이미 설치되어 있습니다. SQL Server 설치를 계속하려면 고유한 인스턴스 이름을 지정하십시오."  
  
 이 문제는 [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)] 인스턴스가 기본 인스턴스인지 명명된 인스턴스인지, 해당 이름의 [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)] 인스턴스가 컴퓨터에 이미 존재하는지 여부에 관계없이 발생합니다.  
  
 다음 방법 중 하나를 사용하여 이 문제를 해결할 수 있습니다.  
  
-   컴퓨터에서 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 를 기본 인스턴스로 실행해야 하는 경우 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 인스턴스를 먼저 설치한 후 [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)] 인스턴스를 설치해야 합니다.  
  
-    [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 인스턴스를 기본 인스턴스로 실행하지 않아도 되는 경우에는 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)] 인스턴스를 설치해야 합니다.  
  
###  <a name="WindowsAuthBreaksAfterUpgrade"></a> SQL Server 2005에서 SQL Server 2012로 업그레이드 한 후 Windows 인증을 사용할 때 401-권한이 없음 오류  
  [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 를 [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)]로 업그레이드할 때 NTLM 인증에 보고서 서버 서비스 계정에 대한 기본 제공 계정을 사용하는 경우 업그레이드 후에 보고서 서버 또는 보고서 관리자에 액세스할 때 401-권한이 없음 오류가 발생할 수 있습니다.  
  
 이 오류는 Windows 인증에 대한 기본 [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)] 구성이 변경되었기 때문에 발생합니다. 보고서 서버 서비스 계정이 네트워크 서비스 또는 로컬 시스템인 경우 협상 인증이 구성됩니다. NTLM은 보고서 서버 서비스 계정이 이러한 기본 제공 계정 중 하나가 아닌 경우에 구성됩니다. 업그레이드 후에 이 문제를 해결하려면 RSReportServer.config 파일을 편집하여 `AuthenticationType`을 `RSWindowsNTLM`으로 구성하면 됩니다. 자세한 내용은 [Configure Windows Authentication on the Report Server](../security/configure-windows-authentication-on-the-report-server.md)을 참조하세요.  
  
###  <a name="Uninstall32BitBreaks64Bit"></a> 인스턴스를 제거 하면 32 비트 SQL Server 2012 Reporting Services의 side-by-side-배포에서 64 비트 인스턴스가 중단 64 비트 인스턴스를 사용 하 여  
 [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)] 의 32비트 인스턴스 및 64비트 인스턴스를 컴퓨터에 함께 설치하는 경우 32비트 인스턴스를 제거하면 4개의 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 레지스트리 키가 제거됩니다. 그 결과 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]의 64비트 인스턴스가 중단됩니다. 32비트 인스턴스를 제거할 때 제거되는 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 레지스트리 키는 다음과 같습니다.  
  
 `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\MSRS 2011 Web Service\Performance:Counter Names` `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\MSRS 2011 Windows Service\Performance:Counter Names` `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\MSRS 2011 Web Service\Performance:Counter Types` `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\MSRS 2011 Windows Service\Performance:Counter Types`  
  
 이 문제를 해결하려면 64비트 인스턴스를 복구하면 됩니다. 복구 방법을 사용하는 것이 좋지만 레지스트리 편집기를 사용하여 위의 레지스트리 키를 수동으로 다시 추가할 수도 있습니다.  
  
> [!CAUTION]  
>  레지스트리를 올바르게 편집하지 않으면 시스템을 심각하게 손상시킬 수 있습니다. 따라서 레지스트리를 변경하기 전에 컴퓨터의 중요한 데이터를 백업해 두어야 합니다.  
  
##  <a name="bkmk_additional"></a> 추가 리소스  
 다음은 문제 해결 지원을 검토할 수 있는 추가 리소스입니다.  
  
-   TechNet Wiki: 문제 해결 항목 [해결 SQL Server Reporting Services (SSRS) SharePoint 통합 모드에서](https://social.technet.microsoft.com/wiki/contents/articles/troubleshoot-sql-server-reporting-services-ssrs-in-sharepoint-integrated-mode.aspx)  
  
-   [포럼: SQL Server Reporting Services](http://social.msdn.microsoft.com/Forums/sqlreportingservices/threads)  
  
 ![SharePoint 설정](../../../2014/analysis-services/media/as-sharepoint2013-settings-gear.gif "SharePoint 설정") [Microsoft SQL Server Connect를 통해 사용자 의견 및 담당자 정보 제출](https://connect.microsoft.com/SQLServer/Feedback) (https://connect.microsoft.com/SQLServer/Feedback)합니다.  
  
  
