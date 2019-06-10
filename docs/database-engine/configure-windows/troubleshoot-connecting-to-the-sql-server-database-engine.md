---
title: SQL Server 데이터베이스 엔진에 대한 연결 문제 해결 | Microsoft Docs
ms.custom: sqlfreshmay19
ms.date: 05/15/2019
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- troubleshooting, connecting to Database Engine
- connecting to Database Engine, troubleshooting
ms.assetid: 474c365b-c451-4b07-b636-1653439f4b1f
author: MikeRayMSFT
ms.author: mikeray
manager: jroth
ms.openlocfilehash: d54ee0a26e82c660c93e8c1f185c4e60e8b75805
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/07/2019
ms.locfileid: "66775244"
---
# <a name="troubleshoot-connecting-to-the-sql-server-database-engine"></a>SQL Server 데이터베이스 엔진에 대한 연결 문제 해결
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

이 문서에는 단일 서버에서 SQL Server 데이터베이스 엔진의 인스턴스에 연결할 수 없는 경우 사용할 수 있는 문제 해결 기술이 나열되어 있습니다.

>[!NOTE]
>다른 시나리오의 경우 다음을 참조하세요.
>- [가용성 그룹 수신기](../availability-groups/windows/listeners-client-connectivity-application-failover.md)
>- [장애 조치(Failover) 클러스터 인스턴스](../../sql-server/failover-clusters/windows/always-on-failover-cluster-instances-sql-server.md)

이러한 단계는 이미 시도한 가장 가능성이 높은 문제 순서가 아닙니다. 가장 기본적인 문제에서 좀 더 복잡한 문제 순서로 표시됩니다. 이러한 단계에서는 TCP/IP 프로토콜을 사용하여 다른 컴퓨터에서 SQL Server 인스턴스에 연결한다고 가정하며, 이것이 가장 일반적인 상황입니다. Windows 10을 실행하는 클라이언트 애플리케이션과 SQL Server 둘 다를 포함하는 SQL Server 2016용으로 작성되었지만 약간만 수정하면 다른 버전의 SQL Server와 다른 운영 체제에도 일반적으로 적용됩니다.

이 지침은 “**서버에 연결**” 오류 문제를 해결하는 데 유용합니다. 자세한 오류 정보는 `Error Number: 11001 (or 53), Severity: 20, State: 0`과 같으며 오류 메시지는 다음과 같습니다.

> `A network-related or instance-specific error occurred while establishing a connection to SQL Server. The server was not found or was not accessible. Verify that the instance name is correct and that SQL Server is configured to allow remote connections.`

> `(provider: Named Pipes Provider, error: 40 - Could not open a connection to SQL Server) (Microsoft SQL Server, Error: 53)`

> `(provider: TCP Provider, error: 0 - No such host is known.) (Microsoft SQL Server, Error: 11001)`

이 오류는 일반적으로 SQL Server 컴퓨터를 찾을 수 없거나, TCP 포트 번호를 알 수 없거나 올바른 포트 번호가 아니거나 방화벽에서 차단되었음을 의미합니다.

