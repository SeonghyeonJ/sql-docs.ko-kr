---
title: MSOLAP.5를 Excel Services에서 신뢰할 수 있는 데이터 공급자로 추가 | Microsoft Docs
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: ppvt-sharepoint
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: d7576aadda3739709acdffcb1b2419c20d39ed4e
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/15/2019
ms.locfileid: "68164452"
---
# <a name="add-msolap5-as-a-trusted-data-provider-in-excel-services"></a>MSOLAP.5를 Excel 서비스에서 신뢰할 수 있는 데이터 공급자로 추가
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  MSOLAP.5는 SQL Server 2012용 Analysis Services OLE DB 공급자를 나타냅니다. Excel Services는 이 공급자를 신뢰해야 서버에서 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 데이터를 사용하는 연결 요청을 수행할 수 있습니다.  
  
 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 구성 도구를 사용하여 SharePoint용 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 을 구성한 경우 이 도구에는 이 요구 사항을 만족시키는 동작이 포함되어 있으므로 MSOLAP.5는 이미 신뢰할 수 있는 공급자일 수 있습니다. 그러나 PowerShell 또는 중앙 관리를 사용하거나 구성 도구에서 신뢰할 수 있는 공급자 동작을 제외한 경우에는 공급자가 누락될 수 있으며 이 경우에는 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 데이터 액세스용 팜을 구성하는 작업의 일부로 지금 이 공급자를 추가해야 합니다.  
  
 각 Excel Services 서비스 애플리케이션에 대해 한 번씩 이 단계를 수행해야 합니다.  
  
 SharePoint용 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 서버나 Excel Services 서버처럼 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 데이터 요청을 처리하는 각 실제 서버의 컴퓨터에는 OLE DB 공급자가 설치되어 있어야 합니다. SharePoint용 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 설치에는 항상 OLE DB 공급자가 포함되지만 Excel Services가 실행되는 컴퓨터에 SharePoint용 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 이 없으면 공급자를 수동으로 설치해야 합니다. 자세한 내용은 [SharePoint 서버에서 Analysis Services OLE DB 공급자 설치](http://msdn.microsoft.com/2c62daf9-1f2d-4508-a497-af62360ee859)를 참조하세요.  
  
## <a name="add-a-trusted-provider-to-excel-services"></a>Excel 서비스에 신뢰할 수 있는 공급자 추가  
  
1.  중앙 관리에서 **서비스 애플리케이션 관리**를 클릭한 다음 Excel 서비스 애플리케이션을 클릭합니다.  
  
2.  **신뢰할 수 있는 데이터 공급자**를 클릭합니다.  
  
3.  MSOLAP.5가 목록에 있는지 확인합니다. SharePoint용 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 을 구성한 방법에 따라 MSOLAP.5가 이미 신뢰할 수 있는 공급자일 수도 있습니다.  
  
4.  목록에 없으면 **신뢰할 수 있는 데이터 공급자 추가**를 클릭합니다.  
  
5.  공급자 ID에 **MSOLAP.5**를 입력합니다.  
  
6.  공급자 유형에서 OLE DB가 선택되어 있는지 확인합니다.  
  
7.  공급자 설명에서 **Microsoft OLE DB Provider for OLAP Services 11.0**을 입력합니다.  
  
  
