---
title: 데이터베이스 미러링 중에 발생 가능한 오류 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- time-out period [SQL Server database mirroring]
- soft errors [SQL Server]
- database mirroring [SQL Server], troubleshooting
- timeout errors [SQL Server]
- troubleshooting [SQL Server], database mirroring
- hard errors
- failed database mirroring sessions [SQL Server]
ms.assetid: d7031f58-5f49-4e6d-9a62-9b420f2bb17e
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: a380b3c4f27df6ad9d60fc27f14a4f5072c676a0
ms.sourcegitcommit: f76b4e96c03ce78d94520e898faa9170463fdf4f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70874506"
---
# <a name="possible-failures-during-database-mirroring"></a>Possible Failures During Database Mirroring
  물리적, 운영 체제 또는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 문제로 인해 데이터베이스 미러링 세션에서 오류가 발생할 수 있습니다. 데이터베이스 미러링은 Sqlservr.exe에서 사용하는 구성 요소를 정기적으로 검사하여 구성 요소가 올바르게 작동하는지, 아니면 실패했는지를 확인하지 않습니다. 하지만 일부 오류 유형의 경우 영향을 받는 구성 요소가 Sqlservr.exe에 오류를 보고합니다. 다른 구성 요소에서 보고된 오류를 *하드 오류*라고 합니다. 확인되지 않는 다른 오류를 감지하기 위해 데이터베이스 미러링은 자체적으로 제한 시간 메커니즘을 구현합니다. 미러링 제한 시간이 발생하면 데이터베이스 미러링은 오류가 발생했다고 가정하고 *소프트 오류*를 선언합니다. 하지만 SQL Server 인스턴스 수준에서 발생하는 일부 오류는 미러링 제한 시간을 일으키지 않으며, 발견되지 않은 상태로 진행될 수 있습니다.  
  
> [!IMPORTANT]  
>  미러된 데이터베이스가 아닌 다른 데이터베이스의 오류는 데이터베이스 미러링 세션에서 감지되지 않습니다. 또한 데이터베이스가 데이터 디스크 오류로 인해 다시 시작되지 않는 한 데이터 디스크 오류도 감지되지 않습니다.  
  
 오류 감지 속도 그리고 이에 따른 미러링 세션의 오류 반응 속도는 오류가 하드 오류인지 소프트 오류인지에 따라 달라집니다. 네트워크 오류와 같은 일부 하드 오류는 즉시 보고되지만 경우에 따라 구성 요소별 제한 시간으로 인해 일부 하드 오류 보고가 지연될 수 있습니다. 소프트 오류의 경우 미러링 제한 시간의 길이가 오류 검색 속도를 결정합니다. 기본적으로 이 시간은 10초( 최소 권장 값)입니다.  
  
## <a name="failures-due-to-hard-errors"></a>하드 오류로 인한 실패  
 하드 오류를 일으킬 수 있는 원인 중에는 다음 조건이 있습니다.  
  
-   연결 또는 전선의 끊어짐  
  
-   잘못된 네트워크 카드  
  
-   라우터 변경  
  
-   방화벽 내의 변경 사항  
  
-   엔드포인트 다시 구성  
  
-   트랜잭션 로그가 있는 드라이브 손실  
  
-   운영 체제 또는 프로세스 오류  
  
 예를 들어 주 데이터베이스의 로그 드라이브가 응답하지 않거나 실패하면 운영 체제에서 Sqlservr.exe에 심각한 오류 발생 사실을 알립니다.  
  
 네트워크 구성 요소 및 일부 IO 하위 시스템과 같은 구성 요소에는 자체적으로 오류를 확인하기 위한 제한 시간이 있습니다. 이러한 제한 시간은 데이터베이스 미러링에 독립적이므로 데이터베이스 미러링에 대해 알지 못하며 데이터베이스 미러링 동작을 전혀 파악할 수 없습니다. 이러한 경우 제한 시간이 지연되어 오류가 발생한 다음 데이터베이스 미러링이 결과 하드 오류를 수신할 때까지의  시간이 늘어납니다.  
  
> [!NOTE]  
>  데이터베이스 미러링에 대한 활성 오류 검사는 소프트웨어 오류의 경우에만 수행됩니다. 자세한 내용은 이 항목의 뒷부분에 나오는 "소프트 오류로 인한 오류"를 참조하십시오.  
  
 네트워크에서 발생하는 오류 상황을 해석하는 데 도움이 되도록 네트워크 엔지니어에게 TCP 연결에서 다음 이벤트가 발생할 경우 어떤 오류 메시지가 포트로 전송되는지 문의하십시오.  
  
-   DNS가 작동하지 않는 경우  
  
-   케이블이 연결되어 있지 않은 경우  
  
