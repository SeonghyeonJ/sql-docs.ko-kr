---
title: sys.dm_exec_query_plan (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 08/02/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_exec_query_plan_TSQL
- sys.dm_exec_query_plan
- dm_exec_query_plan
- sys.dm_exec_query_plan_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_exec_query_plan dynamic management function
ms.assetid: e26f0867-9be3-4b2e-969e-7f2840230770
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: c879af413bd8b3cf4b90e8112f10e5f756201148
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63013270"
---
# <a name="sysdmexecqueryplan-transact-sql"></a>sys.dm_exec_query_plan(Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

계획 핸들로 지정한 일괄 처리에 대한 XML 형식의 실행 계획을 반환합니다. 계획 핸들로 지정된 계획은 캐시되거나 현재 실행 중일 수 있습니다.  
  
실행 계획 XML 스키마는 게시 및에서 사용할 수 있습니다 [Microsoft 웹 사이트](https://go.microsoft.com/fwlink/?linkid=43100&clcid=0x409)합니다. 또한 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]이 설치된 디렉터리에서도 사용할 수 있습니다.  
  
 ![항목 링크 아이콘](../../database-engine/configure-windows/media/topic-link.gif "항목 링크 아이콘") [Transact-SQL 구문 규칙](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>구문  
  
```  
sys.dm_exec_query_plan(plan_handle)  
```  
  
## <a name="arguments"></a>인수  
*plan_handle*  
실행 된 일괄 처리에 대 한 쿼리 실행 계획을 고유 하 게 식별 하는 토큰 및 해당 계획은 계획 캐시에 되거나 현재 실행 합니다. *plan_handle* 됩니다 **varbinary(64)** 합니다.   

합니다 *plan_handle* 다음 동적 관리 개체에서 가져올 수 있습니다.
  
-   [sys.dm_exec_cached_plans &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-cached-plans-transact-sql.md)  
  
-   [sys.dm_exec_query_stats&#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-stats-transact-sql.md)  
  
-   [sys.dm_exec_requests&#40;Transact-SQL&#41](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md)  

-   [sys.dm_exec_procedure_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-procedure-stats-transact-sql.md)  

-   [sys.dm_exec_trigger_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-trigger-stats-transact-sql.md)  
  
## <a name="table-returned"></a>반환된 테이블  
  
|열 이름|데이터 형식|Description|  
|-----------------|---------------|-----------------|  
|**dbid**|**smallint**|이 계획에 해당하는 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문을 컴파일할 당시 유효했던 컨텍스트 데이터베이스의 ID입니다. 임시 및 준비된 SQL 문의 경우 문이 컴파일된 데이터베이스의 ID입니다.<br /><br /> 열이 Null 값을 허용합니다.|  
|**objectid**|**int**|이 쿼리 계획에 대한 저장 프로시저나 사용자 정의 함수와 같은 개체의 ID입니다. 임시 및 준비 된 일괄 처리에 대 한이 열은 **null**.<br /><br /> 열이 Null 값을 허용합니다.|  
|**number**|**smallint**|번호가 매겨진 저장 프로시저 정수입니다. 등의 절차에 대 한 그룹의 **주문** 응용 프로그램 이름은 **orderproc; 1**, **orderproc; 2**등. 임시 및 준비 된 일괄 처리에 대 한이 열은 **null**.<br /><br /> 열이 Null 값을 허용합니다.|  
|**encrypted**|**bit**|해당 저장 프로시저가 암호화되었는지 여부를 나타냅니다.<br /><br /> 0 = 암호화되지 않음<br /><br /> 1 = 암호화됨<br /><br /> 열은 Null을 허용하지 않습니다.|  
|**query_plan**|**xml**|로 지정 된 쿼리 실행 계획의 컴파일 시간 실행 계획 표현을 포함 *plan_handle*합니다. 실행 계획은 XML 형식입니다. 임시 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문, 저장 프로시저 호출, 사용자 정의 함수 호출 등이 포함된 각 일괄 처리에 대해 계획 하나가 생성됩니다.<br /><br /> 열이 Null 값을 허용합니다.|  
  
## <a name="remarks"></a>Remarks  
 다음과 같은 경우 실행 계획 출력이 반환 된 **query_plan** 에 대 한 반환된 된 테이블의 열 **sys.dm_exec_query_plan**:  
  
-   쿼리 계획이 있는 경우 사용 하 여 지정 된 *plan_handle* 계획 캐시에서 제거 되었습니다. 합니다 **query_plan** 반환된 된 테이블의 열은 null입니다. 계획 핸들을 캡처한 경우 사용 된 경우 사이의 시간 지연이 있는 경우이 상황이 발생할 수 있습니다 예를 들어 **sys.dm_exec_query_plan**합니다.  
  
-   대량 작업 문이나 8KB를 넘는 문자열 리터럴이 포함된 문과 같은 일부 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문은 캐시되지 않습니다. 이러한 문의 XML 실행 계획을 사용 하 여 검색할 수 없습니다 **sys.dm_exec_query_plan** 캐시에 없기 때문에 일괄 처리가 현재 실행 중인 경우가 아니면 합니다.  
  
-   경우는 [!INCLUDE[tsql](../../includes/tsql-md.md)] 일괄 처리 또는 저장된 프로시저 예를 들어 EXEC를 사용 하 여 동적 sql 호출이 나 사용자 정의 함수 호출 포함 (*문자열*), 사용자 정의 함수를 테이블에 포함 되지 않습니다에 대해 컴파일된 XML 실행 계획 반환한 **sys.dm_exec_query_plan** 일괄 처리 또는 저장된 프로시저에 대 한 합니다. 에 대 한 별도 호출 대신 해야 **sys.dm_exec_query_plan** 사용자 정의 함수에 해당 하는 계획 핸들에 대 한 합니다.  
  
 임시 쿼리를 간단 하거나 강제 매개 변수화를 사용 하는 경우는 **query_plan** 문 텍스트만 및 실제 쿼리 계획 하지 열이 포함 됩니다. 쿼리 계획을 반환 하려면 호출 **sys.dm_exec_query_plan** 준비 된 매개 변수가 있는 쿼리의 계획 핸들에 대 한 합니다. 참조 하 여 쿼리 매개 변수화 되었는지 여부를 확인할 수 있습니다는 **sql** 열을 [sys.syscacheobjects](../../relational-databases/system-compatibility-views/sys-syscacheobjects-transact-sql.md) 뷰 또는 텍스트 열을는 [sys.dm_exec_sql_text](../../relational-databases/system-dynamic-management-views/sys-dm-exec-sql-text-transact-sql.md)동적 관리 뷰.  
  
> [!NOTE] 
> 에 허용 된 중첩된 수준 수가 제한으로 인해 합니다 **xml** 데이터 형식 **sys.dm_exec_query_plan** 중첩 요소의 128 수준을 충족 하거나 초과 하는 쿼리 계획을 반환할 수 없습니다. 이전 버전의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서는 이 상태로 인해 쿼리 계획을 반환하지 못했으므로 오류 6335가 발생합니다. [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 서비스 팩 2 및 이후 버전에서는 합니다 **query_plan** 열 NULL을 반환 합니다.   
> 사용할 수는 [sys.dm_exec_text_query_plan &#40;TRANSACT-SQL&#41; ](../../relational-databases/system-dynamic-management-views/sys-dm-exec-text-query-plan-transact-sql.md) 동적 관리 함수를 텍스트 형식의 쿼리 계획의 출력을 반환 합니다.  
  
## <a name="permissions"></a>사용 권한  
 실행할 **sys.dm_exec_query_plan**, 사용자의 멤버 여야 합니다.는 **sysadmin** 있거나 고정 서버 역할은 `VIEW SERVER STATE` 서버에 대 한 권한.  
  
## <a name="examples"></a>예  
 다음 예제에서는 사용 하는 방법을 표시 합니다 **sys.dm_exec_query_plan** 동적 관리 뷰.  
  
 XML 실행 계획을 보려면 다음 쿼리를 실행의 쿼리 편집기에서 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], 클릭 **ShowPlanXML** 에 **query_plan** 반환한 테이블의 열 **sys.dm _ exec_query_plan**합니다. [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 보고서 요약 창에 XML 실행 계획이 표시됩니다. XML 실행 계획을 파일로 저장 하려면 마우스 오른쪽 단추로 클릭 **ShowPlanXML** 에 **query_plan** 열을 클릭 **이름으로 결과 저장**, 형식으로 파일 이름을 \< *file_name*>.sqlplan; 예를 들어 MyXMLShowplan.sqlplan 합니다.  
  
### <a name="a-retrieve-the-cached-query-plan-for-a-slow-running-transact-sql-query-or-batch"></a>1\. 실행 속도가 느린 Transact-SQL 쿼리 또는 일괄 처리에 대한 캐시된 쿼리 계획 검색  
 임시 일괄 처리, 저장 프로시저, 사용자 정의 함수 등 다양한 유형의 [!INCLUDE[tsql](../../includes/tsql-md.md)] 일괄 처리에 대한 쿼리 계획은 계획 캐시라는 메모리 영역에서 캐시됩니다. 캐시된 쿼리 계획 각각은 계획 핸들이라는 고유 식별자로 식별됩니다. 이 계획 핸들을 지정할 수 있습니다 합니다 **sys.dm_exec_query_plan** 동적 관리 뷰를 특정 실행 계획을 검색할 [!INCLUDE[tsql](../../includes/tsql-md.md)] 쿼리 또는 일괄 처리 합니다.  
  
 [!INCLUDE[tsql](../../includes/tsql-md.md)]에 대한 특정 연결에서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 쿼리 또는 일괄 처리가 오랫동안 실행되는 경우 이 쿼리나 일괄 처리에 대한 실행 계획을 검색하여 지연 원인을 알아낼 수 있습니다. 다음 예에서는 실행 속도가 느린 쿼리나 일괄 처리에 대한 XML 실행 계획을 검색하는 방법을 보여 줍니다.  
  
> [!NOTE]  
>  이 예제를 실행 하려면 값을 바꿉니다 *session_id* 하 고 *plan_handle* 서버로 지정 된 값입니다.  
  
 먼저 `sp_who` 저장 프로시저를 사용하여 쿼리 또는 일괄 처리를 실행 중인 프로세스의 SPID(서버 프로세스 ID)를 검색합니다.  
  
```sql  
USE master;  
GO  
exec sp_who;  
GO  
```  
  
 `sp_who`에 의해 반환되는 결과 집합은 SPID가 `54`임을 나타냅니다. `sys.dm_exec_requests` 동적 관리 뷰에 이 SPID를 사용하여 다음 쿼리를 통해 계획 핸들을 검색할 수 있습니다.  
  
```sql  
USE master;  
GO  
SELECT * FROM sys.dm_exec_requests  
WHERE session_id = 54;  
GO  
```  
  
 반환 되는 테이블 **sys.dm_exec_requests** 실행 속도가 느린 쿼리나 일괄 처리에 대 한 계획 핸들 임을 나타냅니다 `0x06000100A27E7C1FA821B10600`,으로 지정할 수 있는 합니다 *plan_handle* 인수`sys.dm_exec_query_plan` 를 다음과 같이 XML 형식의 실행 계획을 검색 합니다. 실행 속도가 느린 쿼리나 일괄 처리에 대 한 XML 형식의 실행 계획에 포함 된 **query_plan** 반환한 테이블의 열 `sys.dm_exec_query_plan`.  
  
```sql  
USE master;  
GO  
SELECT * 
FROM sys.dm_exec_query_plan (0x06000100A27E7C1FA821B10600);  
GO  
```  
  
### <a name="b-retrieve-every-query-plan-from-the-plan-cache"></a>2\. 계획 캐시에서 모든 쿼리 계획 검색  
 계획 캐시에 있는 모든 쿼리 계획의 스냅숏을 검색하려면 `sys.dm_exec_cached_plans` 동적 관리 뷰를 쿼리하여 캐시에 있는 모든 쿼리 계획의 계획 핸들을 검색합니다. 계획 핸들은 `plan_handle`의 `sys.dm_exec_cached_plans` 열에 저장됩니다. 그런 다음 CROSS APPLY 연산자를 사용하여 다음과 같이 계획 핸들을 `sys.dm_exec_query_plan`으로 전달합니다. 계획 캐시에 있는 각 계획의 XML 실행 계획 출력은 현재 반환된 테이블의 `query_plan` 열에 있습니다.  
  
```sql  
USE master;  
GO  
SELECT * 
FROM sys.dm_exec_cached_plans AS cp 
CROSS APPLY sys.dm_exec_query_plan(cp.plan_handle);  
GO  
```  
  
### <a name="c-retrieve-every-query-plan-for-which-the-server-has-gathered-query-statistics-from-the-plan-cache"></a>3\. 서버가 계획 캐시에서 쿼리 통계를 수집한 모든 쿼리 계획 검색  
 서버가 통계를 수집한 현재 계획 캐시에 있는 모든 쿼리 계획의 스냅숏을 검색하려면 `sys.dm_exec_query_stats` 동적 관리 뷰를 쿼리하여 캐시에서 이 계획의 계획 핸들을 검색합니다. 계획 핸들은 `plan_handle`의 `sys.dm_exec_query_stats` 열에 저장됩니다. 그런 다음 CROSS APPLY 연산자를 사용하여 다음과 같이 계획 핸들을 `sys.dm_exec_query_plan`으로 전달합니다. 서버가 통계를 수집한 현재 계획 캐시에 있는 각 계획의 XML 실행 계획 출력은 반환된 테이블의 `query_plan` 열에 있습니다.  
  
```sql  
USE master;  
GO  
SELECT * 
FROM sys.dm_exec_query_stats AS qs 
CROSS APPLY sys.dm_exec_query_plan(qs.plan_handle);  
GO  
```  
  
### <a name="d-retrieve-information-about-the-top-five-queries-by-average-cpu-time"></a>4\. 평균 CPU 시간별 상위 5개 쿼리에 대한 정보 검색  
 다음 예에서는 상위 5개 쿼리에 대한 계획과 평균 CPU 시간을 반환합니다.  
  
```sql  
SELECT TOP 5 total_worker_time/execution_count AS [Avg CPU Time],  
   plan_handle, query_plan   
FROM sys.dm_exec_query_stats AS qs  
CROSS APPLY sys.dm_exec_query_plan(qs.plan_handle)  
ORDER BY total_worker_time/execution_count DESC;  
GO  
```  
  
## <a name="see-also"></a>관련 항목  
 [동적 관리 뷰 및 함수&#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [sys.dm_exec_cached_plans &#40;Transact SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-cached-plans-transact-sql.md)   
 [sys.dm_exec_query_stats &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-stats-transact-sql.md)   
 [sys.dm_exec_requests &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md)   
 [sp_who&#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-who-transact-sql.md)   
 [실행 계획 논리 및 물리 연산자 참조](../../relational-databases/showplan-logical-and-physical-operators-reference.md)   
 [sys.dm_exec_text_query_plan &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-text-query-plan-transact-sql.md)  
  
  
