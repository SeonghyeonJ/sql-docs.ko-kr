---
title: 다른 SQL Server 2016 버전으로 업그레이드(설치 프로그램) | Microsoft Docs
ms.custom: ''
ms.date: 07/24/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
ms.assetid: 31d16820-d126-4c57-82cc-27701e4091bc
author: MashaMSFT
ms.author: mathoma
monikerRange: '>=sql-server-2016||=sqlallproducts-allversions'
manager: jroth
ms.openlocfilehash: 51bcd27ee8d2c63103650c8527014716f10bc3f9
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66794697"
---
# <a name="upgrade-to-a-different-edition-of-sql-server-setup"></a>다른 SQL Server 버전으로 업그레이드(설치 프로그램)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]설치 프로그램은 다양한 버전의 [!INCLUDE[ssNoversion](../../includes/ssnoversion-md.md)] 간에 버전 업그레이드를 지원합니다. 지원되는 버전 업그레이드 경로에 대한 자세한 내용은 [지원되는 버전 및 에디션 업그레이드](../../database-engine/install-windows/supported-version-and-edition-upgrades-2017.md)를 참조하세요. [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]의 인스턴스 버전 업그레이드를 시작하기 전에 다음 문서를 검토합니다.  

- [버전 및 SQL Server 2017 의 지원 되는 기능](../../sql-server/editions-and-components-of-sql-server-2017.md)  
- [버전 및 SQL Server 2016 의 지원 되는 기능](../../sql-server/editions-and-components-of-sql-server-2016.md)  
- [SQL Server의 버전별 컴퓨팅 용량 제한](../../sql-server/compute-capacity-limits-by-edition-of-sql-server.md)  
- [SQL Server 설치를 위한 하드웨어 및 소프트웨어 요구 사항](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md)  
  
> [!NOTE]  
> **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 장애 조치(failover) 클러스터 인스턴스에서:** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 장애 조치 클러스터 인스턴스의 노드 중 하나에서 버전 업그레이드를 실행하는 것으로 충분합니다. 이 노드는 활성 또는 수동 모드로 있을 수 있으며, 엔진은 버전 업그레이드 중에 리소스를 오프라인으로 가져오지 않습니다. 버전 업그레이드 후에 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스를 다시 시작하거나 다른 노드에 대한 장애 조치(failover)를 다시 시작해야 합니다.  
  
## <a name="prerequisites"></a>사전 요구 사항  
로컬 설치의 경우 관리자로 설치 프로그램을 실행해야 합니다. 원격 공유에서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 를 설치하는 경우 원격 공유에 대한 읽기 권한이 있는 도메인 계정을 사용해야 합니다.  
  
> [!IMPORTANT]  
> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 버전 변경 사항을 활성화하려면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 서비스를 다시 시작해야 합니다. 그러면 서비스가 오프라인 상태일 때 애플리케이션의 작동이 중단됩니다.  
  
## <a name="procedure"></a>절차  
  
### <a name="to-upgrade-to-a-different-edition-of-includessnoversionincludesssnoversion-mdmd"></a>다른 버전의 [!INCLUDE[ssNoversion](../../includes/ssnoversion-md.md)]로 업그레이드하려면  
  
1.  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 설치 미디어를 넣고 루트 폴더에서 setup.exe를 두 번 클릭하거나, 구성 도구에서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 설치 센터를 시작합니다. 네트워크 공유에서 설치하려면 공유에서 루트 폴더를 찾은 다음 Setup.exe를 두 번 클릭합니다.  
  
2.  기존 [!INCLUDE[ssNoversion](../../includes/ssnoversion-md.md)] 인스턴스를 다른 버전으로 업그레이드하려면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 설치 센터에서 **유지 관리**를 클릭한 다음 **버전 업그레이드**를 선택합니다.  
  
3.  설치 지원 파일이 필요한 경우 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 설치 프로그램이 이를 설치합니다. 컴퓨터를 다시 시작하라는 메시지가 표시되면 컴퓨터를 다시 시작한 후 작업을 계속합니다.  
  
