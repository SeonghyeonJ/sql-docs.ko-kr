---
title: Reporting Services 기본 모드 보고서 서버 설치 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- default configuration [Reporting Services]
- report servers [Reporting Services], default configurations
- installation options [Reporting Services]
ms.assetid: 8f25e6dc-b753-400e-9e9a-50f4f35bf6c4
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 39f3b68f816594d275f48723865c7497f5352fbb
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/28/2018
ms.locfileid: "52527718"
---
# <a name="install-reporting-services-native-mode-report-server"></a>Reporting Services 기본 모드 보고서 서버 설치
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 기본 모드 보고서 서버는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 설치 마법사 또는 명령줄에서 설치할 수 있습니다. 설치 마법사에서 1) 파일을 설치하고 기본 설정을 사용하여 서버를 구성하거나 2) 파일을 설치하고 설치 마법사에서 서버가 구성되지 않도록 선택할 수 있습니다. 이 항목에서는 설치 프로그램이 보고서 서버 인스턴스를 설치하고 구성하는 *기본 모드용 기본 구성* 을 검토합니다. 설치가 완료되면 보고서 서버가 실행되어 사용할 수 있는 상태가 됩니다. 기본 모드 보고서 서버는 독립 실행형 애플리케이션 서버로 실행됩니다. 기본 모드가 기본 서버 모드입니다.  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 기본 모드|  
  
##  <a name="bkmk_top"></a> 항목 내용  
  
