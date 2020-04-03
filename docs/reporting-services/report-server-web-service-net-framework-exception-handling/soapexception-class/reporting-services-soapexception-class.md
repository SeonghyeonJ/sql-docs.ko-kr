---
title: Reporting Services SoapException 클래스 | Microsoft Docs
description: 발생 가능한 특정 Reporting Services SoapException 클래스 오류를 해결하는 방법을 알아봅니다.
ms.date: 03/16/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-server-web-service-net-framework-exception-handling
ms.topic: reference
helpviewer_keywords:
- exceptions [Reporting Services], SoapException class
- SoapException class
ms.assetid: 2cec49ee-20b1-40eb-a75b-0908d9c05b34
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 1e5dca57a7ccc4d3ca08f4b1c22e460747cc6d46
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/29/2020
ms.locfileid: "80215730"
---
# <a name="reporting-services-soapexception-class"></a>Reporting Services SoapException 클래스
  발생할 수 있다고 판단되는 특정 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 오류를 해결해야 합니다. 예를 들어, 사용자에게 폴더를 만들도록 요구하는 애플리케이션에서 사용자는 이미 존재하는 폴더를 만들려고 시도할 수 있습니다. 개발자는 사용자가 애플리케이션의 폴더 이름 및 경로 필드에 입력하는 내용을 제어하지 못하지만, 누군가가 실수로 이미 존재하는 항목을 만들려고 시도할 때 발생하는 사용자 경험은 제어할 수 있습니다.  
  
 특정 오류 조건을 쉽게 파악할 수 있도록 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]은 예외에 대한 오류 코드를 분류하고 **SoapException** 클래스의 속성을 사용하여 오류에 대한 분류를 반환합니다. 자세한 내용은 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] SDK 설명서의 “SoapException 클래스”를 참조하세요.  
  
 다음 표는 **SoapException** 클래스의 공용 속성을 나열합니다.  
  
|공용 속성|Description|  
|---------------------|-----------------|  
|**Actor**|예외를 발생시킨 코드입니다. 값은 웹 서비스 메서드에 대한 URL입니다.|  
|**Detail**|애플리케이션별 오류 정보입니다. 값은 보고서 서버에서 설정되며 XML 형식입니다. 자세한 내용은 참조 [Detail 속성](../../../reporting-services/report-server-web-service-net-framework-exception-handling/soapexception-class/detail-property.md) 및 [Detail 속성을 사용하여 특정 오류 처리](../../../reporting-services/report-server-web-service-net-framework-exception-handling/best-practices/using-the-detail-property-to-handle-specific-errors.md)를 참조하세요.|  
|**HelpLink**|오류와 연관된 도움말 파일에 대한 URL 또는 URN입니다. 일반적으로 웹 서비스에서 설정되는 이 값은 URL을 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] 도움말 및 지원으로 설정합니다. [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]는 발생하는 오류와 관련하여 여러 도움말 링크를 지원하므로 보고서 서버에서는 도움말 링크 정보를 **Detail** 속성의 일부로 설정합니다. 자세한 내용은 [HelpLink 요소](../../../reporting-services/report-server-web-service-net-framework-exception-handling/soapexception-class/helplink-element.md)를 참조하세요.|  
|**메시지**|오류를 설명하는 지역화된 메시지입니다. 이 텍스트는 애플리케이션 UI로 나타날 수 있습니다.|  
  
## <a name="see-also"></a>참고 항목  
 [Reporting Services의 예외 처리 소개](../../../reporting-services/report-server-web-service-net-framework-exception-handling/introducing-exception-handling-in-reporting-services.md)   
 [SoapException 오류 테이블](../../../reporting-services/report-server-web-service-net-framework-exception-handling/soapexception-class/soapexception-errors-table.md)  
  
  
