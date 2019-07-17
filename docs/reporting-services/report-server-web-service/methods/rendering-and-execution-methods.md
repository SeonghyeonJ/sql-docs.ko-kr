---
title: 렌더링 및 실행 메서드 | Microsoft Docs
ms.date: 03/06/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-server-web-service
ms.topic: reference
helpviewer_keywords:
- rendered reports [Reporting Services]
- reports [Reporting Services], execution options
- methods [Reporting Services], execution options
- methods [Reporting Services], rendering
ms.assetid: 12626aad-f0be-4653-87d0-60eb3a3fff78
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 244541348f583ab5384a0ebfe7321509a421fe1b
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63284536"
---
# <a name="rendering-and-execution-methods"></a>렌더링 및 실행 메서드
  다음 메서드를 사용하여 항목 실행 및 캐싱과 보고서 렌더링을 관리할 수 있습니다.  
  
|메서드|작업|  
|------------|------------|  
|<xref:ReportService2010.ReportingService2010.FlushCache%2A>|항목 캐시를 무효화합니다.|  
|<xref:ReportService2010.ReportingService2010.GetCacheOptions%2A>|항목에 대한 캐시 구성 및 캐시된 항목 복사본의 만료 시점을 설명하는 설정을 반환합니다.|  
|<xref:ReportService2010.ReportingService2010.GetExecutionOptions%2A>|개별 항목에 대한 실행 옵션 및 연관된 설정을 반환합니다.|  
|<xref:ReportService2010.ReportingService2010.ListExecutionSettings%2A>|지원되는 실행 설정 목록을 반환합니다.|  
|<xref:ReportExecution2005.ReportExecutionService.Render%2A>|지정된 보고서를 처리하고 지정된 형식으로 렌더링합니다.|  
|<xref:ReportService2010.ReportingService2010.SetCacheOptions%2A>|캐시할 항목을 구성하고 캐시된 항목 복사본의 만료 시점을 지정하는 설정을 제공합니다.|  
|<xref:ReportService2010.ReportingService2010.SetExecutionOptions%2A>|지정된 항목에 대한 실행 옵션 및 연관된 실행 속성을 설정합니다.|  
|<xref:ReportService2010.ReportingService2010.UpdateItemExecutionSnapshot%2A>|지정된 항목에 대한 항목 실행 스냅샷을 생성합니다.|  
  
## <a name="see-also"></a>참고 항목  
 [웹 서비스와 .NET Framework를 사용하여 애플리케이션 빌드](../../../reporting-services/report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md)   
 [보고서 서버 웹 서비스](../../../reporting-services/report-server-web-service/report-server-web-service.md)   
 [보고서 서버 웹 서비스 메서드](../../../reporting-services/report-server-web-service/methods/report-server-web-service-methods.md)   
 [기술 참조&#40;SSRS&#41;](../../../reporting-services/technical-reference-ssrs.md)  
  
  
