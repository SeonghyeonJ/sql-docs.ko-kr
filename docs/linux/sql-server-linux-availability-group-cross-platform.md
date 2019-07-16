---
title: SQL Server Always On Windows 및 Linux에서 가용성 그룹 구성
description: SQL Server 가용성 그룹 복제본에서 Windows 및 Linux를 사용 하 여 구성 하 고 있습니다.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: vanto
ms.date: 01/31/2018
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.assetid: ''
monikerRange: '>= sql-server-2017 || = sqlallproducts-allversions'
ms.openlocfilehash: f6758760d8ea73d9ec0ac95a0e824a0fd46a6dbb
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68045191"
---
# <a name="configure-sql-server-always-on-availability-group-on-windows-and-linux-cross-platform"></a>구성 SQL Server Always On 가용성 그룹에서 Windows 및 Linux (플랫폼 간)

[!INCLUDE[tsql-appliesto-sslinux-only](../includes/tsql-appliesto-ss2017-xxxx-xxxx-xxx-md.md)]

이 문서는 Windows 서버에서 하나의 복제본과 Linux 서버에 다른 복제본을 사용 하 여는 Always On 가용성 그룹 (AG)을 만드는 단계를 설명 합니다. 이 구성은 다양 한 운영 체제에 복제본이 있기 때문에 플랫폼 간입니다. 다른 플랫폼 또는 재해 복구 (DR)에서 마이그레이션에 대 한이 구성을 사용 합니다. 플랫폼 간 구성을 관리 하려면 클러스터 솔루션이 없기 때문에이 구성은 고가용성을 지원 하지 않습니다. 

![하이브리드 없음](./media/sql-server-linux-availability-group-overview/image1.png)

계속 하기 전에 설치와 Windows 및 Linux에서 SQL Server 인스턴스에 대 한 구성에 이해 해야 합니다. 

## <a name="scenario"></a>시나리오

이 시나리오에서는 두 서버는 서로 다른 운영 체제입니다. 라는 Windows Server 2016 `WinSQLInstance` 주 복제본을 호스트 합니다. Linux 서버 `LinuxSQLInstance` 보조 복제본을 호스트 합니다.

## <a name="configure-the-ag"></a>AG 구성 

AG를 만드는 단계 읽기 규모 워크 로드에 대 한 AG를 만드는 단계와 동일 합니다. AG 클러스터 유형이 NONE, 이므로 클러스터 관리자가 없습니다. 

   >[!NOTE]
   >이 문서의 스크립트에서 꺾쇠 괄호 `<` 고 `>` 환경에 교체 해야 하는 값을 식별 합니다. 자체 꺾쇠 괄호 스크립트가 필요 하지 않습니다. 

