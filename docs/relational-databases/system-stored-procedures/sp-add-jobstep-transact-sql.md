---
title: sp_add_jobstep (Transact-sql) | Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_add_jobstep_TSQL
- sp_add_jobstep
dev_langs:
- TSQL
helpviewer_keywords:
- sp_add_jobstep
ms.assetid: 97900032-523d-49d6-9865-2734fba1c755
author: stevestein
ms.author: sstein
ms.openlocfilehash: c312f8798ba4ad42eed327123c9adc5feacba8a8
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2020
ms.locfileid: "74412851"
---
# <a name="sp_add_jobstep-transact-sql"></a>sp_add_jobstep(Transact-SQL)

[!INCLUDE[tsql-appliesto-ss2008-asdbmi-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdbmi-xxxx-xxx-md.md)]

  SQL 에이전트 작업에 단계 (작업)를 추가 합니다.  
  
 ![항목 링크 아이콘](../../database-engine/configure-windows/media/topic-link.gif "항목 링크 아이콘") [Transact-SQL 구문 표기 규칙](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
  > [!IMPORTANT]  
  > [Azure SQL Database Managed Instance](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance)에서는 대부분의 SQL Server 에이전트 작업 유형이 지원 되지 않습니다. 자세한 내용은 [SQL Server에서 Azure SQL Database Managed Instance T-SQL 차이점](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent)을 참조하세요.
  
## <a name="syntax"></a>구문  
  
```
sp_add_jobstep [ @job_id = ] job_id | [ @job_name = ] 'job_name'   
     [ , [ @step_id = ] step_id ]   
     { , [ @step_name = ] 'step_name' }   
     [ , [ @subsystem = ] 'subsystem' ]   
     [ , [ @command = ] 'command' ]   
     [ , [ @additional_parameters = ] 'parameters' ]   
          [ , [ @cmdexec_success_code = ] code ]   
     [ , [ @on_success_action = ] success_action ]   
          [ , [ @on_success_step_id = ] success_step_id ]   
          [ , [ @on_fail_action = ] fail_action ]   
          [ , [ @on_fail_step_id = ] fail_step_id ]   
     [ , [ @server = ] 'server' ]   
     [ , [ @database_name = ] 'database' ]   
     [ , [ @database_user_name = ] 'user' ]   
     [ , [ @retry_attempts = ] retry_attempts ]   
     [ , [ @retry_interval = ] retry_interval ]   
     [ , [ @os_run_priority = ] run_priority ]   
     [ , [ @output_file_name = ] 'file_name' ]   
     [ , [ @flags = ] flags ]   
     [ , { [ @proxy_id = ] proxy_id   
         | [ @proxy_name = ] 'proxy_name' } ]  
```  
  
## <a name="arguments"></a>인수  
`[ @job_id = ] job_id`단계를 추가할 작업의 id입니다. *job_id* 은 **uniqueidentifier**이며 기본값은 NULL입니다.  
  
`[ @job_name = ] 'job_name'`단계를 추가할 작업의 이름입니다. *job_name* 는 **sysname**이며 기본값은 NULL입니다.  
  
> [!NOTE]  
>  *Job_id* 또는 *job_name* 를 지정 해야 하지만 둘 다 지정할 수는 없습니다.  
  
`[ @step_id = ] step_id`작업 단계의 시퀀스 id 번호입니다. 단계 id 번호는 **1** 부터 시작 하 여 간격 없이 증가 합니다. 기존 시퀀스에 단계를 삽입하는 경우에는 시퀀스 번호가 자동으로 조정됩니다. *Step_id* 지정 하지 않으면 값이 제공 됩니다. *step_id* 은 **int**이며 기본값은 NULL입니다.  
  
`[ @step_name = ] 'step_name'`단계의 이름입니다. *step_name* 는 **sysname**이며 기본값은 없습니다.  
  
`[ @subsystem = ] 'subsystem'`[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 서비스에서 *명령을*실행 하는 데 사용 하는 하위 시스템입니다. *하위 시스템* 은 **nvarchar (40)** 이며 다음 값 중 하나일 수 있습니다.  
  
|값|Description|  
|-----------|-----------------|  
|'**ACTIVESCRIPTING**'|액티브 스크립트<br /><br /> ** \* 중요 \* \* **[!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]|  
|'**CMDEXEC**'|운영 체제 명령 또는 실행 프로그램|  
|'**배포**'|복제 배포 에이전트 작업|  
|'**SNAPSHOT**'|복제 스냅샷 에이전트 작업|  
|'**로그 판독기**'|복제 로그 판독기 에이전트 작업|  
|'**MERGE**'|복제 병합 에이전트 작업|  
|'**QueueReader**'|복제 큐 판독기 에이전트 작업|  
|'**ANALYSISQUERY**'|Analysis Services 쿼리(MDX, DMX)|  
|'**ANALYSISCOMMAND**'|Analysis Services 명령(XMLA)|  
|'**Dts**'|[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]패키지 실행|  
|'**PowerShell**'|PowerShell 스크립트|  
|'**TSQL**' (기본값)|[!INCLUDE[tsql](../../includes/tsql-md.md)]선언문|  
  
`[ @command = ] 'command'`*하위 시스템*을 통해 **SQLServerAgent** 서비스에서 실행할 명령입니다. *명령은* **nvarchar (max)** 이며 기본값은 NULL입니다. SQL Server 에이전트에는 소프트웨어 프로그램 작성 시 변수를 사용하는 것과 같은 유연성을 제공하는 토큰 대체 기능이 있습니다.  
  
> [!IMPORTANT]  
>  작업 단계에서 사용되는 모든 토큰에 이스케이프 매크로를 사용해야 하며 그렇지 않으면 작업 단계가 실패합니다. 또한 이제 토큰 이름을 괄호로 묶고 토큰 구문의 시작 부분에 달러 기호(`$`)를 사용해야 합니다. 다음은 그 예입니다.  
>   
>  `$(ESCAPE_`*매크로 이름*`(DATE))`  
  
 이러한 토큰에 대 한 자세한 내용과 새로운 토큰 구문을 사용 하도록 작업 단계를 업데이트 하는 방법에 대 한 자세한 내용은 [작업 단계에서 토큰 사용](../../ssms/agent/use-tokens-in-job-steps.md)을 참조 하세요.  
  
> [!IMPORTANT]  
>  Windows 이벤트 로그에 대한 쓰기 권한이 있는 모든 Windows 사용자는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 경고 또는 WMI 경고로 활성화되는 작업 단계에 액세스할 수 있습니다. 이러한 보안상 위험을 방지하기 위해 경고로 활성화되는 작업에 사용할 수 있는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 토큰은 기본적으로 해제됩니다. 이러한 토큰에는 **A-DBN**, **A-SVR**, **A-ERR**, **A-SEV**, **A-MSG**및 **WMI(**_property_**)** 가 있습니다. 이번 릴리스에서는 모든 경고에 토큰을 사용할 수 있습니다.  
>   
>  이러한 토큰을 사용해야 하는 경우 먼저 Administrators 그룹과 같은 트러스트된 Windows 보안 그룹의 멤버만 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 가 설치된 컴퓨터의 이벤트 로그에 대한 쓰기 권한이 있는지 확인합니다. 그런 다음 개체 탐색기에서 **SQL Server 에이전트** 를 마우스 오른쪽 단추로 클릭한 다음 **속성**을 선택하고 **경고 시스템** 페이지에서 **경고에 대한 모든 응답 작업에 대해 토큰 바꾸기** 를 선택하여 이러한 토큰을 설정합니다.  
  
`[ @additional_parameters = ] 'parameters'`[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)] *매개 변수* 는 **ntext**이며 기본값은 NULL입니다.  
  
`[ @cmdexec_success_code = ] code`*명령이* 성공적으로 실행 되었음을 나타내는 **CmdExec** 하위 시스템 명령에서 반환 하는 값입니다. *코드* 는 **int**이며 기본값은 **0**입니다.  
  
`[ @on_success_action = ] success_action`단계가 성공할 경우 수행할 동작입니다. *success_action* 은 **tinyint**이며 다음 값 중 하나일 수 있습니다.  
  
|값|설명(동작)|  
|-----------|----------------------------|  
|**1** (기본값)|성공적으로 종료|  
|**2**|실패로 종료|  
|**3**|다음 단계로 이동|  
|**4**|단계로 이동 *on_success_step_id*|  
  
`[ @on_success_step_id = ] success_step_id`단계가 성공 하 고 *success_action* **4**인 경우이 작업을 실행할 단계의 ID입니다. *success_step_id* 은 **int**이며 기본값은 **0**입니다.  
  
`[ @on_fail_action = ] fail_action`단계가 실패할 경우 수행할 동작입니다. *fail_action* 은 **tinyint**이며 다음 값 중 하나일 수 있습니다.  
  
|값|설명(동작)|  
|-----------|----------------------------|  
|**1**|성공적으로 종료|  
|**2** (기본값)|실패로 종료|  
|**3**|다음 단계로 이동|  
|**4**|단계로 이동 *on_fail_step_id*|  
  
`[ @on_fail_step_id = ] fail_step_id`단계가 실패 하 고 *fail_action* **4**이면이 작업에서 실행할 단계의 ID입니다. *fail_step_id* 은 **int**이며 기본값은 **0**입니다.  
  
`[ @server = ] 'server'`[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)] *서버* 는 **nvarchar (30)** 이며 기본값은 NULL입니다.  
  
