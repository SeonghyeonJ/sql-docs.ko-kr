---
title: DB 메일 및 Linux에서 SQL 에이전트를 사용 하 여 전자 메일 경고 | Microsoft Docs
description: 이 문서에서는 Linux의 SQL Server를 사용 하 여 DB 메일 및 전자 메일 경고를 사용 하는 방법 설명
author: meet-bhagdev
ms.author: meetb
manager: craigg
ms.date: 02/20/2018
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.assetid: tbd
ms.openlocfilehash: a468fc1b317e906cc27005469ac81cb4eef48045
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66713191"
---
# <a name="db-mail-and-email-alerts-with-sql-agent-on-linux"></a>DB 메일 및 Linux에서 SQL 에이전트를 사용 하 여 전자 메일 경고

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

다음 단계에서는 DB 메일을 설정 하 고 SQL Server 에이전트와 함께 사용 하는 방법을 보여 줍니다. (**mssql server 에이전트**) linux. 

## <a name="1-enable-db-mail"></a>1. DB 메일을 사용 하도록 설정

```sql
USE master 
GO 
sp_configure 'show advanced options',1 
GO 
RECONFIGURE WITH OVERRIDE 
GO 
sp_configure 'Database Mail XPs', 1 
GO 
RECONFIGURE  
GO  
```

## <a name="2-create-a-new-account"></a>2. 새 계정 만들기
```sql
EXECUTE msdb.dbo.sysmail_add_account_sp 
@account_name = 'SQLAlerts', 
@description = 'Account for Automated DBA Notifications', 
@email_address = 'sqlagenttest@gmail.com', 
@replyto_address = 'sqlagenttest@gmail.com', 
@display_name = 'SQL Agent', 
@mailserver_name = 'smtp.gmail.com', 
@port = 587, 
@enable_ssl = 1, 
@username = 'sqlagenttest@gmail.com', 
@password = '<password>' 
GO
```

## <a name="3-create-a-default-profile"></a>3. 기본 프로필 만들기

```sql
EXECUTE msdb.dbo.sysmail_add_profile_sp 
@profile_name = 'default', 
@description = 'Profile for sending Automated DBA Notifications' 
GO
```

## <a name="4-add-the-database-mail-account-to-a-database-mail-profile"></a>4. 데이터베이스 메일 프로필을 데이터베이스 메일 계정을 추가합니다
```sql
EXECUTE msdb.dbo.sysmail_add_principalprofile_sp 
@profile_name = 'default', 
@principal_name = 'public', 
@is_default = 1 ; 
 ```
 
## <a name="5-add-account-to-profile"></a>5. 프로필에 계정 추가 
```sql
EXECUTE msdb.dbo.sysmail_add_profileaccount_sp   
@profile_name = 'default',   
@account_name = 'SQLAlerts',   
@sequence_number = 1;  
 ```
 
## <a name="6-send-test-email"></a>6. 테스트 전자 메일 보내기
> [!NOTE]
> 전자 메일 클라이언트를 이동 하 고는 "하면 덜 안전한 클라이언트 메일을 보낼 수 있습니다.."를 사용 하도록 설정 해야 할 수 있습니다. 일부 클라이언트는 전자 메일 디먼으로 DB 메일을 인식합니다.

```
EXECUTE msdb.dbo.sp_send_dbmail 
@profile_name = 'default', 
@recipients = 'recipient-email@gmail.com', 
@Subject = 'Testing DBMail', 
@Body = 'This message is a test for DBMail' 
GO
```

## <a name="7-set-db-mail-profile-using-mssql-conf-or-environment-variable"></a>7. Mssql conf 또는 환경 변수를 사용 하 여 DB 메일 프로필 설정
DB 메일 프로필을 등록 하려면 mssql conf 유틸리티 또는 환경 변수를 사용할 수 있습니다. 이 경우 프로필 기본을 부르겠습니다.

```bash
# via mssql-conf
sudo /opt/mssql/bin/mssql-conf set sqlagent.databasemailprofile default
# via environment variable
MSSQL_AGENT_EMAIL_PROFILE=default
```

## <a name="8-set-up-an-operator-for-sqlagent-job-notifications"></a>8. SQLAgent 작업 알림에 운영자 설정 

```sql
EXEC msdb.dbo.sp_add_operator 
@name=N'JobAdmins',  
@enabled=1, 
@email_address=N'recipient-email@gmail.com',  
@category_name=N'[Uncategorized]' 
GO 
```

## <a name="9-send-email-when-agent-test-job-succeeds"></a>9. ' 테스트 에이전트 작업 ' 성공 시 전자 메일 보내기 

```
EXEC msdb.dbo.sp_update_job 
@job_name='Agent Test Job', 
@notify_level_email=1, 
@notify_email_operator_name=N'JobAdmins' 
GO
```

## <a name="next-steps"></a>다음 단계
SQL Server 에이전트를 사용 하 여 만들기, 예약 하며, 작업을 실행 하는 방법에 대 한 자세한 내용은 참조 하세요. [Linux에서 SQL Server 에이전트 작업을 실행](sql-server-linux-run-sql-server-agent-job.md)합니다.
