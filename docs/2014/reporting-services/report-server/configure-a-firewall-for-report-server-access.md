---
title: 보고서 서버 액세스를 위한 방화벽 구성 | Microsoft Docs
ms.custom: ''
ms.date: 08/10/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- firewall systems [Reporting Services]
- configuring servers [Reporting Services]
ms.assetid: 04dae07a-a3a4-424c-9bcb-a8000e20dc93
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 00590faa3ef5fb63338465d85202f4010cd3b72d
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66104158"
---
# <a name="configure-a-firewall-for-report-server-access"></a>보고서 서버에 액세스할 수 있도록 방화벽 구성
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 보고서 서버 애플리케이션과 게시된 보고서는 IP 주소, 포트 및 가상 디렉터리를 지정하는 URL을 통해 액세스할 수 있습니다. Windows 방화벽을 켜면 보고서 서버에서 사용하도록 구성된 포트는 대부분 닫혀 있습니다. 보고서를 요청한 후 빈 웹 페이지가 나타나거나 원격 클라이언트 컴퓨터에서 보고서 관리자를 열었을 때 빈 페이지가 나타나면 포트가 닫힌 것입니다.  
  
 이 경우 포트를 열려면 보고서 서버 컴퓨터에서 Windows 방화벽 유틸리티를 사용해야 합니다. Reporting Services에서 자동으로 포트를 열지 않기 때문에 이 단계는 수동으로 수행해야 합니다.  
  
 기본적으로 보고서 서버는 포트 80에서 HTTP 요청을 수신합니다. 따라서 아래 지침에는 이 포트를 지정하는 단계를 설명합니다. 다른 포트를 사용하도록 보고서 서버 URL을 구성한 경우 아래 지침에 따라 해당 포트 번호를 지정해야 합니다.  
  
 외부 컴퓨터에서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 관계형 데이터베이스에 액세스하거나 보고서 서버 데이터베이스가 외부 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스에 있는 경우 외부 컴퓨터에서 포트 1433 및 1434를 열어야 합니다. 자세한 내용은 [온라인 설명서의](../../database-engine/configure-windows/configure-a-windows-firewall-for-database-engine-access.md) 데이터베이스 엔진 액세스에 대한 Windows 방화벽 구성 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 을 참조하세요. 기본 Windows 방화벽 설정 방법과 [!INCLUDE[ssDE](../../includes/ssde-md.md)], [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]및 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]에 영향을 주는 TCP 포트에 대한 자세한 내용은 [온라인 설명서에서](../../sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access.md) SQL Server 액세스를 허용하도록 Windows 방화벽 구성 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 을 참조하세요.  
  
