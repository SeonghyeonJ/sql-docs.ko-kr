---
title: 데이터베이스 미러링 및 AlwaysOn 가용성 그룹 (SQL Server)에 대 한 전송 보안 | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- sessions [SQL Server], database mirroring
- cryptography [SQL Server], database mirroring
- certificates [SQL Server], database mirroring
- encryption [SQL Server], database mirroring
- Windows authentication [SQL Server]
- authentication [SQL Server], database mirroring
- transport security
- database mirroring [SQL Server], security
ms.assetid: 49239d02-964e-47c0-9b7f-2b539151ee1b
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 18b52163cb1e8c6be0cf7fdea37861662d6e4830
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62754292"
---
# <a name="transport-security-for-database-mirroring-and-alwayson-availability-groups-sql-server"></a>데이터베이스 미러링 및 AlwaysOn 가용성 그룹에 대한 전송 보안(SQL Server)
  전송 보안에는 데이터베이스 간에 교환되는 메시지의 인증과 암호화(선택적)가 포함됩니다. 데이터베이스 미러링 및 [!INCLUDE[ssHADR](../../includes/sshadr-md.md)]의 경우 데이터베이스 미러링 엔드포인트에 인증과 암호화가 구성됩니다. 데이터베이스 미러링 엔드포인트에 대한 개요를 보려면 [데이터베이스 미러링 엔드포인트&amp;#40;SQL Server&amp;#41;](the-database-mirroring-endpoint-sql-server.md)을 참조하세요.  
  

  
##  <a name="Authentication"></a> 인증  
 인증은 사용자가 올바른지 여부를 확인하는 과정입니다. 데이터베이스 미러링 엔드포인트 간 연결에는 인증이 필요합니다. 파트너나 미러링 모니터 서버의 연결 요청은 반드시 인증되어야 합니다.  
  
 서버 인스턴스에서 데이터베이스 미러링 또는 [!INCLUDE[ssHADR](../../includes/sshadr-md.md)]에 사용하는 인증 유형은 데이터베이스 미러링 엔드포인트의 속성입니다. 데이터베이스 미러링 끝점에 사용할 수 있는 두 가지 전송 보안 같습니다. Windows 인증 (보안 지원 공급자 인터페이스 (SSPI)) 및 인증서 기반 인증 합니다.  
  
### <a name="windows-authentication"></a>Windows 인증  
 Windows 인증을 사용할 경우 각 서버 인스턴스는 프로세스가 실행되고 있는 Windows 사용자 계정의 Windows 자격 증명을 사용하여 다른 쪽에 로그인합니다. Windows 인증에는 다음과 같은 로그인 계정에 대한 수동 구성이 필요할 수 있습니다.  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스가 동일 도메인 계정에서 서비스로 실행될 경우 추가 구성이 필요하지 않습니다.  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스가 동일 도메인 또는 신뢰할 수 있는 도메인에서 다른 도메인 계정을 사용하여 서비스로 실행될 경우 각 계정의 로그인을 다른 각 서버 인스턴스에서 **마스터** 로 만들어야 하며, 해당 로그인에는 해당 엔드포인트에 대한 CONNECT 권한이 부여되어 있어야 합니다.  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스가 네트워크 서비스 계정으로 실행될 경우 각 호스트 컴퓨터 계정(*DomainName***\\***ComputerName$* )의 로그인은 다른 각 서버의 **마스터**에서 만들어야 하며, 해당 로그인에는 해당 엔드포인트에 대한 CONNECT 권한이 부여되어야 합니다. 네트워크 서비스 계정을 사용하여 서버 인스턴스를 실행할 경우 호스트 컴퓨터의 도메인 계정을 사용하여 인증이 수행되기 때문입니다.  
  
> [!NOTE]  
>  Windows 인증을 사용하여 데이터베이스 미러링 세션을 설정하는 예제는 [예제: Windows 인증을 사용하여 데이터베이스 미러링 설정&#40;Transact-SQL&#41;](example-setting-up-database-mirroring-using-windows-authentication-transact-sql.md)을 참조하세요.  
  
### <a name="certificates"></a>인증서  
 서버 인스턴스가 트러스트된 도메인에 없거나 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 가 로컬 서비스로 실행되고 있는 경우와 같이 Windows 인증을 사용할 수 없는 경우가 있습니다. 이런 경우에는 연결 요청을 인증하는 데 사용자 자격 증명 대신 인증서가 필요합니다. 각 서버 인스턴스의 미러링 엔드포인트는 로컬에서 만든 자체 인증서를 사용하여 구성해야 합니다.  
  
 암호화 방법은 인증서를 만들 때 결정됩니다. 자세햔 내용은 [데이터베이스 미러링 엔드포인트의 아웃바운드 연결에 대한 인증서 사용 허용&amp;#40;Transact-SQL&amp;#41;](database-mirroring-use-certificates-for-outbound-connections.md)을 참조하세요. 인증서는 신중하게 관리해야 합니다.  
  
 서버 인스턴스는 자체 인증서의 프라이빗 키를 사용하여 연결 설정 시 해당 ID를 설정합니다. 연결 요청을 수신하는 서버 인스턴스는 보낸 사람의 인증서 공개 키를 사용하여 보낸 사람의 ID를 인증합니다. 예를 들어 Server_A와 Server_B라는 서버 인스턴스가 있다고 가정합니다. Server_A가 자신의 프라이빗 키를 사용하여 연결 헤더를 암호화한 다음 Server_B에 연결 요청을 보내면 Server_B는 Server_A의 인증서 공개 키를 사용하여 연결 헤더의 암호를 해독합니다. 해독된 헤더가 정확한 경우 Server_B는 Server_A가 헤더를 암호화했음을 확인하고 연결을 인증합니다. 해독된 헤더가 잘못된 경우 Server_B는 연결 요청을 인증할 수 없음을 확인하고 연결을 거부합니다.  
  
##  <a name="DataEncryption"></a> 데이터 암호화  
 기본적으로 데이터베이스 미러링 엔드포인트에서는 미러링 연결을 통해 전송되는 데이터가 암호화되어야 합니다. 이 경우 엔드포인트는 암호화를 사용하는 엔드포인트에만 연결할 수 있습니다. 네트워크 보안을 보장할 수 없는 경우에는 데이터베이스 미러링 연결에 암호화를 사용하는 것이 좋습니다. 그러나 암호화를 해제할 수도 있고 암호화를 지원하지만 필수 사항은 아니도록 설정할 수도 있습니다. 암호화를 해제하면 데이터가 암호화되지 않으며 엔드포인트는 암호화를 요구하는 다른 엔드포인트에 연결할 수 없습니다. 암호화가 지원되면 반대쪽 엔드포인트가 암호화를 지원하거나 암호화를 요구하는 경우에만 데이터가 암호화됩니다.  
  
> [!NOTE]  
>  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]에서는 암호화를 필요로 하거나 암호화가 해제된 상태로 미러링 엔드포인트를 만듭니다. 암호화 설정을 SUPPORTED로 변경하려면 ALTER ENDPOINT [!INCLUDE[tsql](../../includes/tsql-md.md)] 문을 사용합니다. 자세한 내용은 [ALTER ENDPOINT&#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-endpoint-transact-sql)을 참조하세요.  
  
 필요에 따라 CREATE ENDPOINT 문 또는 ALTER ENDPOINT 문의 ALGORITHM 옵션에 다음 값 중 하나를 지정하여 엔드포인트에서 사용할 수 있는 암호화 알고리즘을 제어할 수 있습니다.  
  
|ALGORITHM 값|Description|  
|---------------------|-----------------|  
|RC4|엔드포인트가 반드시 RC4 알고리즘을 사용하도록 지정합니다. 기본값입니다.<br /><br /> 참고: RC4 알고리즘은 더 이상 사용되지 않습니다. [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] AES를 사용하는 것이 좋습니다.|  
|AES|엔드포인트가 반드시 AES 알고리즘을 반드시 사용하도록 지정합니다.|  
|AES RC4|두 엔드포인트가 암호화 알고리즘에 대해 협상하고 이 엔드포인트가 AES 알고리즘에 우선권을 주도록 지정합니다.|  
|RC4 AES|두 엔드포인트가 암호화 알고리즘에 대해 협상하고 이 엔드포인트가 RC4 알고리즘에 우선권을 주도록 지정합니다.|  
  
 연결하는 엔드포인트가 두 알고리즘을 모두 지정하지만 순서가 다른 경우 연결을 수락하는 엔드포인트의 알고리즘이 적용됩니다.  
  
> [!NOTE]  
>  RC4 알고리즘은 이전 버전과의 호환성을 위해서만 지원됩니다. 데이터베이스의 호환성 수준이 90 또는 100인 경우 새 자료는 RC4 또는 RC4_128로만 암호화할 수 있습니다. 이 옵션은 사용하지 않는 것이 좋습니다. 대신 AES 알고리즘 중 하나와 같은 새 알고리즘을 사용하십시오. [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 이상 버전에서 RC4 또는 RC4_128을 사용하여 암호화된 자료는 모든 호환성 수준에서 해독할 수 있습니다.  
>   
>  AES에 비해 상당히 빠르긴 하지만 RC4는 비교적 취약한 알고리즘인 반면 AES는 비교적 강력한 알고리즘입니다. 따라서 AES 알고리즘을 사용하는 것이 좋습니다.  
  
 암호화를 지정하는 [!INCLUDE[tsql](../../includes/tsql-md.md)] 구문에 대한 자세한 내용은 [CREATE ENDPOINT&#40;Transact-SQL&#41;](/sql/t-sql/statements/create-endpoint-transact-sql)를 참조하세요.  
  
##  <a name="RelatedTasks"></a> 관련 태스크  
 **데이터베이스 미러링 엔드포인트에 대한 전송 보안을 구성하려면**  
  
-   [Windows 인증에 대한 데이터베이스 미러링 엔드포인트 만들기&amp;#40;Transact-SQL&amp;#41;](create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md)  
  
-   [Windows 인증을 사용하여 데이터베이스 미러링 세션 구성&#40;SQL Server Management Studio&#41;](establish-database-mirroring-session-windows-authentication.md)  
  
-   [Windows 인증에 대한 데이터베이스 미러링 엔드포인트 만들기&amp;#40;Transact-SQL&amp;#41;](create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md)  
  
-   [데이터베이스 미러링 엔드포인트의 아웃바운드 연결에 대한 인증서 사용 허용&amp;#40;Transact-SQL&amp;#41;](database-mirroring-use-certificates-for-outbound-connections.md)  
  
## <a name="see-also"></a>관련 항목  
 [암호화 알고리즘 선택](../../relational-databases/security/encryption/choose-an-encryption-algorithm.md)   
 [ALTER ENDPOINT&#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-endpoint-transact-sql)   
 [DROP ENDPOINT&#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-endpoint-transact-sql)   
 [SQL Server 데이터베이스 엔진 및 Azure SQL Database에 대한 보안 센터](../../relational-databases/security/security-center-for-sql-server-database-engine-and-azure-sql-database.md)   
 [다른 서버 인스턴스에서 데이터베이스를 사용할 수 있도록 할 때 메타데이터 관리&#40;SQL Server&#41;](../../relational-databases/databases/manage-metadata-when-making-a-database-available-on-another-server.md)   
 [데이터베이스 미러링 엔드포인트&amp;#40;SQL Server&amp;#41;](the-database-mirroring-endpoint-sql-server.md)   
 [sys.database_mirroring_endpoints&#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-mirroring-endpoints-transact-sql)   
 [sys.dm_db_mirroring_connections&#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/database-mirroring-sys-dm-db-mirroring-connections)   
 [데이터베이스 미러링 구성 문제 해결&#40;SQL Server&#41;](troubleshoot-database-mirroring-configuration-sql-server.md)   
 [AlwaysOn 가용성 그룹 구성 문제 해결 &#40;SQL Server&#41;삭제](../availability-groups/windows/troubleshoot-always-on-availability-groups-configuration-sql-server.md)
  
  
