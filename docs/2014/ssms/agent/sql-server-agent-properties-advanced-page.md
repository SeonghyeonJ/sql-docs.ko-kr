---
title: SQL Server 에이전트 속성(고급 페이지) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.ag.agent.advanced.f1
ms.assetid: a4d798ee-4c18-40d4-b6af-63d17503738c
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: aeb0c6c47a9203a7124fbe5d9f4739c52ae430d1
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63246237"
---
# <a name="sql-server-agent-properties-advanced-page"></a>SQL Server 에이전트 속성(고급 페이지)
  이 페이지를 사용하여 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 서비스의 고급 속성을 확인하고 수정할 수 있습니다.  
  
## <a name="options"></a>변수  
 **SQL Server 이벤트 전달**  
 이 범주의 옵션은 이벤트 전달을 활성화하고 구성합니다.  
  
 **다른 서버로 이벤트 전달**  
 다른 서버로 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 이벤트를 전달합니다.  
  
 **Server**  
 이벤트가 전달될 서버 이름을 선택합니다.  
  
 **처리되지 않은 이벤트**  
 지정한 서버로 처리되지 않은 이벤트만 전달합니다. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트에서는 응답하는 경고가 없는 이벤트만 전달합니다.  
  
 **모든 이벤트**  
 모든 이벤트를 전달합니다. 로컬 인스턴스의 경고가 이벤트에 응답하면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트에서는 이벤트를 전달할 뿐 아니라 경고를 처리합니다.  
  
 **이벤트의 심각도가 다음 이상인 경우**  
 심각도가 지정한 수준 이상인 이벤트만 전달합니다.  
  
 **CPU 유휴 상태 판단 기준**  
 이 범주의 옵션은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트에서 CPU 유휴 일정에 실행하도록 예약된 작업을 실행하는 기준을 정의합니다.  
  
 **CPU 유휴 상태 판단 기준 정의**  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트에서 CPU가 유휴 상태인 것으로 간주하는 기준을 정의합니다.  
  
 **평균 CPU 사용량이 다음 미만인 경우**  
 미만인 경우 CPU가 유휴 상태인 것으로 간주하는 CPU 사용량의 비율입니다.  
  
 **다음 시간 미만인 경우**  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트에서 CPU 유휴 일정에 작업을 실행하기 전에 평균 CPU가 지정한 수준 미만이어야 하는 시간입니다.  
  
## <a name="see-also"></a>관련 항목  
 [만들기 및 작업에 일정 연결](create-and-attach-schedules-to-jobs.md)   
 [이벤트 관리](manage-events.md)  
  
  
