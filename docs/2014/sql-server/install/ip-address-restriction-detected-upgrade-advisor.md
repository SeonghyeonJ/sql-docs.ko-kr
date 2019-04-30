---
title: IP 주소 제한이 검색 됨 (업그레이드 관리자) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- report servers [Reporting Services], upgrade issues
ms.assetid: 9a154455-c68f-4403-a3a7-b90f4d35eecb
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 4bbde8eb313d432a7a90cfa7f03c54f4c6aeb06f
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63301377"
---
# <a name="ip-address-restriction-detected-upgrade-advisor"></a>IP 주소 제한이 검색됨(업그레이드 관리자)
  업그레이드 관리자가 보고서 서버 또는 보고서 관리자 가상 디렉터리를 호스팅하는 IIS 웹 사이트에서 하나 이상의 IP 주소 제한을 검색했습니다. [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]는 IP 주소 제한에 대한 기본 지원을 제공하지 않습니다.  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Native.|  
  
## <a name="component"></a>구성 요소  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
## <a name="description"></a>Description  
 설치 프로그램이 업그레이드된 보고서 서버용으로 생성된 URL에 대한 IP 주소 제한을 정의할 수 없습니다. 업그레이드를 계속 진행할 수는 있지만 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] URL에 대한 IP 주소 제한은 정의되지 않습니다.  
  
## <a name="corrective-action"></a>수정 동작  
 업그레이드 후 ISA Server, 방화벽 소프트웨어 또는 다른 솔루션을 사용하여 특정 IP 주소에서 보고서 서버로의 요청을 허용하거나 실행합니다.  
  
## <a name="see-also"></a>관련 항목  
 [Reporting Services 업그레이드 문제 &#40;업그레이드 관리자&#41;](../../../2014/sql-server/install/reporting-services-upgrade-issues-upgrade-advisor.md)  
  
  
