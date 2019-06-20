---
title: RemoveURL 메서드(WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- RemoveURL method
ms.assetid: 3d98bd97-e152-48ce-ab1c-bd2c4f8b7fe9
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: bdd38b66a62b3d839f89f078904f7a3a9cc82d66
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66098167"
---
# <a name="removeurl-method-wmi-msreportserverconfigurationsetting"></a>RemoveURL 메서드(WMI MSReportServer_ConfigurationSetting)
  보고서 서버용으로 예약된 URL을 제거합니다. 제거할 URL이 여러 개인 경우 이 API를 호출하여 하나씩 수행해야 합니다.  
  
## <a name="syntax"></a>구문  
  
```vb  
Public Sub RemoveURL(ByVal Application As String, _  
    ByVal UrlString As String, ByVal Lcid As Int32, _  
    ByRef [Error] As String, ByRef HRESULT As Int32)  
```  
  
```csharp  
public void RemoveURL(string Application, string UrlString, int Lcid,   
    out string Error, out int HRESULT);  
```  
  
## <a name="parameters"></a>매개 변수  
 *응용 프로그램*  
 예약을 제거할 애플리케이션의 이름입니다.  
  
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
 *UrlString*에는 가상 디렉터리 이름이 포함되지 않습니다. 해당 용도로 [SetVirtualDirectory 메서드&#40;WMI MSReportServer_ConfigurationSetting&#41;](configurationsetting-method-setvirtualdirectory.md) 메서드가 제공됩니다.  
  
 [ReserveURL](configurationsetting-method-reserveurl.md) 메서드를 호출하기 전에 *Application* 매개 변수의 VirtualDirectory 구성 속성에 값을 제공해야 합니다. [SetVirtualDirectory 메서드&#40;WMI MSReportServer_ConfigurationSetting&#41;](configurationsetting-method-setvirtualdirectory.md) 메서드를 사용하여 VirtualDirectory 속성을 설정할 수 있습니다.  
  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 에서 제공한 SSL 인증서가 다른 URL에서 더 이상 사용되지 않을 경우 해당 인증서는 제거됩니다.  
  
 이 메서드를 사용하면 구성 응용 프로그램 도메인을 제외한 모든 응용 프로그램 도메인이 하드 재활용됩니다. 이 작업이 진행되는 동안 응용 프로그램 도메인이 중지되므로 이 작업이 완료되면 응용 프로그램 도메인을 다시 시작해야 합니다.  
  
## <a name="requirements"></a>요구 사항  
 **네임스페이스:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>관련 항목  
 [MSReportServer_ConfigurationSetting 멤버](msreportserver-configurationsetting-members.md)  
  
  
