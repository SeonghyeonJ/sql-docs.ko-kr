---
title: sys. fn_trace_getfilterinfo (Transact-sql) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- fn_trace_getfilterinfo
- fn_trace_getfilterinfo_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- status information [SQL Server], filters
- sys.fn_trace_getfilterinfo function
- filters [SQL Server], traces
- fn_trace_getfilterinfo function
ms.assetid: 09fe4a28-ff8a-4655-9da1-4654d5bc514d
author: rothja
ms.author: jroth
ms.openlocfilehash: 79b86365703160ef6f15f8fd89805961997a61e4
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/02/2020
ms.locfileid: "85898295"
---
# <a name="sysfn_trace_getfilterinfo-transact-sql"></a>sys.fn_trace_getfilterinfo(Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  지정된 추적에 적용되는 필터에 대한 정보를 반환합니다.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] 확장 이벤트를 대신 사용하세요.  
  
 
 ![항목 링크 아이콘](../../database-engine/configure-windows/media/topic-link.gif "항목 링크 아이콘") [Transact-SQL 구문 표기 규칙](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>구문  
  
```  
  
fn_trace_getfilterinfo ( trace_id )  
```  
  
## <a name="arguments"></a>인수  
 *trace_id*  
 추적의 ID입니다. *trace_id* 는 **int**이며 기본값은 없습니다.  
  
## <a name="tables-returned"></a>반환된 테이블  
 다음 정보를 반환합니다. 열에 대 한 자세한 내용은 [sp_trace_setfilter &#40;transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-trace-setfilter-transact-sql.md)을 참조 하십시오.  
  
|열 이름|데이터 형식|Description|  
|-----------------|---------------|-----------------|  
|**columnid**|**int**|필터가 적용되는 열의 ID입니다.|  
|**logical_operator**|**int**|AND 또는 OR 연산자의 적용 여부를 지정합니다.|  
|**comparison_operator**|**int**|비교 유형을 지정합니다.<br /><br /> 0 = 같음<br /><br /> 1 = 같지 않음<br /><br /> 2 = 보다 큼<br /><br /> 3 = 보다 작음<br /><br /> 4 = 크거나 같음<br /><br /> 5 = 작거나 같음<br /><br /> 6 = 유사함<br /><br /> 7 = 유사하지 않음|  
|**value**|**sql_variant**|필터가 적용되는 값을 지정합니다.|  
  
## <a name="remarks"></a>설명  
 사용자는 *trace_id* 값을 설정 하 여 추적을 식별, 수정 및 제어할 수 있습니다. 특정 추적의 ID를 전달 하면 **fn_trace_getfilterinfo** 는 해당 추적의 필터에 대 한 정보를 반환 합니다. 지정된 추적에 필터가 없는 경우 이 함수는 빈 행 집합을 반환합니다. 잘못된 ID를 전달하면 빈 행 집합이 반환됩니다. 추적에 대 한 유사한 정보는 [fn_trace_getinfo &#40;transact-sql&#41;](../../relational-databases/system-functions/sys-fn-trace-getinfo-transact-sql.md)을 참조 하십시오.  
  
## <a name="permissions"></a>사용 권한  
 서버에 대한 ALTER TRACE 권한이 필요합니다.  
  
## <a name="examples"></a>예  
 다음 예에서는 추적 번호 2에 대한 모든 필터 정보를 반환합니다.  
  
```  
SELECT * FROM fn_trace_getfilterinfo(2) ;  
GO  
  
```  
  
## <a name="see-also"></a>참고 항목  
 [Transact-sql&#41;&#40;추적 만들기](../../relational-databases/sql-trace/create-a-trace-transact-sql.md)   
 [Transact-sql&#41;sp_trace_setfilter &#40;](../../relational-databases/system-stored-procedures/sp-trace-setfilter-transact-sql.md)   
 [Transact-sql&#41;sp_trace_create &#40;](../../relational-databases/system-stored-procedures/sp-trace-create-transact-sql.md)   
 [Transact-sql&#41;sp_trace_generateevent &#40;](../../relational-databases/system-stored-procedures/sp-trace-generateevent-transact-sql.md)   
 [Transact-sql&#41;sp_trace_setevent &#40;](../../relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql.md)   
 [Transact-sql&#41;sp_trace_setstatus &#40;](../../relational-databases/system-stored-procedures/sp-trace-setstatus-transact-sql.md)   
 [fn_trace_geteventinfo &#40;Transact-sql&#41;](../../relational-databases/system-functions/sys-fn-trace-geteventinfo-transact-sql.md)   
 [fn_trace_getinfo &#40;Transact-sql&#41;](../../relational-databases/system-functions/sys-fn-trace-getinfo-transact-sql.md)   
 [fn_trace_gettable &#40;Transact-sql&#41;](../../relational-databases/system-functions/sys-fn-trace-gettable-transact-sql.md)  
  
  
