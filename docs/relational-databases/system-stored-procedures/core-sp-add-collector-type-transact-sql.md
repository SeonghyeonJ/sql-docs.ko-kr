---
description: core.sp_add_collector_type(Transact-SQL)
title: core. sp_add_collector_type (Transact-sql) | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_add_collector_type
- sp_add_collector_type_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- core.sp_add_collector_type stored procedure
- management data warehouse, data collector stored procedures
- sp_add_collector_type
- data collector [SQL Server], stored procedures
ms.assetid: 1d981037-2147-464e-a456-7d8e479bce89
author: markingmyname
ms.author: maghan
ms.openlocfilehash: b9d907512edb385afba38b4ad1854a4535b67d9d
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89536821"
---
# <a name="coresp_add_collector_type-transact-sql"></a>core.sp_add_collector_type(Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  관리 데이터 웨어하우스 데이터베이스의 core.supported_collector_types 뷰에 새 항목을 추가합니다. 이 프로시저는 관리 데이터 웨어하우스 데이터베이스의 컨텍스트에서 실행해야 합니다.  
  
 ![항목 링크 아이콘](../../database-engine/configure-windows/media/topic-link.gif "항목 링크 아이콘") [Transact-SQL 구문 표기 규칙](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>구문  
  
```  
  
core.sp_add_collector_type [ @collector_type_uid = ] 'collector_type_uid'  
```  
  
## <a name="arguments"></a>인수  
 [ @collector_type_uid =] '*collector_type_uid*'  
 수집기 유형의 GUID입니다. *collector_type_uid* 은 **uniqueidentifier**이며 기본값은 없습니다.  
  
## <a name="return-code-values"></a>반환 코드 값  
 **0** (성공) 또는 **1** (실패)  
  
## <a name="permissions"></a>사용 권한  
 **Mdw_admin** (실행 권한 포함) 고정 데이터베이스 역할의 멤버 자격이 필요 합니다.  
  
## <a name="examples"></a>예제  
 다음 예에서는 core.supported_collector_types 뷰에 일반 T-SQL 쿼리 수집기 유형을 추가합니다. 기본적으로 일반 T-SQL 쿼리 수집기 형식은 이미 있으므로 기본 설치에서 이 코드를 실행하면 수집기 형식이 이미 있다는 메시지가 나타납니다.  
  
 일반 T-SQL 쿼리 수집기 유형을 core.sp_remove_collector_type 저장 프로시저를 사용하여 제거한 다음 관리 데이터 웨어하우스에 데이터를 업로드할 수 있는 등록된 수집기 유형으로 다시 추가하려는 경우 이 코드가 성공적으로 실행됩니다.  
  
```  
USE <management_data_warehouse>;  
GO  
DECLARE @RC int;  
DECLARE @collector_type_uid uniqueidentifier;  
SELECT @collector_type_uid = (SELECT collector_type_uid FROM msdb.dbo.syscollector_collector_types WHERE name = N'Generic T-SQL Query Collector Type');  
EXECUTE @RC = core.sp_add_collector_type @collector_type_uid;  
```  
  
## <a name="see-also"></a>참고 항목  
 [시스템 저장 프로시저&#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [데이터 수집기 저장 프로시저&#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/data-collector-stored-procedures-transact-sql.md)   
 [관리 데이터 웨어하우스](../../relational-databases/data-collection/management-data-warehouse.md)  
  
  
