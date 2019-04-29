---
title: sys.dm_exec_query_optimizer_info (TRANSACT-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_exec_query_optimizer_info_TSQL
- dm_exec_query_optimizer_info
- sys.dm_exec_query_optimizer_info_TSQL
- sys.dm_exec_query_optimizer_info
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_exec_query_optimizer_info dynamic management view
ms.assetid: 1d72cef1-22d8-4ae0-91db-6694fe918c9e
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 7ca0db131690b0b734d7e42175f4ccfb4df6a381
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63013211"
---
# <a name="sysdmexecqueryoptimizerinfo-transact-sql"></a>sys.dm_exec_query_optimizer_info(Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 쿼리 최적화 프로그램의 작업에 대한 자세한 통계를 반환합니다. 쿼리 최적화 문제 또는 개선점을 식별하는 작업을 튜닝할 때 이 뷰를 사용할 수 있습니다. 예를 들어 총 최적화 수, 경과된 시간 값 및 최종 비용 값을 사용하여 현재 작업의 쿼리 최적화와 튜닝 프로세스 동안 관찰된 모든 변경 내용을 비교할 수 있습니다. 일부 카운터에서는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 내부 진단용으로만 사용되는 데이터를 제공합니다. 이러한 카운터는 "내부 전용"으로 표시됩니다.  
  
> [!NOTE]  
>  이를 호출 하 [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] 나 [!INCLUDE[ssPDW](../../includes/sspdw-md.md)], 이름을 사용 하 여 **sys.dm_pdw_nodes_exec_query_optimizer_info**합니다.  
  
|이름|데이터 형식|Description|  
|----------|---------------|-----------------|  
|**counter**|**nvarchar(4000)**|최적화 프로그램 통계 이벤트의 이름입니다.|  
|**occurrence**|**bigint**|이 카운터에 대한 최적화 이벤트의 발생 횟수입니다.|  
|**value**|**float**|이벤트 발생당 평균 속성 값입니다.|  
|**pdw_node_id**|**int**|**적용 대상**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)], [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> 이 배포에 있는 노드에 대 한 식별자입니다.|  
  
## <a name="permissions"></a>사용 권한  

온 [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], 필요한 `VIEW SERVER STATE` 권한.   
온 [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)], 필요를 `VIEW DATABASE STATE` 데이터베이스의 권한.   
    
## <a name="remarks"></a>Remarks  
 **sys.dm_exec_query_optimizer_info** (카운터) 다음 속성을 포함 합니다. 모든 occurrence 값은 누적 값이며 시스템을 다시 시작할 때 0으로 설정됩니다. value 필드의 모든 값은 시스템을 다시 시작할 때 NULL로 설정됩니다. 평균을 지정하는 모든 값 열의 값은 평균 계산의 분모와 같은 행에서 얻은 occurrence 값을 사용합니다. 모든 쿼리 최적화 때 측정 됩니다 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 변경 내용을 확인 **dm_exec_query_optimizer_info**, 사용자 및 시스템에서 생성 된 두 쿼리 모두를 포함 합니다. 이미 캐시 된 계획의 실행에 대 한 값을 변경 하지 **dm_exec_query_optimizer_info**, 최적화만 의미가 있습니다.  
  
