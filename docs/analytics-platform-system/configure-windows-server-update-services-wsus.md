---
title: Analytics Platform System WSUS-구성 | Microsoft Docs
description: 이러한 지침은 Windows Server Update Services (WSUS) 구성 마법사를 사용 하 여 Analytics Platform System에 대 한 WSUS를 구성 하는 단계를 안내 합니다.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 2d1e07fca7c18bdecba265a9e69994a9f728e9ba
ms.sourcegitcommit: 1ab115a906117966c07d89cc2becb1bf690e8c78
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/27/2018
ms.locfileid: "52398623"
---
# <a name="configure-windows-server-update-services-wsus-in-analytics-platform-system"></a>분석 플랫폼 시스템에 Windows Server Update Services (WSUS) 구성
이러한 지침은 Windows Server Update Services (WSUS) 구성 마법사를 사용 하 여 Analytics Platform System에 대 한 WSUS를 구성 하는 단계를 안내 합니다. 어플라이언스로 소프트웨어 업데이트를 적용 하려면 먼저 WSUS를 구성 해야 합니다. WSUS는 이미 어플라이언스의 VMM 가상 컴퓨터에 설치 됩니다.  
  
WSUS를 구성 하는 방법에 대 한 자세한 내용은 참조는 [WSUS 단계별 설치 가이드](https://go.microsoft.com/fwlink/?LinkId=202417) WSUS 웹 사이트입니다. WSUS를 구성한 후 참조 [다운로드 및 Microsoft 업데이트 적용 &#40;Analytics Platform System&#41; ](download-and-apply-microsoft-updates.md) 에 업데이트를 시작 합니다.  
  
> [!WARNING]  
> 이 구성 프로세스 중 오류를 발생 하는 경우 중지 하 고 지원에 문의 합니다. 오류를 무시 하거나 오류가 수신 되는 프로세스를 진행 하지 마십시오.  
  
## <a name="before-you-begin"></a>시작하기 전 주의 사항  
WSUS를 구성 하려면:  
  
-   분석 플랫폼 시스템 어플라이언스 도메인 관리자 계정 로그인 정보가 있습니다.  
  
-   액세스 권한이 있는 Analytics Platform System 로그인이 있어야 합니다 **관리 콘솔** 어플라이언스 상태 정보를 봅니다.  
  
-   Microsoft 업데이트에서 직접 업데이트를 동기화 하는 대신 업스트림 WSUS 서버에서 업데이트를 동기화 하려는 경우 업스트림 WSUS 서버의 IP 주소를 알고 있습니다. 업스트림 WSUS 서버에 익명 연결을 허용 하도록 설정 되어 있고 SSL을 지원 하는지 확인 합니다.  
  
-   어플라이언스에서 사용할 프록시 서버를 업스트림 서버 또는 Microsoft 업데이트에 액세스 하는 경우 프록시 서버의 IP 주소를 알고 있습니다.  
  
-   대부분의 경우, WSUS 서버는 어플라이언스 외부에서 액세스 해야 합니다. 외부 DNS 분석 플랫폼 시스템 Analytics Platform System 호스트 및 Virtual Machines (Vm) 외부 DNS 서버 이름을 확인 하기 위해 사용할 수 있는 외부 이름이 전달자를 지원 하도록 구성할 수 있습니다이 사용 시나리오를 지원 하도록 합니다 어플라이언스입니다. 자세한 내용은 [비 어플라이언스 DNS 이름 확인에 DNS 전달자를 사용 하 여 &#40;Analytics Platform System&#41;](use-a-dns-forwarder-to-resolve-non-appliance-dns-names.md)합니다.  
  
## <a name="to-configure-windows-server-update-services-wsus"></a>Windows Server Update Services (WSUS)를 구성 하려면  
  
1.  에 로그인 합니다 **관리 콘솔**합니다. 에 **어플라이언스 상태** 탭에서 확인 합니다 **클러스터** 및 **네트워크** 열에 녹색 표시 (또는 **NA**) 모든 노드에 대 한 합니다. 모든 노드에 대 한 상태 표시기를 확인 합니다 **어플라이언스 상태**합니다.  
  
    -   녹색 또는 NA 표시기를 사용 하 여 계속 안전 합니다.  
  
    -   (노란색) 중요 하지 않은 경고 오류를 평가 합니다. 일부 경우에서 경고 메시지는 업데이트를 차단 하지 않습니다. C:\ 드라이브에 있지 않은 중요 하지 않은 디스크 볼륨 오류가 있으면 디스크 볼륨 오류를 해결 하기 전에 다음 단계를 진행할 수 있습니다.  
  
    -   대부분의 빨간색 표시기를 계속 하기 전에 확인 되어야 합니다. 디스크 실패의 경우 사용 합니다 **관리 콘솔 경고** 페이지는 각 서버 또는 SAN 배열 내에서 둘 이상의 디스크 오류가 있는지 확인 합니다. 각 서버 또는 SAN 배열 내에서 둘 이상의 디스크 오류 이면 디스크 오류를 수정 하기 전에 다음 단계를 진행할 수 있습니다. 가능한 한 빨리 디스크 오류를 해결 하려면 Microsoft 지원에 문의 해야 합니다.  
  
2.  어플라이언스 도메인 관리자 권한으로 VMM 가상 컴퓨터에 로그온 합니다.  
  
3.  구성 마법사를 시작 합니다.  
  
    #### <a name="to-launch-the-configuration-wizard"></a>구성 마법사를 시작 하려면  
  
    1.  에 **서버 관리자 대시보드**에 **도구** 메뉴에서 클릭 **Windows Server Update Services**.  
  
    2.  왼쪽된 창에서 합니다 **Update Services** 창에서 클릭 하 여 가상 컴퓨터 관리 노드 서버를 확장 (***appliance_domain *-VMM**)를 클릭 하 고 **옵션**합니다.  
  
    3.  에 **옵션** 창 클릭 **WSUS 서버 구성 마법사** 구성 마법사를 시작 합니다.  
  
        ![서버 관리자 대시보드 메뉴](./media/configure-windows-server-update-services-wsus/WSUS_Wiz0.png "WSUS_Wiz0")  
  
    4.  처음으로이 WSUS 마법사를 실행 한 경우 업데이트를 저장 하는 것에 대 한 디렉터리를 구성 하 라는 메시지가 표시 될 수 있습니다. `C:\wsus` 적절 한 위치입니다. 그러나 다른 경로 제공할 수 있습니다.  
  
        ![WSUS 경로](./media/configure-windows-server-update-services-wsus/WSUS_Wiz1.png "WSUS_Wiz1")  
  
    5.  검토 합니다 **시작 하기 전에** 마법사를 완료 하기 전에 완료 하는 항목의 목록입니다.  
  
        ![시작 하기 전에 WSUS](./media/configure-windows-server-update-services-wsus/WSUS_Wiz2.png "WSUS_Wiz2")  
  
    6.  에 **Microsoft 업데이트 개선 프로그램 참여** 페이지에서 **예, Microsoft 업데이트 개선 프로그램에 참여**를 클릭 하 고 **다음**합니다.  
  
        ![WSUS 개선 프로그램](./media/configure-windows-server-update-services-wsus/WSUS_Wiz3.png "WSUS_Wiz3")  
  
    이제 표시 되어야 합니다 **업스트림 서버 선택** 페이지입니다. 다음 스크린샷에서 구성 마법사의 시작 지점입니다.  
  
    ![WSUS 업스트림 서버 동기화](./media/configure-windows-server-update-services-wsus/WSUS_Wiz4a.png "WSUS_Wiz4a")  
  
4.  업스트림 서버를 선택 합니다.  
  
    에 **업스트림 서버 선택** 페이지 WSUS 구성 마법사는 선택한 가상 머신 관리 노드에 WSUS 소프트웨어 업데이트를 받을 업스트림 서버에 연결 하는 방법입니다. 업스트림 서버 동기화 할 두 가지 선택 사항이 [Microsoft Update](https://go.microsoft.com/fwlink/?LinkId=133349) 또는 다른 Windows Server Update Services 서버를 사용 하 여 업데이트를 동기화 합니다.  
  
    #### <a name="to-update-by-using-microsoft-update"></a>Microsoft Update를 사용 하 여 업데이트  
  
    1.  Microsoft Update와 동기화 하려는 경우에 아무 것도 변경 필요가 없습니다 합니다 **업스트림 서버 선택** 페이지입니다. **다음**을 클릭합니다.  
  
        ![WSUS 업스트림 서버 동기화](./media/configure-windows-server-update-services-wsus/WSUS_Wiz4a.png "WSUS_Wiz4a")  
  
    #### <a name="to-update-from-another-wsus-server"></a>다른 WSUS 서버의 업데이트  
  
    1.  Microsoft Update (업스트림 서버) 아닌 다른 소스와 동기화 하려는 경우 서버 지정 (IP 주소 입력)와이 서버는 업스트림 서버와 통신 하는 포트입니다.  
  
        ![WSUS에서 WSUS 업스트림 서버 동기화](./media/configure-windows-server-update-services-wsus/WSUS_Wiz4b.png "WSUS_Wiz4b")  
  
    2.  Secure Sockets Layer (SSL)를 사용 하려면 선택 합니다 **업데이트 정보를 동기화 할 때 SSL 사용** 확인란 합니다. 경우에 서버는 동기화에 대 한 포트 443을 사용 합니다.  
  
        ![WSUS SSL에서 WSUS 업스트림 서버 동기화](./media/configure-windows-server-update-services-wsus/WSUS_Wiz4c.png "WSUS_Wiz4c")  
  
    3.  복제본 서버를 선택 합니다 **이것이 업스트림 서버의 복제본** 확인란 합니다. 모두 선택할 수 있습니다 **업데이트 정보를 동기화 할 때 사용 하 여 SSL** 하 고 **이것이 업스트림 서버의 복제본**합니다.  
  
        ![WSUS 업스트림 서버 복제본](./media/configure-windows-server-update-services-wsus/WSUS_Wiz4d.png "WSUS_Wiz4d")  
  
    4.  이 시점에서 업스트림 서버 구성을 사용 하 여 완료 됩니다. 클릭 **다음**를 선택 하거나 **프록시 서버를 지정** 왼쪽된 탐색 창에서.  
  
5.  프록시 서버를 지정 합니다.  
  
    이 서버에서 Microsoft Update를 액세스 하기 위해 프록시 서버 또는 다른 업스트림 서버에 필요한 경우 여기서; 프록시 서버 설정을 구성할 수 있습니다. 그렇지 않은 경우 클릭 **다음**합니다.  
  
    ![WSUS 프록시](./media/configure-windows-server-update-services-wsus/WSUS_Wiz5a.png "WSUS_Wiz5a")  
  
    #### <a name="to-configure-proxy-server-settings"></a>프록시 서버 설정을 구성 하려면  
  
    1.  에 **프록시 서버 지정** 구성 마법사의 페이지는 **동기화 할 때 프록시 서버를 사용 하 여** 확인란을 선택한 다음 (이름이 아니라) 프록시 서버 IP 주소 및 포트 번호 (포트 80에서 입력 해당 상자에서 기본값).  
  
    2.  특정 사용자 자격을 사용 하 여 프록시 서버에 연결 하려는 경우는 **사용자 자격 증명을 사용 하 여 프록시 서버에 연결할** 확인란을 선택한 다음 해당 사용자 이름, 도메인 및 사용자의 암호를 입력 상자입니다. 프록시 서버에 연결 하는 사용자에 대 한 기본 인증을 사용 하도록 설정 하려는 경우는 **기본 인증 허용 (암호를 일반 텍스트로 보냄)** 확인란 합니다.  
  
        ![WSUS 프록시 자격 증명](./media/configure-windows-server-update-services-wsus/WSUS_Wiz5b.png "WSUS_Wiz5b")  
  
    3.  이 시점에서 프록시 서버 구성을 사용 하 여 완료 됩니다. 클릭 **다음** 설정 동기화 프로세스를 시작할 수 있는 다음 페이지로 이동 합니다.  
  
6.  연결을 시작 합니다.  
  
    ![WSUS 프록시 연결 시작](./media/configure-windows-server-update-services-wsus/WSUS_Wiz6.png "WSUS_Wiz6")  
  
    클릭 **연결 시작**합니다.  
  
    연결 성공, 클릭 **다음** 언어를 선택할 수 있습니다 하 여 다음 페이지로 이동 합니다.  
  
7.  언어를 선택 합니다.  
  
    선택 **이러한 언어의 업데이트만 다운로드**합니다.  
  
    선택 **영어**를 클릭 하 고 **다음**합니다.  
  
    ![언어 선택](./media/configure-windows-server-update-services-wsus/SQL_Server_PDW_WSUSChooseLanguages.png "SQL_Server_PDW_WSUSChooseLanguages")  
  
8.  제품을 선택 합니다.  
  
    > [!NOTE]  
    > 업스트림 서버를 사용 하는 제품 선택 할 수 합니다. 이 옵션을 사용할 수 없는 경우이 단계를 건너뜁니다.  
  
    선택한 모든 업데이트를 선택 취소 합니다.  
  
    선택 **Windows Server 2012 R2**, 및 **System Center 2012 R2 Virtual Machine Manager**를 클릭 하 고 **다음**합니다.  
  
9. 분류를 선택 합니다.  
  
    > [!NOTE]  
    > 업스트림 서버를 사용 하는 경우 있습니다 못할 분류를 선택 합니다.  이 옵션을 사용할 수 없는 경우이 단계를 건너뜁니다.  
  
    이전에 선택한 모든 업데이트를 선택 취소 합니다.  
  
    선택 **중요 업데이트** 하 고 **보안 업데이트** Analytics Platform System appliance에 대 한 동기화 됩니다을 클릭 한 다음 업데이트에 대 한 **다음**합니다.  
  
    ![분류를 선택](./media/configure-windows-server-update-services-wsus/SQL_Server_PDW_WSUSChooseClassifications.png "SQL_Server_PDW_WSUSChooseClassifications")  
  
10. 동기화 일정을 구성 합니다.  
  
    선택 **수동으로 동기화 할**를 클릭 하 고 **다음**합니다.  
  
    ![설정 동기화 일정](./media/configure-windows-server-update-services-wsus/SQL_Server_PDW_WSUSSyncSchedule.png "SQL_Server_PDW_WSUSSyncSchedule")  
  
11. 초기 동기화를 시작 합니다.  
  
    선택 **초기 동기화 시작**, 클릭 **다음**합니다.  
  
12. 완료 합니다.  
  
    **마침**을 클릭합니다.  
  
## <a name="bkmk_WSUSGroup"></a>WSUS에서 어플라이언스 서버 그룹  
Analytics Platform System에 대 한 WSUS를 구성한 후 다음 단계 어플라이언스 서버 그룹화 하는 것입니다. 모든 어플라이언스 서버에 그룹에 추가 하 여 WSUS 어플라이언스의 모든 서버에 소프트웨어 업데이트를 적용할 수 됩니다.  
  
> [!NOTE]  
> WSUS 시스템 비동기적으로 실행 하도록 설계 되었습니다. 작업 시작 항상 얻지는 즉시 업데이트 합니다. 따라서 컴퓨터가 WSUS 대화 상자에 표시 될 때까지 잠시 대기 해야 합니다. 실행를 `setup.exe /action=ReportMicrosoftUpdateClientStatus /DomainAdminPassword="<password>"` 항목의 끝에 설명 된 명령 [다운로드 및 Microsoft 업데이트 적용 &#40;Analytics Platform System&#41; ](download-and-apply-microsoft-updates.md) 대화 상자를 새로 고침 하는 데 도움이 됩니다.  
  
#### <a name="to-group-the-appliance-servers"></a>어플라이언스 서버를 그룹화 하려면  
  
1.  WSUS 콘솔을 열고 마우스 오른쪽 단추로 **모든 컴퓨터** 을 클릭 한 다음 **컴퓨터 그룹 추가**합니다.  
  
    ![컴퓨터 그룹을 추가 합니다. ](./media/configure-windows-server-update-services-wsus/SQL_Server_PDW_WSUSAddComputerGroup.png "SQL_Server_PDW_WSUSAddComputerGroup")  
  
2.  컴퓨터 그룹의 이름을 "AP"를 입력 한 다음 클릭 **추가**합니다.  
  
    ![새 컴퓨터 그룹의 이름을 입력 합니다. ](./media/configure-windows-server-update-services-wsus/SQL_Server_PDW_WSUSSpecifyGroupName.png "SQL_Server_PDW_WSUSSpecifyGroupName")  
  
3.  클릭 **모든 컴퓨터** 다시에서 상태를 변경 합니다 **상태** 드롭 다운 메뉴를 **모든**를 클릭 하 고 **새로 고침**합니다. 확장 해야 할 수 있습니다 **모든 컴퓨터** 방금 추가한 새 그룹을 보려면 왼쪽의 트리 컨트롤에서 클릭 하 여 합니다.  
  
    ![상태를 임의로 변경 하 고 새로 고침을 클릭 합니다. ](./media/configure-windows-server-update-services-wsus/SQL_Server_PDW_WSUSChangeStatusToAny.png "SQL_Server_PDW_WSUSChangeStatusToAny")  
  
4.  어플라이언스, 마우스 클릭의 일부인 모든 컴퓨터를 선택 **구성원 변경**합니다.  
  
    ![모든 PDW 컴퓨터에 대 한 멤버 자격을 변경 합니다. ](./media/configure-windows-server-update-services-wsus/SQL_Server_PDW_WSUSChangeMembership.png "SQL_Server_PDW_WSUSChangeMembership")  
  
5.  확인란을 클릭 한 다음 클릭 하 여 만든 새 컴퓨터 그룹 선택 **확인**합니다.  
  
    ![컴퓨터 그룹 구성원 십](./media/configure-windows-server-update-services-wsus/SQL_Server_PDW_WSUSSetComputerGroupMembership.png "SQL_Server_PDW_WSUSSetComputerGroupMembership")  
  
6.  새 컴퓨터 그룹 선택, 변경 해당 **상태** 하 **모든**를 클릭 하 고 **새로 고침**합니다. 이제 모든 컴퓨터는이 그룹에 할당 된 고, 오른쪽 창에 나열 해야 합니다. 노드 같은 경고를 표시 하는 경우 계속 하려면 일반적으로 안전 **이 노드의 상태를 아직 보고 하지 않았습니다**합니다.  
  
    ![상태를 임의로 변경 하 고 새로 고침을 클릭 합니다. ](./media/configure-windows-server-update-services-wsus/SQL_Server_PDW_WSUSChangeStatusAnyRefresh.png "SQL_Server_PDW_WSUSChangeStatusAnyRefresh")  
  
