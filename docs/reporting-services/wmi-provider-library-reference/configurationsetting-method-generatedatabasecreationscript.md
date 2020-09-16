---
description: ConfigurationSetting 메서드 - GenerateDatabaseCreationScript
title: ConfigurationSetting 메서드 - GenerateDatabaseCreationScript | Microsoft Docs
ms.date: 03/14/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: wmi-provider-library-reference
ms.topic: conceptual
apiname:
- GenerateDatabaseCreationScript (WMI MSReportServer_ConfigurationSetting Class)
apilocation:
- reportingservices.mof
apitype: MOFDef
helpviewer_keywords:
- GenerateDatabaseCreationScript method
ms.assetid: 25232dc7-00fe-4cd1-8a1c-7e36d552de00
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 7d827c26e316280c1946f90bc35d69427fc672df
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88454515"
---
# <a name="configurationsetting-method---generatedatabasecreationscript"></a>ConfigurationSetting 메서드 - GenerateDatabaseCreationScript
  보고서 서버 데이터베이스를 만드는 데 사용할 수 있는 SQL 스크립트를 생성합니다.  
  
## <a name="syntax"></a>구문  
  
```vb  
Public Sub GenerateDatabaseCreationScript(ByVal DatabaseName As String, _  
    ByVal Lcid As Int32, ByVal IsSharePointMode As Boolean, ByRef Script As String, _  
    ByRef HRESULT As Int32)  
```  
  
```csharp  
public void GenerateDatabaseCreationScript(string DatabaseName, Int32 Lcid,   
    Boolean IsSharePointMode, out string Script, out Int32 HRESULT);  
```  
  
## <a name="parameters"></a>매개 변수  
 *Databasename*  
 만들 보고서 서버 데이터베이스의 이름이 들어 있는 문자열입니다.  
  
 *Lcid*  
 역할 이름을 지역화하는 데 사용되는 값입니다.  
  
 *IsSharePointMode*  
 데이터베이스를 기본 모드로 만들지, 아니면 SharePoint 모드로 만들지를 나타냅니다.  
  
> [!IMPORTANT]  
>  SharePoint 모드에서는 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]가 SharePoint 공유 서비스이며 WMI 공급자를 통해 제어되지 않으므로 *부터는*=**IsSharePointMode** True [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 가 지원되지 않습니다. 항상 이 매개 변수를 **False**로 설정해야 합니다.  
  
 *스크립트*  
 [out] 생성된 SQL 스크립트가 들어 있는 문자열입니다.  
  
 *HRESULT*  
 [out] 호출의 성공 여부를 나타내는 값입니다.  
  
## <a name="return-value"></a>Return Value  
 메서드 호출의 성공 또는 실패를 나타내는 *HRESULT* 를 반환합니다. 0 값은 메서드 호출이 성공했음을 나타냅니다. 0 이외의 값은 오류가 발생했음을 나타냅니다.  
  
## <a name="remarks"></a>설명  
 이 메서드는 현재 연결되어 있는 보고서 서버 버전에 대한 보고서 서버 데이터베이스를 만드는 SQL 스크립트를 생성합니다.  
  
 *DatabaseName* 매개 변수에 제공되는 값은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터베이스 명명 규칙을 따라야 합니다.  
  
 이 메서드는 스크립트를 생성할 때 데이터베이스가 있는지 확인하지 않습니다.  
  
 이 메서드는 스크립트를 생성할 때 보고서 서버 데이터베이스가 있는지 확인하지 않습니다.  
  
 생성된 스크립트는 [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)], [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2005 및 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]을(를) 지원합니다.  
  
## <a name="requirements"></a>요구 사항  
 **네임스페이스:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>참고 항목  
 [MSReportServer_ConfigurationSetting 멤버](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-members.md)  
  
  
