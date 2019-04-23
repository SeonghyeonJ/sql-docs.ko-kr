---
title: PowerShell 사용 하 여 Linux에서 SQL Server 관리 | Microsoft Docs
description: 이 문서에서는 Linux의 SQL Server를 사용 하 여 Windows에서 PowerShell을 사용 하는 개요를 제공 합니다.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 10/02/2017
ms.topic: conceptual
ms.prod: sql
ms.custom: sql-linux
ms.technology: linux
ms.assetid: a3492ce1-5d55-4505-983c-d6da8d1a94ad
ms.openlocfilehash: 903d2d89ca0d551cbb78cfb69dd305f852f62313
ms.sourcegitcommit: b87c384e10d6621cf3a95ffc79d6f6fad34d420f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60158769"
---
# <a name="use-powershell-on-windows-to-manage-sql-server-on-linux"></a>Linux의 SQL Server를 관리 하는 Windows에서 PowerShell을 사용 하 여

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

이 문서에서는 소개 [SQL Server PowerShell](../powershell/sql-server-powershell.md) Linux의 SQL Server와 함께 사용 하는 방법에 몇 가지 예가 단계적으로 안내 합니다. SQL Server에 대 한 PowerShell 지원, Windows에서 현재 사용할 수 이므로 Linux에서 원격 SQL Server 인스턴스에 연결할 수 있는 Windows 컴퓨터의 경우 사용할 수 있습니다.

## <a name="install-the-newest-version-of-sql-powershell-on-windows"></a>Windows에서 SQL PowerShell의 최신 버전을 설치 합니다.

[SQL PowerShell](../powershell/download-sql-server-ps-module.md) Windows에 PowerShell 갤러리에 유지 됩니다. SQL Server에서 작업할 때 SqlServer PowerShell 모듈의 최신 버전 항상 사용 해야 합니다.

## <a name="before-you-begin"></a>시작하기 전 주의 사항

읽기를 [알려진 문제](sql-server-linux-release-notes.md) Linux의 SQL Server에 대 한 합니다.

## <a name="launch-powershell-and-import-the-sqlserver-module"></a>PowerShell을 시작 하 고 가져올는 *sqlserver* 모듈

Windows에서 PowerShell을 시작 하 여 시작 해 보겠습니다. 열기를 *명령 프롬프트* 입력 하 여 Windows 컴퓨터에서 **PowerShell** 새 Windows PowerShell 세션을 시작 합니다.

```
PowerShell
```

SQL Server 라는 Windows PowerShell 모듈을 제공 **SqlServer** PowerShell 환경 또는 스크립트로 SQL Server 구성 (SQL Server 공급자 및 cmdlet)를 가져오는 데 사용할 수 있습니다.

복사 하 고 가져오는 PowerShell 프롬프트에서 다음 명령을 붙여 합니다 **SqlServer** 현재 PowerShell 세션에 모듈:

```powershell
Import-Module SqlServer
```

확인 하려면 PowerShell 프롬프트에서 다음 명령을 입력 합니다 **SqlServer** 모듈을 제대로 가져온:

```powershell
Get-Module -Name SqlServer
```

PowerShell은 다음 출력과 유사한 정보가 표시 되어야 합니다.

```
ModuleType Version    Name          ExportedCommands
---------- -------    ----          ----------------
Script     21.1.18102 SqlServer     {Add-SqlAvailabilityDatabase, Add-SqlAvailabilityGroupList...
```

## <a name="connect-to-sql-server-and-get-server-information"></a>SQL Server에 연결 하 고 서버 정보 가져오기

Linux의 SQL Server 인스턴스에 연결의 서버 속성을 표시 하에서 Windows PowerShell을 사용 하겠습니다.

복사 하 고 PowerShell 프롬프트에서 다음 명령을 붙여 넣습니다. 이러한 명령은 실행 하면 PowerShell 됩니다.
- 표시 된 *Windows PowerShell 자격 증명 요청* 자격 증명을 묻는 대화 (*SQL 사용자 이름* 및 *SQL 암호*) SQL Server에 연결 Linux 기반 인스턴스
- 인스턴스를 만듭니다는 [Server](https://msdn.microsoft.com/library/microsoft.sqlserver.management.smo.server.aspx) 개체
- 에 연결 합니다 **Server** 몇 가지 속성을 표시 하 고

대체 **\<your_server_instance\>** IP 주소 또는 Linux에서 SQL Server 인스턴스의 호스트 이름입니다.

```powershell
# Prompt for credentials to login into SQL Server
$serverInstance = "<your_server_instance>"
$credential = Get-Credential

# Connect to the Server and get a few properties
Get-SqlInstance -ServerInstance $serverInstance -Credential $credential
# done
```

PowerShell은 다음 출력과 유사한 정보가 표시 되어야 합니다.

```
Instance Name                   Version    ProductLevel UpdateLevel  HostPlatform HostDistribution                
-------------                   -------    ------------ -----------  ------------ ----------------                
your_server_instance            14.0.3048  RTM          CU13         Linux        Ubuntu 
```
> [!NOTE]
> 아무 것도 이러한 값에 대 한 표시를 하는 경우 대상 SQL Server 인스턴스에 대 한 연결 가능성이 실패 했습니다. SQL Server Management Studio에서 연결 하려면 동일한 연결 정보를 사용할 수 있습니다 있는지 확인 합니다. 그런 다음 [connection troubleshooting recommendations](sql-server-linux-troubleshooting-guide.md#connection)(연결 문제 해결 권장 사항)를 검토합니다.

## <a name="examine-sql-server-error-logs"></a>SQL Server 오류 로그를 검사 합니다.

Linux의 SQL Server 인스턴스에서 오류 로그를 검사 하는 Windows에서 PowerShell 사용 하 여 연결 하겠습니다. 사용 합니다 **Out-gridview** 표 보기에서에서 로그 오류에서 정보를 표시 하는 cmdlet입니다.

복사 하 고 PowerShell 프롬프트에서 다음 명령을 붙여 넣습니다. 이러한 실행 하려면 몇 분 정도 걸릴 수 있습니다. 이 명령은 다음을 수행 합니다.
- 표시 된 *Windows PowerShell 자격 증명 요청* 자격 증명을 묻는 대화 (*SQL 사용자 이름* 및 *SQL 암호*) SQL Server에 연결 Linux 기반 인스턴스
- 사용 된 **Get SqlErrorLog** cmdlet은 Linux에서 SQL Server 인스턴스에 연결 하 고 오류를 검색 이후 로그 **어제**
- 출력을 파이프 합니다 **Out-gridview** cmdlet

대체 **\<your_server_instance\>** IP 주소 또는 Linux에서 SQL Server 인스턴스의 호스트 이름입니다.

```powershell
# Prompt for credentials to login into SQL Server
$serverInstance = "<your_server_instance>"
$credential = Get-Credential

# Retrieve error logs since yesterday
Get-SqlErrorLog -ServerInstance $serverInstance -Credential $credential -Since Yesterday | Out-GridView
# done
```
## <a name="see-also"></a>참고자료
- [SQL Server PowerShell](../relational-databases/scripting/sql-server-powershell.md)
