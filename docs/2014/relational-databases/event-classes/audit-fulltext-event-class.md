---
title: Audit Fulltext 이벤트 클래스 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
ms.assetid: 95e4c5fd-e16f-446e-b42b-105495a8f39a
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 1ad7019b30555077d274af62156115cfb71944fc
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2020
ms.locfileid: "62938641"
---
# <a name="audit-fulltext-event-class"></a>Audit Fulltext 이벤트 클래스
  **Audit Fulltext** 이벤트 클래스는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 가 전체 텍스트 필터 데몬 프로세스에 연결되어 통신할 때 발생합니다.  
  
## <a name="audit-fulltext-event-class-data-columns"></a>Audit Fulltext 이벤트 클래스 데이터 열  
  
|데이터 열 이름|데이터 형식|Description|열 ID|필터 가능|  
|----------------------|---------------|-----------------|---------------|----------------|  
|**오류**|**int**|이 이벤트에서 오류를 보고하는 경우 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 오류 번호입니다.|31|yes|  
|**EventSequence**|**int**|요청 내의 지정된 이벤트 시퀀스입니다.|51|예|  
|**EventSubClass**|**int**|로그인에 사용된 연결의 유형입니다. 1 = 풀링 안 됨, 2 = 풀링됨|21|yes|  
|**IsSystem**|**int**|이벤트가 시스템 프로세스에서 발생했는지 아니면 사용자 프로세스에서 발생했는지를 나타냅니다. 1 = 시스템, 0 = 사용자|60|yes|  
|**SessionLoginName**|**nvarchar**|세션을 시작한 사용자의 로그인 이름입니다. 예를 들어 Login1을 사용하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에 연결하고 Login2로 문을 실행할 경우 **SessionLoginName** 은 Login1을 표시하고 **LoginName** 은 Login2를 표시합니다. 이 열은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 및 Windows 로그인을 모두 표시합니다.|64|yes|  
|**SPID**|**int**|이벤트가 발생한 세션의 ID입니다.|12|yes|  
|**StartTime**|**datetime**|이벤트가 시작된 시간입니다(사용 가능한 경우).|14|yes|  
|**Success**|**int**|1 = 성공, 0 = 실패. 예를 들어 값 1은 사용 권한 확인이 성공했음을 나타내고, 값 0은 확인이 실패했음을 나타냅니다.|23|yes|  
|**TargetLoginName**|**int**|로그인을 대상으로 하는 동작(예: 새 로그인 추가)의 경우 대상 로그인의 이름입니다.|42|yes|  
|**TargetLoginSid**|**int**|로그인을 대상으로 하는 동작(예: 새 로그인 추가)의 경우 대상 로그인의 SID(보안 ID)입니다.|43|yes|  
|**TextData**|**ntext**|전체 텍스트 이벤트에 대한 텍스트 정보입니다. 일반적으로 이 필드에는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 프로세스와 전체 텍스트 필터 데몬 프로세스간 연결에 대한 정보가 표시됩니다.|1|yes|  
  
## <a name="see-also"></a>참고 항목  
 [확장 이벤트](../extended-events/extended-events.md)   
 [sp_trace_setevent&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql)  
  
  