## <a name="prerequisites"></a>사전 요구 사항  
 이 지침에서는 사용자가 이미 서비스 계정을 구성했고 보고서 서버 데이터베이스를 만들었으며 보고서 서버 웹 서비스 및 보고서 관리자에 대한 URL을 구성했다고 가정합니다. 자세한 내용은 [Reporting Services 기본 모드 보고서 서버 관리](manage-a-reporting-services-native-mode-report-server.md)를 참조하세요.  
  
 로컬 웹 브라우저에서 로컬 보고서 서버 인스턴스에 연결하여 보고서 서버에 액세스할 수 있는지도 확인해야 합니다. 이 단계에서는 사용 가능한 설치가 있는지 확인합니다. 포트를 열기 전에 설치가 올바르게 구성되어 있는지 확인해야 합니다. Windows Server에서 이 단계를 완료하려면 보고서 서버 사이트를 신뢰할 수 있는 사이트에 추가해야 합니다. 자세한 내용은 [로컬 관리에 대해 기본 모드 보고서 서버 구성&#40;SSRS&#41;](configure-a-native-mode-report-server-for-local-administration-ssrs.md)을 참조하세요.  
  
## <a name="opening-ports-in-windows-firewall"></a>Windows 방화벽에서 포트 열기  
 Windows 방화벽 버전마다 다른 지침이 적용됩니다.  
  
#### <a name="to-open-port-80-on-windows-7-windows-server-2008-r2-windows-server-2012-and-2012-r2"></a>Windows 7, Windows Server 2008 R2, Windows Server 2012 및 2012 R2에서 포트 80을 열려면  
  
1.  **시작** 메뉴에서 **제어판**을 클릭한 다음 **시스템 및 보안**, **Windows 방화벽**을 차례로 클릭합니다. 제어판이 '범주' 보기로 구성되지 않은 경우에는 **Windows 방화벽**을 바로 선택하면 됩니다.  
  
2.  **고급 설정**을 클릭합니다.  
  
3.   **인바운드 규칙**을 클릭합니다.  
  
4.  **동작** 창의 **새 규칙** 을 클릭합니다 **.**  
  
5.   **포트** 의 **규칙 종류**를 클릭합니다.  
  
6.  **다음**을 클릭합니다.  
  
7.  **프로토콜 및 포트** 페이지에서 **TCP**를 클릭합니다.  
  
8.  **특정 로컬 포트** 를 선택하고 값으로 **80**을 입력합니다.  
  
9. **다음**을 클릭합니다.  
  
10. **동작** 페이지에서 **연결 허용**을 클릭합니다.  
  
11. **다음**을 클릭합니다.  
  
12. **프로필** 페이지에서 사용자 환경에 적합한 옵션을 클릭합니다.  
  
13. **다음**을 클릭합니다.  
  
14.  **이름** 페이지에서 이름으로**ReportServer (TCP on port 80)** 를 입력합니다.  
  
15. **마침**을 클릭합니다.  
  
16. 컴퓨터를 다시 시작합니다.  
  
#### <a name="to-open-port-80-on-windows-vista-or-windows-server-2008"></a>Windows Vista 또는 Windows Server 2008에서 포트 80을 열려면  
  
1.  **시작** 메뉴에서 클릭 **제어판**, 클릭 **보안**를 클릭 하 고 **Windows 방화벽**합니다.  
  
2.  클릭 **Windows 방화벽을 통해 프로그램 허용**합니다.  
  
3.  **계속**을 클릭합니다.  
  
4.  예외 탭에서 클릭 **포트 추가**합니다.  
  
5.  이름 입력 **ReportServer (TCP 포트 80에서)** 합니다.  
  
6.  포트 번호를 입력 **80**합니다.  
  
7.  확인 **TCP** 을 선택 합니다.  
  
8.  클릭 **범위 변경**합니다.  
  
9. 클릭 **내 네트워크 (서브넷)만**를 클릭 하 고 **확인**합니다.  
  
10. **확인** 을 클릭하여 대화 상자를 닫습니다.  
  
11. 컴퓨터를 다시 시작합니다.  
  
## <a name="next-steps"></a>다음 단계  
 포트를 연 다음 원격 사용자가 이 포트에서 보고서 서버에 액세스할 수 있는지 확인하기 전에 홈 및 사이트 수준에서 역할 할당을 통해 사용자에게 보고서 서버에 대한 액세스 권한을 부여해야 합니다. 사용자에게 충분한 권한이 없는 경우 포트는 제대로 열리지만 보고서 서버에는 연결할 수 없습니다. 자세한 내용은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 온라인 설명서에서 [사용자에게 보고서 서버에 대한 액세스 권한 부여&#40;보고서 관리자&#41;](../security/grant-user-access-to-a-report-server.md)를 참조하세요.  
  
 다른 컴퓨터에서 보고서 관리자를 시작하여 포트가 제대로 열리는지 확인할 수도 있습니다. 자세한 내용은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 온라인 설명서에서 [보고서 관리자&#40;SSRS 기본 모드&#41;](../report-manager-ssrs-native-mode.md)를 참조하세요.  
  
## <a name="see-also"></a>관련 항목  
 [보고서 서버 서비스 계정 구성&#40;SSRS 구성 관리자&#41;](../install-windows/configure-the-report-server-service-account-ssrs-configuration-manager.md)   
 [보고서 서버 URL 구성&#40;SSRS 구성 관리자&#41;](../install-windows/configure-report-server-urls-ssrs-configuration-manager.md)   
 [보고서 서버 데이터베이스 만들기&#40;SSRS 구성 관리자&#41;](../../sql-server/install/create-a-report-server-database-ssrs-configuration-manager.md)   
 [보고서 서버 서비스 계정 구성&#40;SSRS 구성 관리자&#41;](../install-windows/configure-the-report-server-service-account-ssrs-configuration-manager.md)   
 [Reporting Services 기본 모드 보고서 서버 관리](manage-a-reporting-services-native-mode-report-server.md)  
  
  
