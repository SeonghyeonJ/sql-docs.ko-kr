---
title: 데이터베이스 구성 페이지(Master Data Services 구성 관리자) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
f1_keywords:
- sql12.mds.configmanager.dbpg.f1
ms.assetid: dd72220e-a599-465d-8b84-9bb6a7433216
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 7f5f11ba4154b70c5aa1fd0ae0e7579c746ce744
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/26/2020
ms.locfileid: "65483181"
---
# <a name="database-configuration-page-master-data-services-configuration-manager"></a>데이터베이스 구성 페이지(Master Data Services 구성 관리자)
  **데이터베이스 구성** 페이지를 사용하여 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 데이터베이스의 시스템 설정을 편집할 수 있습니다. 시스템 설정은 선택한 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 데이터베이스와 연결된 모든 웹 애플리케이션 및 웹 서비스에 영향을 줍니다. 시스템 설정을 활성화하고 구성에 사용하려면 먼저 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 데이터베이스를 선택하거나 만들어야 합니다.  
  
## <a name="current-database"></a>현재 데이터베이스  
 시스템 설정을 편집할 기존 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 데이터베이스를 선택하거나 새 데이터베이스를 만듭니다. 새 데이터베이스는 만든 후 자동으로 선택됩니다.  
  
|컨트롤 이름|설명|  
|------------------|-----------------|  
|**SQL Server 인스턴스**|선택한 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 인스턴스의 이름을 표시합니다. 인스턴스에 연결하고 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 데이터베이스를 선택하거나 만들 때까지 비어 있습니다.|  
|**MDS(Master Data Services) 데이터베이스**|선택한 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 데이터베이스의 이름을 표시합니다. 인스턴스에 연결하고 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 데이터베이스를 선택하거나 만들 때까지 비어 있습니다.|  
|**Master Data Services 데이터베이스 버전**|[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 데이터베이스 스키마의 버전입니다.|  
|**데이터베이스 만들기**|**데이터베이스 만들기** 마법사를 열어 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 인스턴스에 연결하고 해당 인스턴스에 대한 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 데이터베이스를 만듭니다.|  
|**데이터베이스 선택**|**인스턴스에 연결하고** 데이터베이스를 선택할 수 있는 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 데이터베이스에 연결 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 대화 상자를 엽니다.|  
|**데이터베이스 업그레이드**|지정한 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 데이터베이스를 업그레이드할 수 있는 마법사를 엽니다. 이 단추는 지정한 데이터베이스에 업그레이드가 필요할 때만 사용할 수 있습니다.|  
|**데이터베이스 복구**|MDS 데이터베이스가 올바르게 설치되었는지 확인하려면 이 단추를 클릭합니다. 이렇게 하면 MDS 데이터베이스를 호스팅하지 않은 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 인스턴스에 대해 MDS 데이터베이스를 백업하거나 복원할 경우에 도움이 될 수 있습니다.|  
  
## <a name="system-settings"></a>시스템 설정  
 선택한 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 데이터베이스와 연결된 모든 웹 애플리케이션 및 웹 서비스에 대한 시스템 설정을 편집합니다.  
  
 이러한 설정은 [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] 에서 사용할 수 있으며 시스템 설정 테이블(mdm.tblSystemSetting)의 데이터베이스에 저장됩니다. 모든 설정 목록은 [시스템 설정&#40;Master Data Services&#41;](system-settings-master-data-services.md)을 참조하세요.  
  
## <a name="see-also"></a>참고 항목  
 [MDS(Master Data Services)에 대 한 데이터베이스 및 웹 사이트 설정](../../2014/master-data-services/set-up-the-database-and-website-for-master-data-services.md)   
 [데이터베이스 요구 사항&#40;Master Data Services&#41;](install-windows/database-requirements-master-data-services.md)  
  
  