1. Windows Server 2016에서 SQL Server 2017을 설치, Always On 가용성 그룹 SQL Server 구성 관리자에서 사용 하도록 설정 하 고 혼합된 모드 인증을 설정 합니다. 

   >[!TIP]
   >Azure에서이 솔루션에서 유효성을 검사할 경우 동일한 가용성 집합은 데이터 센터에 구분 되도록에서 두 서버를 배치 합니다. 

   **가용성 그룹을 사용 하도록 설정**

   자세한 내용은 [을 사용 하도록 설정 하 고 Always On 가용성 그룹 (SQL Server)를 사용 하지 않도록 설정](../database-engine/availability-groups/windows/enable-and-disable-always-on-availability-groups-sql-server.md)합니다.

   ![가용성 그룹을 사용 하도록 설정](./media/sql-server-linux-availability-group-cross-platform/1-sqlserver-configuration-manager.png)

   SQL Server 구성 관리자 정보는 컴퓨터는 장애 조치 클러스터의 노드가 아닙니다. 

   가용성 그룹을 사용 하도록 설정 하면 SQL Server를 다시 시작 합니다.

   **혼합된 모드 인증을 설정**

   자세한 내용은 [서버 인증 모드 변경](../database-engine/configure-windows/change-server-authentication-mode.md#SSMSProcedure)합니다.

1. Linux의 SQL Server 2017을 설치 합니다. 자세한 내용은 [Install SQL Server](sql-server-linux-setup.md)합니다. 사용 하도록 설정 `hadr` mssql 구성이 통해

   사용 하도록 설정 하려면 `hadr` mssql conf 셸 프롬프트에서를 통해 다음 명령을 실행 합니다.

   ```bash
   sudo /opt/mssql/bin/mssql-conf set hadr.hadrenabled 1
   ```

   사용 하도록 설정한 후 `hadr`, SQL Server 인스턴스를 다시 시작 합니다.  

   다음 이미지는이 단계를 완료를 표시 합니다.

   ![가용성 그룹이 Linux를 사용 하도록 설정](./media/sql-server-linux-availability-group-cross-platform/2-sqlserver-linux-set-hadr.png)

1. 두 서버 모두에서 호스트 파일 구성 또는 DNS 서버 이름을 등록 합니다.

1. 방화벽 포트를 엽니다 TPC 1433 and 5022 Windows와 Linux 모두에서.

1. 주 복제본에서 데이터베이스 로그인 및 암호를 만듭니다.

   ```sql
   CREATE LOGIN dbm_login WITH PASSWORD = '<C0m9L3xP@55w0rd!>';
   CREATE USER dbm_user FOR LOGIN dbm_login;
   GO
   ```

1. 주 복제본에서 마스터 키 및 인증서를 만든 다음 개인 키를 사용 하 여 인증서를 백업 합니다.

   ```sql
   CREATE MASTER KEY ENCRYPTION BY PASSWORD = '<C0m9L3xP@55w0rd!>';
   CREATE CERTIFICATE dbm_certificate WITH SUBJECT = 'dbm';
   BACKUP CERTIFICATE dbm_certificate
   TO FILE = 'C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\MSSQL\DATA\dbm_certificate.cer'
   WITH PRIVATE KEY (
           FILE = 'C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\MSSQL\DATA\dbm_certificate.pvk',
           ENCRYPTION BY PASSWORD = '<C0m9L3xP@55w0rd!>'
       );
   GO
   ```

1. 인증서와 개인 키를 Linux 서버 (보조 복제본)에 복사 `/var/opt/mssql/data`합니다. 사용할 수 있습니다 `pscp` Linux 서버에 파일을 복사 합니다. 

1. 그룹 및 개인 키 및 인증서의 소유권 `mssql:mssql`합니다.

   다음 스크립트는 그룹 및 파일의 소유권을 설정합니다. 

   ```bash
   sudo chown mssql:mssql /var/opt/mssql/data/dbm_certificate.pvk
   sudo chown mssql:mssql /var/opt/mssql/data/dbm_certificate.cer
   ```

   다음 다이어그램에서 소유권 및 그룹 올바르게 설정 인증서 및 키에 대 한 합니다.

   ![가용성 그룹이 Linux를 사용 하도록 설정](./media/sql-server-linux-availability-group-cross-platform/3-cert-key-owner-group.png)


1. 보조 복제본에서 데이터베이스 로그인 및 암호를 만들고 마스터 키를 만듭니다.

   ```sql
   CREATE LOGIN dbm_login WITH PASSWORD = '<C0m9L3xP@55w0rd!>';
   CREATE USER dbm_user FOR LOGIN dbm_login;
   GO
   CREATE MASTER KEY ENCRYPTION BY PASSWORD = '<M@st3rKeyP@55w0rD!>'
   GO
   ```

1. 보조 복제본에서 복원에 복사한 인증서 `/var/opt/mssql/data`합니다. 

   ```sql
   CREATE CERTIFICATE dbm_certificate   
       AUTHORIZATION dbm_user
       FROM FILE = '/var/opt/mssql/data/dbm_certificate.cer'
       WITH PRIVATE KEY (
       FILE = '/var/opt/mssql/data/dbm_certificate.pvk',
       DECRYPTION BY PASSWORD = '<C0m9L3xP@55w0rd!>'
   )
   GO
   ```

1. 주 복제본에서 끝점을 만듭니다.

   ```sql
   CREATE ENDPOINT [Hadr_endpoint]
       AS TCP (LISTENER_IP = (0.0.0.0), LISTENER_PORT = 5022)
       FOR DATA_MIRRORING (
           ROLE = ALL,
           AUTHENTICATION = CERTIFICATE dbm_certificate,
           ENCRYPTION = REQUIRED ALGORITHM AES
           );
   ALTER ENDPOINT [Hadr_endpoint] STATE = STARTED;
   GRANT CONNECT ON ENDPOINT::[Hadr_endpoint] TO [dbm_login]
   GO
   ```

   >[!IMPORTANT]
   >방화벽이는 TCP 포트 수신기에 대해 열려 있어야 합니다. 앞의 스크립트에서 포트는 5022를 사용 합니다. 사용 가능한 모든 TCP 포트를 사용 합니다. 

1. 보조 복제본에서 끝점을 만듭니다. 끝점을 만들고 보조 복제본에서 앞의 스크립트를 반복 합니다. 

1. 주 복제본에서 사용 하 여 AG를 만들 `CLUSTER_TYPE = NONE`합니다. 예제 스크립트를 사용 하 여 `SEEDING_MODE = AUTOMATIC` AG를 만들려고 합니다. 

   >[!NOTE]
   >경우 SQL Server의 Windows 인스턴스는 이러한 경로 보조 복제본에서 존재 하지 않으므로 SQL Server Linux 인스턴스의 실패를 시드 자동 데이터 및 로그 파일에 대 한 서로 다른 경로 사용 합니다. 플랫폼 간 AG에 대해 다음 스크립트를 사용 하려면 데이터베이스는 Windows 서버에서 데이터 및 로그 파일에 대 한 동일한 경로 필요 합니다. 또는 설정 하는 스크립트를 업데이트할 수 있습니다 `SEEDING_MODE = MANUAL` 한 다음 백업 및 사용 하 여 데이터베이스를 복원 `NORECOVERY` 데이터베이스를 시드해야 합니다. 
   >
   >이 동작은 Azure Marketplace 이미지에 적용 됩니다. 
   >
   >자동 시 딩 하는 방법에 대 한 자세한 내용은 참조 하세요. [자동 시드-디스크 레이아웃](../database-engine/availability-groups/windows/automatic-seeding-secondary-replicas.md#disklayout)합니다. 

   스크립트를 실행 하기 전에 Ag에 대 한 값을 업데이트 합니다.

      * 대체 `<WinSQLInstance>` 주 복제본 SQL Server 인스턴스의 서버 이름입니다.

      * 대체 `<LinuxSQLInstance>` 보조 복제본 SQL Server 인스턴스의 서버 이름입니다. 

   AG를 만들려면 값을 업데이트 하 고 주 복제본에서 스크립트를 실행 합니다.  

   ```sql
   CREATE AVAILABILITY GROUP [ag1]
       WITH (CLUSTER_TYPE = NONE)
       FOR REPLICA ON
           N'<WinSQLInstance>' 
        WITH (
           ENDPOINT_URL = N'tcp://<WinSQLInstance>:5022',
           AVAILABILITY_MODE = ASYNCHRONOUS_COMMIT,
            SEEDING_MODE = AUTOMATIC,
            FAILOVER_MODE = MANUAL,
           SECONDARY_ROLE (ALLOW_CONNECTIONS = ALL)
            ),
           N'<LinuxSQLInstance>' 
       WITH (
            ENDPOINT_URL = N'tcp://<LinuxSQLInstance>:5022',
           AVAILABILITY_MODE = ASYNCHRONOUS_COMMIT,
           SEEDING_MODE = AUTOMATIC,
           FAILOVER_MODE = MANUAL,
           SECONDARY_ROLE (ALLOW_CONNECTIONS = ALL)
           )
   GO
   ```
   
   자세한 내용은 [CREATE AVAILABILITY GROUP (TRANSACT-SQL)](../t-sql/statements/create-availability-group-transact-sql.md)합니다.

1. 보조 복제본을 AG를 조인 합니다.

   ```sql
   ALTER AVAILABILITY GROUP [ag1] JOIN WITH (CLUSTER_TYPE = NONE)
   ALTER AVAILABILITY GROUP [ag1] GRANT CREATE ANY DATABASE
   GO
   ```

1. AG에 대해 데이터베이스를 만듭니다. 라는 데이터베이스를 사용 하는 예제 단계 `<TestDB>`합니다. 자동 시드를 사용 하는 경우에 데이터와 로그 파일에 대 한 동일한 경로 설정 합니다. 

   스크립트를 실행 하기 전에 데이터베이스에 대 한 값을 업데이트 합니다.

      * 대체 `<TestDB>` 데이터베이스의 이름입니다.

      * 대체 `<F:\Path>` 데이터베이스 및 로그 파일에 대 한 경로 사용 하 여 합니다. 데이터베이스 및 로그 파일에 대 한 동일한 경로 사용 합니다. 

      또한 기본 경로 사용할 수 있습니다. 

    데이터베이스를 만들려면 스크립트를 실행 합니다. 

   ```sql
   CREATE DATABASE [<TestDB>]
      CONTAINMENT = NONE
     ON  PRIMARY ( NAME = N'<TestDB>', FILENAME = N'<F:\Path>\<TestDB>.mdf')
     LOG ON ( NAME = N'<TestDB>_log', FILENAME = N'<F:\Path>\<TestDB>_log.ldf')
   GO
   ```

1. 전체 데이터베이스 백업을 수행 합니다. 

1. 자동 시드를 사용 하지 않는 경우 보조 복제본 (Linux) 서버에서 데이터베이스를 복원 합니다. [Windows에서 SQL Server 데이터베이스를 백업 및 복원을 사용 하 여 Linux로](sql-server-linux-migrate-restore-database.md)합니다. 데이터베이스를 복원 `WITH NORECOVERY` 보조 복제본에서. 

1. AG에 데이터베이스를 추가 합니다. 예제 스크립트를 업데이트 합니다. 대체 `<TestDB>` 데이터베이스의 이름입니다. 주 복제본에서 데이터베이스 AG에 추가할 SQL 쿼리를 실행 합니다.

   ```sql
   ALTER AG [ag1] ADD DATABASE <TestDB>
   GO
   ```

1. 보조 복제본에서 데이터베이스가 입력 시작 되었는지 확인 합니다. 

## <a name="fail-over-the-primary-replica"></a>주 복제본 장애 조치

[!INCLUDE[Force failover](../includes/ss-force-failover-read-scale-out.md)]

이 문서에서는 플랫폼 간 AG를 마이그레이션 또는 읽기-배율 작업을 지원 하도록 만드는 단계를 검토 합니다. 수동 재해 복구를 위해 사용할 수 있습니다. 또한 AG 조치 (failover) 하는 방법을 설명 했습니다. 플랫폼 간 AG를 클러스터 유형을 사용 하 여 `NONE` 없는 클러스터 도구-플랫폼 간에 있기 때문에 고가용성을 지원 하지 않습니다. 

## <a name="next-steps"></a>다음 단계

[Always On 가용성 그룹 개요](../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)

[Linux 배포에 대 한 SQL Server 가용성 기본 사항](sql-server-linux-ha-basics.md)
