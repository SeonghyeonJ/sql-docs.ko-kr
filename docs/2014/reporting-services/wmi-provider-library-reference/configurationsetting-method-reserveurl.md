---
title: ReserveURL 메서드(WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- ReservedURL method
ms.assetid: b9008a62-3edd-4f8a-99f2-7598c2133899
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: 2b771042ca00c9a9a80d7ffa035b100e2c4a6dc0
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/11/2019
ms.locfileid: "56020514"
---
# <a name="reserveurl-method-wmi-msreportserverconfigurationsetting"></a>ReserveURL 메서드(WMI MSReportServer_ConfigurationSetting)
  지정된 애플리케이션에 대한 URL 예약을 추가합니다.  
  
## <a name="syntax"></a>구문  
  
```vb  
Public Sub ReserveURL(Application as String, _  
    UrlString as String, Lcid as Int32, _   
    ByRef [Error] as String, ByRef HRESULT as Int32)  
```  
  
```csharp  
public void ReserveURL(string Application, string UrlString, int Lcid,   
    out string error, out int HRESULT);  
```  
  
## <a name="parameters"></a>매개 변수  
 *응용 프로그램*  
 URL을 예약할 애플리케이션의 이름입니다.  
  
 *URLString*  
 예약에 대한 URL입니다.  
  
 *lcid*  
 반환되는 오류 메시지에 사용할 로캘입니다.  
  
 *오류*  
 [out] 발생한 오류에 대한 설명입니다.  
  
 *HRESULT*  
 [out] 호출의 성공 여부를 나타내는 값입니다.  
  
## <a name="return-value"></a>반환 값  
 메서드 호출의 성공 또는 실패를 나타내는 *HRESULT* 를 반환합니다. 0 값은 메서드 호출이 성공했음을 나타내고 오류 코드는 호출이 실패했음을 나타냅니다.  
  
## <a name="remarks"></a>Remarks  
 *UrlString* 에는 가상 디렉터리 이름이 포함되지 않습니다. [SetVirtualDirectory](configurationsetting-method-setvirtualdirectory.md) 메서드를 사용하면 가상 디렉터리 이름을 포함할 수 있습니다.  
  
 현재 Windows 서비스 계정에 대한 URL 예약이 만들어집니다. Windows 서비스 계정을 변경하려면 모든 URL 예약을 수동으로 업데이트해야 합니다.  
  
 이 메서드를 사용하면 모든 애플리케이션 도메인이 하드 재활용됩니다. 이 작업이 완료된 후 애플리케이션 도메인을 다시 시작해야 합니다.  
  
## <a name="requirements"></a>요구 사항  
 **네임스페이스:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>관련 항목  
 [MSReportServer_ConfigurationSetting 멤버](msreportserver-configurationsetting-members.md)  
  
  
