---
title: IsSharePointIntegrated 속성(WMI) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- IsSharePointIntegrated property
ms.assetid: c548fed8-5e04-4faf-8b10-b37c86178056
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: a8f996b0f4a2f7b29647195f64dad3c7558f4d4c
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/26/2020
ms.locfileid: "66097669"
---
# <a name="issharepointintegrated-property-wmi"></a>IsSharePointIntegrated 속성(WMI)
  보고서 서버가 SharePoint 통합 모드에 있는지 여부를 지정합니다. SharePoint 모드에서는 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 인스턴스가 SharePoint 공유 서비스이며 WMI 공급자를 통해 제어되지 않으므로 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]부터는 이 속성이 항상 `False`를 반환합니다.  
  
## <a name="syntax"></a>구문  
  
```vb  
Public Dim IsSharePointIntegrated As Boolean  
```  
  
```csharp  
public Boolean IsSharePointIntegrated;  
```  
  
## <a name="property-values"></a>속성 값  
 보고서 서버가 SharePoint 통합 모드에 있는지 여부를 나타내는 `Boolean` 개체입니다.  
  
## <a name="example-code"></a>코드 예  
 [MSReportServer_ConfigurationSetting 클래스](msreportserver-configurationsetting-class.md)  
  
## <a name="requirements"></a>요구 사항  
 **네임스페이스:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>참고 항목  
 [MSReportServer_ConfigurationSetting 멤버](msreportserver-configurationsetting-members.md)  
  
  
