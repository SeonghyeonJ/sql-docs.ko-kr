---
title: LOGON 트리거 이벤트 데이터 캡처 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
ms.assetid: e05b1ab4-c10b-402a-9591-f6ec1e3db8c0
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: e9ee204d55114b7e31a9a9550d86cae3baa4dffc
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63130363"
---
# <a name="capture-logon-trigger-event-data"></a>LOGON 트리거 이벤트 데이터 캡처
  LOGON 트리거 내에서 사용할 LOGON 이벤트에 대한 XML 데이터를 캡처하려면 [EVENTDATA](/sql/t-sql/functions/eventdata-transact-sql) 함수를 사용합니다. LOGON 이벤트는 다음 이벤트 데이터 스키마를 반환합니다.  
  
 `<EVENT_INSTANCE>`  
  
 `<EventType>event_type</EventType>`  
  
 `<PostTime>post_time</PostTime>`  
  
 `<SPID>spid</SPID>`  
  
 `<ServerName>server_name</ServerName>`  
  
 `<LoginName>login_name</LoginName>`  
  
 `<LoginType>login_type</LoginType>`  
  
 `<SID>sid</SID>`  
  
 `<ClientHost>client_host</ClientHost>`  
  
 `<IsPooled>is_pooled</IsPooled>`  
  
 `</EVENT_INSTANCE>`  
  
 `<EventType>`  
 `LOGON`을 포함합니다.  
  
 `<PostTime>`  
 세션 설정이 요청된 시간을 포함합니다.  
  
 `<SID>`  
 지정된 로그인 이름에 대한 SID(보안 ID)의 base 64로 인코딩된 이진 스트림을 포함합니다.  
  
 `<ClientHost>`  
 연결을 설정할 클라이언트의 호스트 이름을 포함합니다. 클라이언트 이름과 서버 이름이 같을 경우 이 값은 '`<local_machine>`'입니다. 그렇지 않으면 값은 클라이언트의 IP 주소입니다.  
  
 `<IsPooled>`  
 연결 풀링을 사용하여 연결이 다시 사용될 경우 `1` 입니다. 그렇지 않으면 값은 `0`입니다.  
  
  