`[ @database_name = ] 'database'`[!INCLUDE[tsql](../../includes/tsql-md.md)] 단계를 실행할 데이터베이스의 이름입니다. *데이터베이스* 는 **sysname**이며 기본값은 NULL입니다 .이 경우 **master** 데이터베이스가 사용 됩니다. 이름을 대괄호([ ])로 묶는 것은 허용되지 않습니다. ActiveX 작업 단계의 경우 *데이터베이스* 는 단계에서 사용 하는 스크립트 언어의 이름입니다.  
  
`[ @database_user_name = ] 'user'`단계를 [!INCLUDE[tsql](../../includes/tsql-md.md)] 실행할 때 사용할 사용자 계정의 이름입니다. *사용자* 는 **sysname**이며 기본값은 NULL입니다. *사용자* 가 NULL 이면 단계가 *데이터베이스*의 작업 소유자 사용자 컨텍스트에서 실행 됩니다.  SQL Server 에이전트는 작업 소유자가 SQL Server sysadmin인 경우에만 이 매개 변수를 포함합니다. 작업 소유자가 SQL Server sysadmin일 경우 지정한 Transact-SQL 단계가 지정한 SQL Server 사용자 이름의 컨텍스트에서 실행됩니다. 작업 소유자가 sysadmin SQL Server 아닌 경우 Transact-sql 단계는 항상이 작업을 소유 하는 로그인의 컨텍스트에서 실행 되 고 매개 변수는 @database_user_name 무시 됩니다.  
  
