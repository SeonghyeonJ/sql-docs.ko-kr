---
description: core.sp_purge_data(Transact-SQL)
title: core. sp_purge_data (Transact-sql) | Microsoft Docs
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_purge_data_TSQL
- sp_purge_data
dev_langs:
- TSQL
helpviewer_keywords:
- sp_purge_data
- management data warehouse, data collector stored procedures
- core.sp_purge_data stored procedure
- data collector [SQL Server], stored procedures
ms.assetid: 056076c3-8adf-4f51-8a1b-ca39696ac390
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: d2ab402b1641e72225bf579d5b0aa5a21b345637
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88489793"
---
# <a name="coresp_purge_data-transact-sql"></a>core.sp_purge_data(Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  보존 정책을 기준으로 관리 데이터 웨어하우스에서 데이터를 제거합니다. 이 프로시저는 지정된 인스턴스와 연결된 관리 데이터 웨어하우스에 대해 mdw_purge_data [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 작업에 의해 매일 실행됩니다. 다음 저장 프로시저를 사용하여 관리 데이터 웨어하우스에서 데이터를 요청 시 제거할 수 있습니다.  
  
 ![항목 링크 아이콘](../../database-engine/configure-windows/media/topic-link.gif "항목 링크 아이콘") [Transact-SQL 구문 표기 규칙](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>구문  
  
```  
  
core.sp_purge_data  
    [ [ @retention_days = ] retention_days ]  
    [ , [ @instance_name = ] 'instance_name' ]  
    [ , [ @collection_set_uid = ] 'collection_set_uid' ]  
    [ , [ @duration = ] duration ]  
```  
  
## <a name="arguments"></a>인수  
 [ @retention_days =] *retention_days*  
 데이터를 관리 데이터 웨어하우스 테이블에 보관하는 일 수입니다. 타임 스탬프가 *retention_days* 보다 오래 된 데이터는 제거 됩니다. *retention_days* 은 **smallint**이며 기본값은 NULL입니다. 지정된 경우 값은 양수여야 합니다. NULL인 경우 core.snapshots 뷰의 valid_through 열에 있는 값에 따라 제거에 적합한 행이 결정됩니다.  
  
 [ @instance_name =] '*instance_name*'  
 컬렉션 집합의 인스턴스 이름입니다. *instance_name* 는 **sysname**이며 기본값은 NULL입니다.  
  
 *instance_name* 는 *computername*instancename 형식의 컴퓨터 이름과 인스턴스 이름으로 구성 된 정규화 된 인스턴스 이름 이어야 합니다 \\ *instancename*. NULL인 경우 로컬 서버의 기본 인스턴스가 사용됩니다.  
  
 [ @collection_set_uid =] '*collection_set_uid*'  
 컬렉션 집합에 대한 GUID입니다. *collection_set_uid* 은 **uniqueidentifier**이며 기본값은 NULL입니다. NULL인 경우 모든 컬렉션 집합에서 한정하는 행이 제거됩니다. 이 값을 확인하려면 syscollector_collection_sets 카탈로그 뷰를 쿼리합니다.  
  
 [ @duration =] *기간*  
 제거 작업을 실행해야 하는 최대 시간(분)입니다. *duration* 은 **smallint**이며 기본값은 NULL입니다. 지정된 경우 값은 0 또는 양의 정수여야 합니다. NULL인 경우 한정된 모든 행이 제거될 때까지 작업이 실행되거나 작업이 수동으로 중지됩니다.  
  
## <a name="return-code-values"></a>반환 코드 값  
 **0** (성공) 또는 **1** (실패)  
  
## <a name="remarks"></a>설명  
 이 프로시저는 보존 기간을 기준으로 제거에 적합한 core.snapshots 뷰에서 행을 선택합니다. 그러면 제거에 적합한 모든 행이 core.snapshots_internal 테이블에서 삭제됩니다. 이전 행을 삭제하면 모든 관리 데이터 웨어하우스 테이블에서 연계 삭제 동작이 트리거됩니다. 이 작업은 수집된 데이터를 저장하는 모든 테이블에 대해 정의된 ON DELETE CASCADE 절을 사용하여 수행됩니다.  
  
 각 스냅샷과 이와 연결된 데이터는 명시적 트랜잭션 내에서 삭제된 다음 커밋됩니다. 따라서 제거 작업을 수동으로 중지 하거나에 지정 된 값을 초과 하는 경우 @duration 커밋되지 않은 데이터만 유지 됩니다. 이 데이터는 다음에 작업이 실행될 때 제거될 수 있습니다.  
  
 이 프로시저는 관리 데이터 웨어하우스 데이터베이스의 컨텍스트에서 실행해야 합니다.  
  
## <a name="permissions"></a>사용 권한  
 **Mdw_admin** (실행 권한 포함) 고정 데이터베이스 역할의 멤버 자격이 필요 합니다.  
  
## <a name="examples"></a>예제  
  
### <a name="a-running-sp_purge_data-with-no-parameters"></a>A. 매개 변수 없이 sp_purge_data 실행  
 다음 예에서는 매개 변수를 지정하지 않고 core.sp_purge_data를 실행합니다. 따라서 모든 매개 변수에 대해 기본값 NULL이 연결된 동작과 함께 사용됩니다.  
  
```  
USE <management_data_warehouse>;  
EXECUTE core.sp_purge_data;  
GO  
```  
  
### <a name="b-specifying-retention-and-duration-values"></a>B. 보존 및 기간 값 지정  
 다음 예에서는 관리 데이터 웨어하우스에서 7일보다 오래된 데이터를 제거합니다. 또한 @duration 작업을 5 분 이상 실행 하지 않도록 매개 변수를 지정 해야 합니다.  
  
```  
USE <management_data_warehouse>;  
EXECUTE core.sp_purge_data @retention_days = 7, @duration = 5;  
GO  
```  
  
### <a name="c-specifying-an-instance-name-and-collection-set"></a>C. 인스턴스 이름 및 컬렉션 집합 지정  
 다음 예에서는 관리 데이터 웨어하우스에서 지정된 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스의 지정된 컬렉션 집합에 대한 데이터를 제거합니다. @retention_days을 지정 하지 않았기 때문에, 핵심 스냅숏의 뷰에서 valid_through 열의 값을 사용 하 여 제거할 수 있는 컬렉션 집합의 행을 확인 합니다.  
  
```  
USE <management_data_warehouse>;  
GO  
-- Get the collection set unique identifier for the Disk Usage system collection set.  
DECLARE @disk_usage_collection_set_uid uniqueidentifier = (SELECT collection_set_uid   
    FROM msdb.dbo.syscollector_collection_sets WHERE name = N'Disk Usage');   
  
EXECUTE core.sp_purge_data @instance_name = @@SERVERNAME, @collection_set_uid = @disk_usage_collection_set_uid;  
GO  
```  
  
## <a name="see-also"></a>관련 항목  
 [Transact-sql&#41;&#40;시스템 저장 프로시저 ](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [데이터 수집기 저장 프로시저&#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/data-collector-stored-procedures-transact-sql.md)  
  
  
