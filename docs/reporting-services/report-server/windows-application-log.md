---
title: Windows 애플리케이션 로그 | Microsoft Docs
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-server
ms.topic: conceptual
helpviewer_keywords:
- Windows application logs [Reporting Services]
- logs [Reporting Services], Windows application logs
- application logs [Reporting Services]
ms.assetid: 742fd00e-aa6c-4c8a-b58f-c03c489b1699
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: f3d51afd8a27786be3c66bfdf935ad8b2e328d36
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 06/15/2019
ms.locfileid: "65580929"
---
# <a name="windows-application-log"></a>Windows 애플리케이션 로그
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 에서는 이벤트 메시지를 Windows 애플리케이션 로그에 기록합니다. 애플리케이션 로그에 기록된 메시지 정보를 사용하여 로컬 시스템에서 실행되는 보고서 서버 애플리케이션에서 생성된 이벤트를 확인할 수 있습니다.  
  
## <a name="viewing-report-server-events"></a>보고서 서버 이벤트 보기  
 이벤트 뷰어를 사용하여 로그 파일을 보고 로그 파일에 들어 있는 메시지를 필터링할 수 있습니다. 이벤트 메시지에 대한 자세한 내용은 [오류 및 이벤트 참조&#40;Reporting Services&#41;](../../reporting-services/troubleshooting/errors-and-events-reference-reporting-services.md)를 참조하세요. Windows 애플리케이션 로그나 이벤트 뷰어에 대한 자세한 내용은 Windows 제품 설명서를 참고하십시오.  
  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 는 다음과 같은 세 가지 이벤트 원본을 제공합니다.  
  
-   보고서 서버(보고서 서버 Windows 서비스)  
  
-   보고서 관리자  
  
-   일정 예약 및 배달 프로세서  
  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 에서는 보고서 서버의 애플리케이션 이벤트 로깅을 해제하거나 기록 대상 이벤트를 변경할 수 없습니다. 보고서 서버 이벤트 로깅을 설명하는 스키마는 고정되어 있습니다. 사용자 지정 이벤트를 지원하도록 스키마를 확장할 수 없습니다.  
  
 다음 표에서는 보고서 서버에서 애플리케이션 이벤트 로그에 기록하는 이벤트 유형을 설명합니다.  
  
|이벤트 유형|설명|  
|----------------|-----------------|  
|정보|성공한 작업을 보여 주는 이벤트(예: 보고서 서버 서비스 시작 시간)|  
|경고|잠재적인 문제를 나타내는 이벤트(예: 디스크 공간 부족)|  
|Error|중요한 문제점을 보여 주는 이벤트(예: 서비스가 시작되지 않았음)|  
|성공 감사|성공적인 로그온을 보여 주는 보안 이벤트|  
|실패 감사|로그온 시도가 실패할 때 기록되는 이벤트|  
  
## <a name="see-also"></a>참고 항목  
 [Reporting Services 로그 파일 및 소스](../../reporting-services/report-server/reporting-services-log-files-and-sources.md)   
 [오류 및 이벤트 참조&#40;Reporting Services&#41;](../../reporting-services/troubleshooting/errors-and-events-reference-reporting-services.md)  
  
  
