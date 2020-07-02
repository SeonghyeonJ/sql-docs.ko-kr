---
title: MDS 데이터베이스에 연결 대화 상자
ms.custom: seo-lt-2019
ms.date: 03/20/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
f1_keywords:
- sql13.mds.configmanager.srvconnect.f1
ms.assetid: b2f8c9b9-c31e-4f0d-9095-978709423190
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: f6791a728c13a5e33b2557243d70563177465e08
ms.sourcegitcommit: 6be9a0ff0717f412ece7f8ede07ef01f66ea2061
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85811858"
---
# <a name="connect-to-a-master-data-services-database-dialog-box"></a>Master Data Services 데이터베이스에 연결 대화 상자

[!INCLUDE [SQL Server - Windows only ASDBMI  ](../includes/applies-to-version/sql-windows-only-asdbmi.md)]

  **Master Data Services 데이터베이스에 연결** 대화 상자를 사용하여 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 데이터베이스를 선택할 수 있습니다.  
  
 이 대화 상자는 [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)]의 다음 페이지에서 사용할 수 있습니다.  
  
-   **데이터베이스 구성** 페이지에서 **데이터베이스 선택**을 클릭합니다. 을 클릭합니다. 이 대화 상자를 사용하여 시스템 설정을 구성할 데이터베이스를 선택할 수 있습니다.  
  
-   **웹 구성** 페이지의 **애플리케이션을 데이터베이스에 연결**에서 **선택** 을 클릭하여 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 웹 사이트 또는 애플리케이션과 연결할 데이터베이스를 선택할 수 있습니다.  
  
## <a name="select-database"></a>데이터베이스 선택  
 [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] 데이터베이스를 호스팅하는 로컬 또는 원격 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 인스턴스에 연결할 정보를 지정합니다. 원격 인스턴스에 연결하려면 원격 연결을 설정해야 합니다.  
  
|컨트롤 이름|설명|  
|------------------|-----------------|  
|**SQL Server 인스턴스**|[!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] 데이터베이스를 호스팅할 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 인스턴스의 이름을 지정합니다. 로컬 컴퓨터나 원격 컴퓨터의 기본 또는 명명된 인스턴스를 사용할 수 있습니다. 다음을 입력하여 정보를 지정하십시오.<br /><br /> 마침표(.) - 로컬 컴퓨터의 기본 인스턴스에 연결하려는 경우<br /><br /> 서버 이름 또는 IP 주소 - 지정된 로컬 또는 원격 컴퓨터의 기본 인스턴스에 연결하려는 경우<br /><br /> 서버 이름 또는 IP 주소 및 인스턴스 이름 - 지정된 로컬 또는 원격 컴퓨터의 명명된 인스턴스에 연결하려는 경우. *Server_name*instance_name 형식으로이 정보를 지정 \\ *instance_name*합니다.|  
|**인증 유형**|지정된 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 인스턴스에 연결할 때 사용할 인증 유형을 선택합니다. 연결하는 데 사용한 자격 증명에 따라 **Master Data Services 데이터베이스** 드롭다운 목록에 표시되는 데이터베이스가 결정됩니다.<br /><br /> 인증 유형은 다음과 같습니다.<br /><br /> **현재 사용자 통합 보안**: Windows 통합 인증을 사용 하 여 현재 windows 사용자 계정의 자격 증명을 사용 하 여 연결 합니다. [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] 에서는 컴퓨터에 로그온하여 애플리케이션을 연 사용자의 Windows 자격 증명을 사용합니다. 애플리케이션에서 다른 Windows 자격 증명은 지정할 수 없습니다. 다른 Windows 자격 증명으로 연결하려면 해당 사용자로 컴퓨터에 로그온한 다음 [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)]를 열어야 합니다.<br /><br /> **SQL Server 계정**: SQL Server 계정을 사용하여 연결합니다. 이 옵션을 선택하면 **사용자 이름** 및 **암호** 필드가 활성화됩니다. 이 필드에 지정된 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 인스턴스의 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 계정에 대한 자격 증명을 지정해야 합니다.|  
|**사용자 이름**|지정된 SQL Server 인스턴스에 연결하는 데 사용되는 사용자 계정의 이름을 지정합니다. 계정은 지정된 **인스턴스에 대한** sysadmin [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 역할의 일부여야 합니다.<br /><br /> **인증 유형이** **현재 사용자 통합 보안**인 경우 **사용자 이름** 상자는 읽기 전용 이며 컴퓨터에 로그온 된 Windows 사용자 계정의 이름을 표시 합니다.<br /><br /> **인증 유형** 이 **SQL Server 계정**인 경우 **사용자 이름** 상자가 활성화되며, 지정된 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 인스턴스의 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 계정에 대한 자격 증명을 지정해야 합니다.|  
|**암호**|사용자 계정에 연결된 암호를 지정합니다.<br /><br /> **인증 유형이** **현재 사용자 통합 보안**인 경우 **암호** 상자는 읽기 전용 이며 지정 된 Windows 사용자 계정의 자격 증명을 사용 하 여 연결 합니다.<br /><br /> **인증 유형** 이 **SQL Server 계정**인 경우 **암호** 상자가 활성화되며, 지정된 사용자 계정에 연결된 암호를 지정해야 합니다.|  
|**연결**|지정된 자격 증명으로 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 인스턴스에 연결합니다.|  
|**MDS(Master Data Services) 데이터베이스**|지정된 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 인스턴스의 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 데이터베이스를 다음 조건에 따라 표시합니다.<br /><br /> 사용자가 해당 인스턴스에 대한 **sysadmin** 서버 역할의 멤버인 경우 해당 인스턴스의 모든 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 데이터베이스가 표시됩니다.<br /><br /> 사용자가 해당 인스턴스의 **데이터베이스에 대한** db_owner [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 데이터베이스 역할의 멤버인 경우 해당 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 데이터베이스가 표시됩니다.<br /><br/> SQL Server 역할에 대한 자세한 내용은 [서버 수준 역할](../relational-databases/security/authentication-access/server-level-roles.md) 및 [데이터베이스 수준 역할](../relational-databases/security/authentication-access/database-level-roles.md)을 참조하세요.|  
  
## <a name="see-also"></a>참고 항목  
 [데이터베이스 구성 페이지&#40;Master Data Services 구성 관리자&#41;](../master-data-services/database-configuration-page-master-data-services-configuration-manager.md)   

[Master Data Services 설치 및 구성](../master-data-services/master-data-services-installation-and-configuration.md)
  
  
