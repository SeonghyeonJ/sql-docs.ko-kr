---
title: TransactionLog 이벤트 클래스 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- TransactionLog event class
ms.assetid: bbcf09c6-3128-4775-b3de-e986a70411e0
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: d6b6fa07c2cb2f4880420885fefc30d0fd419c38
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2020
ms.locfileid: "63011992"
---
# <a name="transactionlog-event-class"></a>TransactionLog 이벤트 클래스
  TransactionLog 이벤트 클래스를 사용하여 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]인스턴스의 트랜잭션 로그에 있는 작업을 모니터링할 수 있습니다.  
  
## <a name="transactionlog-event-class-data-columns"></a>TransactionLog 이벤트 클래스 데이터 열  
  
|데이터 열 이름|데이터 형식|Description|열 ID|필터 가능|  
|----------------------|---------------|-----------------|---------------|----------------|  
|ApplicationName|`nvarchar`|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]인스턴스에 연결한 클라이언트 애플리케이션의 이름입니다. 이 열은 프로그램의 표시 이름이 아니라 애플리케이션에서 전달한 값으로 채워집니다.|10|yes|  
|BinaryData|`image`|추적에서 캡처된 이벤트 클래스에 의존하는 이진 값입니다.|2|yes|  
|ClientProcessID|`int`|클라이언트 애플리케이션이 실행 중인 프로세스에 대해 호스트 컴퓨터가 할당한 ID입니다. 클라이언트가 클라이언트 프로세스를 제공하면 이 데이터 열이 채워집니다.|9|yes|  
|DatabaseID|`int`|데이터가 로깅되는 데이터베이스의 ID 입니다.|3|yes|  
|DatabaseName|`nvarchar`|사용자 문이 실행되는 데이터베이스의 이름입니다.|35|yes|  
|EventClass|`int`|이벤트 유형 = 54|27|예|  
|EventSequence|`int`|요청 내에 지정된 이벤트 시퀀스입니다.|51|예|  
|EventSubClass|`int`|이벤트 하위 클래스의 유형입니다.|21|yes|  
|GroupID|`int`|SQL 추적 이벤트가 발생한 작업 그룹의 ID입니다.|66|yes|  
|HostName|`nvarchar`|클라이언트를 실행 중인 컴퓨터 이름입니다. 클라이언트가 호스트 이름을 제공할 경우 이 데이터 열이 채워집니다. 호스트 이름을 확인하려면 HOST_NAME 함수를 사용합니다.|8|yes|  
|IndexID|`int`|이벤트에 의해 영향 받는 개체의 인덱스 ID입니다. 개체의 인덱스 ID를 확인하려면 sys.indexes 카탈로그 뷰의 index_id 열을 사용합니다.|24|yes|  
|IntegerData|`int`|추적에서 캡처된 이벤트 클래스에 의존하는 정수 값입니다.|25|yes|  
|IsSystem|`int`|이벤트가 시스템 프로세스에서 발생했는지 아니면 사용자 프로세스에서 발생했는지를 나타냅니다. 1 = 시스템, 0 = 사용자|60|yes|  
|LoginName|`nvarchar`|사용자 로그인 이름이며 DOMAIN\username 형식의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Windows 로그인 자격 증명 또는 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 보안 로그인입니다.|11|yes|  
|LoginSid|`image`|로그인한 사용자의 SID(보안 ID)입니다. 이 정보는 sys.server_principals 카탈로그 뷰에 있습니다. 각 SID는 서버의 각 로그인마다 고유합니다.|41|yes|  
|NTDomainName|`nvarchar`|사용자가 속한 Windows 도메인입니다.|7|yes|  
|NTUserName|`nvarchar`|Windows 사용자 이름입니다.|6|yes|  
|ObjectID|`int`|시스템이 할당한 개체의 ID입니다.|22|yes|  
|RequestID|`int`|문을 포함하는 요청의 ID입니다.|49|yes|  
|ServerName|`nvarchar`|추적 중인 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스의 이름입니다.|26|예|  
|SessionLoginName|`nvarchar`|세션을 시작한 사용자의 로그인 이름입니다. 예를 들어 Login1을 사용하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에 연결하고 Login2로 문을 실행할 경우 SessionLoginName은 Login1을 표시하고 LoginName은 Login2를 표시합니다. 이 열은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 및 Windows 로그인을 모두 표시합니다.|64|yes|  
|SPID|`int`|이벤트가 발생한 세션의 ID입니다.|12|yes|  
|StartTime|`datetime`|이벤트가 시작된 시간입니다(사용 가능한 경우).|14|yes|  
|TransactionID|`bigint`|시스템이 할당한 트랜잭션의 ID입니다.|4|yes|  
  
## <a name="see-also"></a>참고 항목  
 [sp_trace_setevent&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql)   
 [트랜잭션 로그&#40;SQL Server&#41;](../logs/the-transaction-log-sql-server.md)  
  
  
