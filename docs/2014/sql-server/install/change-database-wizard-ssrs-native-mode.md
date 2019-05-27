---
title: 데이터베이스 변경 마법사 (SSRS 기본 모드) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- SQL12.rsconfigtool.changedatabase.F1
helpviewer_keywords:
- Change Database Wizard
- report server database, create
ms.assetid: 1a2e8d18-5997-482f-a9c1-87d99f7407b8
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: bc07e94db985ce156fdd5cd59620c2e7fddc2d73
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66096664"
---
# <a name="change-database-wizard-ssrs-native-mode"></a>데이터베이스 변경 마법사(SSRS 기본 모드)
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 구성 관리자에서는 새 보고서 서버 데이터베이스를 만들거나 현재 보고서 서버 인스턴스에 사용할 기존 보고서 서버 데이터베이스를 선택하는 단계를 안내하는 데이터베이스 변경 마법사를 제공합니다.  
  
 이전 버전에서 보고서 서버 데이터베이스를 선택하는 경우 이 데이터베이스는 연결된 보고서 서버 인스턴스의 버전과 일치하도록 업그레이드됩니다. 서비스를 시작하면 데이터베이스 버전이 검사되고 현재 스키마로 자동 업그레이드됩니다.  
  
 마법사를 시작하려면 **구성 관리자의 데이터베이스 페이지에서** 데이터베이스 변경 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 을 클릭합니다. 시작 하는 방법에 대 한 지침은 합니다 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 구성 관리자를 참조 하세요 [Reporting Services 구성 관리자 &#40;기본 모드&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md)합니다.  
  
 [!INCLUDE[applies](../../includes/applies-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 기본 모드입니다.  
  
## <a name="options"></a>변수  
 **동작**  
 수행할 태스크를 선택합니다. 기본 모드 또는 SharePoint 통합 모드로 새 데이터베이스를 만들거나 현재 보고서 서버 인스턴스에서 사용할 기존 보고서 서버 데이터베이스를 선택할 수 있습니다.  
  
 **데이터베이스 서버**  
 보고서 서버 데이터베이스를 호스팅하는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] 인스턴스의 이름을 지정합니다. 로컬 컴퓨터나 원격 컴퓨터에서 기본 또는 명명된 인스턴스를 사용할 수 있습니다. 명명 된 인스턴스에 연결 하는 경우이 형식으로 서버 이름을 입력 합니다. \< *server*>\\<*인스턴스*>.  
  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 인스턴스에 연결하려면 서버에 로그온하여 데이터베이스 정보를 업데이트할 권한이 있는 자격 증명을 사용해야 합니다. [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 구성 관리자는 사용자의 현재 Windows 자격 증명을 사용하지만 사용자에게 로그인 또는 데이터베이스 권한이 없는 경우 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터베이스 로그인을 지정해야 합니다. 다른 Windows 자격 증명은 지정할 수 없습니다. 다른 Windows 사용자로 연결하려면 해당 사용자로 로그인한 다음 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 구성 관리자를 시작합니다.  
  
 원격 인스턴스에 연결하려면 먼저 원격 연결을 사용할 수 있도록 해당 인스턴스를 설정해야 합니다. 일부 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 버전은 기본적으로 원격 연결을 허용하지 않습니다. 원격 연결의 허용 여부를 확인하려면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 구성 관리자를 사용하여 TCP/IP 및 명명된 파이프 프로토콜이 설정되어 있는지 확인합니다. 원격 인스턴스도 명명된 인스턴스인 경우 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser 서비스가 대상 서버에서 활성화되어 실행되고 있는지 확인합니다. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser는 명명된 인스턴스에서 사용되는 포트 번호를 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 구성 관리자에 제공합니다.  
  
 **데이터베이스 백업**  
 서버 데이터를 저장하는 보고서 서버 데이터베이스의 이름을 지정합니다. 기존 데이터베이스를 지정하거나 새 데이터베이스를 만들 수 있습니다.  
  
 동작 페이지에서 **새 데이터베이스 만들기** 를 선택하면 새 데이터베이스를 만드는 데 사용되는 속성이 마법사에 나타납니다. [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 구성 관리자는 정적 데이터를 포함하는 데이터베이스와 세션 및 작업 데이터를 저장하기 위한 임시 데이터베이스를 이름별로 바인딩하여 만듭니다. 자세한 내용은 [보고서 서버 데이터베이스 &#40;SSRS 기본 모드&#41; ](../../reporting-services/report-server/report-server-database-ssrs-native-mode.md) 에서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 온라인입니다.  
  
 기존 보고서 서버 데이터베이스를 선택할 수도 있습니다. [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 구성 관리자는 잘못된 데이터베이스를 필터링하지 않습니다. 올바른 데이터베이스는 보고서 서버 스키마를 기반으로 합니다(필수 테이블, 뷰 또는 저장 프로시저가 누락된 데이터베이스는 선택할 수는 없음). 이전 버전의 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]에서 만든 데이터베이스를 선택하면 데이터베이스가 현재 형식으로 업그레이드됩니다.  
  
 **언어**  
 이 값은 새 보고서 서버 데이터베이스를 만드는 경우에만 설정합니다.  
  
 이 값으로 역할 정의 및 설명을 작성하는 언어를 지정합니다. [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]는 미리 정의된 역할 집합이 포함된 역할 기반 인증 모델을 제공합니다. 이러한 역할은 지정한 언어로 한 번 만들어집니다. 역할 이름 및 설명은 다른 언어로는 표시되지 않습니다. 서버에서 지원하는 culture 또는 언어가 설정된 브라우저를 사용하여 보고서 서버에 연결하더라도 마찬가지입니다. 지정하는 언어에 따라 내 보고서 기능의 일부인 내 보고서 폴더와 사용자 폴더의 이름을 만드는 데 사용되는 언어도 결정됩니다.  
  
 **서버 모드**  
 보고서 서버 데이터베이스는 기본 모드 또는 SharePoint 통합 모드를 지원합니다. 두 모드는 함께 사용할 수 없습니다.  
  
 새 보고서 서버 데이터베이스를 만드는 경우 모드를 지정해야 합니다. 선택한 모드에 따라 보고서 서버 데이터베이스 구조가 결정되고 `SharePointIntegrated` 보고서 서버 시스템 속성이 `true` 또는 `false`로 설정됩니다.  
  
 다른 보고서 서버 데이터베이스를 선택하면 현재 데이터베이스의 사용 방식을 알 수 있도록 현재 데이터베이스 모드가 표시됩니다.  
  
 **자격 증명**  
 보고서 서버가 보고서 서버 데이터베이스에 연결할 때 사용하는 계정을 지정합니다. 유효한 값으로는 보고서 서버 웹 서비스의 서비스 계정, 보고서 서버를 호스팅하는 데 사용 중인 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스에 정의된 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 데이터베이스 로그인 또는 Windows 계정이 있습니다. Windows 계정을 사용 하는 경우 로컬 계정을 지정할 수 있습니다 (*\<컴퓨터 이름 >\\< 사용자 이름\>*) 동일한 컴퓨터 또는 도메인 사용자를 보고서 서버 및 데이터베이스에 있는 경우 계정 (*\<도메인 >\\< 사용자 이름\>*) 하는 경우 동일한 도메인의 다른 컴퓨터에 있습니다.  
  
 그러면 보고서 서버에서 지정한 계정에 대한 데이터베이스 로그인을 만들고 데이터베이스 권한을 할당합니다.  
  
 보고서 서버에서 계정 자체를 만들지는 않습니다. 지정한 계정은 이미 있어야 하며 현재 배포 구성에 대해 유효해야 합니다. 특히 데이터베이스가 원격 컴퓨터에 있는 경우 Windows 계정을 사용하려면 해당 컴퓨터에 대한 로그온 권한이 있는 계정을 지정해야 합니다.  
  
 컴퓨터가 다른 도메인이나 트러스트되지 않은 도메인에 있는 경우 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터베이스 로그인을 사용하는 것이 좋습니다. 계정을 선택 하는 방법에 대 한 자세한 내용은 참조 하세요. [보고서 서버 데이터베이스 연결 구성 &#40;SSRS 구성 관리자&#41;](../../../2014/sql-server/install/configure-a-report-server-database-connection-ssrs-configuration-manager.md)합니다.  
  
 **요약**  
 설치 프로그램에서 연결을 구성하기 전에 설정을 확인합니다.  
  
 **진행 후 마침**  
 각 태스크의 진행률을 모니터링합니다.  
  
## <a name="see-also"></a>관련 항목  
 [데이터베이스 &#40;SSRS 기본 모드&#41;](../../../2014/sql-server/install/database-ssrs-native-mode.md)   
 [자격 증명 변경 마법사 &#40;SSRS 기본 모드&#41;](../../../2014/sql-server/install/change-credentials-wizard-ssrs-native-mode.md)   
 [기본 모드 보고서 서버 데이터베이스 만들기&#40;SSRS 구성 관리자&#41;](../../reporting-services/install-windows/ssrs-report-server-create-a-native-mode-report-server-database.md)   
 [Reporting Services 구성 관리자 F1 도움말 항목 &#40;SSRS 기본 모드&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-f1-help-topics-ssrs-native-mode.md)   
 [보고서 서버 데이터베이스 연결 구성&#40;SSRS 구성 관리자&#41;](../../../2014/sql-server/install/configure-a-report-server-database-connection-ssrs-configuration-manager.md)  
  
  
