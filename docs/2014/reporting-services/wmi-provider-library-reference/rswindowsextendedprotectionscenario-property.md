---
title: RSWindowsExtendedProtectionScenario 속성 (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
ms.assetid: 5ac7ab80-9adf-4f65-abfa-fedf53b082b5
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 122ecf44095611d25065401972b8ccfefdae5fb8
ms.sourcegitcommit: 1ab115a906117966c07d89cc2becb1bf690e8c78
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/27/2018
ms.locfileid: "52394719"
---
# <a name="rswindowsextendedprotectionscenario-property-wmi-msreportserverconfigurationsetting"></a>RSWindowsExtendedProtectionScenario 속성(WMI MSReportServer_ConfigurationSetting)
  보고서 서버에서 허용하도록 구성된 확장된 보호 시나리오를 나타내는 문자열 값을 반환합니다.  
  
## <a name="syntax"></a>구문  
  
```vb  
Public Dim RSWindowsExtendedProtectionScenario As String  
```  
  
```csharp  
public string RSWindowsExtendedProtectionScenario;  
```  
  
## <a name="remarks"></a>Remarks  
 보고서 서버에서 허용하도록 구성된 확장된 보호 시나리오를 나타내는 문자열 값을 반환합니다. WMI 공급자가 연결되어 있는 보고서 서버에서 확장된 보호를 지원하지 않으면 ""(빈 문자열)이 반환됩니다.  
  
 다음 목록에서는 유효한 값을 보여 줍니다.  
  
 `"Any | Proxy | Direct"`  
  
## <a name="example-code"></a>코드 예  
 [MSReportServer_ConfigurationSetting 클래스](msreportserver-configurationsetting-class.md)  
  
## <a name="see-also"></a>관련 항목:  
 [RSWindowsExtendedProtectionLevel 속성&#40;WMI MSReportServer_ConfigurationSetting&#41;](rswindowsextendedprotectionlevel-property.md)   
 [SetExtendedProtectionSettings 메서드&#40;WMI MSReportServer_ConfigurationSetting&#41;](configurationsetting-method-setextendedprotectionsettings.md)   
 [Reporting Services 인증에 대한 확장된 보호](../security/extended-protection-for-authentication-with-reporting-services.md)   
 [RSReportServer 구성 파일](../report-server/rsreportserver-config-configuration-file.md)  
  
  