`[ @retry_attempts = ] retry_attempts`이 단계가 실패 하는 경우 다시 시도 하는 횟수입니다. *retry_attempts* 는 **int**이며 기본값은 다시 시도 하지 않음을 나타내는 **0**입니다.  
  
`[ @retry_interval = ] retry_interval`다시 시도 간의 시간 간격 (분)입니다. *retry_interval* 는 **int**이며 기본값 **은 0 분 간격을 나타내는** **0**입니다.  
  
`[ @os_run_priority = ] run_priority`쓰이는.  
  
`[ @output_file_name = ] 'file_name'`이 단계의 출력이 저장 되는 파일의 이름입니다. *file_name* 은 **nvarchar (200)** 이며 기본값은 NULL입니다. *file_name* *명령*아래에 나열 된 토큰을 하나 이상 포함할 수 있습니다. [!INCLUDE[tsql](../../includes/tsql-md.md)]이 매개 변수는, **CmdExec**, **PowerShell**, [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]또는 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 하위 시스템에서 실행 되는 명령에만 사용할 수 있습니다.  
  
`[ @flags = ] flags`는 동작을 제어 하는 옵션입니다. *flags* 는 **int**이며 다음 값 중 하나일 수 있습니다.  
  
|값|Description|  
|-----------|-----------------|  
|**0** (기본값)|출력 파일을 덮어씁니다.|  
|**2**|출력 파일에 추가합니다.|  
|**4**|
  [!INCLUDE[tsql](../../includes/tsql-md.md)] 작업 단계 출력을 단계 기록에 씁니다.|  
