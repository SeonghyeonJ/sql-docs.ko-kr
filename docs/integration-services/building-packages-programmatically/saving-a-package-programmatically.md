---
title: 프로그래밍 방식으로 패키지 저장 | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- programmatically saving a package
- saving a package programmatically
ms.assetid: 4204f817-d5df-475a-9338-d7f01305d566
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 822f6a364b06c6e2a88c8880cbe97fe94dba510f
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47650921"
---
# <a name="saving-a-package-programmatically"></a>프로그래밍 방식으로 패키지 저장
  프로그래밍 방식으로 새 패키지를 작성하거나 기존 패키지를 수정한 후에는 일반적으로 변경 내용을 저장합니다.  
  
 이 항목에서 설명하는 패키지 저장 방법을 사용할 경우에는 항상 **Microsoft.SqlServer.ManagedDTS** 어셈블리에 대한 참조가 필요합니다. 새 프로젝트에 참조를 추가한 후 **using** 또는 **Imports** 문을 사용하여 <xref:Microsoft.SqlServer.Dts.Runtime> 네임스페이스를 가져옵니다.  
  
## <a name="saving-a-package-programmatically"></a>프로그래밍 방식으로 패키지 저장  
 프로그래밍 방식으로 패키지를 저장하려면 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] <xref:Microsoft.SqlServer.Dts.Runtime.Application> 클래스의 다음 메서드 중 하나를 호출합니다.  
  
|스토리지 위치|호출할 메서드|  
|----------------------|--------------------|  
|파일|<xref:Microsoft.SqlServer.Dts.Runtime.Application.SaveToXml%2A>|  
|SSIS 패키지 저장소|<xref:Microsoft.SqlServer.Dts.Runtime.Application.SaveToDtsServer%2A>|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|<xref:Microsoft.SqlServer.Dts.Runtime.Application.SaveToSqlServer%2A><br /><br /> 로 구분하거나 여러<br /><br /> <xref:Microsoft.SqlServer.Dts.Runtime.Application.SaveToSqlServerAs%2A>|  
  
> [!IMPORTANT]  
>  SSIS 패키지 저장소를 사용하기 위한 <xref:Microsoft.SqlServer.Dts.Runtime.Application> 클래스의 메서드는 "." 또는 로컬 서버의 서버 이름만 지원합니다. "(local)" 또는 "localhost"는 사용할 수 없습니다.  
  
## <a name="see-also"></a>참고 항목  
 [패키지 저장](../../integration-services/save-packages.md)  
  
  