-   [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows에 특정 포트를 차단하는 방화벽이 있는 경우  
  
-   포트를 모니터링하는 애플리케이션에서 오류가 발생한 경우  
  
-   Windows 기반 서버 이름이 바뀐 경우  
  
-   Windows 기반 서버가 다시 부팅된 경우  
  
> [!NOTE]  
>  미러링은 서버에 액세스하는 클라이언트 관련 문제에 대해 보호하지 않습니다. 예를 들어 프라이빗 네트워크 인터페이스 카드가 서버 인스턴스 간의 모든 미러링 트래픽을 처리하는 동안 퍼블릭 네트워크 어댑터가 주 서버 인스턴스에 대한 클라이언트 연결을 처리하는 경우 데이터베이스를 계속 미러링하려고 하지만 공용 네트워크 어댑터의 오류로 인해 클라이언트가 데이터베이스에 액세스하지 못합니다.  
  
## <a name="failures-due-to-soft-errors"></a>소프트 오류로 인한 오류  
 미러링 제한 시간 초과가 발생할 수 있는 상황은 다음과 같습니다.  
  
-   TCP 연결 제한 시간 초과, 삭제되거나 손상된 패킷, 잘못된 순서의 패킷 등의 네트워크 오류  
  
-   응답 하지 않는 운영 체제, 서버 또는 데이터베이스입니다.  
  
-   Windows 서버 제한 시간 초과  
  
-   CPU 또는 디스크 오버로드, 꽉 찬 트랜잭션 로그 또는 시스템의 메모리나 스레드 부족과 같은 컴퓨팅 리소스 부족. 이런 경우에는 제한 시간을 늘이거나, 작업을 줄이거나, 작업을 처리할 수 있도록 하드웨어를 변경해야 합니다.  
  
### <a name="the-mirroring-time-out-mechanism"></a>미러링 제한 시간 메커니즘  
 소프트 오류는 서버 인스턴스에서 직접 감지되지 않으므로 소프트 오류 발생 시 서버 인스턴스가 무기한 대기할 수 있습니다. 이를 방지하기 위해 데이터베이스 미러링은 미러링 세션의 각 서버 인스턴스를 기반으로 열려 있는 각 연결에서 일정한 간격으로 ping을 보내는 제한 시간 메커니즘을 구현합니다.  
  
 연결이 열려 있으려면 서버 인스턴스가 ping을 하나 더 보내는 데 필요한 시간을 더하여 정의되는 제한 시간에서 해당 연결에 대한 ping을 받아야 합니다. 제한 시간 내에 ping을 받은 경우 연결이 열려 있으며 서버 인스턴스가 해당 연결을 통해 통신하고 있음을 나타냅니다. ping을 받으면 서버 인스턴스는 해당 연결의 제한 시간 카운터를 다시 설정합니다.  
  
 제한 시간 내에 ping을 받지 못한 경우 서버 인스턴스는 해당 연결이 제한 시간을 초과했다고 간주하고 연결을 닫은 후 세션의 상태와 운영 모드에 따라 제한 시간 이벤트를 처리합니다.  
  
 실제로 다른 서버가 올바로 실행되고 있는 경우에도 제한 시간 초과는 오류로 간주됩니다. 각 파트너의 일반 응답에 비해 세션의 제한 시간 값이 지나치게 짧은 경우 거짓 오류가 발생할 수 있습니다. 거짓 오류는 한 서버 인스턴스가 다른 서버 인스턴스에 성공적으로 연결하지만 해당 서버 인스턴스의 응답 시간이 너무 느려 제한 시간이 만료되기 전에 ping을 받을 수 없는 경우에 발생합니다.  
  
 성능 우선 모드 세션에서 제한 시간은 항상 10초이며 이는 일반적으로 거짓 오류를 방지하기에 충분한 시간입니다. 보안 우선 모드 세션에서 기본 제한 시간은 10초이지만 이 시간을 변경할 수 있습니다. 거짓 오류를 방지하려면 미러링 제한 시간을 항상 10초 이상으로 설정하는 것이 좋습니다.  
  
 **제한 시간 값을 변경하려면(보안 우선 모드 전용)**  
  
-   [ALTER DATABASE \<데이터베이스> SET PARTNER TIMEOUT \<정수>](/sql/t-sql/statements/alter-database-transact-sql) 문을 사용합니다.  
  
 **현재 제한 시간 값을 보려면**  
  
-   **sys.database_mirroring** 에서 [mirroring_connection_timeout](/sql/relational-databases/system-catalog-views/sys-database-mirroring-transact-sql)을 쿼리합니다.  
  
## <a name="responding-to-an-error"></a>오류에 대한 응답  
 오류 유형에 관계없이 오류를 감지하는 서버 인스턴스는 인스턴스의 역할, 세션의 운영 모드 및 세션 내 다른 연결의 상태를 기반으로 적절하게 오류에 응답합니다. 파트너 손실로 인해 발생하는 상황에 대한 자세한 내용은 [Database Mirroring Operating Modes](database-mirroring-operating-modes.md)를 참조하십시오.  
  
## <a name="see-also"></a>관련 항목  
 [역할 전환 중 서비스 중단 예측&#40;데이터베이스 미러링&#41;](estimate-the-interruption-of-service-during-role-switching-database-mirroring.md)   
 [데이터베이스 미러링 운영 모드](database-mirroring-operating-modes.md)   
 [데이터베이스 미러링 세션 중 역할 전환&#40;SQL Server&#41;](role-switching-during-a-database-mirroring-session-sql-server.md)   
 [데이터베이스 미러링&#40;SQL Server&#41;](database-mirroring-sql-server.md)  
  
  
