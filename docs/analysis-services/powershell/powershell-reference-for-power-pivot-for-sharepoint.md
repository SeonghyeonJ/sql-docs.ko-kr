---
title: 분석에 대 한 PowerShell 참조 SharePoint 용 파워 피벗 서비스 | Microsoft Docs
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: powershell
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 9228eb879ed1417b31c95d53783d32acf53bcdb4
ms.sourcegitcommit: 8a64c59c5d84150659a015e54f8937673cab87a0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/08/2018
ms.locfileid: "53072410"
---
# <a name="powershell-reference-for-power-pivot-for-sharepoint"></a>SharePoint용 Power Pivot에 대한 PowerShell 참조
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  이 섹션에는 [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] 설치를 구성하거나 관리하는 데 사용하는 PowerShell cmdlet이 나열되어 있습니다. cmdlet 사용 및 기본 제공 도움말 보기에 대한 자세한 내용은 [Windows PowerShell을 사용하여 파워 피벗 구성](../../analysis-services/power-pivot-sharepoint/power-pivot-configuration-using-windows-powershell.md)을 참조하세요.  

>[!NOTE] 
>이 문서는 오래 된 정보 및 예제에 포함할 수 있습니다. 최신 Get-help cmdlet을 사용 합니다.
  
## <a name="cmdlet-list"></a>Cmdlet 목록  
 PowerShell 프롬프트에서 cmdlet의 목록을 보려면:  
  
1.  **관리자 권한으로 실행** 옵션을 사용하여 SharePoint 관리 셸을 엽니다.  
  
2.  다음 명령을 입력합니다. `Get-help *powerpivot*`  
  
|Cmdlet|Supported Versions|  
|------------|------------------------|  
|[Get-PowerPivotServiceApplication cmdlet](../../analysis-services/powershell/get-powerpivotserviceapplication-cmdlet.md)|SharePoint 2013 &#124; SharePoint 2016|  
|[Get-PowerPivotSystemService cmdlet](../../analysis-services/powershell/get-powerpivotsystemservice-cmdlet.md)|SharePoint 2013 &#124; SharePoint 2016|  
|[Get-PowerPivotSystemServiceInstance cmdlet](../../analysis-services/powershell/get-powerpivotsystemserviceinstance-cmdlet.md)|SharePoint 2013 &#124; SharePoint 2016|  
|[New-PowerPivotServiceApplication cmdlet](../../analysis-services/powershell/new-powerpivotserviceapplication-cmdlet.md)|SharePoint 2013 &#124; SharePoint 2016|  
|[New-PowerPivotSystemServiceInstance cmdlet](../../analysis-services/powershell/new-powerpivotsystemserviceinstance-cmdlet.md)|SharePoint 2013 &#124; SharePoint 2016|  
|[Remove-PowerPivotServiceApplication cmdlet](../../analysis-services/powershell/remove-powerpivotserviceapplication-cmdlet.md)|SharePoint 2013 &#124; SharePoint 2016|  
|[Remove-PowerPivotSystemServiceInstance cmdlet](../../analysis-services/powershell/remove-powerpivotsystemserviceinstance-cmdlet.md)|SharePoint 2013 &#124; SharePoint 2016|  
|[Set-PowerPivotServiceApplication cmdlet](../../analysis-services/powershell/set-powerpivotserviceapplication-cmdlet.md)|SharePoint 2013 &#124; SharePoint 2016|  
|[Set-PowerPivotSystemService cmdlet](../../analysis-services/powershell/set-powerpivotsystemservice-cmdlet.md)|SharePoint 2013 &#124; SharePoint 2016|  
|[Update-PowerPivotSystemService cmdlet](../../analysis-services/powershell/update-powerpivotsystemservice-cmdlet.md)|SharePoint 2013 &#124; SharePoint 2016|  
  
 참고: 다음 Cmdlet은 SharePoint 2010 으로만 작동 하는 [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] 지원 하지 않습니다.  
  
-   Get-PowerPivotEngineService  
  
-   Get-PowerPivotEngineServiceInstance  
  
-   New-PowerPivotEngineServiceInstance  
  
-   Remove-PowerPivotEngineServiceInstance  
  
-   Set-PowerPivotEngineService  
  
-   Set-PowerPivotEngineServiceInstance  
  
-   Update-PowerPivotEngineService  
  
  
