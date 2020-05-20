---
title: sys. sp_cdc_enable_table (Transact-sql) | Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.sp_cdc_enable_table_TSQL
- sp_cdc_enable_table_TSQL
- sys.sp_cdc_enable_table
- sp_cdc_enable_table
dev_langs:
- TSQL
helpviewer_keywords:
- change data capture [SQL Server], enabling tables
- sys.sp_cdc_enable_table
- sp_cdc_enable_table
ms.assetid: 26150c09-2dca-46ad-bb01-3cb3165bcc5d
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: f66891393527b12f859d1a0aa6447470473a4d49
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/05/2020
ms.locfileid: "82808637"
---
# <a name="syssp_cdc_enable_table-transact-sql"></a>sys.sp_cdc_enable_table(Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  현재 데이터베이스에서 지정된 원본 테이블에 대해 변경 데이터 캡처를 활성화합니다. 테이블에서 변경 데이터 캡처를 사용할 수 있도록 설정하면 해당 테이블에 적용된 각 DML(데이터 조작 언어) 작업의 레코드가 트랜잭션 로그에 기록됩니다. 변경 데이터 캡처 프로세스는 로그에서 이 정보를 검색하고 일련의 함수를 사용하여 액세스하는 변경 테이블에 이 정보를 기록합니다.  
  
 변경 데이터 캡처는 일부 [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]버전에서 사용할 수 없습니다. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]버전에서 지원되는 기능 목록은 [SQL Server 2016 버전에서 지원하는 기능](~/sql-server/editions-and-supported-features-for-sql-server-2016.md)을 참조하세요.  
  
 ![항목 링크 아이콘](../../database-engine/configure-windows/media/topic-link.gif "항목 링크 아이콘") [Transact-SQL 구문 표기 규칙](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>구문  
  
```  
  
sys.sp_cdc_enable_table   
  [ @source_schema = ] 'source_schema',   
  [ @source_name = ] 'source_name' ,  [,[ @capture_instance = ] 'capture_instance' ]  
  [,[ @supports_net_changes = ] supports_net_changes ]  
  , [ @role_name = ] 'role_name'  
  [,[ @index_name = ] 'index_name' ]  
  [,[ @captured_column_list = ] 'captured_column_list' ]  
  [,[ @filegroup_name = ] 'filegroup_name' ]  
  [,[ @allow_partition_switch = ] 'allow_partition_switch' ]  
  [;]  
```  
  
## <a name="arguments"></a>인수  
`[ @source_schema = ] 'source_schema'`원본 테이블이 속한 스키마의 이름입니다. *source_schema* 는 **sysname**이며 기본값은 없고 NULL 일 수 없습니다.  
  
`[ @source_name = ] 'source_name'`변경 데이터 캡처를 사용할 원본 테이블의 이름입니다. *source_name* 는 **sysname**이며 기본값은 없고 NULL 일 수 없습니다.  
  
 *source_name* 는 현재 데이터베이스에 있어야 합니다. **Cdc** 스키마의 테이블은 변경 데이터 캡처를 사용 하도록 설정할 수 없습니다.  
  
`[ @role_name = ] 'role_name'`변경 데이터에 대 한 액세스를 게이트 하는 데 사용 되는 데이터베이스 역할의 이름입니다. *role_name* 는 **sysname** 이며 반드시 지정 해야 합니다. 명시적으로 NULL로 설정하면 변경 데이터에 대한 액세스를 제어하는 데 제어 역할이 사용되지 않습니다.  
  
 현재 역할이 있는 경우 해당 역할이 사용됩니다. 역할이 없는 경우 지정된 이름의 데이터베이스 역할이 생성됩니다. 역할을 생성하기 전에 역할 이름 문자열의 오른쪽에 있는 공백은 잘립니다. 호출자에게 데이터베이스 내에서 역할을 생성할 권한이 없는 경우 저장 프로시저 작업은 실패합니다.  
  
`[ @capture_instance = ] 'capture_instance'`인스턴스별 변경 데이터 캡처 개체의 이름을 지정 하는 데 사용 되는 캡처 인스턴스의 이름입니다. *capture_instance* 는 **sysname** 이며 NULL 일 수 없습니다.  
  
 지정 하지 않으면 이름이 *schemaname_sourcename*형식으로 원본 스키마 이름에 원본 테이블 이름을 붙인 이름이 파생 됩니다. *capture_instance* 는 100 자를 초과할 수 없으며 데이터베이스 내에서 고유 해야 합니다. 지정 된 또는 파생 된 *capture_instance* 문자열의 오른쪽에 있는 공백을 잘라냅니다.  
  
 원본 테이블은 최대 두 개의 캡처 인스턴스를 가질 수 있습니다. 자세한 내용은 [sp_cdc_help_change_data_capture &#40;transact-sql&#41;](../../relational-databases/system-stored-procedures/sys-sp-cdc-help-change-data-capture-transact-sql.md)을 참조 하십시오.  
  
`[ @supports_net_changes = ] supports_net_changes`이 캡처 인스턴스에서 순 변경 쿼리에 대 한 지원을 사용 하도록 설정할지 여부를 나타냅니다. 테이블에 기본 키가 있거나 매개 변수를 사용 하 여 식별 된 고유 인덱스가 테이블에 있는 경우 *supports_net_changes* 은 **bit** 이며 기본값은 1입니다 @index_name . 그렇지 않으면 이 매개 변수의 기본값은 0입니다.  
  
 0인 경우 모든 변경을 쿼리하는 지원 함수만 생성됩니다.  
  
 1인 경우 순 변경을 쿼리하는 데 필요한 함수도 생성됩니다.  
  
 *Supports_net_changes* 1로 설정 된 경우 *index_name* 을 지정 해야 합니다. 그렇지 않으면 원본 테이블에 정의 된 기본 키가 있어야 합니다.  
  
`[ @index_name = ] 'index_name_'`원본 테이블에서 행을 고유 하 게 식별 하는 데 사용할 고유 인덱스의 이름입니다. *index_name* 는 **sysname** 이며 NULL 일 수 있습니다. 지정 하는 경우 *index_name* 은 원본 테이블의 유효한 고유 인덱스 여야 합니다. *Index_name* 지정 하면 식별 된 인덱스 열이 테이블의 고유 행 식별자로 정의 된 기본 키 열 보다 우선적으로 적용 됩니다.  
  
`[ @captured_column_list = ] 'captured_column_list'`변경 테이블에 포함 될 원본 테이블 열을 식별 합니다. *captured_column_list* 은 **nvarchar (MAX)** 이며 NULL 일 수 있습니다. NULL이면 모든 열이 변경 테이블에 포함됩니다.  
  
 열 이름은 원본 테이블의 유효한 열이어야 합니다. 기본 키 인덱스에 정의 된 열 또는 *index_name* 에서 참조 하는 인덱스에 정의 된 열이 포함 되어야 합니다.  
  
 *captured_column_list* 은 쉼표로 구분 된 열 이름 목록입니다. 목록에 있는 각 열 이름은 필요에 따라 큰따옴표("")나 대괄호([])를 사용하여 묶을 수 있습니다. 열 이름에 포함된 쉼표가 있으면 열 이름을 따옴표로 묶어야 합니다.  
  
 *captured_column_list* 에는 다음 예약 된 열 이름을 사용할 수 없습니다. **__ $ start_lsn**, **__ $ end_lsn**, **__ $ seqval**, **__ $ operation**, **__ $ update_mask**.  
  
`[ @filegroup_name = ] 'filegroup_name'`캡처 인스턴스에 대해 생성 된 변경 테이블에 사용할 파일 그룹입니다. *filegroup_name* 는 **sysname** 이며 NULL 일 수 있습니다. 지정 된 경우 현재 데이터베이스에 대해 *filegroup_name* 를 정의 해야 합니다. NULL이면 기본 파일 그룹이 사용됩니다.  
  
 변경 데이터 캡처 변경 테이블에 대해서는 별도의 파일 그룹을 만드는 것이 좋습니다.  
  
`[ @allow_partition_switch = ] 'allow_partition_switch'`변경 데이터 캡처가 설정 된 테이블에 대해 ALTER TABLE의 SWITCH PARTITION 명령을 실행할 수 있는지 여부를 나타냅니다. *allow_partition_switch* 은 **bit**이며 기본값은 1입니다.  
  
 분할되지 않은 테이블의 경우 스위치 설정은 항상 1이고 실제 설정은 무시됩니다. 분할되지 않은 테이블에 대해 스위치를 명시적으로 0으로 설정하면 스위치 설정이 무시되었음을 나타내는 경고 22857이 발생합니다. 분할된 테이블에 대해 스위치를 명시적으로 0으로 설정하면 원본 테이블에서 파티션 전환 작업이 허용되지 않음을 나타내는 경고 22356이 발생합니다. 마지막으로 스위치 설정을 명시적으로 1로 설정하거나 기본적으로 1로 설정되도록 허용한 경우 설정된 테이블이 분할된 테이블이면 파티션 전환이 차단되지 않음을 나타내는 경고 22855가 발생합니다. 파티션 전환이 발생해도 변경 데이터 캡처는 전환으로 인한 변경 내용을 추적하지 않습니다. 따라서 변경 데이터가 사용될 때 데이터 불일치가 발생합니다.  
  
> [!IMPORTANT]  
>  SWITCH PARTITION은 메타데이터 작업이지만 데이터를 변경합니다. 이 작업과 연관된 데이터 변경은 변경 데이터 캡처 변경 테이블에 캡처되지 않습니다. 세 개의 파티션이 있는 테이블이 있고 이 테이블이 변경된다고 가정합니다. 캡처 프로세스는 이 테이블에 대해 실행되는 사용자 삽입, 업데이트 및 삭제 작업을 추적합니다. 그러나 대량 삭제 등의 작업을 위해 파티션을 다른 테이블로 스위치 아웃하면 이 작업의 일부로 이동된 행이 변경 테이블에 삭제된 행으로 캡처되지 않습니다. 마찬가지로 행으로 채워진 새 파티션을 테이블에 추가해도 이러한 행이 변경 테이블에 반영되지 않습니다. 이로 인해 변경 내용이 애플리케이션에서 사용되고 대상에 적용될 때 데이터 불일치가 발생할 수 있습니다.  
  
## <a name="return-code-values"></a>반환 코드 값  
 **0** (성공) 또는 **1** (실패)  
  
## <a name="result-sets"></a>결과 집합  
 None  
  
## <a name="remarks"></a>설명  
 테이블에서 변경 데이터 캡처를 사용할 수 있도록 설정하려면 먼저 데이터베이스에서 변경 데이터 캡처를 사용할 수 있도록 설정해야 합니다. 데이터베이스에 변경 데이터 캡처가 설정 되어 있는지 여부를 확인 하려면 [sys. databases](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md) 카탈로그 뷰의 **is_cdc_enabled** 열을 쿼리 합니다. 데이터베이스를 사용 하도록 설정 하려면 [sp_cdc_enable_db](../../relational-databases/system-stored-procedures/sys-sp-cdc-enable-db-transact-sql.md) 저장 프로시저를 사용 합니다.  
  
 테이블에서 변경 데이터 캡처를 사용할 수 있으면 변경 테이블과 하나 또는 두 개의 쿼리 함수가 생성됩니다. 변경 테이블은 캡처 프로세스가 트랜잭션 로그에서 추출하는 원본 테이블 변경 내용의 리포지토리 역할을 합니다. 쿼리 함수는 변경 테이블에서 데이터를 추출하는 데 사용됩니다. 이러한 함수의 이름은 다음과 같은 방법으로 *capture_instance* 매개 변수에서 파생 됩니다.  
  
-   모든 변경 내용 함수: **cdc. fn_cdc_get_all_changes_<capture_instance>**  
  
-   Net changes 함수: **cdc. fn_cdc_get_net_changes_<capture_instance>**  
  
 또한 sp_cdc_enable_table은 원본 테이블이 변경 데이터 캡처를 사용 하도록 설정 하 고 데이터베이스에 대 한 트랜잭션 게시가 없는 경우 데이터베이스에 대 한 캡처 및 정리 작업을 만듭니다 **.** 이 예제에서는 [sys. tables](../../relational-databases/system-catalog-views/sys-tables-transact-sql.md) 카탈로그 뷰의 **is_tracked_by_cdc** 열을 1로 설정 합니다.  
  
> [!NOTE]  
>  테이블에서 변경 데이터 캡처를 사용할 수 있도록 설정한 경우에는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트를 실행하지 않아도 됩니다. 그러나 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트를 실행하지 않으면 캡처 프로세스가 트랜잭션을 로그를 처리하지 않고 변경 테이블에 항목을 기록하지 않습니다.  
  
## <a name="permissions"></a>권한  
 **Db_owner** 고정 데이터베이스 역할의 멤버 자격이 필요 합니다.  
  
## <a name="examples"></a>예  
  
### <a name="a-enabling-change-data-capture-by-specifying-only-required-parameters"></a>A. 필요한 매개 변수만 지정하여 변경 데이터 캡처 활성화  
 다음 예에서는 `HumanResources.Employee` 테이블에 대해 변경 데이터 캡처를 활성화합니다. 필요한 매개 변수만 지정됩니다.  
  
```  
USE AdventureWorks2012;  
GO  
EXECUTE sys.sp_cdc_enable_table  
    @source_schema = N'HumanResources'  
  , @source_name = N'Employee'  
  , @role_name = N'cdc_Admin';  
GO  
```  
  
### <a name="b-enabling-change-data-capture-by-specifying-additional-optional-parameters"></a>B. 선택적 추가 매개 변수를 지정하여 변경 데이터 캡처 활성화  
 다음 예에서는 `HumanResources.Department` 테이블에 대해 변경 데이터 캡처를 활성화합니다. `@allow_partition_switch`를 제외한 모든 매개 변수가 지정됩니다.  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sys.sp_cdc_enable_table  
    @source_schema = N'HumanResources'  
  , @source_name = N'Department'  
  , @role_name = N'cdc_admin'  
  , @capture_instance = N'HR_Department'   
  , @supports_net_changes = 1  
  , @index_name = N'AK_Department_Name'   
  , @captured_column_list = N'DepartmentID, Name, GroupName'   
  , @filegroup_name = N'PRIMARY';  
GO  
```  
  
## <a name="see-also"></a>참고 항목  
 [sp_cdc_disable_table &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sys-sp-cdc-disable-table-transact-sql.md)   
 [sp_cdc_help_change_data_capture &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sys-sp-cdc-help-change-data-capture-transact-sql.md)   
 [fn_cdc_get_all_changes_&#60;capture_instance&#62;  &#40;Transact-sql&#41;](../../relational-databases/system-functions/cdc-fn-cdc-get-all-changes-capture-instance-transact-sql.md)   
 [fn_cdc_get_net_changes_&#60;capture_instance&#62; &#40;Transact-sql&#41;](../../relational-databases/system-functions/cdc-fn-cdc-get-net-changes-capture-instance-transact-sql.md)   
 [sp_cdc_help_jobs &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sys-sp-cdc-help-jobs-transact-sql.md)  
  
  
