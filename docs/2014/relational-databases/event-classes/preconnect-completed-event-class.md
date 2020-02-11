---
title: PreConnect:Completed 이벤트 클래스 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- PreConnect:Completed Event Class
ms.assetid: 7ed2f620-6511-4985-9961-d2927c2b1759
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: eaad0a80fd77257c6e79e092733d75c0c8df5df5
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2020
ms.locfileid: "62827084"
---
# <a name="preconnectcompleted-event-class"></a>PreConnect:Completed 이벤트 클래스
  PreConnect:Completed 이벤트 클래스는 LOGON 트리거나 리소스 관리자 분류자 함수가 언제 실행을 종료하는지 표시합니다.  
  
## <a name="preconnectcompleted-event-class-data-columns"></a>PreConnect:Completed 이벤트 클래스 데이터 열  
  
|데이터 열 이름|데이터 형식|Description|열 ID|필터 가능|  
|----------------------|---------------|-----------------|---------------|----------------|  
|EventClass|`int`|216|27|예|  
|SPID|`int`|이 이벤트를 발생시키는 서버 프로세스의 ID입니다.|12|yes|  
|EventSubClass|`int`|사용자 정의 분류자 함수의 경우 1입니다.|21|yes|  
|StartTime|`datetime`|사용자 정의 분류자 함수가 시작되는 시간입니다.|14|yes|  
|EndTime|`datetime`|사용자 정의 분류자 함수가 시작되는 시간입니다.|15|yes|  
|Duration|`bigint`|분류자 함수에 의해 사용된 시간(마이크로초)입니다.|13|yes|  
|ObjectID|`int`|사용자 정의 분류자 개체의 ID입니다.|22|yes|  
|CPU|`int`|CPU 사용량(밀리초)입니다.|18|yes|  
|읽기|`int`|논리적 읽기 수입니다.|16|yes|  
|쓰기|`int`|논리적 쓰기 수입니다.|17|yes|  
|GroupID|`int`|분류된 작업 그룹의 ID입니다.|66|yes|  
|Error|`int`|사용자 정의 분류자 함수를 실행하지 못할 경우 마지막 오류 번호입니다.|31|yes|  
|시스템 상태|`int`|마지막 오류의 상태입니다.|30|yes|  
|TargetUserName|`sysname`|시스템에서 해당 활성 그룹을 찾을 수 없는 경우 사용자 정의 분류자 함수의 반환 값(작업 그룹 이름)입니다. 그렇지 않으면 이 열은 NULL로 설정됩니다.|39|yes|  
|ObjectName|`nvarchar(256)`|분류자 사용자 정의 함수의 두 부분으로 이루어진 이름입니다(예: dbo.classifier).|34|yes|  
  
## <a name="see-also"></a>참고 항목  
 [확장 이벤트](../extended-events/extended-events.md)   
 [PreConnect: Starting 이벤트 클래스](preconnect-starting-event-class.md)   
 [리소스 관리자](../resource-governor/resource-governor.md)  
  
  