-   [기본 구성 이란?](#bkmk_whatisdefaultconfiguration)  
  
-   [기본 모드용 기본 구성을 설치 하는 경우](#bkmk_whentoinstalldefaultconfig)  
  
-   [요구 사항](#bkmk_requirements)  
  
-   [기본 URL 예약](#bkmk_defaultURLreservations)  
  
-   [SQL Server 설치 마법사로 기본 모드 설치](#bkmk_installwithwizard)  
  
-   [명령줄을 사용 하 여 기본 모드 설치](#bkmk_commandline)  
  
##  <a name="bkmk_whatisdefaultconfiguration"></a> 기본 구성 이란?  
 기본 모드 옵션에 대해 기본 구성을 선택하면 다음과 같은 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 기능이 설치됩니다.  
  
-   보고서 서버 서비스(보고서 서버 웹 서비스, 백그라운드 처리 애플리케이션 및 보고서 관리자 포함)  
  
-   [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 구성 관리자  
  
-   [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 명령줄 유틸리티(rsconfig.exe, rskeymgmt.exe 및 rs.exe)  
  
 이 옵션은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 또는 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]와 같은 공유 기능에는 적용되지 않습니다. 이러한 공유 기능을 설치하려면 별도의 항목으로 지정해야 합니다.  
  
 기본 모드 보고서 서버 설치에 대해 구성되는 항목은 다음과 같습니다.  
  
-   보고서 서버 서비스 계정  
  
-   보고서 서버 웹 서비스 URL  
  
-   보고서 관리자 URL  
  
-   보고서 서버 데이터베이스  
  
-   보고서 서버 데이터베이스에 대한 서비스 계정 액세스  
  
-   보고서 서버 데이터베이스에 대한 DSN 연결  
  
 설치 프로그램은 무인 실행 계정, 보고서 서버 전자 메일, 암호화 키 백업 또는 스케일 아웃 배포는 구성하지 않습니다. [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 구성 관리자를 사용하여 이러한 속성을 구성할 수 있습니다. 자세한 내용은 [Reporting Services 구성 관리자&#40;기본 모드&#41;](../../sql-server/install/reporting-services-configuration-manager-native-mode.md)을 참조하세요.  
  
##  <a name="bkmk_whentoinstalldefaultconfig"></a> 기본 모드용 기본 구성을 설치 하는 경우  
 기본 구성은 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 를 작동 상태로 설치하므로 설치가 완료되면 보고서 서버를 즉시 사용할 수 있습니다. 필수 구성 태스크를 생략하여 단계를 줄이려는 경우 이 모드를 지정하세요. 그렇지 않을 경우 이 필수 구성 태스크는 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 구성 도구에서 수행해야 합니다.  
  
 기본 구성을 설치해도 설치가 완료된 후 보고서 서버가 완전하게 작동하지 않을 수 있습니다. 따라서 서비스가 시작되어도 기본 URL이 등록되지 않을 수 있습니다. 서비스가 실행되어 예상대로 작동하는지 항상 설치를 테스트하세요.  
  
##  <a name="bkmk_requirements"></a> 요구 사항  
 이 기본 구성 옵션은 기본값을 사용하여 보고서 서버 작동에 필요한 핵심 설정을 구성합니다. 요구 사항은 다음과 같습니다.  
  
-   하드웨어가 Microsoft SQL Server를 실행하기 위한 최소 하드웨어 및 소프트웨어 요구 사항을 충족해야 합니다. 자세한 내용은 [Hardware and Software Requirements for Installing SQL Server 2014](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md)을 참조하세요.  
  
-   [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 및 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] 은 같은 인스턴스에 함께 설치해야 합니다. [!INCLUDE[ssDE](../../includes/ssde-md.md)] 인스턴스는 설치 프로그램에서 만들어 구성한 보고서 서버 데이터베이스를 호스팅합니다.  
  
-   설치 프로그램을 실행하는 데 사용된 사용자 계정은 로컬 Administrators 그룹에 속해야 하고, 보고서 서버 데이터베이스를 호스팅하는 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 인스턴스에서 데이터베이스에 액세스하고 이러한 데이터베이스를 만들 수 있는 권한이 있어야 합니다.  
  
-   설치 프로그램은 기본값을 사용하여 보고서 서버와 보고서 관리자에 액세스할 수 있는 URL을 예약할 수 있어야 합니다. 이러한 값은 포트 80, 강력한 와일드카드, **ReportServer_\<***instance_name***>** 및 **Reports_\<***instance_name***>** 형식의 가상 디렉터리 이름입니다.  
  
-   설치 프로그램은 기본값을 사용하여 보고서 서버 데이터베이스를 만들 수 있어야 합니다. 기본값은 **ReportServer** 및 **ReportServerTempDB**입니다. 이전에 설치한 기존 데이터베이스가 있는 경우 보고서 서버를 기본 모드용 기본 구성으로 구성할 수 없으므로 설치 프로그램이 차단됩니다. 설치 프로그램의 차단을 해제하려면 데이터베이스의 이름을 바꾸거나 데이터베이스를 이동 또는 삭제해야 합니다.  
  
 컴퓨터가 기본 설치에 대한 모든 요구 사항에 맞지 않는 경우 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]를 파일만 모드로 설치한 다음 설치가 완료된 후 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 구성 관리자를 사용하여 구성해야 합니다.  
  
 기본 설치를 진행할 목적으로만 컴퓨터를 다시 구성하지 마십시오. 그럴 경우 상당한 작업 시간이 필요하므로 결과적으로 이 설치 옵션이 제공하는 시간 절약이라는 이점이 없어집니다. 가장 좋은 방법은 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 를 파일만 모드로 설치한 다음 특정 값을 사용하도록 보고서 서버를 구성하는 것입니다.  
  
##  <a name="bkmk_defaultURLreservations"></a> 기본 URL 예약  
 URL 예약은 접두사, 호스트 이름, 포트 및 가상 디렉터리로 구성됩니다.  
  
|부분|Description|  
|----------|-----------------|  
|접두사|기본 접두사는 HTTP입니다. 이전에 SSL(Secure Sockets Layer) 인증서를 설치한 경우 설치 프로그램에서 HTTPS 접두사를 사용하는 URL 예약을 만들려고 시도합니다.|  
|호스트 이름|기본 호스트 이름은 강력한 와일드카드(+)로서 보고서 서버에서 http://를 포함 하 여 컴퓨터로 확인 되는 모든 호스트 이름에 대해 지정된 된 포트에서 HTTP 요청을 받아들이도록 지정\<컴퓨터 이름 > / reportserver를 http://localhost/reportserver, 또는 http://\<ip 주소 > / reportserver입니다.|  
|포트|기본 포트는 80입니다. 80 이외의 포트를 사용하는 경우 브라우저 창에서 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 웹 애플리케이션을 열 때 URL에 해당 포트를 명시적으로 추가해야 합니다.|  
|가상 디렉터리|기본적으로 가상 디렉터리의 형식으로 만들어집니다\<*instance_name*>는 보고서 서버 웹 서비스 및 이때 다음과\<*instance_name*> 보고서 관리자입니다. 보고서 서버 웹 서비스의 기본 가상 디렉터리는 **reportserver**이고 보고서 관리자의 기본 가상 디렉터리는 **reports**입니다.|  
  
 전체 URL 문자열의 예는 다음과 같습니다.  
  
-   http://+:80/reportserver, 보고서 서버에 대한 액세스를 제공합니다.  
  
-   http://+:80/reports보고서 관리자에 대 한 액세스를 제공 합니다.  
  
##  <a name="bkmk_installwithwizard"></a> SQL Server 설치 마법사로 기본 모드 설치  
 다음 목록에서는 SQL Server 설치 마법사에서 선택하는  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 특정 단계와 옵션에 대해 설명합니다. 설치 마법사에 표시될 각 페이지가 아니라 기본 모드 설치에 포함된 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 관련 페이지에 대해서만 설명합니다.  
  
1.  **설치 역할** 페이지에서 **SQL Server 기능 설치**를 선택합니다.  
  
     ![설치 역할을 위한 SQL Server 기능 설치](../../../2014/sql-server/install/media/rs-setuprole.gif "설치 역할을 위한 SQL Server 기능 설치")  
  
2.  **기능 선택** 페이지에서 다음을 선택합니다.  
  
    -   데이터베이스 엔진 인스턴스가 아직 설치되지 않은 경우**데이터베이스 엔진 서비스**  
  
    -   **Reporting Services - 기본**  
  
    -   **관리 도구-기본**입니다. 관리 도구는 필수 항목이 아니지만 다른 관리 도구를 설치하지 않은 경우 선택하는 것이 좋습니다. 기본 구성 옵션은 작동 하는 보고서 서버 되지만 나중에 구성 옵션을 변경 하는 것이 좋습니다. ' 내 보고서 '와 같은 일부 옵션을 통해 관리 됩니다. [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]  
  
     ![기능 선택에서 SSRS 기본 모드 선택](../../../2014/sql-server/install/media/rs-setupfeatureselection-native-withcircles.gif "기능 선택에서 SSRS 기본 모드 선택")  
  
3.  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 구독 기능을 사용하려는 경우 **서버 구성** 페이지에서 SQL Server 에이전트가 **자동** 설치 유형에 대해 구성되어 있는지 확인할 수 있습니다.  
  
4.  **Reporting Services 구성** 페이지에서 **설치 및 구성**을 선택합니다.  
  
     ![SSRS 기본 모드 구성](../../../2014/sql-server/install/media/rs-setupconfiguration-native-with-circles.gif "SSRS 기본 모드 구성")  
  
5.  SQL Server 설치 마법사를 완료한 후에 다음과 같은 기본 단계를 사용하여 기본 모드 설치를 확인합니다.  
  
    -   [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 구성 관리자를 열고 보고서 서버에 연결할 수 있는지 확인합니다.  
  
    -   관리자 권한을 가진 브라우저를 열고 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 보고서 관리자에 연결합니다. 예를 들어 `http://loclahost/Reports`입니다.  
  
    -   관리자 권한을 가진 브라우저를 열고 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 보고서 서버 페이지에 연결합니다. 예:  `http://loclahost/ReportServer`  
  
 자세한 내용은 다음 두 항목의 기본 섹션을 참조하세요.  
  
 [Verify a Reporting Services Installation](../../reporting-services/install-windows/verify-a-reporting-services-installation.md)  
  
 [Reporting Services 설치 문제 해결](../../reporting-services/install-windows/troubleshoot-a-reporting-services-installation.md)  
  
##  <a name="bkmk_commandline"></a> 명령줄을 사용 하 여 기본 모드 설치  
 다음 예에는 기본 구성에 필요한 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 서비스가 포함되어 있습니다.  
  
```  
setup /q /ACTION=install /FEATURES=SQL,RS,TOOLS /INSTANCENAME=MSSQLSERVER /SQLSYSADMINACCOUNTS="BUILTIN\ADMINISTRATORS"   
/RSSVCACCOUNT="NT AUTHORITY\NETWORK SERVICE" /SQLSVCACCOUNT="NT AUTHORITY\NETWORK SERVICE" /AGTSVCACCOUNT="NT AUTHORITY\NETWORK   
SERVICE" /RSSVCSTARTUPTYPE="Manual" /RSINSTALLMODE="DefaultNativeMode"  
```  
  
 자세한 내용 및 예제를 참조 하세요 [명령 프롬프트 설치의 Reporting Services SharePoint 모드 및 기본 모드](../../reporting-services/install-windows/install-reporting-services-at-the-command-prompt.md) 고 [명령 프롬프트에서 SQL Server 2014 설치](../../database-engine/install-windows/install-sql-server-from-the-command-prompt.md)  
  
## <a name="see-also"></a>관련 항목  
 [Reporting Services 설치 문제 해결](../../reporting-services/install-windows/troubleshoot-a-reporting-services-installation.md)   
 [Verify a Reporting Services Installation](../../reporting-services/install-windows/verify-a-reporting-services-installation.md)   
 [보고서 서버 서비스 계정 구성&#40;SSRS 구성 관리자&#41;](../../reporting-services/install-windows/configure-the-report-server-service-account-ssrs-configuration-manager.md)   
 [보고서 서버 URL 구성&#40;SSRS 구성 관리자&#41;](../../reporting-services/install-windows/configure-report-server-urls-ssrs-configuration-manager.md)   
 [보고서 서버 데이터베이스 연결 구성&#40;SSRS 구성 관리자&#41;](../../../2014/sql-server/install/configure-a-report-server-database-connection-ssrs-configuration-manager.md)   
 [파일만 설치&#40;Reporting Services&#41;](../../reporting-services/install-windows/files-only-installation-reporting-services.md)   
 [보고서 서버 초기화&#40;SSRS 구성 관리자&#41;](../../reporting-services/install-windows/ssrs-encryption-keys-initialize-a-report-server.md)   
 [기본 모드 보고서 서버에서 SSL 연결 구성](../security/configure-ssl-connections-on-a-native-mode-report-server.md)   
 [보고서 서버 URL 구성&#40;SSRS 구성 관리자&#41;](../../reporting-services/install-windows/configure-report-server-urls-ssrs-configuration-manager.md)   
 [Windows 서비스 계정 및 권한 구성](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md)   
 [SQL Server 2014 빠른 시작 설치](../../../2014/getting-started/quick-start-installation-of-sql-server-2014.md)  
  
  
