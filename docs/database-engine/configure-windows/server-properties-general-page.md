---
title: 서버 속성(일반 페이지) - SQL Server Management Studio | Microsoft Docs
description: SQL Server의 읽기 전용 속성을 파악합니다. 예를 들면 서버 이름, 운영 체제, 데이터 정렬, SQL Server 버전이 있습니다.
ms.custom: ''
ms.date: 08/25/2016
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
f1_keywords:
- sql13.swb.serverproperties.setsapassword.f1
- sql13.swb.serverproperties.activedirectory.f1
- sql13.swb.serverproperties.prodinfo.f1
ms.assetid: 10ac57f1-b4bd-4528-bb66-3e47ccf663e7
author: markingmyname
ms.author: maghan
ms.openlocfilehash: da2180230cfc80775f07a73dbc41f12ad9e46641
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85726655"
---
# <a name="server-properties---general-page"></a>서버 속성 - 일반 페이지
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  이 페이지를 사용하여 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 설치에 대한 읽기 전용 정보를 볼 수 있습니다.  
  
## <a name="property-grid"></a>속성 표  
 서버 이름, 서버 운영 체제 또는 프로세서 수 등 선택한 서버의 속성을 표시합니다.  
  
 **이름**  
 서버 인스턴스의 이름을 표시합니다.  
  
 **Product**  
 현재 실행되는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 버전을 표시합니다.  
  
 **운영 체제**  
 현재 실행되는 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 운영 체제를 표시합니다.  
  
 **플랫폼**  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]가 실행되는 운영 체제 및 하드웨어에 대해 설명합니다.  
  
 **버전**  
 현재 실행되는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 의 버전 번호를 표시합니다.  
  
 **언어**  
 실행 중인 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]인스턴스가 지원하는 언어를 표시합니다.  
  
 **메모리**  
 서버에 설치된 RAM의 크기를 보여 줍니다.  
  
 **프로세서**  
 설치된 CPU 수를 표시합니다.  
  
 **루트 디렉터리**  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스가 있는 경로를 표시하며 대개 C:\Program Files\Microsoft SQL Server\\입니다.  
  
 **서버 데이터 정렬**  
 서버가 지원하는 데이터 정렬을 표시합니다. 데이터 정렬은 유니코드 및 비유니코드 데이터에 사용되는 특정 코드 페이지와 정렬 순서를 지정합니다.  
  
 **클러스터형 여부**  
 서버 인스턴스가 **장애 조치(Failover) 클러스터에 구성되어 있는 경우** True [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 를 표시하고, 서버 인스턴스가 클러스터링되지 않은 경우 **False** 를 표시합니다.  
  
 **HADR 사용**  
 **기능이 사용하도록 설정되어 있으면** True [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] 를 표시하고, **기능이 사용하지 않도록 설정되어 있으면** False [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] 를 표시합니다. [!INCLUDE[ssHADR](../../includes/sshadr-md.md)]를 사용하거나 사용하지 않도록 설정하는 방법에 대한 자세한 내용은 [Always On 가용성 그룹 활성화 및 비활성화&#40;SQL Server&#41;](../../database-engine/availability-groups/windows/enable-and-disable-always-on-availability-groups-sql-server.md)를 참조하세요.  
  
## <a name="description-field"></a>설명 필드  
 서버 속성에 대한 추가 정보를 표시합니다.  
  
## <a name="see-also"></a>참고 항목  
 [서버 구성 옵션&#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md)  
  
  