|카운터|발생 빈도|값|  
|-------------|----------------|-----------|  
|optimizations|총 최적화 수입니다.|해당 사항 없음|  
|elapsed time|총 최적화 수입니다.|개별 문(쿼리)의 최적화당 평균 경과 시간(초)입니다.|  
|final cost|총 최적화 수입니다.|최적화된 계획의 평균 예상 비용(내부 비용 단위)입니다.|  
|trivial plan|내부 전용|내부 전용|  
|tasks|내부 전용|내부 전용|  
|no plan|내부 전용|내부 전용|  
|search 0|내부 전용|내부 전용|  
|search 0 time|내부 전용|내부 전용|  
|search 0 tasks|내부 전용|내부 전용|  
|search 1|내부 전용|내부 전용|  
|search 1 time|내부 전용|내부 전용|  
|search 1 tasks|내부 전용|내부 전용|  
|search 2|내부 전용|내부 전용|  
|search 2 time|내부 전용|내부 전용|  
|search 2 tasks|내부 전용|내부 전용|  
|gain stage 0 to stage 1|내부 전용|내부 전용|  
|gain stage 1 to stage 2|내부 전용|내부 전용|  
|timeout|내부 전용|내부 전용|  
|memory limit exceeded|내부 전용|내부 전용|  
|insert stmt|INSERT 문에 대한 최적화 수입니다.|해당 사항 없음|  
|delete stmt|DELETE 문에 대한 최적화 수입니다.|해당 사항 없음|  
|update stmt|UPDATE 문에 대한 최적화 수입니다.|해당 사항 없음|  
|contains subquery|하나 이상의 하위 쿼리를 포함하는 쿼리에 대한 최적화 수입니다.|해당 사항 없음|  
|unnest failed|내부 전용|내부 전용|  
|테이블|총 최적화 수입니다.|최적화된 쿼리당 참조된 평균 테이블 수입니다.|  
|힌트|일부 힌트가 지정된 횟수입니다. 계산 된 힌트는 다음과 같습니다. 조인, 그룹, UNION 및 FORCE ORDER 쿼리 힌트, FORCE PLAN 집합 옵션 및 조인 힌트를 제공 합니다.|해당 사항 없음|  
|order hint|FORCE ORDER 힌트가 지정된 횟수입니다.|해당 사항 없음|  
|join hint|조인 힌트를 통해 조인 알고리즘이 강제 적용된 횟수입니다.|해당 사항 없음|  
|view reference|쿼리에서 뷰가 참조된 횟수입니다.|해당 사항 없음|  
|remote query|쿼리에서 네 부분으로 된 이름이나 OPENROWSET 결과가 있는 테이블 등의 원격 데이터 원본을 하나 이상 참조한 최적화 수입니다.|해당 사항 없음|  
|maximum DOP|총 최적화 수입니다.|최적화된 계획에 대한 평균 유효 MAXDOP 값입니다. 기본적으로 유효 MAXDOP에서 결정 합니다 **최대 병렬 처리 수준** 서버 구성 옵션 및 MAXDOP 쿼리 힌트 값을 기준으로 특정 쿼리에 대해 재정의할 수 있습니다.|  
|maximum recursion level|0보다 큰 MAXRECURSION 수준이 쿼리 힌트와 함께 지정된 최적화 수입니다.|최대 재귀 수준이 쿼리 힌트와 함께 지정되는 최적화의 평균 MAXRECURSION 수준입니다.|  
|indexed views loaded|내부 전용|내부 전용|  
|indexed views matched|하나 이상의 인덱싱된 뷰가 일치된 최적화 수입니다.|일치된 평균 뷰 수입니다.|  
|indexed views used|일치된 후 하나 이상의 인덱싱된 뷰가 출력 계획에 사용되는 최적화 수입니다.|사용된 평균 뷰 수입니다.|  
|indexed views updated|하나 이상의 인덱싱된 뷰를 유지 관리하는 계획을 생성하는 DML 문의 최적화 수입니다.|유지 관리된 평균 뷰 수입니다.|  
|dynamic cursor request|동적 커서 요청이 지정된 최적화 수입니다.|해당 사항 없음|  
|fast forward cursor request|빠른 전진 커서 요청이 지정된 최적화 수입니다.|해당 사항 없음|  
|merge stmt|MERGE 문에 대한 최적화 수입니다.|해당 사항 없음|  
  
## <a name="examples"></a>예  
  
### <a name="a-viewing-statistics-on-optimizer-execution"></a>1. 최적화 프로그램 실행 통계 보기  
 이 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스에 대한 현재 최적화 프로그램 실행 통계를 확인할 수 있습니다.  
  
```  
SELECT * FROM sys.dm_exec_query_optimizer_info;  
```  
  
### <a name="b-viewing-the-total-number-of-optimizations"></a>2. 총 최적화 수 보기  
 최적화 수행 횟수를 알 수 있습니다.  
  
```  
SELECT occurrence AS Optimizations FROM sys.dm_exec_query_optimizer_info  
WHERE counter = 'optimizations';  
```  
  
### <a name="c-average-elapsed-time-per-optimization"></a>3. 최적화당 평균 경과 시간  
 최적화당 평균 경과 시간을 알 수 있습니다.  
  
```  
SELECT ISNULL(value,0.0) AS ElapsedTimePerOptimization  
FROM sys.dm_exec_query_optimizer_info WHERE counter = 'elapsed time';  
```  
  
### <a name="d-fraction-of-optimizations-that-involve-subqueries"></a>4. 하위 쿼리를 포함하는 최적화 부분  
 하위 쿼리를 포함하는 최적화 쿼리 부분을 확인할 수 있습니다.  
  
```  
SELECT (SELECT CAST (occurrence AS float) FROM sys.dm_exec_query_optimizer_info WHERE counter = 'contains subquery') /  
       (SELECT CAST (occurrence AS float)   
        FROM sys.dm_exec_query_optimizer_info WHERE counter = 'optimizations')  
        AS ContainsSubqueryFraction;  
```  
  
## <a name="see-also"></a>관련 항목  
 [동적 관리 뷰 및 함수&#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [실행 관련 동적 관리 뷰 및 함수&#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/execution-related-dynamic-management-views-and-functions-transact-sql.md)  
  
  


