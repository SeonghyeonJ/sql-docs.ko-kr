---
title: 만들기 및 Linux에서 SQL Server에 대 한 작업 실행
description: 이 자습서에서는 Linux의 SQL Server 에이전트 작업을 실행 하는 방법을 보여줍니다.
author: VanMSFT
ms.author: vanto
ms.date: 02/20/2018
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.assetid: 1d93d95e-9c89-4274-9b3f-fa2608ec2792
ms.openlocfilehash: 5abd2db590a89350f45497d7f94b81940a0ec5bc
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68065148"
---
# <a name="create-and-run-sql-server-agent-jobs-on-linux"></a>만들기 및 Linux에서 SQL Server 에이전트 작업 실행

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

SQL Server 작업에는 SQL Server 데이터베이스에서 명령의 순서를 정기적으로 수행 하는 데 사용 됩니다. 이 자습서 Transact SQL 및 SQL Server Management Studio (SSMS)를 사용 하 여 Linux에서 SQL Server 에이전트 작업을 만드는 방법의 예제를 제공 합니다.

> [!div class="checklist"]
> * Linux에서 SQL Server 에이전트를 설치 합니다.
> * 일별 데이터베이스 백업을 수행 하는 새 작업 만들기
> * 예약 및 실행 작업
> * SSMS (선택 사항)에서 동일한 단계를 수행 합니다.

Linux의 SQL Server 에이전트를 사용 하 여 알려진된 문제에 대 한 참조를 [릴리스](sql-server-linux-release-notes.md)합니다.

## <a name="prerequisites"></a>사전 요구 사항

이 자습서를 완료 하려면 다음 필수 조건이 필요 합니다.

* 다음 필수 구성 요소를 사용 하 여 Linux 컴퓨터:
  * SQL Server ([RHEL](quickstart-install-connect-red-hat.md)하십시오 [SLES](quickstart-install-connect-suse.md), 또는 [Ubuntu](quickstart-install-connect-ubuntu.md)) 명령줄 도구를 사용 합니다.

다음 필수 구성 요소는 선택 사항:

* SSMS 사용 하 여 Windows 컴퓨터:
  * [SQL Server Management Studio](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms) SSMS 단계에 대 한 합니다.

## <a name="enable-sql-server-agent"></a>SQL Server 에이전트를 사용 하도록 설정

Linux의 SQL Server 에이전트를 사용 하려면 먼저 설치 된 SQL Server에 이미 있는 컴퓨터에서 SQL Server 에이전트를 활성화 해야 합니다.

1. SQL Server 에이전트를 사용 하도록 설정 하려면 다음 단계를 수행 합니다.
  ```bash
  sudo /opt/mssql/bin/mssql-conf set sqlagent.enabled true 
  ```

1. 다음 명령을 사용 하 여 SQL Server를 다시 시작 합니다.
  ```bash
  sudo systemctl restart mssql-server
  ```

> [!NOTE]
> SQL Server 2017 CU4부터 SQL Server 에이전트에 포함 됩니다. 합니다 **mssql server** 을 패키지 하 고 기본적으로 비활성화 됩니다. CU4 방문 하기 전에 에이전트 설정에 대 한 [Linux에서 SQL Server 에이전트 설치](sql-server-linux-setup-sql-agent.md)합니다.

## <a name="create-a-sample-database"></a>예제 데이터베이스 만들기

이라는 샘플 데이터베이스를 만들려면 다음 단계를 사용 하 여 **SampleDB**합니다. 이 데이터베이스는 매일 백업 작업에 사용 됩니다.

1. Linux 컴퓨터에 bash 터미널 세션을 엽니다.

1. 사용 하 여 **sqlcmd** TRANSACT-SQL을 실행 하려면 **CREATE DATABASE** 명령입니다.

   ```bash
   /opt/mssql-tools/bin/sqlcmd -S localhost -U SA -Q 'CREATE DATABASE SampleDB'
   ```

1. 데이터베이스 서버에서 데이터베이스를 나열 하 여 생성 되었는지 확인 합니다.

   ```bash
   /opt/mssql-tools/bin/sqlcmd -S localhost -U SA -Q 'SELECT Name FROM sys.Databases'
   ```

## <a name="create-a-job-with-transact-sql"></a>TRANSACT-SQL을 사용 하 여 작업 만들기

다음 단계를 TRANSACT-SQL 명령을 사용 하 여 Linux에서 SQL Server 에이전트 작업을 만듭니다. 작업 실행에 샘플 데이터베이스의 매일 백업을 **SampleDB**합니다.

> [!TIP]
> 이러한 명령을 실행 하는 T-SQL 클라이언트를 사용할 수 있습니다. 예를 들어 Linux에서 사용할 수 있습니다 [sqlcmd](sql-server-linux-setup-tools.md) 하거나 [Visual Studio Code](sql-server-linux-develop-use-vscode.md)합니다. 원격 Windows 서버에서 SQL Server Management Studio (SSMS)에서 쿼리를 실행 하거나 UI 인터페이스를 사용 하 여 다음 섹션에 설명 된 작업 관리에 대 한 수도 있습니다.

1. 사용 하 여 [sp_add_job](../relational-databases/system-stored-procedures/sp-add-job-transact-sql.md) 명명 된 작업을 만들려면 `Daily SampleDB Backup`합니다.

   ```sql
   -- Adds a new job executed by the SQLServerAgent service
   -- called 'Daily SampleDB Backup'
   USE msdb ;
   GO
   EXEC dbo.sp_add_job
      @job_name = N'Daily SampleDB Backup' ;
   GO
   ```

