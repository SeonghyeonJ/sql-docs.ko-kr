---
title: Reporting Services SOAP 헤더 사용 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- Web service [Reporting Services], SOAP
- Report Server Web service, SOAP
- SOAP headers [Reporting Services]
- SOAP [Reporting Services], headers
- XML Web service [Reporting Services], SOAP
ms.assetid: 306d2c06-a25a-40f8-8a35-13dd32e8841e
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: f48be183398d4d441b5781c9f9467178c3011e32
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/26/2020
ms.locfileid: "63012284"
---
# <a name="using-reporting-services-soap-headers"></a>Reporting Services SOAP 헤더 사용
  SOAP를 사용한 웹 서비스 메서드와의 통신은 표준 형식을 따릅니다. 이 형식의 일부는 XML 문서로 인코딩되는 데이터입니다. XML 문서는 루트 **Envelope** 요소로 구성되고, 이것은 다시 필수 **Body** 요소와 선택적 **Header** 요소로 구성됩니다. **Body** 요소는 메시지 관련 데이터를 포함합니다. 선택적 **Header** 요소는 특정 메시지와 직접 관련되지 않은 추가 정보를 포함할 수 있습니다. **Header** 요소의 각 자식 요소를 SOAP 헤더라고 합니다.  
  
 SOAP 헤더가 메시지와 관련된 데이터를 포함할 수는 있지만 일반적으로 웹 서버 인프라에서 처리되는 정보를 포함합니다.  
  
 보고서 서버 웹 서비스는 SOAP 헤더에서 사용할 여러 클래스를 정의합니다. <xref:ReportService2005.BatchHeader>, <xref:ReportService2010.ItemNamespaceHeader>, <xref:ReportService2010.ServerInfoHeader>, <xref:ReportService2010.TrustedUserHeader> 및 <xref:ReportExecution2005.ExecutionHeader>  
  
## <a name="in-this-section"></a>섹션 내용  
  
|항목|설명|  
|-----------|-----------------|  
|[일괄 처리 메서드](batching-methods.md)|<xref:ReportService2005.BatchHeader>를 사용하여 여러 작업을 단일 트랜잭션으로 일괄 처리하는 방법을 설명합니다.|  
|[실행 상태 식별](identifying-execution-state.md)|**SessionHeader**를 사용하여 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]에서 세션 상태를 관리하는 방법을 설명합니다.|  
|[GetProperties 메서드에 대한 항목 네임스페이스 설정](setting-the-item-namespace-for-the-getproperties-method.md)|<xref:ReportService2010.ReportingService2010.GetProperties%2A> 메서드 및 <xref:ReportService2010.ItemNamespaceHeader> SOAP 헤더를 사용하여 항목의 경로나 ID를 기반으로 속성을 검색하는 방법을 설명합니다.|  
  
## <a name="see-also"></a>참고 항목  
 [웹 서비스와 .NET Framework를 사용하여 애플리케이션 빌드](../report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md)   
 [기술 참조&#40;SSRS&#41;](../technical-reference-ssrs.md)  
  
  