|**20cm(8**|테이블에 로그를 씁니다(기존 기록을 덮어씀).|  
|**x**|테이블에 로그를 씁니다(기존 기록에 추가).|  
|**32**|모든 출력을 작업 기록에 씁니다.|  
|**64**|중단할 Cmd jobstep에 대한 신호로 사용할 Windows 이벤트를 만듭니다.|  
  
`[ @proxy_id = ] proxy_id`작업 단계가 실행 되는 프록시의 id입니다. *proxy_id* 은 **int**형식 이며 기본값은 NULL입니다. *Proxy_id* 지정 되지 않은 경우 *proxy_name* 지정 되지 않고 *user_name* 지정 되지 않은 경우 작업 단계는 에이전트의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 서비스 계정으로 실행 됩니다.  
  
`[ @proxy_name = ] 'proxy_name'`작업 단계가 실행 되는 프록시의 이름입니다. *proxy_name* 는 **sysname**형식 이며 기본값은 NULL입니다. *Proxy_id* 지정 되지 않은 경우 *proxy_name* 지정 되지 않고 *user_name* 지정 되지 않은 경우 작업 단계는 에이전트의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 서비스 계정으로 실행 됩니다.  
  
## <a name="return-code-values"></a>반환 코드 값  
 **0** (성공) 또는 **1** (실패)  
  
## <a name="result-sets"></a>결과 집합  
 None  
  
## <a name="remarks"></a>설명  
 **sp_add_jobstep** 는 **msdb** 데이터베이스에서 실행 해야 합니다.  
  
 SQL Server Management Studio는 작업 구조를 만들고 관리할 수 있는 바람직한 방법을 제공하는데, 이는 그래픽을 사용하여 쉽게 작업을 관리할 수 있는 방법입니다.  
  
 기본적으로 다른 프록시를 지정 하지 않으면 작업 단계는 에이전트에 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 대 한 서비스 계정으로 실행 됩니다. 이 계정의 요구 사항은 **sysadmin** 고정 보안 역할의 멤버 여야 합니다.
  
 프록시는 *proxy_name* 또는 *proxy_id*로 식별할 수 있습니다.  
  
## <a name="permissions"></a>사용 권한  
 기본적으로 **sysadmin** 고정 서버 역할의 멤버는이 저장 프로시저를 실행할 수 있습니다. 다른 사용자는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] msdb **데이터베이스의 다음** 에이전트 고정 데이터베이스 역할 중 하나를 부여 받아야 합니다.  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 이러한 역할의 사용 권한에 대한 자세한 내용은 [SQL Server 에이전트 고정 데이터베이스 역할](../../ssms/agent/sql-server-agent-fixed-database-roles.md)을 참조하세요.  
  
 작업 단계의 생성자는 작업 단계에 대한 프록시에 액세스할 수 있어야 합니다. **Sysadmin** 고정 서버 역할의 멤버는 모든 프록시에 액세스할 수 있습니다. 다른 사용자에게는 프록시에 대한 액세스 권한을 명시적으로 부여해야 합니다.  
  
## <a name="examples"></a>예  
 다음 예에서는 Sales 데이터베이스에 대한 액세스 권한을 읽기 전용으로 변경하는 작업 단계를 만듭니다. 또한 이 예에서는 다시 시도 횟수를 5로 지정하고 각 다시 시도는 5분 대기한 후에 발생하도록 지정합니다.  
  
> [!NOTE]  
>  이 예에서는 `Weekly Sales Data Backup` 작업이 이미 있다고 가정합니다.  
  
```sql
USE msdb;  
GO  
EXEC sp_add_jobstep  
    @job_name = N'Weekly Sales Data Backup',  
    @step_name = N'Set database to read only',  
    @subsystem = N'TSQL',  
    @command = N'ALTER DATABASE SALES SET READ_ONLY',
    @retry_attempts = 5,  
    @retry_interval = 5 ;  
GO  
```  
  
## <a name="see-also"></a>참고 항목  
 [작업 보기 또는 수정](../../ssms/agent/view-or-modify-jobs.md)   
 [Transact-sql&#41;sp_add_job &#40;](../../relational-databases/system-stored-procedures/sp-add-job-transact-sql.md)   
 [Transact-sql&#41;sp_add_schedule &#40;](../../relational-databases/system-stored-procedures/sp-add-schedule-transact-sql.md)   
 [Transact-sql&#41;sp_delete_jobstep &#40;](../../relational-databases/system-stored-procedures/sp-delete-jobstep-transact-sql.md)   
 [Transact-sql&#41;sp_help_job &#40;](../../relational-databases/system-stored-procedures/sp-help-job-transact-sql.md)   
 [Transact-sql&#41;sp_help_jobstep &#40;](../../relational-databases/system-stored-procedures/sp-help-jobstep-transact-sql.md)   
 [Transact-sql&#41;sp_update_jobstep &#40;](../../relational-databases/system-stored-procedures/sp-update-jobstep-transact-sql.md)   
 [시스템 저장 프로시저&#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
