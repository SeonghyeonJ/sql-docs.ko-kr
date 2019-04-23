---
title: GetDatabaseVersionDisplayName 메서드(WMI) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- GetDatabaseVersionDisplayName method
ms.assetid: e1286424-7043-4f12-a7ad-1cf69e81baa4
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 05f7e8818f5300ee1c7e391ad1345b696eb08154
ms.sourcegitcommit: 8d6fb6bbe3491925909b83103c409effa006df88
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/22/2019
ms.locfileid: "59933479"
---
# <a name="getdatabaseversiondisplayname-method-wmi"></a>GetDatabaseVersionDisplayName 메서드(WMI)
  지정된 보고서 서버 데이터베이스 버전 문자열의 표시 이름을 가져옵니다.  
  
## <a name="syntax"></a>구문  
  
```vb  
Public Sub GetDatabaseVersionDisplayName(Version As String, DisplayName As String, ByRef HRESULT As Int32)  
```  
  
```csharp  
public void GetDatabaseVersionDisplayName(string Version, string DisplayName, out Int32 HRESULT);  
```  
  
## <a name="parameters"></a>매개 변수  
 *버전*  
 보고서 서버 데이터베이스의 버전 문자열이 들어 있는 문자열입니다.  
  
 *DisplayName*  
 [out] 제공된 버전에 해당하는 표시 이름이 들어 있는 문자열입니다.  
  
 *HRESULT*  
 [out] 호출의 성공 여부를 나타내는 값입니다.  
  
## <a name="remarks"></a>Remarks  
 다음 표에서는 표시 문자열에 대한 데이터베이스 버전의 매핑을 보여 줍니다.  
  
|**릴리스**|`Version`|**표시 이름**|  
|-----------------|-----------------|----------------------|  
|RS 2005 SP2|@DBVersion = 'C.0.8.54'|SQL Server 2005 SP2|  
|RS 2005 SP1|@DBVersion = 'C.0.8.43'|SQL Server 2005 SP1|  
|RS 2005 RTM|@DBVersion = 'C.0.8.40'|SQL Server 2005|  
|RS 2000 SP2|@DBVersion = 'C.0.6.54'|SQL Server 2000 SP2|  
|RS 2000 SP1|@DBVersion = 'C.0.6.51'|SQL Server 2000 SP1|  
|RS 2000 RTM|@DBVersion = 'C.0.6.43'|SQL Server 2000|  
|핫픽스||적용 가능한 가장 가까운 버전|  
  
 *2000 이전* 버전 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 의 경우 ACT_E_BAD_VERSION의 HRESULT가 반환됩니다.  
  
## <a name="return-value"></a>반환 값  
 메서드 호출의 성공 또는 실패를 나타내는 *HRESULT* 를 반환합니다. 0 값은 메서드 호출이 성공했음을 나타냅니다. 0 이외의 값은 오류가 발생했음을 나타냅니다.  
  
## <a name="requirements"></a>요구 사항  
 **네임스페이스:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>관련 항목  
 [MSReportServer_ConfigurationSetting 멤버](msreportserver-configurationsetting-members.md)  
  
  
