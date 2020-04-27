---
title: sys. fn_cdc_map_lsn_to_time (Transact-sql) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.fn_cdc_map_lsn_to_time_TSQL
- sys.fn_cdc_map_lsn_to_time
- fn_cdc_map_lsn_to_time_TSQL
- fn_cdc_map_lsn_to_time
dev_langs:
- TSQL
helpviewer_keywords:
- sys.fn_cdc_map_lsn_to_time
- fn_cdc_map_lsn_to_time
ms.assetid: 405aa29c-8bd8-42d3-9f39-7494b643fc6f
author: rothja
ms.author: jroth
ms.openlocfilehash: c3573b876a10b4400969bf63200682e91bfc45fb
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/26/2020
ms.locfileid: "68046342"
---
# <a name="sysfn_cdc_map_lsn_to_time-transact-sql"></a>sys.fn_cdc_map_lsn_to_time(Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  지정 된 LSN (로그 시퀀스 번호)에 대해 [lsn_time_mapping](../../relational-databases/system-tables/cdc-lsn-time-mapping-transact-sql.md) 시스템 테이블의 **tran_end_time** 열에서 날짜 및 시간 값을 반환 합니다. 이 함수를 사용하여 변경 테이블의 날짜 범위에 LSN 범위를 체계적으로 매핑할 수 있습니다.  
  
 ![항목 링크 아이콘](../../database-engine/configure-windows/media/topic-link.gif "항목 링크 아이콘") [Transact-SQL 구문 표기 규칙](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>구문  
  
```  
  
sys.fn_cdc_map_lsn_to_time ( lsn_value )  
```  
  
## <a name="arguments"></a>인수  
 *lsn_value*  
 대조할 LSN 값입니다. *lsn_value* 는 **binary (10)** 입니다.  
  
## <a name="return-type"></a>반환 형식  
 **datetime**  
  
## <a name="remarks"></a>설명  
 이 함수를 사용 하 여 변경 데이터의 행에서 반환 된 **__ $ start_lsn** 값에 따라 변경 내용이 커밋된 시간을 확인할 수 있습니다.  
  
## <a name="permissions"></a>사용 권한  
 **public** 역할의 멤버 자격이 필요합니다.  
  
## <a name="examples"></a>예  
 다음 예에서는 `sys.fn_cdc_map_lsn_to_time` 함수를 사용하여 `HumanResources_Employee` 캡처 인스턴스에 대해 지정된 LSN 간격에서 처리된 마지막 변경에 관련된 커밋 시간을 확인합니다.  
  
```  
USE AdventureWorks2012;  
GO  
DECLARE @max_lsn binary(10);  
SELECT @max_lsn = MAX(__$start_lsn)  
FROM cdc.fn_cdc_get_all_changes_HumanResources_Employee(@from_lsn, @to_lsn, 'all');  
SELECT sys.fn_cdc_map_lsn_to_time(@max_lsn);  
GO   
```  
  
## <a name="see-also"></a>참고 항목  
 [lsn_time_mapping &#40;Transact-sql&#41;](../../relational-databases/system-tables/cdc-lsn-time-mapping-transact-sql.md)   
 [fn_cdc_map_time_to_lsn &#40;Transact-sql&#41;](../../relational-databases/system-functions/sys-fn-cdc-map-time-to-lsn-transact-sql.md)   
 [fn_cdc_get_net_changes_&#60;capture_instance&#62; &#40;Transact-sql&#41;](../../relational-databases/system-functions/cdc-fn-cdc-get-net-changes-capture-instance-transact-sql.md)   
 [fn_cdc_get_all_changes_&#60;capture_instance&#62;  &#40;Transact-sql&#41;](../../relational-databases/system-functions/cdc-fn-cdc-get-all-changes-capture-instance-transact-sql.md)  
  
  
