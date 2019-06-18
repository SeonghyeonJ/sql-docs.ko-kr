---
title: 권한 부여 메서드 | Microsoft Docs
ms.date: 03/06/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-server-web-service
ms.topic: reference
helpviewer_keywords:
- security [Reporting Services], reports
- authorization [Reporting Services]
- reports [Reporting Services], security
- tasks [Reporting Services]
- roles [Reporting Services], methods
ms.assetid: 45e9cf2c-facf-4801-9482-c855403f42a8
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 119b795eacb217aff6b5a4aeca2fffa12519c752
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63025945"
---
# <a name="authorization-methods"></a>권한 부여 메서드
  다음 메서드를 사용하여 보고서 서버에서 태스크, 역할 및 정책을 관리할 수 있습니다.  
  
|메서드|작업|  
|------------|------------|  
|<xref:ReportService2010.ReportingService2010.CreateRole%2A>|보고서 서버 데이터베이스에 새 역할을 추가합니다. 이 메서드는 기본 모드에만 적용됩니다.|  
|<xref:ReportService2010.ReportingService2010.DeleteRole%2A>|보고서 서버 데이터베이스에서 역할을 삭제합니다. 이 메서드는 기본 모드에만 적용됩니다.|  
|<xref:ReportService2010.ReportingService2010.GetPermissions%2A>|보고서 서버 데이터베이스 또는 SharePoint 라이브러리의 특정 항목과 연결된 사용자 권한을 반환합니다.|  
|<xref:ReportService2010.ReportingService2010.GetPolicies%2A>|보고서 서버 데이터베이스 또는 또는 SharePoint 라이브러리의 특정 항목과 연결된 정책을 반환합니다.|  
|<xref:ReportService2010.ReportingService2010.GetRoleProperties%2A>|역할 메타데이터 속성 및 관련 태스크 모음을 반환합니다.|  
|<xref:ReportService2010.ReportingService2010.GetSystemPermissions%2A>|사용자의 시스템 사용 권한을 반환합니다. 이 메서드는 기본 모드에만 적용됩니다.|  
|<xref:ReportService2010.ReportingService2010.GetSystemPolicies%2A>|연결된 그룹 및 역할을 포함한 시스템 정책을 반환합니다. 이 메서드는 기본 모드에만 적용됩니다.|  
|<xref:ReportService2010.ReportingService2010.InheritParentSecurity%2A>|보고서 서버 데이터베이스의 특정 항목과 연결된 정책을 삭제하고 항목에 대한 보안 정책을 부모의 보안 정책으로 설정합니다.|  
|<xref:ReportService2010.ReportingService2010.IsSSLRequired%2A>|<xref:ReportService2010> 끝점을 사용하는 데 SSL(Secure Sockets Layer) 프로토콜이 필요한지 여부를 나타내는 부울 값을 반환합니다.|  
|<xref:ReportService2010.ReportingService2010.ListRoles%2A>|보고서 서버에서 관리되는 역할의 이름과 설명을 반환합니다.|  
|<xref:ReportExecution2005.ReportExecutionService.ListSecureMethods%2A>|<xref:ReportExecution2005> 엔드포인트에서 호출될 때 보안 연결이 필요한 SOAP(Simple Object Access Protocol) 메서드 목록을 반환합니다. 반환되는 메서드를 결정하는 데는 보고서 서버의 **SecureConnectionLevel** 설정이 사용됩니다.|  
|<xref:ReportService2010.ReportingService2010.ListTasks%2A>|보고서 서버에서 관리되는 태스크를 반환합니다.|  
|<xref:ReportService2010.ReportingService2010.SetPolicies%2A>|지정된 항목과 연결된 정책을 설정합니다.|  
|<xref:ReportService2010.ReportingService2010.SetRoleProperties%2A>|역할 메타데이터 속성을 설정하고 태스크 집합과 역할을 연결합니다. 이 메서드는 기본 모드에만 적용됩니다.|  
|<xref:ReportService2010.ReportingService2010.SetSystemPolicies%2A>|그룹 및 그룹과 연관된 역할을 정의하는 시스템 정책을 설정합니다. 이 메서드는 기본 모드에만 적용됩니다.|  
  
## <a name="see-also"></a>참고 항목  
 [웹 서비스와 .NET Framework를 사용하여 애플리케이션 빌드](../../../reporting-services/report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md)   
 [보고서 서버 웹 서비스](../../../reporting-services/report-server-web-service/report-server-web-service.md)   
 [보고서 서버 웹 서비스 메서드](../../../reporting-services/report-server-web-service/methods/report-server-web-service-methods.md)   
 [기술 참조&#40;SSRS&#41;](../../../reporting-services/technical-reference-ssrs.md)  
  
  