4.  시스템 구성 검사기가 컴퓨터에서 검색 작업을 실행합니다. 계속하려면 **확인**을 클릭합니다.  
  
5.  제품 키 페이지에서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]무료 버전으로 업그레이드할지, 아니면 제품의 프로덕션 버전에 대한 PID 키가 있는지를 나타내는 라디오 단추를 선택합니다. 자세한 내용은 [SQL Server 버전 및 구성 요소](../../sql-server/editions-and-components-of-sql-server-2017.md) 및 [지원되는 버전 및 에디션 업그레이드](../../database-engine/install-windows/supported-version-and-edition-upgrades.md)를 참조하세요.  
  
6.  사용 조건 페이지에서 사용권 계약을 읽은 다음 동의함 확인란을 선택합니다. 계속하려면 **다음**을 클릭합니다. 설치를 끝내려면 **취소**를 클릭합니다.  
  
7.  인스턴스 선택 페이지에서 업그레이드할 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스를 지정합니다.  
  
8.  버전 업그레이드 규칙 페이지는 버전 업그레이드 작업이 시작되기 전에 사용자 컴퓨터 구성의 유효성을 검사합니다.  
  
9. 버전 업그레이드 준비 페이지에는 설치 중에 지정된 설치 옵션이 트리 뷰로 표시됩니다. 계속하려면 **업그레이드**를 클릭합니다.  
  
10. 버전 업그레이드 프로세스 도중 선택한 새로운 설정을 적용하려면 서비스를 다시 시작해야 합니다. 버전 업그레이드가 끝나면 버전 업그레이드에 대한 요약 로그 파일을 볼 수 있는 링크가 완료 페이지에 제공됩니다. 마법사를 닫으려면 **닫기**를 클릭합니다.  
  
11. 설치 및 기타 중요한 참고 사항에 대한 요약 로그 파일을 볼 수 있는 링크가 완료 페이지에 제공됩니다.  
  
12. 컴퓨터를 다시 시작합니다. 설치가 완료되면 설치 마법사에 표시되는 메시지를 꼭 읽으십시오. 설치 로그 파일에 대한 자세한 내용은 [SQL Server 설치 로그 파일 보기 및 읽기](../../database-engine/install-windows/view-and-read-sql-server-setup-log-files.md)를 참조하세요.  
  
13. [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]에서 업그레이드한 경우 업그레이드된 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]인스턴스를 사용하려면 추가 단계를 수행해야 합니다.  
  
    -   Windows SCM에서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 서비스를 설정합니다.  
  
    -   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 구성 관리자를 사용하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 서비스 계정을 프로비전합니다.  
  
 [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]에서 업그레이드했다면 위의 단계 외에 다음을 추가로 수행해야 합니다.  
  
-   [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] 로 프로비전된 사용자는 업그레이드 후에도 프로비전 상태가 유지됩니다. 특히 BUILTIN\Users 그룹은 프로비전 상태로 유지됩니다. 필요에 따라 이러한 계정을 비활성화 또는 제거하거나 다시 프로비전합니다. 자세한 내용은 [Windows 서비스 계정 및 권한 구성](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md)을 참조하세요.  
  
-   tempdb 및 model 시스템 데이터베이스에 대한 크기 및 복구 모드는 업그레이드 후에도 변경되지 않은 상태로 유지됩니다. 필요에 따라 이러한 설정을 다시 구성하십시오. 자세한 내용은 [시스템 데이터베이스 백업 및 복원&#40;SQL Server&#41;](../../relational-databases/backup-restore/back-up-and-restore-of-system-databases-sql-server.md)를 참조하세요.  
  
-   템플릿 데이터베이스는 업그레이드 후에도 컴퓨터에 그대로 유지됩니다.  
  
## <a name="see-also"></a>참고 항목  
 [SQL Server 업그레이드](../../database-engine/install-windows/upgrade-sql-server.md)   
 [이전 버전과의 호환성_삭제됨](https://msdn.microsoft.com/library/15d9117e-e2fa-4985-99ea-66a117c1e9fd)  
  
  