> [!TIP]
> 대화형 문제 해결 페이지는 [!INCLUDE[msCoName_md](../../includes/msconame-md.md)] 고객 지원 서비스의 [SQL Server에 대한 연결 오류 해결(영문)](http://support.microsoft.com/help/4009936/solving-connectivity-errors-to-sql-server)에서 사용할 수 있습니다.

### <a name="not-included"></a>포함되지 않음

* 이 항목에는 SSPI 오류 정보가 포함되어 있지 않습니다. SSPI 오류의 경우 ["SSPI 컨텍스트를 생성할 수 없습니다" 오류 메시지의 문제를 해결하는 방법](http://support.microsoft.com/kb/811889)을 참조하세요. 
* 이 항목에는 Kerberos 오류 정보가 포함되어 있지 않습니다. 도움말을 보려면 [SQL Server용 Microsoft Kerberos 구성 관리자](http://www.microsoft.com/download/details.aspx?id=39046)를 참조하세요.
* 이 항목에는 SQL Azure 연결 정보가 포함되어 있지 않습니다. 도움말은 [Microsoft Azure SQL Database 연결 문제 해결(영문)](http://support.microsoft.com/help/10085/troubleshooting-connectivity-issues-with-microsoft-azure-sql-database)을 참조하세요.

## <a name="get-instance-name-from-configuration-manger"></a>Configuration Manger에서 인스턴스 이름 가져오기

[SQL Server 구성 관리자](../../relational-databases/sql-server-configuration-manager.md)의 서버 이름을 확인합니다.

Configuration Manager는 SQL Server를 설치할 때 컴퓨터에 자동으로 설치됩니다. 구성 관리자를 시작하는 방법에 대한 지침은 SQL Server 및 Windows 버전에 따라 약간씩 다릅니다. 버전 세부 정보를 확인하려면 [SQL Server 구성 관리자](../../relational-databases/sql-server-configuration-manager.md)를 참조하세요.

1. SQL Server 인스턴스를 호스팅하는 컴퓨터에 로그인합니다.
1. SQL Server 구성 관리자를 시작합니다.
1. 왼쪽 창에서 **SQL Server Services**를 선택합니다.
1. 오른쪽 창에서 데이터베이스 엔진 인스턴스의 이름을 확인합니다.

    * `SQL SERVER (MSSQLSERVER)`는 SQL Server의 기본 인스턴스를 나타냅니다. 기본 인스턴스 이름은 `<computer name>`입니다.
    * `SQL SERVER (<instance name>)`는 SQL Server의 명명된 인스턴스를 나타냅니다. 이름 인스턴스 이름은 `<computer name>\<instance name>`입니다.

## <a name="verify---the-instance-is-running"></a>인스턴스가 실행되고 있는지 확인

인스턴스가 실행되고 있는지 확인하려면 Configuration Manager에서 SQL Server별 기호를 확인하세요.

* 녹색 화살표는 인스턴스가 실행되고 있음을 나타냅니다.
* 빨간색 정사각형은 인스턴스가 중지되었음을 나타냅니다.

인스턴스가 중지된 경우 인스턴스를 마우스 오른쪽 단추로 클릭한 다음 **시작**을 클릭합니다. 서버 인스턴스가 시작되면 표시기가 녹색 화살표로 바뀝니다.

<a name = "startbrowser"></a>명명된 인스턴스에 연결하려면 SQL Server Browser 서비스를 실행하고 있어야 합니다. Configuration Manager에서 **SQL Server Browser** 서비스를 찾고 해당 서비스가 실행 중인지 확인합니다. 서비스가 실행되고 있지 않은 경우 서비스를 시작합니다. SQL Server Browser 서비스는 기본 인스턴스의 필수 요소가 아닙니다.

## <a name="get-the-ip-address-of-the-server"></a>서버의 IP 주소 가져오기

SQL Server 인스턴스를 호스팅하는 컴퓨터의 IP 주소를 가져옵니다.

1. 시작 메뉴에서 **실행**을 클릭합니다. **실행** 창에서 **cmd**를 입력하고 **확인**을 클릭합니다.
1. 명령 프롬프트 창에서 **ipconfig** 를 입력하고 Enter 키를 누릅니다. **IPv4** 주소와 **IPv6** 주소를 적어둡니다. 

  >SQL Server는 IP 버전 4 프로토콜 또는 IP 버전 6 프로토콜을 사용하여 연결할 수 있습니다. 네트워크에서 둘 중 하나 또는 둘 다를 허용할 수 있습니다. 대부분의 사용자는 먼저 **IPv4** 주소의 문제를 해결합니다. 이것이 더 간결하고 입력하기 쉽습니다.

## <a name = "getTCP"></a>SQL Server 인스턴스 TCP 포트 가져오기

대부분의 경우 TCP 프로토콜을 사용하여 다른 컴퓨터에서 데이터베이스 엔진에 연결할 수 있습니다.

1. SQL Server를 실행하는 컴퓨터에서 SQL Server Management Studio를 사용하여 SQL Server 인스턴스에 연결합니다. 개체 탐색기에서 **관리**, **SQL Server 로그**를 차례로 확장하고 현재 로그를 두 번 클릭합니다.
2. 로그 뷰어의 도구 모음에서 **필터** 단추를 클릭합니다. **메시지에 텍스트 포함** 상자에 `server is listening on`을 입력하고 **필터 적용**을 클릭한 다음 **확인**을 클릭합니다.
3. `Server is listening on [ 'any' <ipv4> 1433]`과 유사한 메시지가 나열되어야 합니다. 

  이 메시지는 이 SQL Server 인스턴스가 이 컴퓨터의 모든 IP 주소(IP 버전 4)에서 수신 대기 중이며 TCP 포트 1433을 수신 대기 중음을 나타냅니다. TCP 포트 1433은 일반적으로 데이터베이스 엔진에서 사용하는 포트입니다. SQL Server 인스턴스 하나만 포트를 사용할 수 있으므로 SQL Server 인스턴스가 둘 이상 설치되어 있을 경우 일부 인스턴스는 다른 포트 번호를 사용해야 합니다. 연결하려는 [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] 인스턴스에서 사용하는 포트 번호에 대해 적어둡니다.

  > [!NOTE]
  > `IP address 127.0.0.1`이 표시될 가능성이 높습니다. 루프백 어댑터 주소라고 합니다. 동일한 컴퓨터의 프로세스만 이 주소를 사용하여 연결할 수 있습니다. 문제 해결에 유용할 수 있지만 다른 컴퓨터에서 연결하는 데 사용할 수 없습니다.

## <a name = "enableprotocols"></a>프로토콜 사용

일부 SQL Server 설치에서는 관리자가 구성 관리자를 통해 사용하도록 설정하지 않을 경우 다른 컴퓨터에서 데이터베이스 엔진에 연결할 수 없습니다. 다른 컴퓨터에서 연결할 수 있게 하려면

1. 앞에서 설명한 대로 SQL Server 구성 관리자를 엽니다.
2. 구성 관리자의 왼쪽 창에서 **SQL Server 네트워크 구성**을 확장하고 연결할 SQL Server 인스턴스를 선택합니다. 오른쪽 창에는 사용할 수 있는 연결 프로토콜이 표시됩니다. 공유 메모리는 일반적으로 사용할 수 있습니다. 동일한 컴퓨터에서만 사용할 수 있으므로 대부분의 설치에서 공유 메모리를 사용할 수 있도록 유지됩니다. 다른 컴퓨터에서 SQL Server에 연결하려면 일반적으로 TCP/IP를 사용합니다. TCP/IP를 사용할 수 없는 경우 **TCP/IP**를 마우스 오른쪽 단추로 클릭한 다음 **사용**을 클릭합니다.
3. 모든 프로토콜에 대해 사용 설정을 변경한 경우 데이터베이스 엔진을 다시 시작해야 합니다. 왼쪽 창에서 **SQL Server 서비스**를 선택합니다. 오른쪽 창에서 데이터베이스 엔진 인스턴스를 마우스 오른쪽 단추로 클릭한 다음 **다시 시작**을 클릭합니다.

## <a name="testTCPIP"></a>TCP/IP 연결 테스트

TCP/IP를 사용하여 SQL Server에 연결하려면 Windows에서 연결을 설정할 수 있어야 합니다. `ping` 도구를 사용하여 TCP를 테스트합니다.
1. 시작 메뉴에서 **실행**을 클릭합니다. **실행** 창에서 **cmd**를 입력하고 **확인**을 클릭합니다. 
2. 명령 프롬프트 창에서 `ping <ip address>` 과 SQL Server를 실행하는 컴퓨터의 IP 주소를 입력합니다. 예를 들어

   * IPv4: `ping 192.168.1.101`
   * IPv6: `ping fe80::d51d:5ab5:6f09:8f48%11`

1. 네트워크가 올바르게 구성된 경우 `ping`이 `Reply from <IP address>`를 반환하고 추가 정보가 표시됩니다. `ping`이 `Destination host unreachable` 또는 `Request timed out`을 반환한다면 TCP/IP가 올바르게 구성되니 않은 것입니다. 이 시점의 오류는 클라이언트 컴퓨터, 서버 컴퓨터 또는 라우터 등의 네트워크 관련 문제를 나타낼 수 있습니다. 네트워크 문제를 해결하려면 [TCP/IP 문제의 고급 문제 해결](/windows/client-management/troubleshoot-tcpip)을 참조하세요.
1. 그런 다음 IP 주소를 사용하여 ping 테스트에 성공한 경우 컴퓨터 이름을 TCP/IP 주소를 확인할 수 있는지 테스트합니다. 클라이언트 컴퓨터의 명령 프롬프트 창에서 `ping` 과 SQL Server를 실행하는 컴퓨터의 컴퓨터 이름을 입력합니다. 예를 들면 다음과 같습니다. `ping newofficepc` 
1. IP 주소에 대한 `ping`은 성공하지만 컴퓨터에 대한 `ping`이 `Destination host unreachable` 또는 `Request timed out`을 반환하는 경우 클라이언트 컴퓨터에 이전(오래된) 이름 확인 정보가 캐시되어 있을 수 있습니다. `ipconfig /flushdns` 를 입력하여 DNS(동적 이름 확인) 캐시를 지웁니다. 다시 이름으로 컴퓨터를 ping합니다. DNS 캐시가 비어 있으므로 클라이언트 컴퓨터가 서버 컴퓨터의 IP 주소에 대한 최신 정보를 확인합니다. 
1. 네트워크가 올바르게 구성된 경우 `ping`이 `Reply from <IP address>`를 반환하고 추가 정보가 표시됩니다. IP 주소로 서버 컴퓨터를 ping할 수 있지만 컴퓨터 이름을 ping하는 경우 `Destination host unreachable.` 또는 `Request timed out.` 등의 오류가 발생한다면 이름 확인이 올바르게 구성되지 않은 것입니다. 자세한 내용은 앞에서 참조한 2006년 문서 [기본적인 TCP/IP 문제를 해결하는 방법](http://support.microsoft.com/kb/169790)을 참조하세요. SQL Server에 연결하기 위해 이름 확인에 성공해야 하는 것은 아니지만 컴퓨터 이름을 IP 주소로 확인할 수 없는 경우 IP 주소를 지정하여 연결해야 합니다. 이름 확인은 나중에 수정할 수 있습니다.

## <a name="testing-a-local-connection"></a>로컬 연결 테스트

다른 컴퓨터에서 연결 문제를 해결하기 전에 먼저 SQL Server를 실행하는 컴퓨터에 로컬로 설치된 클라이언트 애플리케이션에서 연결할 수 있는지 테스트합니다. 로컬로 연결하여 네트워크와 방화벽 문제를 방지합니다. 이 절차에서는 SQL Server Management Studio를 사용합니다. Management Studio가 설치되어 있지 않으면 [SSMS(SQL Server Management Studio) 다운로드](../../ssms/download-sql-server-management-studio-ssms.md)를 참조하세요. Management Studio를 설치할 수 없는 경우 `sqlcmd.exe` 유틸리티를 사용하여 연결을 테스트할 수 있습니다. `sqlcmd.exe`가 데이터베이스 엔진으로 설치됩니다. `sqlcmd.exe`에 대한 자세한 내용은 [sqlcmd 유틸리티](../../tools/sqlcmd-utility.md)를 참조하세요.

1. SQL Server에 액세스할 수 있는 권한을 가진 로그인을 사용하여 SQL Server가 설치된 컴퓨터에 로그인합니다. 설치 중 SQL Server에 대해 하나 이상의 로그인을 SQL Server 관리자로 지정해야 합니다. 관리자를 모르는 경우 [시스템 관리자가 잠겨 있는 경우 SQL Server에 연결](connect-to-sql-server-when-system-administrators-are-locked-out.md)을 참조하세요.
2. 시작 페이지에서 **SQL Server Management Studio**를 입력하거나, 이전 버전의 Windows 시작 메뉴에서 **모든 프로그램**, **Microsoft SQL Server**를 차례로 가리킨 다음 **SQL Server Management Studio**를 클릭합니다.
3. **서버에 연결** 대화 상자의 **서버** 유형 상자에서 **데이터베이스 엔진**을 선택합니다. **인증** 상자에서 **Windows 인증**을 선택합니다. **서버 이름** 상자에 다음 연결 형식 중 하나를 입력합니다.

   |연결 대상:|형식|예제|
   |:-----------------|:---------------|:-----------------|
   |기본 인스턴스|`<computer name>`|`ACCNT27`|
   |명명된 인스턴스|`<computer name\instance name>`|`ACCNT27\PAYROLL`|

   > [!NOTE]
   > 동일한 컴퓨터의 클라이언트 애플리케이션에서 SQL Server에 연결하는 경우 공유 메모리 프로토콜이 사용됩니다. 공유 메모리는 명명된 로컬 파이프의 한 유형이므로 때때로 파이프와 관련된 오류가 발생합니다.

   이 시점에서 오류가 발생하면 계속하기 전에 해결해야 합니다. 문제가 될 수 있는 여러 가지 사항이 있습니다. 로그인에 연결 권한이 없을 수 있습니다. 기본 데이터베이스가 누락되었을 수도 있습니다.

   > [!NOTE]
   > 클라이언트에 전달되는 일부 오류 메시지는 의도적으로 문제 해결에 충분한 정보를 제공하지 않습니다. 이는 공격자에게 SQL Server에 대한 정보를 제공하지 않기 위한 보안 기능입니다. 오류에 대한 전체 정보를 보려면 SQL Server 오류 로그를 확인하세요. 여기에 세부 정보가 제공됩니다. 

1. `18456 Login failed for user` 오류가 발생하는 경우 온라인 설명서 항목 [MSSQLSERVER_18456](../../relational-databases/errors-events/mssqlserver-18456-database-engine-error.md)에 오류 코드의 추가 정보가 포함되어 있습니다. 또한 Aaron Bertrand 블로그의 [오류 18456 문제 해결](http://sqlblog.org/2011/01/14/troubleshooting-error-18456)에는 광범위한 오류 목록이 있습니다. 개체 탐색기의 관리 섹션에서 SSMS를 사용하여 오류 로그를 볼 수 있습니다(연결할 수 있는 경우). 또는 Windows 메모장 프로그램을 사용하여 오류 로그를 볼 수 있습니다. 기본 위치는 사용 중인 버전에 따라 달라지며, 설치하는 동안 변경할 수 있습니다. [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] 의 기본 위치는 `C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\Log\ERRORLOG`입니다. 

1. 공유 메모리를 사용하여, 연결할 수 있는 경우 TCP를 사용하여 연결을 테스트합니다. 이름 앞에 `tcp:`를 지정하여 강제로 TCP 연결을 적용할 수 있습니다. 예를 들어

   |연결 대상:|유형:|예:|
   |-----------------|---------------|-----------------|
   |기본 인스턴스|`tcp:<computer name>`|`tcp:ACCNT27`|
   |명명된 인스턴스|`tcp:<computer name/instance name>`|`tcp:ACCNT27\PAYROLL`|

1. 공유 메모리를 사용하여 연결할 수 있지만 TCP로는 연결할 수 없는 경우 TCP 문제를 해결해야 합니다. 가장 가능성이 큰 문제는 TCP를 사용할 수 없기 때문입니다. TCP를 사용하도록 설정하려면 위의 [프로토콜 사용](#enableprotocols) 단계를 참조하세요.

1. 관리자 계정이 아닌 계정으로 연결하는 것이 목표인 경우 관리자 권한으로 연결할 수 있으면 Windows 인증 로그인 또는 클라이언트 애플리케이션에서 사용하는 SQL Server 인증 로그인으로 다시 연결해 보세요.

## <a name = "openport"></a>방화벽에서 포트 열기

기본적으로 Windows 방화벽이 켜져 있고 다른 컴퓨터에서 연결을 차단합니다. 다른 컴퓨터에서 TCP/IP를 사용하여 연결하려면 SQL Server 컴퓨터에서 데이터베이스 엔진이 사용하는 TCP 포트에 대한 연결을 허용하도록 방화벽을 구성해야 합니다. 기본 인스턴스는 기본적으로 TCP 포트 1433에서 수신 대기합니다. 명명된 인스턴스가 있거나, 기본 인스턴스 포트를 변경한 경우 [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] TCP 포트는 다른 포트에서 수신할 수도 있습니다. [SQL Server 인스턴스 TCP 포트 가져오기](#getTCP)를 참조하세요.

명명된 인스턴스 또는 TCP 포트 1433 이외의 포트에 연결하는 경우 SQL Server Browser 서비스에 대해 UDP 포트 1434도 열어야 합니다. Windows 방화벽에서 포트를 여는 방법에 대한 단계별 지침은 [데이터베이스 엔진 액세스에 대한 Windows 방화벽 구성](configure-a-windows-firewall-for-database-engine-access.md)을 참조하세요.

## <a name="testing-the-connection"></a>연결 테스트

동일한 컴퓨터에서 TCP를 사용하여 연결할 수 있으면 클라이언트 컴퓨터에서 연결을 시도해야 합니다. 이론적으로는 모든 클라이언트 애플리케이션을 사용할 수 있지만 추가 복잡성을 방지하기 위해 클라이언트에 SQL Server 관리 도구를 설치하고 SQL Server Management Studio를 사용하여 연결을 시도합니다.

1. 클라이언트 컴퓨터에서 SQL Server Management Studio를 사용하여 IP 주소 쉼표 포트 번호 형식의 IP 주소와 TCP 포트 번호로 연결을 시도합니다. `192.168.1.101,1433`)을 입력합니다. 이 연결에 실패한다면 다음 중 한 가지 문제가 있음을 의미합니다.

    * IP 주소의 `ping`이 작동하지 않으며 일반적인 TCP 구성 문제를 나타냅니다. [TCP/IP 연결 테스트](#testTCPIP)섹션으로 돌아갑니다.
    * SQL Server가 TCP 프로토콜에서 수신 대기하고 있지 않습니다. [프로토콜 사용](#enableprotocols)섹션으로 돌아갑니다.
    * SQL Server가 지정한 포트 이외의 포트에서 수신 대기 중입니다. 섹션으로 돌아가 [TCP 포트 번호를 가져옵니다](#getTCP).
    * SQL Server TCP 포트가 방화벽에 의해 차단되고 있습니다. [방화벽에서 포트 열기](#opening-a-port-in-the-firewall)섹션으로 돌아갑니다.

2. IP 주소와 포트 번호를 사용하여 연결할 수 있으면 포트 번호 없이 IP 주소를 사용하여 연결을 시도합니다. 기본 인스턴스의 경우 IP 주소만 사용합니다. 명명된 인스턴스의 경우 IP 주소 백슬래시 인스턴스 이름 형식으로 IP 주소와 인스턴스 이름을 사용합니다(예: `192.168.1.101\<instance name`). 작동하지 않을 경우 다음 문제 중 하나가 있는 것입니다.

    * 기본 인스턴스에 연결하는 경우 TCP 포트 1433 이외의 포트에서 수신 대기 중일 수 있으며 클라이언트가 올바른 포트 번호에 연결하고 있지 않습니다.
    * 명명된 인스턴스에 연결하는 경우 포트 번호가 클라이언트에 반환되고 있지 않습니다.

이러한 문제는 둘 다 클라이언트에 포트 번호를 제공하는 SQL Server Browser 서비스와 관련이 있습니다. 해결 방법은 다음과 같습니다.

  * SQL Server Browser 서비스를 시작합니다. 지침을 참조하여 [SQL Server 구성 관리자에서 브라우저를 시작하세요](#startbrowser).
  * SQL Server Browser 서비스가 방화벽에 의해 차단되고 있습니다. 방화벽에서 UDP 포트 1434를 엽니다. [방화벽에서 포트 열기](#opening-a-port-in-the-firewall)섹션으로 돌아갑니다. TCP 포트가 아니라 UDP 포트를 열고 있는지 확인하세요.
  * UDP 포트 1434 정보가 라우터에 의해 차단되고 있습니다. UDP 통신(사용자 데이터그램 프로토콜)은 라우터를 통과하도록 설계되지 않았습니다. 이는 우선 순위가 낮은 트래픽이 네트워크를 채우지 않도록 합니다. UDP 트래픽을 전달하도록 라우터를 구성하거나, 연결 시 항상 포트 번호를 제공하도록 결정할 수 있습니다.
  * 클라이언트 컴퓨터에서 Windows 7 또는 Windows Server 2008(또는 최신 운영 체제)을 사용하는 경우 서버 응답이 쿼리된 IP 주소가 아닌 다른 IP 주소에서 반환되기 때문에 클라이언트 운영 체제에서 UDP 트래픽을 삭제할 수 있습니다. 이는 "느슨한 원본 매핑"을 차단하는 보안 기능입니다. 자세한 내용은 온라인 설명서 항목 [문제 해결의 **여러 항목의 IP 주소** 섹션을 참조하세요. 제한 시간 만료됨](http://msdn.microsoft.com/library/ms190181.aspx). SQL Server 2008 R2의 문서이지만 원칙은 똑같이 적용됩니다. 올바른 IP 주소를 사용하도록 클라이언트를 구성하거나, 연결 시 항상 포트 번호를 제공하도록 결정할 수 있습니다.

3. IP 주소(또는 명명된 인스턴스의 IP 주소 및 인스턴스 이름)를 사용하여 연결할 수 있으면 컴퓨터 이름(또는 명명된 인스턴스의 경우 컴퓨터 이름 및 인스턴스 이름)을 사용하여 연결을 시도합니다. TCP/IP 연결을 강제로 적용하려면 컴퓨터 이름 앞에 `tcp:` 를 넣습니다. 예를 들어 `ACCNT27`컴퓨터에 있는 기본 인스턴스의 경우 `tcp:ACCNT27` 을 사용합니다. 해당 컴퓨터에 있는 `PAYROLL`이라는 명명된 인스턴스의 경우 `tcp:ACCNT27\PAYROLL` 을 사용합니다. IP 주소를 사용하여 연결할 수 있지만 컴퓨터 이름을 사용해서는 연결할 수 없는 경우 이름 확인 문제가 있는 것입니다. 섹션 4, **TCP/IP 연결 테스트**섹션으로 돌아갑니다.

4. 컴퓨터 이름을 사용해서 TCP를 강제로 적용하여 연결할 수 있으면 컴퓨터 이름을 사용하되 TCP를 강제로 적용하지 않고 연결을 시도합니다. 예를 들어 기본 인스턴스의 경우 `CCNT27` 등의 컴퓨터 이름만 사용합니다. 명명된 인스턴스의 경우 `ACCNT27\PAYROLL` 등의 컴퓨터 이름과 인스턴스 이름을 사용합니다. TCP를 강제로 적용할 때는 연결할 수 있었지만 TCP를 강제로 적용하지 않으면 연결할 수 없는 경우 클라이언트가 다른 프로토콜(예: 명명된 파이프)을 사용 중일 수 있습니다.

    1. 클라이언트 컴퓨터에서 SQL Server 구성 관리자를 사용하고 왼쪽 창에서 **SQL Native Client** *version* **구성**을 확장한 다음 **클라이언트 프로토콜**을 선택합니다.
    2. 오른쪽 창에서 TCP/IP를 사용할 수 있는지 확인합니다. TCP/IP를 사용할 수 없는 경우 **TCP/IP** 를 마우스 오른쪽 단추로 클릭한 다음 **사용**을 클릭합니다.
    3. TCP/IP의 프로토콜 순서가 명명된 파이프(또는 이전 버전의 VIA) 프로토콜보다 작은 숫자인지 확인합니다. 일반적으로 공유 메모리를 순서 1, TCP/IP를 순서 2로 유지해야 합니다. 공유 메모리는 클라이언트와 SQL Server가 동일한 컴퓨터에서 실행되는 경우에만 사용됩니다. 동일한 컴퓨터에 대한 연결이 아닐 때 공유 메모리를 건너뛰는 경우를 제외하고 하나가 성공할 때까지 사용 가능한 모든 프로토콜이 순서대로 시도됩니다.

