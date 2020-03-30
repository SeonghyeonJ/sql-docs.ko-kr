---
title: network packet size 서버 구성 옵션 구성 | Microsoft Docs
ms.custom: ''
ms.date: 03/02/2017
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- default packet size
- size [SQL Server], packets
- packets [SQL Server], size
- network packet size option
ms.assetid: 236985bf-fc4a-4a57-98f7-a71ef977fd7b
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: be854d2002692611289d401b4ad98cb63cf4a27b
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/30/2020
ms.locfileid: "68731107"
---
# <a name="configure-the-network-packet-size-server-configuration-option"></a>network packet size 서버 구성 옵션 구성
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  이 항목에서는 **또는** 을 사용하여 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 에서 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 네트워크 패킷 크기 [!INCLUDE[tsql](../../includes/tsql-md.md)]서버 구성 옵션을 구성하는 방법에 대해 설명합니다. **네트워크 패킷 크기** 옵션은 전체 네트워크에서 사용되는 패킷 크기(바이트)를 설정합니다. 패킷은 클라이언트와 서버 간에 요청 및 결과를 전송하는 고정된 크기의 데이터 청크입니다. 기본 패킷 크기는 4,096바이트입니다.  
  
> [!NOTE]  
>  성능이 향상될 것이라는 확신이 없으면 패킷 크기를 변경하지 마세요. 대부분의 애플리케이션에는 기본 패킷 크기가 제일 좋습니다.  
  
 **항목 내용**  
  
-   **시작하기 전 주의 사항:**  
  
     [제한 사항](#Restrictions)  
  
     [권장 사항](#Recommendations)  
  
     [보안](#Security)  
  
-   **네트워크 패킷 크기 옵션을 구성하려면:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
-   **후속 작업:**  [네트워크 패킷 크기 옵션을 구성한 후](#FollowUp)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> 시작하기 전에  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> 제한 사항  
  
-   암호화된 연결의 최대 network packet size는 16,383바이트입니다.  
  
> [!NOTE]  
> MARS를 사용하는 경우 SMUX 공급자는 SSL 암호화 전에 패킷에 16바이트 헤더를 추가하여 최대 네트워크 패킷 크기를 16368바이트로 줄입니다.
   
###  <a name="recommendations"></a><a name="Recommendations"></a> 권장 사항  
  
-   이 옵션은 고급 옵션으로, 숙련된 데이터베이스 관리자나 공인된 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 전문가만이 변경해야 합니다.  
  
-   애플리케이션에서 대량 복사 작업을 수행하거나 많은 양의 텍스트 또는 이미지 데이터를 주고받을 때 패킷 크기를 기본값보다 크게 설정하면 네트워크에서 읽기 및 쓰기 작업의 양이 줄어들므로 효율성이 향상될 수 있습니다. 애플리케이션이 적은 양의 정보를 보내거나 받을 경우 대부분의 데이터를 전송할 수 있도록 패킷 크기를 512바이트로 설정할 수 있습니다.  
  
-   서로 다른 네트워크 프로토콜을 사용하는 시스템에서는 네트워크 패킷 크기를 가장 일반적으로 사용되는 프로토콜 크기로 설정합니다. network packet size 옵션은 네트워크 프로토콜이 보다 큰 패킷을 지원할 때 네트워크 성능을 향상시킵니다. 클라이언트 애플리케이션에서 이 값을 덮어쓸 수 있습니다.  
  
-   OLE DB, ODBC(Open Database Connectivity) 및 DB-Library 함수를 호출하여 패킷 크기 변경을 요청할 수도 있습니다. 서버에서 요청된 패킷 크기가 지원되지 않으면 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 이 클라이언트에게 경고 메시지를 보냅니다. 일부 환경에서는 패킷 크기를 변경할 경우 다음 오류가 발생하면서 통신 연결이 실패할 수 있습니다.  
  
     `Native Error: 233, no process is on the other end of the pipe.`  
  
###  <a name="security"></a><a name="Security"></a> 보안  
  
####  <a name="permissions"></a><a name="Permissions"></a> 권한  
 매개 변수 없이 또는 첫 번째 매개 변수만 사용하여 **sp_configure** 를 실행할 수 있는 권한은 기본적으로 모든 사용자에게 부여됩니다. 구성 옵션을 변경하거나 RECONFIGURE 문을 실행하는 두 매개 변수를 사용하여 **sp_configure** 를 실행하려면 사용자에게 ALTER SETTINGS 서버 수준 권한이 있어야 합니다. **sysadmin** 및 **serveradmin** 고정 서버 역할은 ALTER SETTINGS 권한을 암시적으로 보유하고 있습니다.  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> SQL Server Management Studio 사용  
  
#### <a name="to-configure-the-network-packet-size-option"></a>네트워크 패킷 크기 옵션을 구성하려면  
  
1.  개체 탐색기에서 서버를 마우스 오른쪽 단추로 클릭하고 **속성**을 선택합니다.  
  
2.  **고급** 노드를 클릭합니다.  
  
3.  **네트워크**에서 **네트워크 패킷 크기** 상자의 값을 선택합니다.  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Transact-SQL 사용  
  
#### <a name="to-configure-the-network-packet-size-option"></a>네트워크 패킷 크기 옵션을 구성하려면  
  
1.  [!INCLUDE[ssDE](../../includes/ssde-md.md)]에 연결합니다.  
  
2.  표준 도구 모음에서 **새 쿼리**를 클릭합니다.  
  
3.  다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다. 다음 예제에서는 [sp_configure](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md) 를 사용하여 `network packet size` 옵션의 값을 `6500` 바이트로 설정하는 방법을 보여 줍니다.  
  
```sql  
USE AdventureWorks2012 ;  
GO  
EXEC sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE ;  
GO  
EXEC sp_configure 'network packet size', 6500 ;  
GO  
RECONFIGURE;  
GO  
  
```  
  
 자세한 내용은 [서버 구성 옵션&#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md)서버 구성 옵션을 보거나 구성하는 방법에 대해 설명합니다.  
  
##  <a name="follow-up-after-you-configure-the-network-packet-size-option"></a><a name="FollowUp"></a> 후속 작업: 네트워크 패킷 크기 옵션을 구성한 후  
 이 설정은 서버를 다시 시작하지 않아도 즉시 적용됩니다.  
  
## <a name="see-also"></a>참고 항목  
 [RECONFIGURE&#40;Transact-SQL&#41;](../../t-sql/language-elements/reconfigure-transact-sql.md)   
 [서버 구성 옵션&#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md)   
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)  
  
  
