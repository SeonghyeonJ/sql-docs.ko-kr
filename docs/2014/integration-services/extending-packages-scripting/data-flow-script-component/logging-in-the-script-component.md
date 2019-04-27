---
title: 스크립트 구성 요소의 로깅 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- Script component [Integration Services], logging
ms.assetid: 17c19787-379e-43fe-9107-e36e17ecda53
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: c4723c0e78b37142d7f0a2ccdc16e37ce0fb78fe
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62768429"
---
# <a name="logging-in-the-script-component"></a>스크립트 구성 요소의 로깅
  [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 패키지의 로깅 기능을 사용하면 나중에 분석할 수 있도록 미리 정의된 이벤트나 사용자 정의 메시지를 기록하여 실행 진행률, 결과 및 문제에 대한 세부 정보를 저장할 수 있습니다. 스크립트 구성 요소에서는 `ScriptMain` 클래스의 <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.Log%2A> 메서드를 사용하여 사용자 정의 데이터를 로깅할 수 있습니다. 로깅을 사용하도록 설정하고 **SSIS 로그 구성** 대화 상자의 **자세히** 탭에서 **ScriptComponentLogEntry** 이벤트를 로깅하도록 선택할 경우 <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.Log%2A> 메서드를 한 번만 호출하면 데이터 흐름 태스크에 대해 구성된 모든 로그 공급자에 해당 이벤트 정보가 저장됩니다.  
  
 다음은 간단한 로깅 예입니다.  
  
 `Dim bt(0) As Byte`  
  
 `Me.Log("Test Log Event", _`  
  
 `0, _`  
  
 `bt)`  
  
> [!NOTE]  
>  스크립트 구성 요소에서 직접 로깅을 수행할 수도 있지만 로깅보다는 이벤트를 구현하는 것이 좋습니다. 이벤트를 사용하면 이벤트 메시지의 로깅 기능을 사용할 수 있을 뿐 아니라 기본 또는 사용자 정의 이벤트 처리기를 사용하여 이벤트에 응답할 수도 있습니다.  
  
 로깅에 대한 자세한 내용은 [Integration Services&#40;SSIS&#41; 로깅](../../performance/integration-services-ssis-logging.md)를 참조하세요.  
  
![Integration Services 아이콘 (작은)](../../media/dts-16.gif "Integration Services 아이콘 (작은)")**Integration Services를 사용 하 여 날짜를 알림 설정**<br /> Microsoft의 최신 다운로드, 문서, 예제 및 비디오와 커뮤니티에서 선택된 솔루션을 보려면 MSDN의 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 페이지를 방문하세요.<br /><br /> [MSDN의 Integration Services 페이지 방문](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> 이러한 업데이트에 대한 자동 알림을 받으려면 해당 페이지에서 제공하는 RSS 피드를 구독하세요.  
  
## <a name="see-also"></a>관련 항목  
 [Integration Services&#40;SSIS&#41; 로깅](../../performance/integration-services-ssis-logging.md)  
  
  
