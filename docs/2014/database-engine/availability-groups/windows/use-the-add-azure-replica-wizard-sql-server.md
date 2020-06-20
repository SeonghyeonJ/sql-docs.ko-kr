---
title: Azure 복제본 추가 마법사 사용(SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.addreplicawizard.azurereplica.f1
ms.assetid: b89cc41b-07b4-49f3-82cc-bc42b2e793ae
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 95cb279c939298256a623d67e3db8f979f65c40f
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84936266"
---
# <a name="use-the-add-azure-replica-wizard-sql-server"></a>Azure 복제본 추가 마법사 사용(SQL Server)
  Azure 복제본 추가 마법사를 사용 하 여 하이브리드 IT에서 새 Azure VM을 만들고 새로운 또는 기존 AlwaysOn 가용성 그룹에 대 한 보조 복제본으로 구성할 수 있습니다.  
  
-   **시작하기 전 주의 사항:**  
  
     [필수 구성 요소](#Prerequisites)  
  
     [보안](#Security)  
  
-   **복제본을 추가하려면:**  [Azure 복제본 추가 마법사(SQL Server Management Studio)](#SSMSProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> 시작하기 전에  
 가용성 그룹에 가용성 복제본을 추가 하지 않은 경우 [AlwaysOn 가용성 그룹 &#40;SQL Server&#41;에 대 한 필수 조건, 제한 사항 및 권장 사항 ](prereqs-restrictions-recommendations-always-on-availability.md)에서 "서버 인스턴스" 및 "가용성 그룹 및 복제본" 섹션을 참조 하세요.  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> 전제 조건  
  
-   현재 주 복제본을 호스팅하는 서버 인스턴스에 연결되어 있어야 합니다.  
  
-   온-프레미스 서브넷에 Azure를 사용하는 사이트 간 VPN을 갖춘 하이브리드 IT 환경이 있어야 합니다. 자세한 내용은 [관리 포털에서 사이트 간 VPN 구성](https://azure.microsoft.com/documentation/articles/vpn-gateway-site-to-site-create)을 참조하세요.  
  
-   가용성 그룹은 온-프레미스 가용성 복제본을 포함해야 합니다.  
  
-   가용성 그룹 수신기의 클라이언트는 가용성 그룹이 Azure 복제본으로 장애 조치될 때 수신기와 연결을 유지하려는 경우 인터넷에 연결해야 합니다.  
  
-   **전체 초기 데이터 동기화를 사용하기 위한 사전 요구 사항** 마법사에서 백업을 만들고 액세스하려면 네트워크 공유를 지정해야 합니다. 주 복제본의 경우 [!INCLUDE[ssDE](../../../includes/ssde-md.md)] 을 시작하는 데 사용되는 계정은 네트워크 공유에 대한 읽기 및 쓰기 파일 시스템 권한이 있어야 합니다. 보조 복제본에 대한 계정은 네트워크 공유에 대한 읽기 권한이 있어야 합니다.  
  
     마법사를 사용하여 전체 초기 데이터 동기화를 수행할 수 없는 경우에는 보조 데이터베이스를 수동으로 준비해야 합니다. 마법사를 실행하기 전이나 후에 이 작업을 수행할 수 있습니다. 자세한 내용은 [가용성 그룹에 대한 보조 데이터베이스 수동 준비&#40;SQL Server&#41;](manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md)또는 PowerShell을 사용하여 Always On 가용성 그룹에 보조 데이터베이스를 조인하는 방법에 대해 설명합니다.  
  
###  <a name="security"></a><a name="Security"></a> 보안  
  
####  <a name="permissions"></a><a name="Permissions"></a> 권한  
 [Security](use-the-add-replica-to-availability-group-wizard-sql-server-management-studio.md#Security)를 참조하세요.  
  
##  <a name="using-the-add-azure-replica-wizard-sql-server-management-studio"></a><a name="SSMSProcedure"></a>Azure 복제본 추가 마법사 사용 (SQL Server Management Studio)  
 [복제본 페이지 지정](specify-replicas-page-new-availability-group-wizard-add-replica-wizard.md)에서 Azure 복제본 추가 마법사를 시작할 수 있습니다. 다음 두 가지 방법으로 이 페이지에 도달할 수 있습니다.  
  
-   [가용성 그룹 마법사 사용&#40;SQL Server Management Studio&#41;](use-the-availability-group-wizard-sql-server-management-studio.md)  
  
-   [가용성 그룹에 복제본 추가 마법사 사용&#40;SQL Server Management Studio&#41;](use-the-add-replica-to-availability-group-wizard-sql-server-management-studio.md)  
  
 Azure 복제본 추가 마법사를 시작한 후 아래 단계를 따릅니다.  
  
1.  먼저 Azure 구독의 관리 인증서를 다운로드합니다. **다운로드** 를 클릭하여 로그인 페이지를 엽니다.  
  
2.  로그인 페이지에서 Azure 구독에 로그인 합니다. 로그인하면 마법사가 관리 인증서를 로컬 컴퓨터에 설치합니다. 이 관리 인증서는 이 마법사를 다시 사용할 때 자동으로 로드됩니다. 관리 인증서를 여러 개 다운로드한 경우 **...** 단추를 클릭하여 사용할 단추를 선택합니다.  
  
3.  다음에는 **연결**을 클릭하여 구독에 연결합니다. 연결되면 드롭다운 목록에 **가상 네트워크** 및 **가상 네트워크 서브넷**과 같은 Azure 매개 변수가 채워집니다.  
  
4.  새 보조 복제본을 호스트할 Azure VM에 대한 설정을 지정합니다.  
  
     이미지  
     Azure VM에 사용할 SQL Server 이미지의 이름  
  
     VM 크기  
     Azure VM의 크기  
  
     VM 이름  
     Azure VM의 DNS 이름  
  
     VM 사용자 이름  
     Azure VM 기본 관리자의 사용자 이름  
  
     VM 관리자 암호(및 암호 확인)  
     Azure VM 기본 관리자의 암호  
  
     Virtual Network  
     Azure VM을 배치할 가상 네트워크  
  
     가상 네트워크 서브넷  
     Azure VM을 배치할 가상 네트워크 서브넷  
  
     도메인  
     Azure VM을 조인할 Active Directory(AD) 도메인  
  
     도메인 사용자 이름  
     Azure VM을 도메인에 조인하는 데 사용되는 AD 사용자 이름  
  
     암호  
     Azure VM을 도메인에 조인하는 데 사용되는 암호  
  
5.  **확인** 을 클릭하여 설정을 커밋하고 Azure 복제본 추가 마법사를 끝냅니다.  
  
6.  새 복제본에 대해 수행하는 것과 같은 방법으로 [복제본 지정 페이지](specify-replicas-page-new-availability-group-wizard-add-replica-wizard.md) 의 나머지 구성 단계를 계속합니다.  
  
     가용성 그룹 마법사 또는 가용성 그룹에 복제본 추가 마법사를 마치면 구성 프로세스에서 Azure의 모든 작업을 수행 하 여 새 VM을 만들고, AD 도메인에 연결 하 고, Windows 클러스터에 추가 하 고, AlwaysOn 고가용성을 사용 하도록 설정 하 고, 가용성 그룹에 새 복제본을 추가 합니다.  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> 관련 작업  
  
-   [가용성 그룹에 보조 복제본 추가&#40;SQL Server&#41;](add-a-secondary-replica-to-an-availability-group-sql-server.md)  
  
## <a name="see-also"></a>참고 항목  
 [AlwaysOn 가용성 그룹 &#40;SQL Server 개요&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [AlwaysOn 가용성 그룹 &#40;SQL Server에 대 한 필수 조건, 제한 사항 및 권장 사항&#41;](prereqs-restrictions-recommendations-always-on-availability.md)   
 [가용성 그룹에 보조 복제본 추가&#40;SQL Server&#41;](add-a-secondary-replica-to-an-availability-group-sql-server.md)  
  
  
