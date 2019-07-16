---
title: sys.sp_cdc_help_change_data_capture (TRANSACT-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_cdc_help_change_data_capture_TSQL
- sys.sp_cdc_help_change_data_capture_TSQL
- sp_cdc_help_change_data_capture
- sys.sp_cdc_help_change_data_capture
dev_langs:
- TSQL
helpviewer_keywords:
- change data capture [SQL Server], querying metadata
- sys.sp_cdc_help_change_data_capture
- sp_cdc_help_change_data_capture
ms.assetid: 91fd41f5-1b4d-44fe-a3b5-b73eff65a534
author: rothja
ms.author: jroth
ms.openlocfilehash: fdf0086fe3a87823a419f3535888ea3211ee9ef1
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67905172"
---
# <a name="sysspcdchelpchangedatacapture-transact-sql"></a>sys.sp_cdc_help_change_data_capture(Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  현재 데이터베이스에서 변경 데이터 캡처가 활성화된 각 테이블에 대한 변경 데이터 캡처 구성을 반환합니다. 각 원본 테이블당 최대 두 개의 열, 각 캡처 인스턴스당 한 개의 열을 반환할 수 있습니다. 변경 데이터 캡처는 일부 [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]버전에서 사용할 수 없습니다. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]버전에서 지원되는 기능 목록은 [SQL Server 2016 버전에서 지원하는 기능](../../sql-server/editions-and-supported-features-for-sql-server-2016.md)을 참조하세요.  
  
 ![항목 링크 아이콘](../../database-engine/configure-windows/media/topic-link.gif "항목 링크 아이콘") [Transact-SQL 구문 규칙](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>구문  
  
```  
  
sys.sp_cdc_help_change_data_capture   
  [ [ @source_schema = ] 'source_schema' ]  
  [, [ @source_name = ] 'source_name' ]  
```  
  
## <a name="arguments"></a>인수  
 [ @source_schema =] '*source_schema*'  
 원본 테이블이 속한 스키마의 이름입니다. *source_schema* 됩니다 **sysname**, 기본값은 NULL입니다. 때 *source_schema* 를 지정 하면 *source_name* 도 지정 해야 합니다.  
  
 Null이 아닌 *source_schema* 현재 데이터베이스에 존재 해야 합니다.  
  
 하는 경우 *source_schema* 가 NULL이 아닌 *source_name* NULL이 아닌 수도 있어야 합니다.  
  
 [ @source_name =] '*source_name*'  
 원본 테이블의 이름입니다. *source_name* 됩니다 **sysname**, 기본값은 NULL입니다. 때 *source_name* 를 지정 하면 *source_schema* 도 지정 해야 합니다.  
  
 Null이 아닌 *source_name* 현재 데이터베이스에 존재 해야 합니다.  
  
 하는 경우 *source_name* 가 NULL이 아닌 *source_schema* NULL이 아닌 수도 있어야 합니다.  
  
## <a name="return-code-values"></a>반환 코드 값  
 0(성공) 또는 1(실패)  
  
## <a name="result-sets"></a>결과 집합  
  
|열 이름|데이터 형식|설명|  
|-----------------|---------------|-----------------|  
|source_schema|**sysname**|원본 테이블 스키마의 이름입니다.|  
|source_table|**sysname**|원본 테이블의 이름입니다.|  
|capture_instance|**sysname**|캡처 인스턴스의 이름입니다.|  
|object_id|**int**|원본 테이블과 관련된 변경 테이블의 ID입니다.|  
|source_object_id|**int**|원본 테이블의 ID입니다.|  
|start_lsn|**binary(10)**|변경 테이블 쿼리의 하위 엔드포인트를 나타내는 LSN(로그 시퀀스 번호)입니다.<br /><br /> NULL = 하위 엔드포인트가 설정되지 않았습니다.|  
|end_lsn|**binary(10)**|변경 테이블 쿼리의 상위 엔드포인트를 나타내는 LSN입니다. [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]에서 이 열은 항상 NULL입니다.|  
|supports_net_changes|**bit**|순 변경 지원이 활성화됩니다.|  
|has_drop_pending|**bit**|[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]에서는 사용되지 않습니다.|  
|role_name|**sysname**|변경 데이터에 대한 액세스를 제어하는 데 사용되는 데이터베이스 역할의 이름입니다.<br /><br /> NULL = 역할이 사용되지 않습니다.|  
|index_name|**sysname**|원본 테이블의 행을 고유하게 식별하는 데 사용되는 인덱스 이름입니다.|  
|filegroup_name|**sysname**|변경 테이블이 있는 파일 그룹의 이름입니다.<br /><br /> NULL = 변경 테이블이 데이터베이스의 기본 파일 그룹에 있습니다.|  
|create_date|**datetime**|캡처 인스턴스가 활성화된 날짜입니다.|  
|index_column_list|**nvarchar(max)**|원본 테이블의 행을 고유하게 식별하는 데 사용되는 인덱스 열의 목록입니다.|  
|captured_column_list|**nvarchar(max)**|캡처된 원본 열 목록입니다.|  
  
## <a name="remarks"></a>설명  
 때 둘 다 *source_schema* 하 고 *source_name* 기본적으로 NULL 또는 NULL을 명시적으로 설정 되어이 저장된 프로시저 호출자가 선택 하는 캡처 인스턴스의 모든 데이터베이스에 대 한 정보를 반환 에 대 한 액세스. 때 *source_schema* 하 고 *source_name* 는 NULL이 아닌 명명된 된 특정 설정 된 테이블에 대 한 정보만 반환 됩니다.  
  
## <a name="permissions"></a>사용 권한  
 때 *source_schema* 하 고 *source_name* 이 NULL 이면 결과 집합에 설정된 된 테이블이 포함 된 호출자의 권한 부여를 결정 합니다. 호출자는 캡처 인스턴스의 모든 캡처된 열에 대해 SELECT 권한을 가지고 있어야 하며 포함할 테이블 정보에 대해 정의된 제어 역할의 멤버여야 합니다. db_owner 데이터베이스 역할의 멤버는 정의된 모든 캡처 인스턴스에 대한 정보를 볼 수 있습니다. 설정된 특정 테이블에 대한 정보가 요청되면 동일한 SELECT 및 멤버 자격 조건이 명명된 테이블에 적용됩니다.  
  
## <a name="examples"></a>예  
  
### <a name="a-returning-change-data-capture-configuration-information-for-a-specified-table"></a>A. 지정된 테이블에 대한 변경 데이터 캡처 구성 정보 반환  
 다음 예에서는 `HumanResources.Employee` 테이블에 대한 변경 데이터 캡처 구성을 반환합니다.  
  
```  
USE AdventureWorks2012;  
GO  
EXECUTE sys.sp_cdc_help_change_data_capture   
    @source_schema = N'HumanResources',   
    @source_name = N'Employee';  
GO  
```  
  
### <a name="b-returning-change-data-capture-configuration-information-for-all-tables"></a>2\. 모든 테이블에 대한 변경 데이터 캡처 구성 정보 반환  
 다음 예에서는 호출자에게 액세스 권한이 부여된 변경 데이터가 포함된 데이터베이스에서 사용하도록 설정된 모든 테이블에 대한 구성 정보를 반환합니다.  
  
```  
USE AdventureWorks2012;  
GO  
EXECUTE sys.sp_cdc_help_change_data_capture;  
GO  
```  
  
  