1. 호출 [sp_add_jobstep](../relational-databases/system-stored-procedures/sp-add-jobstep-transact-sql.md) 의 백업을 만듭니다는 작업 단계를 만들려면를 `SampleDB` 데이터베이스입니다.

   ```sql
   -- Adds a step (operation) to the job
   EXEC sp_add_jobstep
      @job_name = N'Daily SampleDB Backup',
      @step_name = N'Backup database',
      @subsystem = N'TSQL',
      @command = N'BACKUP DATABASE SampleDB TO DISK = \
         N''/var/opt/mssql/data/SampleDB.bak'' WITH NOFORMAT, NOINIT, \
         NAME = ''SampleDB-full'', SKIP, NOREWIND, NOUNLOAD, STATS = 10',
      @retry_attempts = 5,
      @retry_interval = 5 ;
   GO
   ```

1. 다음 사용 하 여 작업에 대 한 일별 일정을 만듭니다 [sp_add_schedule](../relational-databases/system-stored-procedures/sp-add-jobschedule-transact-sql.md)합니다.

   ```sql
   -- Creates a schedule called 'Daily'
   EXEC dbo.sp_add_schedule
      @schedule_name = N'Daily SampleDB',
      @freq_type = 4,
      @freq_interval = 1,
      @active_start_time = 233000 ;
   USE msdb ;
   GO
   ```

1. 작업 일정을 작업과 연결할 [sp_attach_schedule](../relational-databases/system-stored-procedures/sp-attach-schedule-transact-sql.md)합니다.

   ```sql
   -- Sets the 'Daily' schedule to the 'Daily SampleDB Backup' Job
   EXEC sp_attach_schedule
      @job_name = N'Daily SampleDB Backup',
      @schedule_name = N'Daily SampleDB';
   GO
   ```

1. 사용 하 여 [sp_add_jobserver](../relational-databases/system-stored-procedures/sp-add-jobserver-transact-sql.md) 대상 서버에 작업을 할당 합니다. 이 예제에서는 대상이 로컬 서버입니다.

   ```sql
   EXEC dbo.sp_add_jobserver
      @job_name = N'Daily SampleDB Backup',
      @server_name = N'(LOCAL)';
   GO
   ```
1. 사용 하 여 작업 시작 [sp_start_job](../relational-databases/system-stored-procedures/sp-start-job-transact-sql.md)합니다.

   ```sql
   EXEC dbo.sp_start_job N' Daily SampleDB Backup' ;
   GO
   ```

## <a name="create-a-job-with-ssms"></a>SSMS를 사용 하 여 작업 만들기

만들기 및 원격으로 SQL Server Management Studio (SSMS)를 사용 하 여 Windows에서 작업을 관리도 있습니다.

1. Windows에서 SSMS를 시작 하 고 Linux SQL Server 인스턴스에 연결 합니다. 자세한 내용은 [SSMS 사용 하 여 Linux에서 SQL Server 관리](sql-server-linux-manage-ssms.md)합니다.

1. 이라는 샘플 데이터베이스를 만들지 않았는지 확인 **SampleDB**합니다.

   <img src="./media/sql-server-linux-run-sql-server-agent-job/ssms-agent-0.png" alt="Create a SampleDB database" style="width: 550px;"/>

1. SQL 에이전트 되었는지 확인 [설치](sql-server-linux-setup-sql-agent.md) 하 고 올바르게 구성 합니다. 개체 탐색기에서 SQL Server 에이전트 옆에 있는 더하기 기호를 찾습니다. SQL Server 에이전트를 사용 하지 않는 경우 다시 시작 합니다 **mssql server** Linux에서 서비스 합니다.

   ![SQL Server 에이전트 설치 확인](./media/sql-server-linux-run-sql-server-agent-job/ssms-agent-1.png)

1. 새 작업을 만듭니다.

   ![새 작업 만들기](./media/sql-server-linux-run-sql-server-agent-job/ssms-agent-2.png)

1. 작업 이름을 지정 하 고 사용자 작업 단계를 만듭니다.

   ![작업 단계 만들기](./media/sql-server-linux-run-sql-server-agent-job/ssms-agent-3.png)

1. 사용 하려는 하위 시스템 및 작업 단계를 수행 해야 할 작업을 지정 합니다.

   ![작업 하위 시스템](./media/sql-server-linux-run-sql-server-agent-job/ssms-agent-4.png)

   ![작업 단계](./media/sql-server-linux-run-sql-server-agent-job/ssms-agent-5.png)

1. 새 작업 일정을 만듭니다.

   ![작업 일정](./media/sql-server-linux-run-sql-server-agent-job/ssms-agent-6.png)

   ![작업 일정](./media/sql-server-linux-run-sql-server-agent-job/ssms-agent-8.png)

1. 작업을 시작 합니다.

   <img src="./media/sql-server-linux-run-sql-server-agent-job/ssms-agent-9.png" alt="Start the SQL Server Agent job" style="width: 550px;"/>

## <a name="next-steps"></a>다음 단계

이 자습서에서는 다음과 같은 방법을 학습했습니다.

> [!div class="checklist"]
> * Linux에서 SQL Server 에이전트를 설치 합니다.
> * 사용 하 여 Transact SQL 및 시스템 저장 프로시저 작업을 만들려면
> * 일별 데이터베이스 백업을 수행 하는 작업 만들기
> * SSMS UI를 사용 하 여 작업 만들기 및 관리 하려면

다음으로, 만들기 및 관리 작업에 대 한 다른 기능 살펴보기

> [!div class="nextstepaction"]
>[SQL Server 에이전트 설명서](https://docs.microsoft.com/sql/ssms/agent/sql-server-agent)
