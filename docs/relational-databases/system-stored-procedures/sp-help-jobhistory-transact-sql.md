---
title: sp_help_jobhistory (Transact-sql) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_help_jobhistory_TSQL
- sp_help_jobhistory
dev_langs:
- TSQL
helpviewer_keywords:
- sp_help_jobhistory
ms.assetid: a944d44e-411b-4735-8ce4-73888d4262d7
author: stevestein
ms.author: sstein
ms.openlocfilehash: 10033b2525ba28e79bd31a73bd9e71a7cca15e42
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68054934"
---
# <a name="sp_help_jobhistory-transact-sql"></a>sp_help_jobhistory(Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  다중 서버 관리 도메인 내의 서버에 관한 작업 관련 정보를 제공합니다.  
  
 ![항목 링크 아이콘](../../database-engine/configure-windows/media/topic-link.gif "항목 링크 아이콘") [Transact-SQL 구문 표기 규칙](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>구문  
  
```  
  
sp_help_jobhistory [ [ @job_id = ] job_id ]   
     [ , [ @job_name = ] 'job_name' ]   
     [ , [ @step_id = ] step_id ]   
     [ , [ @sql_message_id = ] sql_message_id ]   
     [ , [ @sql_severity = ] sql_severity ]   
     [ , [ @start_run_date = ] start_run_date ]   
     [ , [ @end_run_date = ] end_run_date ]   
     [ , [ @start_run_time = ] start_run_time ]   
     [ , [ @end_run_time = ] end_run_time ]   
     [ , [ @minimum_run_duration = ] minimum_run_duration ]   
     [ , [ @run_status = ] run_status ]   
     [ , [ @minimum_retries = ] minimum_retries ]   
     [ , [ @oldest_first = ] oldest_first ]   
     [ , [ @server = ] 'server' ]   
     [ , [ @mode = ] 'mode' ]  
```  
  
## <a name="arguments"></a>인수  
`[ @job_id = ] job_id`작업 id입니다. *job_id* 은 **uniqueidentifier**이며 기본값은 NULL입니다.  
  
`[ @job_name = ] 'job_name'`작업의 이름입니다. *job_name* 는 **sysname**이며 기본값은 NULL입니다.  
  
`[ @step_id = ] step_id`단계 id입니다. *step_id* 은 **int**이며 기본값은 NULL입니다.  
  
`[ @sql_message_id = ] sql_message_id`작업을 실행할 때 Microsoft SQL Server에서 반환 하는 오류 메시지의 id 번호입니다. *sql_message_id* 은 **int**이며 기본값은 NULL입니다.  
  
`[ @sql_severity = ] sql_severity`작업을 실행할 때 SQL Server에서 반환 하는 오류 메시지의 심각도 수준입니다. *sql_severity* 은 **int**이며 기본값은 NULL입니다.  
  
`[ @start_run_date = ] start_run_date`작업이 시작 된 날짜입니다. *start_run_date*은 **int**이며 기본값은 NULL입니다. *start_run_date* 은 YYYYMMDD 형식으로 입력 해야 합니다. 여기서 YYYY는 4 자리 연도, MM은 두 자리 월, DD는 두 자리 일입니다.  
  
`[ @end_run_date = ] end_run_date`작업이 완료 된 날짜입니다. *end_run_date* 은 **int**이며 기본값은 NULL입니다. *end_run_date*은 YYYYMMDD 형식으로 입력 해야 합니다. 여기서 YYYY는 4 자리 연도, MM은 두 자리 월, DD는 두 자리 일입니다.  
  
`[ @start_run_time = ] start_run_time`작업이 시작 된 시간입니다. *start_run_time* 은 **int**이며 기본값은 NULL입니다. *start_run_time*은 HHMMSS 형식으로 입력 해야 합니다. 여기서 HH는 두 자리 시간, MM은 두 자리 분, SS는 두 자리 초입니다.  
  
`[ @end_run_time = ] end_run_time`작업 실행을 완료 한 시간입니다. *end_run_time* 은 **int**이며 기본값은 NULL입니다. *end_run_time*은 HHMMSS 형식으로 입력 해야 합니다. 여기서 HH는 두 자리 시간, MM은 두 자리 분, SS는 두 자리 초입니다.  
  
`[ @minimum_run_duration = ] minimum_run_duration`작업을 완료 하는 데 소요 된 최소 시간입니다. *minimum_run_duration* 은 **int**이며 기본값은 NULL입니다. *minimum_run_duration*은 HHMMSS 형식으로 입력 해야 합니다. 여기서 HH는 두 자리 시간, MM은 두 자리 분, SS는 두 자리 초입니다.  
  
`[ @run_status = ] run_status`작업의 실행 상태입니다. *run_status* 은 **int**이며 기본값은 NULL이 고 다음 값 중 하나일 수 있습니다.  
  
|값|Description|  
|-----------|-----------------|  
|**0**|Failed|  
|**1**|Succeeded|  
|**2**|다시 시도(단계에만 적용됨)|  
|**3**|취소됨|  
|**4**|메시지 처리 중|  
|**5**|알 수 없음|  
  
`[ @minimum_retries = ] minimum_retries`작업 실행을 다시 시도해 야 하는 최소 횟수입니다. *minimum_retries* 은 **int**이며 기본값은 NULL입니다.  
  
`[ @oldest_first = ] oldest_first`가장 오래 된 작업의 출력을 먼저 표시할지 여부입니다. *oldest_first* 는 **int**이며 기본값은 최신 작업을 먼저 표시 하는 **0**입니다. **1** 은 가장 오래 된 작업을 먼저 표시 합니다.  
  
`[ @server = ] 'server'`작업이 수행 된 서버의 이름입니다. *서버* 는 **nvarchar (30)** 이며 기본값은 NULL입니다.  
  
`[ @mode = ] 'mode'`SQL Server 결과 집합의 모든 열 (**FULL**) 또는 열의 요약을 인쇄할지 여부입니다. *모드* 는 **varchar (7)** 이며 기본값은 **SUMMARY**입니다.  
  
## <a name="return-code-values"></a>반환 코드 값  
 **0** (성공) 또는 **1** (실패)  
  
## <a name="result-sets"></a>결과 집합  
 실제 열 목록은 *mode*의 값에 따라 달라 집니다. 가장 포괄적인 열 집합은 다음과 같이 표시 되며 *모드가* FULL 이면 반환 됩니다.  
  
|열 이름|데이터 형식|Description|  
|-----------------|---------------|-----------------|  
|**instance_id**|**int**|기록 항목 ID입니다.|  
|**job_id**|**uniqueidentifier**|작업 ID입니다.|  
|**job_name**|**sysname**|작업 이름입니다.|  
|**step_id**|**int**|단계 id 번호입니다 (작업 기록의 경우 **0** 이 됨).|  
|**step_name**|**sysname**|단계 이름입니다. 작업 기록의 경우 NULL입니다.|  
|**sql_message_id**|**int**|
  [!INCLUDE[tsql](../../includes/tsql-md.md)] 단계의 경우 명령 실행 중에 발생한 오류 중 가장 최근의 [!INCLUDE[tsql](../../includes/tsql-md.md)] 오류 번호입니다.|  
|**sql_severity**|**int**|
  [!INCLUDE[tsql](../../includes/tsql-md.md)] 단계의 경우 명령 실행 중에 발생한 오류 중 가장 높은 [!INCLUDE[tsql](../../includes/tsql-md.md)] 오류 심각도입니다.|  
|**메시지**|**nvarchar(1024)**|작업 또는 단계 기록 메시지입니다.|  
|**run_status**|**int**|작업 또는 단계의 결과입니다.|  
|**run_date**|**int**|작업 또는 단계가 실행을 시작한 날짜입니다.|  
|**run_time**|**int**|작업 또는 단계가 실행을 시작한 시간입니다.|  
|**run_duration**|**int**|HHMMSS 형식의 작업 또는 단계 실행의 경과 시간입니다.|  
|**operator_emailed**|**nvarchar (20)**|해당 작업에 관한 전자 메일을 받는 운영자입니다. 단계 기록의 경우에는 NULL입니다.|  
|**operator_netsent**|**nvarchar (20)**|해당 작업에 관한 네트워크 메시지를 받는 운영자입니다. 단계 기록의 경우에는 NULL입니다.|  
|**operator_paged**|**nvarchar (20)**|해당 작업에 관한 호출을 받는 운영자입니다. 단계 기록의 경우에는 NULL입니다.|  
|**retries_attempted**|**int**|단계를 다시 시도하는 횟수입니다. 작업 기록의 경우에는 항상 0입니다.|  
|**서버인**|**nvarchar (30)**|단계 또는 작업을 실행하는 서버입니다. 항상 (**local**)입니다.|  
  
## <a name="remarks"></a>설명  
 **sp_help_jobhistory** 는 지정 된 예약 된 작업의 기록이 포함 된 보고서를 반환 합니다. 매개 변수를 지정하지 않은 경우에는 보고서에 예정된 모든 작업에 관한 기록이 포함됩니다.  
  
## <a name="permissions"></a>사용 권한  
 기본적으로 **sysadmin** 고정 서버 역할의 멤버는이 저장 프로시저를 실행할 수 있습니다. 다른 사용자는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] msdb **데이터베이스의 다음** 에이전트 고정 데이터베이스 역할 중 하나를 부여 받아야 합니다.  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 이러한 역할의 사용 권한에 대한 자세한 내용은 [SQL Server 에이전트 고정 데이터베이스 역할](../../ssms/agent/sql-server-agent-fixed-database-roles.md)을 참조하세요.  
  
 **SQLAgentUserRole** 데이터베이스 역할의 멤버는 자신이 소유한 작업에 대 한 기록만 볼 수 있습니다.  
  
## <a name="examples"></a>예  
  
### <a name="a-listing-all-job-information-for-a-job"></a>A. 작업에 대한 모든 정보 나열  
 다음 예에서는 `NightlyBackups` 작업에 대한 모든 작업 정보를 나열합니다.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_help_jobhistory   
    @job_name = N'NightlyBackups' ;  
GO  
```  
  
### <a name="b-listing-information-for-jobs-that-match-certain-conditions"></a>B. 특정 조건에 일치하는 작업에 대한 정보 나열  
 다음 예에서는 실패한 작업과 실패한 작업 단계에 대한 모든 열과 모든 작업 정보를 `50100`(사용자 정의 오류 메시지) 오류 메시지 및 `20`의 심각도와 함께 출력합니다.  
  
```  
USE msdb  
GO  
  
EXEC dbo.sp_help_jobhistory  
    @sql_message_id = 50100,  
    @sql_severity = 20,  
    @run_status = 0,  
    @mode = N'FULL' ;  
GO  
```  
  
## <a name="see-also"></a>참고 항목  
 [Transact-sql&#41;sp_purge_jobhistory &#40;](../../relational-databases/system-stored-procedures/sp-purge-jobhistory-transact-sql.md)   
 [시스템 저장 프로시저&#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
