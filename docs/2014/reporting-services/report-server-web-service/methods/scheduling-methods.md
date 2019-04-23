---
title: 일정 예약 메서드 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- schedules [Reporting Services], methods
- reports [Reporting Services], scheduling
- shared schedules [Reporting Services], methods
- methods [Reporting Services], scheduling
ms.assetid: 68ae13f9-d91e-4572-a82a-8fa42001569e
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 99dac71ba0be4f4c3f3ff669f838b0409b996f06
ms.sourcegitcommit: b87c384e10d6621cf3a95ffc79d6f6fad34d420f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60153879"
---
# <a name="scheduling-methods"></a>일정 예약 메서드
  이러한 메서드는 보고서 실행 및 전달을 위한 공유 일정을 만들고 관리하는 데 사용할 수 있으며 보고서 서버에서 사용하는 캐시 새로 고침 계획에도 사용할 수 있습니다.  
  
|메서드|작업|  
|------------|------------|  
|<xref:ReportService2010.ReportingService2010.CreateCacheRefreshPlan%2A>|항목에 대한 캐시 새로 고침 계획을 만듭니다.|  
|<xref:ReportService2010.ReportingService2010.CreateSchedule%2A>|새 공유 일정을 만듭니다.|  
|<xref:ReportService2010.ReportingService2010.DeleteCacheRefreshPlan%2A>|캐시 새로 고침 계획을 삭제합니다.|  
|<xref:ReportService2010.ReportingService2010.DeleteSchedule%2A>|특정 일정 ID를 기준으로 공유 일정을 삭제합니다.|  
|<xref:ReportService2010.ReportingService2010.GetCacheRefreshPlanProperties%2A>|지정된 캐시 새로 고침 계획의 속성을 반환합니다.|  
|<xref:ReportService2010.ReportingService2010.GetScheduleProperties%2A>|공유 일정의 속성 값을 반환합니다.|  
|<xref:ReportService2010.ReportingService2010.ListCacheRefreshPlans%2A>|카탈로그 항목과 연결된 캐시 새로 고침 계획의 목록을 반환합니다.|  
|<xref:ReportService2010.ReportingService2010.ListScheduledItems%2A>|공유 일정과 연결된 항목 목록을 반환합니다.|  
|<xref:ReportService2010.ReportingService2010.ListSchedules%2A>|보고서 서버 또는 SharePoint 사이트의 모든 공유 일정 목록을 반환합니다.|  
|<xref:ReportService2010.ReportingService2010.ListScheduleStates%2A>|지원되는 일정 상태 목록을 반환합니다.|  
|<xref:ReportService2010.ReportingService2010.PauseSchedule%2A>|지정된 일정의 실행을 일시 중지합니다.|  
|<xref:ReportService2010.ReportingService2010.ResumeSchedule%2A>|일시 중지된 공유 일정을 다시 시작합니다.|  
|<xref:ReportService2010.ReportingService2010.SetCacheRefreshPlanProperties%2A>|캐시 새로 고침 계획의 속성을 설정합니다.|  
|<xref:ReportService2010.ReportingService2010.SetScheduleProperties%2A>|공유 일정의 속성 값을 설정합니다.|  
  
## <a name="see-also"></a>관련 항목  
 [웹 서비스와 .NET Framework를 사용하여 응용 프로그램 빌드](../net-framework/building-applications-using-the-web-service-and-the-net-framework.md)   
 [보고서 서버 웹 서비스](../report-server-web-service.md)   
 [보고서 서버 웹 서비스 메서드](report-server-web-service-methods.md)   
 [기술 참조&#40;SSRS&#41;](../../technical-reference-ssrs.md)  
  
  
