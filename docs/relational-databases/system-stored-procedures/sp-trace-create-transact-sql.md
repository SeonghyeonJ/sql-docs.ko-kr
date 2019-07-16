---
title: sp_trace_create (TRANSACT-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_trace_create_TSQL
- sp_trace_create
dev_langs:
- TSQL
helpviewer_keywords:
- sp_trace_create
ms.assetid: f3a43597-4c5a-4520-bcab-becdbbf81d2e
author: stevestein
ms.author: sstein
ms.openlocfilehash: 7d698932bb7ef7e0fd37a0ced8ab536eeb0d5d68
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68096027"
---
# <a name="sptracecreate-transact-sql"></a>sp_trace_create(Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  추적 정의를 만듭니다. 새 추적은 중지된 상태가 됩니다.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] 확장 이벤트를 대신 사용하세요.  
  
 ![항목 링크 아이콘](../../database-engine/configure-windows/media/topic-link.gif "항목 링크 아이콘") [Transact-SQL 구문 규칙](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>구문  
  
```  
  
sp_trace_create [ @traceid = ] trace_id OUTPUT   
          , [ @options = ] option_value   
          , [ @tracefile = ] 'trace_file'   
     [ , [ @maxfilesize = ] max_file_size ]  
     [ , [ @stoptime = ] 'stop_time' ]  
     [ , [ @filecount = ] 'max_rollover_files' ]  
```  
  
## <a name="arguments"></a>인수  
`[ @traceid = ] trace_id` 할당입니다 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 를 새 추적 합니다. 모든 사용자 제공 입력은 무시됩니다. *trace_id* 됩니다 **int**, 기본값은 NULL입니다. 사용자를 사용 합니다 *trace_id* 식별, 수정 및이 저장된 프로시저에 정의 된 추적을 제어 하는 값입니다.  
  
`[ @options = ] option_value` 추적에 대해 설정 된 옵션을 지정 합니다. *option_value* 됩니다 **int**, 기본값은 없습니다. 선택한 옵션 값의 합계를 지정하여 이러한 옵션의 조합을 선택할 수 있습니다. 예를 들어 TRACE_FILE_ROLLOVER와 shutdown_on_error 두 두 옵션을 켜려면 지정할 **6** 에 대 한 *option_value*합니다.  
  
 다음 표에서는 옵션, 설명 및 해당 값을 나열합니다.  
  
|옵션 이름|옵션 값|설명|  
|-----------------|------------------|-----------------|  
|TRACE_FILE_ROLLOVER|**2**|되도록 지정 합니다 *max_file_size* 에 도달 하면 현재 추적 파일이 닫히고 새 파일이 만들어집니다. 모든 새 기록은 새 파일에 기록합니다. 새 파일은 이전 파일과 같은 이름을 갖지만 정수를 붙여 시퀀스를 표시합니다. 예를 들어 원래 추적 파일 이름이 filename.trc이면, 다음 추적 파일 이름은 filename_1.trc이고 그 다음은 filename_2.trc의 식으로 명명됩니다.<br /><br /> 롤오버 추적 파일이 많이 생성될수록 파일 이름에 붙이는 정수 값도 순차적으로 증가합니다.<br /><br /> SQL Server의 기본 값을 사용 하 여 *max_file_size* (5MB) 값을 지정 하지 않고이 옵션을 지정 하는 경우 *max_file_size*합니다.|  
|SHUTDOWN_ON_ERROR|**4**|어떤 이유에서건 추적을 파일에 쓸 수 없으면 SQL Server가 시스템을 종료하도록 지정합니다. 이 옵션은 보안 감사 추적을 수행할 때 유용합니다.|  
|TRACE_PRODUCE_BLACKBOX|**8**|서버가 만든 마지막 5MB 추적 정보의 기록은 서버에 의해 저장됨을 지정합니다. TRACE_PRODUCE_BLACKBOX는 다른 모든 옵션과 호환되지 않습니다.|  
  
`[ @tracefile = ] 'trace_file'` 추적을 쓸 파일 이름과 위치를 지정 합니다. *trace_file* 됩니다 **nvarchar(245)** 기본값은 없습니다. *trace_file* (N 'C:\MSSQL\Trace\trace.trc')와 같은 로컬 디렉터리 또는 공유 또는 경로의 UNC 일 수 있습니다 (N'\\\\*Servername*\\*Sharename* \\ *Directory*\trace.trc').  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 추가 되는 **.trc** 모든 추적 파일 이름에는 확장 합니다. 경우 TRACE_FILE_ROLLOVER 옵션으로 *max_file_size* 지정 된 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 원래 추적 파일 최대 크기에 도달한 경우 새 추적 파일을 만듭니다. 새 파일 이름이 동일한 원본 파일을 하지만 _*n* 부터 시퀀스를 나타내는 추가할 **1**합니다. 예를 들어 첫 번째 추적 파일의 이름이 **filename.trc**, 두 번째 추적 파일의 이름이 **filename_1.trc**합니다.  
  
 TRACE_FILE_ROLLOVER 옵션을 사용하는 경우 원래 추적 파일 이름에 밑줄 문자를 사용하지 않는 것이 좋습니다. 밑줄을 사용할 경우 다음 동작이 발생합니다.  
  
-   [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 부하를 자동으로 않습니다 또는 (이러한 파일 롤오버 옵션 중 하나는 구성 된 경우)에서 롤오버 파일을 로드 하 라는 메시지가 표시 됩니다.  
  
-   Fn_trace_gettable 함수 롤오버 파일을 로드 하지 않습니다 (사용 하 여 지정 합니다 *number_files* 인수)는 원래 파일 이름이 밑줄과 숫자 값으로 끝나는 합니다. 이는 파일이 롤오버될 때 자동으로 추가된 밑줄과 숫자에는 적용되지 않습니다.  
  
> [!NOTE]  
>  추적 파일의 이름을 변경하여 원래 파일 이름에서 밑줄을 제거하면 이러한 문제를 모두 해결할 수 있습니다. 예를 들어 원래 파일 이름이 **my_trace.trc**, 있고 롤오버 파일 이름이 **my_trace_1.trc**에서 파일 이름을 바꿀 수 있습니다 **경우** 및 **mytrace_1.trc** 파일을 열기 전에 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]입니다.  
  
 *trace_file* TRACE_PRODUCE_BLACKBOX 옵션을 사용 하는 경우 지정할 수 없습니다.  
  
`[ @maxfilesize = ] max_file_size` 메가바이트 (MB) 추적 파일의에서 최대 크기가 커질 수를 지정 합니다. *max_file_size* 됩니다 **bigint**, 기본값은 **5**합니다.  
  
 추적이 사용 된 디스크 공간으로 지정 된 크기를 초과 하는 경우의 파일 기록이 중지 TRACE_FILE_ROLLOVER 옵션 없이이 매개 변수를 지정 합니다 *max_file_size*합니다.  
  
`[ @stoptime = ] 'stop_time'` 날짜 및 시간 추적을 중지할 지정 합니다. *stop_time* 됩니다 **datetime**, 기본값은 NULL입니다. NULL일 경우 추적은 수동으로 중지하거나 서버가 시스템을 종료할 때까지 계속 실행됩니다.  
  
 둘 다 *stop_time* 하 고 *max_file_size* 지정 된 TRACE_FILE_ROLLOVER 아니며 추적 위쪽 지정 하면 지정 된 중지 시간 또는 최대 파일 크기에 도달한 경우입니다. 하는 경우 *stop_time*를 *max_file_size*, TRACE_FILE_ROLLOVER를 지정 하면를 지정 된 중지 시간에 중지 추적 추적 드라이브를 채우지 않을 것으로 가정 합니다.  
  
`[ @filecount = ] 'max_rollover_files'` 동일한 기본 파일 이름으로 유지할 수 최대 추적 파일을 지정 합니다. *max_rollover_files* 됩니다 **int**1 보다 큰 합니다. 이 매개 변수는 TRACE_FILE_ROLLOVER 옵션을 지정한 경우에만 유효합니다. 때 *max_rollover_files* 를 지정 하면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 유지 하려고 둘 *max_rollover_files* 새 추적 파일을 열기 전에 가장 오래 된 추적 파일을 삭제 하 여 파일을 추적 합니다. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서는 기본 파일 이름에 숫자를 추가하여 추적 파일의 보존 기간을 추적합니다.  
  
 예를 들어 경우는 *trace_file* 매개 변수 이름 "c:\mytrace_123.trc" 파일 이름 "c:\mytrace_124.trc" 파일 보다 오래 된 "c:\mytrace"로 지정 됩니다. 하는 경우 *max_rollover_files* 가 2로 설정 "c:\mytrace_123.trc" 파일을 삭제 하는 SQL Server "c:\mytrace_125.trc" 추적 파일을 만들기 전에 합니다.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서는 각 파일을 한 번만 삭제하려고 시도하며 다른 프로세스에서 사용 중인 파일은 삭제할 수 없습니다. 그러므로 추적을 실행하는 동안 다른 응용 프로그램에서 추적 파일을 사용하는 경우 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서는 이 추적 파일을 파일 시스템에 유지합니다.  
  
## <a name="return-code-values"></a>반환 코드 값  
 아래 표에서는 저장 프로시저가 완료된 후 사용자가 얻을 수 있는 코드 값을 설명합니다.  
  
|반환 코드|Description|  
|-----------------|-----------------|  
|0|오류가 없습니다.|  
|1|알 수 없는 오류입니다.|  
|10|잘못된 옵션입니다. 지정한 옵션이 호환되지 않으면 반환됩니다.|  
|12|파일이 생성되지 않았습니다.|  
|13|메모리가 부족합니다. 지정한 동작을 수행할 메모리가 충분하지 않으면 반환됩니다.|  
|14|잘못된 중지 시간입니다. 지정한 중지 시간이 이미 지난 경우 반환됩니다.|  
|15|잘못된 매개 변수입니다. 사용자가 호환되지 않는 매개 변수를 제공하면 반환됩니다.|  
  
## <a name="remarks"></a>설명  
 **sp_trace_create** 되는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 저장 프로시저를 실행 하 던 작업의 대부분을 수행 **xp_trace_\***  확장 저장된 프로시저의 SQL Server 이전 버전에서 사용할 수 있습니다. 사용 하 여 **sp_trace_create** 대신:  
  
-   **xp_trace_addnewqueue**  
  
-   **xp_trace_setqueuecreateinfo**  
  
-   **xp_trace_setqueuedestination**  
  
 **sp_trace_create** 만 추적 정의 만듭니다. 추적을 시작하거나 변경하는 데 사용할 수 없는 저장 프로시저입니다.  
  
 모든 SQL Trace 저장 프로시저(**sp_trace_xx**)의 매개 변수는 엄격하게 형식이 지정되어 있습니다. 이러한 매개 변수가 인수 설명에서 지정한대로 정확한 입력 매개 변수 데이터 형식으로 호출되지 않으면 저장 프로시저는 오류를 반환합니다.  
  
 에 대 한 **sp_trace_create**, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 서비스 계정에 추적 파일 폴더에 대 한 쓰기 권한이 있어야 합니다. 추적 파일이 있는 컴퓨터에서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 서비스 계정이 관리자가 아닌 경우 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 서비스 계정에 명시적으로 쓰기 권한을 부여해야 합니다.  
  
> [!NOTE]  
>  사용 하 여 만든 추적 파일을 자동으로 로드할 수 있습니다 **sp_trace_create** 사용 하 여 테이블에는 **fn_trace_gettable** 시스템 함수입니다. 이 시스템 함수를 사용 하는 방법에 대 한 정보를 참조 하세요 [sys.fn_trace_gettable &#40;TRANSACT-SQL&#41;](../../relational-databases/system-functions/sys-fn-trace-gettable-transact-sql.md)합니다.  
  
 추적 저장 프로시저 사용에 대한 예는 [추적 만들기&#40;Transact-SQL&#41;](../../relational-databases/sql-trace/create-a-trace-transact-sql.md)를 참조하세요.  
  
 **TRACE_PRODUCE_BLACKBOX** 다음과 같은 특징이 있습니다.  
  
-   이 옵션은 롤오버 추적입니다. 기본값 *file_count* 는 2 이지만 사용자 사용 하 여 재정의할 수 있습니다 *filecount* 옵션입니다.  
  
-   기본값 *file_size* 5MB는 다른 추적과 변경할 수 있습니다.  
  
-   파일 이름을 지정할 수 없습니다. 파일으로 저장 됩니다. **N'%SQLDIR%\MSSQL\DATA\blackbox.trc'**  
  
-   이 추적에는 다음과 같은 이벤트와 이러한 이벤트의 열만 포함됩니다.  
  
    -   **RPC 시작**  
  
    -   **일괄 처리 시작**  
  
    -   **Exception**  
  
    -   **주의**  
  
-   이 추적에서는 이벤트나 열을 추가 또는 제거할 수 없습니다.  
  
-   이 추적에는 필터를 지정할 수 없습니다.  
  
## <a name="permissions"></a>사용 권한  
 사용자는 ALTER TRACE 권한이 있어야 합니다.  
  
## <a name="see-also"></a>관련 항목  
 [sp_trace_generateevent &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-generateevent-transact-sql.md)   
 [sp_trace_setevent&#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql.md)   
 [sp_trace_setfilter&#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-setfilter-transact-sql.md)   
 [sp_trace_setstatus&#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-setstatus-transact-sql.md)   
 [SQL 추적](../../relational-databases/sql-trace/sql-trace.md)  
  
  
