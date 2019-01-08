---
title: sp_addarticle (TRANSACT-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 10/28/2015
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_addarticle
- sp_addarticle_TSQL
helpviewer_keywords:
- sp_addarticle
ms.assetid: 0483a157-e403-4fdb-b943-23c1b487bef0
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 732e8a03742e6e2ccc66c158c300222a0701e0c0
ms.sourcegitcommit: 37310da0565c2792aae43b3855bd3948fd13e044
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/18/2018
ms.locfileid: "53591917"
---
# <a name="spaddarticle-transact-sql"></a>sp_addarticle(Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  아티클을 만들어 게시에 추가합니다. 이 저장 프로시저는 게시 데이터베이스의 게시자에서 실행됩니다.  
  
 ![항목 링크 아이콘](../../database-engine/configure-windows/media/topic-link.gif "항목 링크 아이콘") [Transact-SQL 구문 규칙](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>구문  
  
```  
  
sp_addarticle [ @publication = ] 'publication'   
        , [ @article = ] 'article'   
    [ , [ @source_table = ] 'source_table' ]  
    [ , [ @destination_table = ] 'destination_table' ]   
    [ , [ @vertical_partition = ] 'vertical_partition' ]   
    [ , [ @type = ] 'type' ]   
    [ , [ @filter = ] 'filter' ]   
    [ , [ @sync_object= ] 'sync_object' ]   
        [ , [ @ins_cmd = ] 'ins_cmd' ]   
    [ , [ @del_cmd = ] 'del_cmd' ]   
        [ , [ @upd_cmd = ] 'upd_cmd' ]   
    [ , [ @creation_script = ] 'creation_script' ]   
    [ , [ @description = ] 'description' ]   
    [ , [ @pre_creation_cmd = ] 'pre_creation_cmd' ]   
    [ , [ @filter_clause = ] 'filter_clause' ]   
    [ , [ @schema_option = ] schema_option ]   
    [ , [ @destination_owner = ] 'destination_owner' ]   
    [ , [ @status = ] status ]   
    [ , [ @source_owner = ] 'source_owner' ]   
    [ , [ @sync_object_owner = ] 'sync_object_owner' ]   
    [ , [ @filter_owner = ] 'filter_owner' ]   
    [ , [ @source_object = ] 'source_object' ]   
    [ , [ @artid = ] article_ID  OUTPUT ]   
    [ , [ @auto_identity_range = ] 'auto_identity_range' ]   
    [ , [ @pub_identity_range = ] pub_identity_range ]   
    [ , [ @identity_range = ] identity_range ]   
    [ , [ @threshold = ] threshold ]   
    [ , [ @force_invalidate_snapshot = ] force_invalidate_snapshot ]  
    [ , [ @use_default_datatypes = ] use_default_datatypes  
    [ , [ @identityrangemanagementoption = ] identityrangemanagementoption ]  
    [ , [ @publisher = ] 'publisher' ]  
    [ , [ @fire_triggers_on_snapshot = ] 'fire_triggers_on_snapshot' ]   
```  
  
## <a name="arguments"></a>인수  
 [  **@publication =** ] **'**_게시_**'**  
 아티클을 포함하는 게시의 이름입니다. 이 이름은 데이터베이스에서 고유해야 합니다. *게시* 됩니다 **sysname**, 기본값은 없습니다.  
  
 [  **@article =** ] **'**_문서_**'**  
 아티클의 이름입니다. 이름은 반드시 게시 내에서 고유해야 합니다. *문서* 됩니다 **sysname**, 기본값은 없습니다.  
  
 [  **@source_table =** ] **'**_source_table_**'**  
 이 매개 변수는 더 이상 사용 되지 않습니다. 사용 하 여 *source_object* 대신 합니다.  
  
 *이 매개 변수는 Oracle 게시자에 대해서는 지원 되지 않습니다.*  
  
 [  **@destination_table =** ] **'**_destination_table_**'**  
 다른 경우 대상 (구독) 테이블의 이름인 *source_table*또는 저장된 프로시저입니다. *destination_table* 됩니다 **sysname**에 기본값은 NULL입니다. 즉 *source_table* equals *destination_table * *.*  
  
 [  **@vertical_partition =** ] **'**_vertical_partition_**'**  
 테이블 아티클에 열 필터링을 사용하거나 사용하지 않도록 합니다. *vertical_partition* 됩니다 **nchar(5)**, 기본값은 FALSE입니다.  
  
 **false** 있음을 세로 필터링을 하지 않고 모든 열을 게시 합니다.  
  
 **true** 모든 제외한 선언된 된 기본 키 열, 기본값은 없고 null 허용 열 및 고유 키 열을 지웁니다. 사용 하 여 열이 추가 됩니다 [sp_articlecolumn](../../relational-databases/system-stored-procedures/sp-articlecolumn-transact-sql.md)합니다.  
  
 [  **@type =** ] **'**_형식_**'**  
 아티클의 유형입니다. *형식* 됩니다 **sysname**, 이며 다음 값 중 하나일 수 있습니다.  
  
|값|Description|  
|-----------|-----------------|  
|**집계 스키마만**|스키마가 있는 집계 함수 전용입니다.|  
|**func 스키마만**|스키마가 있는 함수 전용입니다.|  
|**인덱싱된 뷰 logbased**|로그 기반의 인덱싱된 뷰 아티클입니다. Oracle 게시자에 대해서는 지원되지 않습니다. 이 유형의 아티클은 기본 테이블을 별도로 게시할 필요가 없습니다.|  
|**logbased manualboth 인덱싱된 뷰**|수동 필터 및 수동 뷰가 있는 로그 기반의 인덱싱된 뷰 아티클입니다. 이 옵션 둘 다 지정 해야 *sync_object* 하 고 *필터* 매개 변수입니다. 이 유형의 아티클은 기본 테이블을 별도로 게시할 필요가 없습니다. Oracle 게시자에 대해서는 지원되지 않습니다.|  
|**logbased manualfilter 인덱싱된 뷰**|수동 필터가 있는 로그 기반의 인덱싱된 뷰 아티클입니다. 이 옵션 둘 다 지정 해야 *sync_object* 하 고 *필터* 매개 변수입니다. 이 유형의 아티클은 기본 테이블을 별도로 게시할 필요가 없습니다. Oracle 게시자에 대해서는 지원되지 않습니다.|  
|**logbased manualview 인덱싱된 뷰**|수동 뷰가 있는 로그 기반의 인덱싱된 뷰 아티클입니다. 이 옵션을 지정 해야 합니다 *sync_object* 매개 변수입니다. 이 유형의 아티클은 기본 테이블을 별도로 게시할 필요가 없습니다. Oracle 게시자에 대해서는 지원되지 않습니다.|  
|**인덱싱된 뷰 스키마 전용**|스키마가 있는 인덱싱된 뷰 전용입니다. 이 유형의 아티클은 기본 테이블도 게시해야 합니다.|  
|**logbased** (기본값)|로그 기반 아티클입니다.|  
|**logbased manualboth**|수동 필터 및 수동 뷰가 있는 로그 기반 아티클입니다. 이 옵션 둘 다 지정 해야 *sync_object* 하 고 *필터* 매개 변수입니다. Oracle 게시자에 대해서는 지원되지 않습니다.|  
|**logbased manualfilter**|수동 필터가 있는 로그 기반 아티클입니다. 이 옵션 둘 다 지정 해야 *sync_object* 하 고 *필터* 매개 변수입니다. Oracle 게시자에 대해서는 지원되지 않습니다.|  
|**logbased manualview**|수동 뷰가 있는 로그 기반 아티클입니다. 이 옵션을 지정 해야 합니다 *sync_object* 매개 변수입니다. Oracle 게시자에 대해서는 지원되지 않습니다.|  
|**proc exec**|아티클의 모든 구독자로 저장 프로시저의 실행을 복제합니다. Oracle 게시자에 대해서는 지원되지 않습니다. 옵션을 사용 하는 것이 좋습니다 **serializable proc exec** of **proc exec**합니다. 자세한 내용은 "종류의 저장 프로시저 실행 아티클을" 섹션을 참조 [트랜잭션 복제에 있는 Publishing Stored Procedure Execution](../../relational-databases/replication/transactional/publishing-stored-procedure-execution-in-transactional-replication.md)합니다. 변경 데이터 캡처가 설정된 경우 사용할 수 없습니다.|  
|**프로시저 스키마 전용**|스키마가 있는 프로시저 전용입니다. Oracle 게시자에 대해서는 지원되지 않습니다.|  
|**serializable proc exec**|직렬화할 수 있는 트랜잭션 컨텍스트 내에서 실행된 경우에만 저장 프로시저의 실행을 복제합니다. Oracle 게시자에 대해서는 지원되지 않습니다.<br /><br /> 또한 프로시저는 복제 될 프로시저 실행에 대 한 명시적 트랜잭션 내에서 실행 되어야 합니다.|  
|**뷰 스키마 전용**|스키마가 있는 뷰 전용입니다. Oracle 게시자에 대해서는 지원되지 않습니다. 이 옵션을 사용할 때는 기본 테이블도 게시해야 합니다.|  
  
 [  **@filter =** ] **'**_필터_**'**  
 FOR REPLICATION으로 생성되며 테이블을 행 필터링하는 데 사용되는 저장 프로시저입니다. *필터* 됩니다 **nvarchar(386)**, 기본값은 NULL입니다. [sp_articleview](../../relational-databases/system-stored-procedures/sp-articleview-transact-sql.md) 하 고 [sp_articlefilter](../../relational-databases/system-stored-procedures/sp-articlefilter-transact-sql.md) 뷰를 만들 필터 저장된 프로시저를 수동으로 실행 해야 합니다. NULL이 아닌 경우 저장 프로시저가 수동으로 생성되었다고 가정하여 필터 프로시저가 생성되지 않습니다.  
  
 [  **@sync_object =** ] **'**_sync_object_**'**  
 이 아티클의 스냅숏을 표시하는 데 사용되는 데이터 파일을 생성하는 테이블 또는 뷰의 이름입니다. *sync_object* 됩니다 **nvarchar(386)**, 기본값은 NULL입니다. NULL 인 경우 [sp_articleview](../../relational-databases/system-stored-procedures/sp-articleview-transact-sql.md) 자동으로 출력 파일을 생성 하는 데 사용 하는 뷰를 만들기 위해 호출 됩니다. 사용 하 여 모든 열을 추가한 후 이런 [sp_articlecolumn](../../relational-databases/system-stored-procedures/sp-articlecolumn-transact-sql.md)합니다. NULL이 아닌 경우 뷰가 수동으로 생성된 것으로 가정하며 뷰가 생성되지 않습니다.  
  
 [  **@ins_cmd =** ] **'**_ins_cmd_**'**  
 이 아티클에 대한 삽입을 복제할 때 사용하는 복제 명령 유형입니다. *ins_cmd* 됩니다 **nvarchar(255)**, 이며 다음 값 중 하나일 수 있습니다.  
  
|값|Description|  
|-----------|-----------------|  
|**NONE**|아무 작업도 수행 합니다.|  
|**CALL sp_MSins_**<br /> **_테이블_**  (기본값)<br /><br /> -또는-<br /><br /> **Custom_stored_procedure_name 호출**|구독자에서 실행할 저장 프로시저를 호출합니다. 이 방법의 복제를 사용 하려면 *schema_option* 문서의 각 구독자의 대상 데이터베이스에서 지정된 된 저장된 프로시저를 만들거나 저장된 프로시저의 자동으로 만들도록 지정 합니다. *custom_stored_procedure* 사용자가 만든 저장된 프로시저의 이름입니다. <strong>sp_MSins_*테이블*</strong>  대신 대상 테이블의 이름을 포함 합니다 *(_t)* 매개 변수의 부분입니다. 때 *destination_owner* 를 지정 하면 대상 테이블 이름 앞에 추가 합니다. 예를 들어,를 **ProductCategory** 테이블을 소유 합니다 **프로덕션** 매개 변수는 일은 구독자에서 스키마를 `CALL sp_MSins_ProductionProductCategory`입니다. 피어 투 피어 복제 토폴로지에서 아티클의 *(_t)* GUID 값으로 추가 됩니다. 지정 *custom_stored_procedure* 업데이트 구독자가 지원 되지 않습니다.|  
|**SQL** 또는 NULL|INSERT 문을 복제합니다. INSERT 문에는 아티클에 게시된 모든 열에 대한 값이 제공됩니다. 삽입에서 다음 명령이 복제됩니다.<br /><br /> `INSERT INTO <table name> VALUES (c1value, c2value, c3value, ..., cnvalue)`|  
  
 자세한 내용은 [트랜잭션 아티클에 대한 변경 내용을 전파하는 방법 지정](../../relational-databases/replication/transactional/transactional-articles-specify-how-changes-are-propagated.md)을 참조하세요.  
  
 [  **@del_cmd =**] **'**_del_cmd_**'**  
 이 아티클에 대한 삭제를 복제할 때 사용하는 복제 명령 유형입니다. *del_cmd* 됩니다 **nvarchar(255)**, 이며 다음 값 중 하나일 수 있습니다.  
  
|값|Description|  
|-----------|-----------------|  
|**NONE**|아무 작업도 수행 합니다.|  
|**CALLsp_MSdel_**<br /> **_테이블_**  (기본값)<br /><br /> -또는-<br /><br /> **Custom_stored_procedure_name 호출**|구독자에서 실행할 저장 프로시저를 호출합니다. 이 방법의 복제를 사용 하려면 *schema_option* 문서의 각 구독자의 대상 데이터베이스에서 지정된 된 저장된 프로시저를 만들거나 저장된 프로시저의 자동으로 만들도록 지정 합니다. *custom_stored_procedure* 사용자가 만든 저장된 프로시저의 이름입니다. <strong>sp_MSdel_*테이블*</strong>  대신 대상 테이블의 이름을 포함 합니다 *(_t)* 매개 변수의 부분입니다. 때 *destination_owner* 를 지정 하면 대상 테이블 이름 앞에 추가 합니다. 예를 들어,를 **ProductCategory** 테이블을 소유 합니다 **프로덕션** 매개 변수는 일은 구독자에서 스키마를 `CALL sp_MSdel_ProductionProductCategory`입니다. 피어 투 피어 복제 토폴로지에서 아티클의 *(_t)* GUID 값으로 추가 됩니다. 지정 *custom_stored_procedure* 업데이트 구독자가 지원 되지 않습니다.|  
|**XCALL sp_MSdel_**<br /> **_테이블_**<br /><br /> -또는-<br /><br /> **XCALL custom_stored_procedure_name**|XCALL 스타일 매개 변수를 사용하는 저장 프로시저를 호출합니다. 이 방법의 복제를 사용 하려면 *schema_option* 문서의 각 구독자의 대상 데이터베이스에서 지정된 된 저장된 프로시저를 만들거나 저장된 프로시저의 자동으로 만들도록 지정 합니다. 구독자 업데이트의 경우 사용자가 만든 저장 프로시저를 지정할 수 없습니다.|  
|**SQL** 또는 NULL|DELETE 문을 복제합니다. DELETE 문에는 모든 기본 키 열 값이 제공됩니다. 삭제에서 다음 명령이 복제됩니다.<br /><br /> `DELETE FROM <table name> WHERE pkc1 = pkc1value AND pkc2 = pkc2value AND pkcn = pkcnvalue`|  
  
 자세한 내용은 [트랜잭션 아티클에 대한 변경 내용을 전파하는 방법 지정](../../relational-databases/replication/transactional/transactional-articles-specify-how-changes-are-propagated.md)을 참조하세요.  
  
 [  **@upd_cmd =**] **'**_upd_cmd_**'**  
 이 아티클에 대한 업데이트를 복제할 때 사용하는 복제 명령 유형입니다. *upd_cmd* 됩니다 **nvarchar(255)**, 이며 다음 값 중 하나일 수 있습니다.  
  
|값|Description|  
|-----------|-----------------|  
|**NONE**|아무 작업도 수행 합니다.|  
|**Sp_MSupd_ 호출**<br /> **_테이블_**<br /><br /> -또는-<br /><br /> **Custom_stored_procedure_name 호출**|구독자에서 실행할 저장 프로시저를 호출합니다. 이 방법의 복제를 사용 하려면 *schema_option* 문서의 각 구독자의 대상 데이터베이스에서 지정된 된 저장된 프로시저를 만들거나 저장된 프로시저의 자동으로 만들도록 지정 합니다.|  
|**MCALL sp_MSupd_**<br /> **_테이블_**<br /><br /> -또는-<br /><br /> **MCALL custom_stored_procedure_name**|MCALL 스타일 매개 변수를 사용하는 저장 프로시저를 호출합니다. 이 방법의 복제를 사용 하려면 *schema_option* 문서의 각 구독자의 대상 데이터베이스에서 지정된 된 저장된 프로시저를 만들거나 저장된 프로시저의 자동으로 만들도록 지정 합니다. *custom_stored_procedure* 사용자가 만든 저장된 프로시저의 이름입니다. <strong>sp_MSupd_*테이블*</strong>  대신 대상 테이블의 이름을 포함 합니다 *(_t)* 매개 변수의 부분입니다. 때 *destination_owner* 를 지정 하면 대상 테이블 이름 앞에 추가 합니다. 예를 들어,를 **ProductCategory** 테이블을 소유 합니다 **프로덕션** 매개 변수는 일은 구독자에서 스키마를 `MCALL sp_MSupd_ProductionProductCategory`입니다. 피어 투 피어 복제 토폴로지에서 아티클의 *(_t)* GUID 값으로 추가 됩니다. 구독자 업데이트의 경우 사용자가 만든 저장 프로시저를 지정할 수 없습니다.|  
|**SCALL sp_MSupd_**<br /> **_테이블_**  (기본값)<br /><br /> -또는-<br /><br /> **SCALL custom_stored_procedure_name**|SCALL 스타일 매개 변수를 사용하는 저장 프로시저를 호출합니다. 이 방법의 복제를 사용 하려면 *schema_option* 문서의 각 구독자의 대상 데이터베이스에서 지정된 된 저장된 프로시저를 만들거나 저장된 프로시저의 자동으로 만들도록 지정 합니다. *custom_stored_procedure* 사용자가 만든 저장된 프로시저의 이름입니다. <strong>sp_MSupd_*테이블*</strong>  대신 대상 테이블의 이름을 포함 합니다 *(_t)* 매개 변수의 부분입니다. 때 *destination_owner* 를 지정 하면 대상 테이블 이름 앞에 추가 합니다. 예를 들어,를 **ProductCategory** 테이블을 소유 합니다 **프로덕션** 매개 변수는 일은 구독자에서 스키마를 `SCALL sp_MSupd_ProductionProductCategory`입니다. 피어 투 피어 복제 토폴로지에서 아티클의 *(_t)* GUID 값으로 추가 됩니다. 구독자 업데이트의 경우 사용자가 만든 저장 프로시저를 지정할 수 없습니다.|  
|**XCALL sp_MSupd_**<br /> **_테이블_**<br /><br /> -또는-<br /><br /> **XCALL custom_stored_procedure_name**|XCALL 스타일 매개 변수를 사용하는 저장 프로시저를 호출합니다. 이 방법의 복제를 사용 하려면 *schema_option* 문서의 각 구독자의 대상 데이터베이스에서 지정된 된 저장된 프로시저를 만들거나 저장된 프로시저의 자동으로 만들도록 지정 합니다. 구독자 업데이트의 경우 사용자가 만든 저장 프로시저를 지정할 수 없습니다.|  
|**SQL** 또는 NULL|UPDATE 문을 복제합니다. UPDATE 문에는 모든 열 값 및 기본 키 열 값이 제공됩니다. 업데이트에서 다음 명령이 복제됩니다.<br /><br /> `UPDATE <table name> SET c1 = c1value, SET c2 = c2value, SET cn = cnvalue WHERE pkc1 = pkc1value AND pkc2 = pkc2value AND pkcn = pkcnvalue`|  
  
> [!NOTE]  
>  CALL, MCALL, SCALL 및 XCALL 구문에서 구독자에 전파되는 데이터 양은 각각 다릅니다. CALL 구문은 삽입 및 삭제한 모든 열의 모든 값을 전달합니다. SCALL 구문은 영향을 받은 열 값만 전달합니다. XCALL 구문은 열의 이전 값과 함께 변경 여부에 관계없이 모든 열의 값을 전달합니다. 자세한 내용은 [트랜잭션 아티클에 대한 변경 내용을 전파하는 방법 지정](../../relational-databases/replication/transactional/transactional-articles-specify-how-changes-are-propagated.md)을 참조하세요.  
  
 [  **@creation_script =**] **'**_creation_script_**'**  
 구독 데이터베이스에서 아티클을 만드는 데 사용된 선택적 아티클 스키마 스크립트의 경로 및 이름입니다. *creation_script* 됩니다 **nvarchar(255)**, 기본값은 NULL입니다.  
  
 [  **@description =**] **'**_설명을_**'**  
 아티클에 대한 설명 항목입니다. *설명* 됩니다 **nvarchar(255)**, 기본값은 NULL입니다.  
  
 [  **@pre_creation_cmd =**] **'**_pre_creation_cmd_**'**  
 해당 아티클에 대한 스냅숏을 적용할 때 구독자에서 같은 이름의 기존 개체가 검색될 경우 시스템이 할 일을 지정합니다. *pre_creation_cmd* 됩니다 **nvarchar(10)**, 이며 다음 값 중 하나일 수 있습니다.  
  
|값|Description|  
|-----------|-----------------|  
|**없음**|명령을 사용하지 않습니다.|  
|**delete**|스냅숏을 적용하기 전에 대상 테이블에서 데이터를 삭제합니다. 아티클이 행 필터링되면 필터 절에서 지정한 열에 있는 데이터만 삭제됩니다. 행 필터를 정의하면 Oracle 게시자에 대해서는 지원되지 않습니다.|  
|**drop** (기본값)|대상 테이블을 삭제합니다.|  
|**truncate**|대상 테이블을 자릅니다. ODBC 또는 OLE DB 구독자에는 유효하지 않습니다.|  
  
 [  **@filter_clause=**] **'**_filter_clause_**'**  
 행 필터를 정의하는 제한(WHERE) 절입니다. 제약 조건 절을 입력할 때는 키워드인 WHERE를 생략합니다. *filter_clause* 됩니다 **ntext**, 기본값은 NULL입니다. 자세한 내용은 [게시된 데이터 필터링](../../relational-databases/replication/publish/filter-published-data.md)을 참조하세요.  
  
 [  **@schema_option =**] *schema_option*  
 지정한 아티클에 대한 스키마 생성 옵션의 비트 마스크입니다. *schema_option* 됩니다 **binary (8)**, 수 및는 [| (비트 OR) ](../../t-sql/language-elements/bitwise-or-transact-sql.md) 다음이 값 중 하나 이상의 제품:  
  
> [!NOTE]  
>  이 값이 NULL인 경우 시스템은 다른 아티클 속성에 따라 이 아티클에 대해 유효한 스키마 옵션을 자동으로 생성합니다. 합니다 **기본 스키마 옵션** 주의 있는 테이블 아티클 유형과 복제 유형의 조합을 기반으로 선택할 수 있는 값을 표시 합니다.  
  
|값|Description|  
|-----------|-----------------|  
|**0x00**|사용 하 여 스냅숏 에이전트로 스크립팅을 할 *creation_script*합니다.|  
|**0x01**|개체 만들기 스크립트(CREATE TABLE, CREATE PROCEDURE 등)를 생성합니다. 이 값은 저장 프로시저 아티클에 대한 기본값입니다.|  
|**0x02**|정의된 경우 아티클에 대한 변경 내용을 전파하는 저장 프로시저를 생성합니다.|  
|**0x04**|IDENTITY 속성을 사용하여 ID 열이 스크립팅됩니다.|  
|**0x08**|복제할 **타임 스탬프** 열입니다. 그렇지 않은 경우 설정 **타임 스탬프** 열으로 복제할지 **이진**합니다.|  
|**0x10**|해당 클러스터형 인덱스를 생성합니다. 이 옵션을 설정하지 않아도 게시된 테이블에 이미 정의되어 있으면 기본 키 및 UNIQUE 제약 조건과 관련된 인덱스가 생성됩니다.|  
|**0x20**|사용자 정의 데이터 형식(UDT)을 구독자에서의 기본 데이터 형식으로 변환합니다. UDT 열에 CHECK 또는 DEFAULT 제약 조건이 있거나 UDT 열이 기본 키의 일부이거나 계산 열이 UDT 열을 참조하는 경우 이 옵션을 사용할 수 없습니다. *Oracle 게시자에 대해서는 지원 되지 않습니다*합니다.|  
|**0x40**|해당 비클러스터형 인덱스를 생성합니다. 이 옵션을 설정하지 않아도 게시된 테이블에 이미 정의되어 있으면 기본 키 및 UNIQUE 제약 조건과 관련된 인덱스가 생성됩니다.|  
|**0x80**|PRIMARY KEY 제약 조건을 복제합니다. 제약 조건에 연결 된 인덱스가 모두 복제 됩니다 경우에 옵션 **0x10** 하 고 **0x40** 를 사용할 수 없습니다.|  
|**0x100**|정의된 경우 테이블 아티클에 사용자 트리거를 복제합니다. *Oracle 게시자에 대해서는 지원 되지 않습니다*합니다.|  
|**0x200**|FOREIGN KEY 제약 조건을 복제합니다. 참조되는 테이블이 게시되지 않는 경우 게시된 테이블의 모든 FOREIGN KEY 제약 조건은 복제되지 않습니다. *Oracle 게시자에 대해서는 지원 되지 않습니다*합니다.|  
|**0x400**|CHECK 제약 조건을 복제합니다. *Oracle 게시자에 대해서는 지원 되지 않습니다*합니다.|  
|**0x800**|기본값을 복제합니다. *Oracle 게시자에 대해서는 지원 되지 않습니다*합니다.|  
|**0x1000**|열 수준 데이터 정렬을 복제합니다.<br /><br /> **참고:** 대/소문자 구분 비교를 사용하려면 Oracle 게시자에 대해 이 옵션을 설정해야 합니다.|  
|**0x2000**|게시된 아티클 원본 개체와 연관된 확장 속성을 복제합니다. *Oracle 게시자에 대해서는 지원 되지 않습니다*합니다.|  
|**0x4000**|UNIQUE 제약 조건을 복제합니다. 제약 조건에 연결 된 인덱스가 모두 복제 됩니다 경우에 옵션 **0x10** 하 고 **0x40** 를 사용할 수 없습니다.|  
|**0x8000**|이 옵션은 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 게시자에 적합하지 않습니다.|  
|**0x10000**|동기화하는 동안 CHECK 조건이 강제 적용되지 않도록 해당 제약 조건을 NOT FOR REPLICATION으로 복제합니다.|  
|**0x20000**|동기화하는 동안 FOREIGN KEY 제약 조건이 강제 적용되지 않도록 해당 제약 조건을 NOT FOR REPLICATION으로 복제합니다.|  
|**0x40000**|분할된 테이블이나 인덱스와 연결된 파일 그룹을 복제합니다.|  
|**0x80000**|분할된 테이블에 대한 파티션 구성표를 복제합니다.|  
|**0x100000**|분할된 인덱스에 대한 파티션 구성표를 복제합니다.|  
|**0x200000**|테이블 통계를 복제합니다.|  
|**0x400000**|기본 바인딩|  
|**0x800000**|규칙 바인딩|  
|**0x1000000**|전체 텍스트 인덱스|  
|**0x2000000**|XML 스키마 컬렉션에 바인딩된 **xml** 열 복제 되지 않습니다.|  
|**0x4000000**|인덱스를 복제 **xml** 열입니다.|  
|**0x8000000**|구독자에 없는 스키마를 만듭니다.|  
|**0x10000000**|변환 **xml** 열을 **ntext** 구독자의 합니다.|  
|**0x20000000**|변환 큰 개체 데이터 형식 (**nvarchar (max)** 하십시오 **varchar (max)**, 및 **varbinary (max)**)에 도입 된 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 에서지원되는데이터형식[!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)].|  
|**0x40000000**|사용 권한을 복제합니다.|  
|**0x80000000**|게시의 일부가 아닌 개체에 대한 종속성을 삭제합니다.|  
|**0x100000000**|에 지정 된 경우 FILESTREAM 특성을 복제 하려면이 옵션을 사용 **varbinary (max)** 열입니다. 테이블을 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 구독자에 복제할 경우에는 이 옵션을 지정하지 마십시오. FILESTREAM 열이 있는 테이블을 복제 [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] 이 스키마 옵션을 설정 하는 방법에 관계 없이 구독자 지원 되지 않습니다.<br /><br /> 관련된 옵션을 참조 하세요 **0x800000000**합니다.|  
|**0x200000000**|날짜 및 시간 데이터 형식 변환 (**날짜**를 **시간**를 **datetimeoffset**, 및 **datetime2**)에 도입 된 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 데이터 이전 버전의 지원 되는 형식을 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]합니다.|  
|**0x400000000**|데이터 및 인덱스에 대한 압축 옵션을 복제합니다. 자세한 내용은 [Data Compression](../../relational-databases/data-compression/data-compression.md)을 참조하세요.|  
|**0x800000000**|FILESTREAM 데이터를 구독자에서 고유한 파일 그룹에 저장하려면 이 옵션을 설정합니다. 이 옵션을 설정하지 않으면 FILESTREAM 데이터는 기본 파일 그룹에 저장됩니다. 복제 기능에서는 파일 그룹을 만들지 않으므로 이 옵션을 설정할 경우 구독자에서 스냅숏을 적용하기 전에 파일 그룹을 만들어야 합니다. 스냅숏을 적용 하기 전에 개체를 만드는 방법에 대 한 자세한 내용은 참조 하세요. [하기 전에 스크립트 실행 및 스냅숏 적용 전후](../../relational-databases/replication/execute-scripts-before-and-after-the-snapshot-is-applied.md)합니다.<br /><br /> 관련된 옵션을 참조 하세요 **0x100000000**합니다.|  
|**0x1000000000**|공용 언어 런타임 (CLR) 사용자 정의 형식 (Udt) 8000 바이트 보다 큰 경우에 변환 **varbinary (max)** 실행 하는 구독자에 게 UDT 형식의 열을 복제할 수 있도록 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]입니다.|  
|**0x2000000000**|변환 된 **hierarchyid** 데이터 형식입니다 **varbinary (max)** 있도록 형식의 열 **hierarchyid** 실행 하는 구독자에 복제할 수 있습니다 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]. 사용 하는 방법에 대 한 자세한 내용은 **hierarchyid** 복제 된 테이블의 열 참조 [hierarchyid &#40;TRANSACT-SQL&#41;](../../t-sql/data-types/hierarchyid-data-type-method-reference.md).|  
|**0x4000000000**|테이블의 필터링된 인덱스를 복제합니다. 필터링 된 인덱스에 대 한 자세한 내용은 참조 하세요. [필터링 된 인덱스 만들기](../../relational-databases/indexes/create-filtered-indexes.md)합니다.|  
|**0x8000000000**|변환 된 **지리** 및 **기 하 도형** 데이터 형식에 **varbinary (max)** 중인구독자에게이러한형식의열을복제할수있도록[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].|  
|**0x10000000000**|형식의 열에 인덱스를 복제 **지리** 하 고 **기 하 도형**합니다.|  
|**0x20000000000**|열에 대한 SPARSE 특성을 복제합니다. 이 특성에 대 한 자세한 내용은 참조 하세요. [스파스 열 사용](../../relational-databases/tables/use-sparse-columns.md)합니다.|  
|**0x40000000000**|구독자에서 메모리 최적화 테이블을 만들려면 스냅숏 에이전트로 스크립팅을 사용 하도록 설정 합니다.|  
|**0x80000000000**|메모리 액세스에 최적화 된 아티클에 대 한 비클러스터형된 인덱스를 클러스터형 인덱스를 변환 합니다.|  
|**0x400000000000**|테이블의 모든 비클러스터형 columnstore 인덱스를 복제합니다.|  
|**0x800000000000**|테이블의 모든 flitered 비클러스터형 columnstore 인덱스를 복제합니다.|  
|NULL|복제를 자동으로 설정 *schema_option* 기본값을 하는 값에 따라 달라 집니다 다른 아티클 속성입니다. 주의 섹션에 있는 “기본 스키마 옵션” 표에서는 아티클 유형과 복제 유형을 기반으로 하는 기본 스키마 옵션을 보여 줍니다.<br /><br /> 에 대 한 기본값 이외[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 게시 됩니다 **0x050D3**합니다.|  
  
 일부 *schema_option* 값은 모든 유형의 복제 및 문서 유형에 대 한 유효 합니다. 합니다 **유효한 스키마 옵션** 주의 섹션의 표에서 아티클 유형과 복제 유형의 조합을 기반으로 유효한 스키마 옵션을 선택할 수 있습니다.  
  
 [  **@destination_owner =**] **'**_destination_owner_**'**  
 대상 개체의 소유자 이름입니다. *destination_owner* 됩니다 **sysname**, 기본값은 NULL입니다. 때 *destination_owner* 지정 하지 않으면 다음 규칙에 따라 자동으로 소유자가 지정 합니다.  
  
|조건|대상 개체 소유자|  
|---------------|------------------------------|  
|게시는 기본 모드 대량 복사를 사용하여 초기 스냅숏을 생성하며 이는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 구독자만 지원합니다.|값을 기본값으로 *source_owner*합니다.|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 이외 게시자에서 게시합니다.|기본값은 대상 데이터베이스의 소유자입니다.|  
|게시는 문자 모드 대량 복사를 사용하여 초기 스냅숏을 생성하며 이는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 이외 구독자를 지원합니다.|할당되지 않습니다.|  
  
 지원 하도록 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 구독자 *destination_owner* NULL 이어야 합니다.  
  
 [  **@status=**] *상태*  
 아티클이 활성 상태인지 여부와 변경 내용 전파 방법에 대한 추가 옵션을 지정합니다. *상태* 됩니다 **tinyint**, 수 및는 [| (비트 OR) ](../../t-sql/language-elements/bitwise-or-transact-sql.md) 다음이 값 중 하나 이상의 제품입니다.  
  
|값|Description|  
|-----------|-----------------|  
|**1**|아티클이 활성 상태입니다.|  
|**8**|INSERT 문에 열 이름을 포함합니다.|  
|**16** (기본값)|매개 변수가 있는 문을 사용합니다.|  
|**24**|INSERT 문에 열 이름도 포함하고 매개 변수가 있는 문도 사용합니다.|  
|**64**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
  
 예를 들어 매개 변수가 있는 문을 사용하는 활성 아티클은 이 열의 값이 17이 되며 값이 **0** 는 아티클이 활성 상태입니다. 추가 속성 없이 정의 된 의미 합니다.  
  
 [  **@source_owner =**] **'**_source_owner_**'**  
 원본 개체의 소유자입니다. *source_owner* 됩니다 **sysname**, 기본값은 NULL입니다. *source_owner* Oracle 게시자를 지정 해야 합니다.  
  
 [  **@sync_object_owner =**] **'**_sync_object_owner_**'**  
 게시된 아티클을 정의하는 뷰의 소유자입니다. *sync_object_owner* 됩니다 **sysname**, 기본값은 NULL입니다.  
  
 [  **@filter_owner =**] **'**_filter_owner_**'**  
 필터의 소유자입니다. *filter_owner* 됩니다 **sysname**, 기본값은 NULL입니다.  
  
 [  **@source_object =**] **'**_source_object_**'**  
 게시할 데이터베이스 개체입니다. *source_object* 됩니다 **sysname**, 기본값은 NULL입니다. 하는 경우 *source_table* 가 null 인 경우 *source_object* NULL 일 수 없습니다. *source_object* 대신 사용 해야 *source_table*합니다. 스냅숏 또는 트랜잭션 복제를 사용 하 여 게시할 수 있는 개체의 형식에 대 한 자세한 내용은 참조 하세요. [데이터 및 데이터베이스 개체 게시](../../relational-databases/replication/publish/publish-data-and-database-objects.md)합니다.  
  
 [  **@artid =** ] _article_ID_ **출력**  
 새 아티클의 아티클 ID입니다. *article_ID* 됩니다 **int** 이며 기본값은 NULL이 고 출력 매개 변수입니다.  
  
 [  **@auto_identity_range =** ] **'**_auto_identity_range_**'**  
 게시를 생성할 때 자동 ID 범위 처리를 게시에 사용하거나 사용하지 않도록 합니다. *auto_identity_range* 됩니다 **nvarchar(5)**, 이며 다음 값 중 하나일 수 있습니다.  
  
|값|Description|  
|-----------|-----------------|  
|**true**|자동 ID 범위 처리를 사용합니다.|  
|**false**|자동 ID 범위 처리를 사용하지 않습니다.|  
|NULL(default)|Id 범위 처리는 설정한 *identityrangemanagementoption*합니다.|  
  
> [!NOTE]  
>  *auto_identity_range* 사용 되지 않으며 이전 버전과 호환성만 제공 됩니다. 기능을 사용할지 *identityrangemanagementoption* id 범위 관리 옵션을 지정 합니다. 자세한 내용은 [ID 열 복제](../../relational-databases/replication/publish/replicate-identity-columns.md)를 참조하세요.  
  
 [  **@pub_identity_range =** ] *pub_identity_range*  
 기술 자료 문서에 하는 경우 게시자 범위 크기를 제어 *identityrangemanagementoption* 로 설정 **자동** 하거나 *auto_identity_range* 로 **true** . *pub_identity_range* 됩니다 **bigint**, 기본값은 NULL입니다. *Oracle 게시자에 대해서는 지원 되지 않습니다*합니다.  
  
 [  **@identity_range =** ] *identity_range*  
 문서에 있는 경우 구독자 범위 크기를 제어 *identityrangemanagementoption* 로 설정 **자동** 하거나 *auto_identity_range* 로 **true** . *identity_range* 됩니다 **bigint**, 기본값은 NULL입니다. 사용 시기 *auto_identity_range* 로 설정 된 **true**합니다. *Oracle 게시자에 대해서는 지원 되지 않습니다*합니다.  
  
 [  **@threshold =** ] *임계값*  
 배포 에이전트가 새로운 ID 범위를 할당하는 시기를 지정하는 백분율 값입니다. 에 지정 된 값의 백분율 *임계값* 는 사용, 배포 에이전트가 새 id 범위를 만듭니다. *임계값* 됩니다 **bigint**, 기본값은 NULL입니다. 때 사용 되는 *identityrangemanagementoption* 로 설정 된 **자동** 하거나 *auto_identity_range* 로 설정 되어 **true**합니다. *Oracle 게시자에 대해서는 지원 되지 않습니다*합니다.  
  
 [  **@force_invalidate_snapshot =** ] *force_invalidate_snapshot*  
 으로 인해이 저장된 프로시저가 수행한 동작 기존 스냅숏을 무효화 될 수 있습니다. *force_invalidate_snapshot* 되는 **비트**, 기본값은 0 사용 하 여 합니다.  
  
 **0** 아티클을 추가 유효 하지 않게 스냅숏이 무효화 되지 않습니다 지정 합니다. 저장 프로시저가 새 스냅숏을 필요로 하는 변경을 발견하면 오류가 발생하며 변경이 수행되지 않습니다.  
  
 **1** 지정 하는 않음으로 표시 될 기존 스냅숏과 새 스냅숏을 생성할 권한을 부여 아티클의을 유효 하지 않게 스냅숏을 무효화 하 고 새 스냅숏을 해야 하는 구독이 있는 경우 추가 합니다.  
  
 [  **@use_default_datatypes =** ] *use_default_datatypes*  
 Oracle 게시자에서 아티클을 게시할 때 기본 열 데이터 형식 매핑의 사용 여부입니다. *use_default_datatypes* 는 bit 이며 기본값은 1입니다.  
  
 **1** = 기본 아티클 열 매핑이 사용 됩니다. 실행 하 여 기본 데이터 형식 매핑을 표시할 수 있습니다 [sp_getdefaultdatatypemapping](../../relational-databases/system-stored-procedures/sp-getdefaultdatatypemapping-transact-sql.md)합니다.  
  
 **0** = 사용자 지정 아티클 열 매핑이 정의 되어 있어 [sp_articleview](../../relational-databases/system-stored-procedures/sp-articleview-transact-sql.md) 호출 되지 않습니다 **sp_addarticle**합니다.  
  
 때 *use_default_datatypes* 로 설정 된 **0**를 실행 해야 합니다 [sp_changearticlecolumndatatype](../../relational-databases/system-stored-procedures/sp-changearticlecolumndatatype-transact-sql.md) 기본값에서 변경 된 각 열 매핑에 대 한 한 번입니다. 모든 사용자 지정 열 매핑이 정의 된 후 실행 해야 합니다 [sp_articleview](../../relational-databases/system-stored-procedures/sp-articleview-transact-sql.md)합니다.  
  
> [!NOTE]  
>  이 매개 변수는 Oracle 게시자에 대해서만 사용해야 합니다. 설정 *use_default_datatypes* 하 **0** 에 대 한는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 게시자 오류를 생성 합니다.  
  
 [  **@identityrangemanagementoption =** ] *identityrangemanagementoption*  
 아티클에 대해 ID 범위 관리를 처리하는 방법을 지정합니다. *identityrangemanagementoption* 됩니다 **nvarchar(10)**, 이며 다음 값 중 하나일 수 있습니다.  
  
|값|Description|  
|-----------|-----------------|  
|**없음**|복제에서 ID 범위 관리를 명시적으로 수행하지 않습니다. 이 옵션은 이전 버전 SQL Server와의 호환성을 위해서만 사용하는 것이 좋습니다. 피어 복제에 대해서는 허용되지 않습니다.|  
|**수동**|수동 ID 범위 처리를 사용하려면 NOT FOR REPLICATION을 사용하여 ID 열을 표시합니다.|  
|**자동**|ID 범위의 자동 관리를 지정합니다.|  
|NULL(default)|기본값으로 **none** 때 변수의 *auto_identity_range* 아닙니다 **true**합니다. 기본값으로 **수동** 에 피어 투 피어 토폴로지 기본값 (*auto_identity_range* 무시 됩니다).|  
  
 이전 버전과 호환성에 대 한 경우 값 *identityrangemanagementoption* 가 null 인 경우 값 *auto_identity_range* 확인란이 선택 되어 있습니다. 그러나 경우 값 *identityrangemanagementoption* 가 NULL이 아니면 값 *auto_identity_range* 무시 됩니다.  
  
 자세한 내용은 [ID 열 복제](../../relational-databases/replication/publish/replicate-identity-columns.md)를 참조하세요.  
  
 [  **@publisher =** ] **'**_게시자_**'**  
 지정 된 비- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 게시자입니다. *게시자* 됩니다 **sysname**, 기본값은 NULL입니다.  
  
> [!NOTE]  
>  *게시자* 해서는 안에 아티클을 추가 하는 경우는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 게시자입니다.  
  
 [  **@fire_triggers_on_snapshot =** ] **'**_fire_triggers_on_snapshot_**'**  
 복제된 사용자 트리거를 초기 스냅숏이 적용될 때 실행할지 여부입니다. *fire_triggers_on_snapshot* 됩니다 **nvarchar(5)**, 기본값은 FALSE입니다. **true** 는 스냅숏을 적용할 때 복제 된 테이블의 사용자 트리거가 실행 됨을 의미 합니다. 복제 된 트리거에 대 한 순서 대로 비트 마스크 값 *schema_option* 값이 있어야 **0x100**합니다.  
  
## <a name="return-code-values"></a>반환 코드 값  
 **0** (성공) 또는 **1** (실패)  
  
## <a name="remarks"></a>Remarks  
 **sp_addarticle** 스냅숏 복제 또는 트랜잭션 복제에 사용 됩니다.  
  
 기본적으로 복제는 열 데이터 형식이 복제에서 지원되지 않으면 원본 테이블의 어떤 열도 게시하지 않습니다. 이러한 열을 게시 해야 할 경우 실행 해야 합니다 [sp_articlecolumn](../../relational-databases/system-stored-procedures/sp-articlecolumn-transact-sql.md) 열을 추가 합니다.  
  
 피어 투 피어 트랜잭션 복제를 지원하는 게시에 아티클을 추가하는 경우 다음 제한이 적용됩니다.  
  
-   모든 logbased 아티클에 대해 매개 변수가 있는 문을 지정해야 하며 포함 해야 합니다 **16** 에 *상태* 값입니다.  
  
-   대상 테이블의 이름 및 소유자는 원본 테이블과 일치해야 합니다.  
  
-   아티클을 행 또는 열 필터링할 수 없습니다.  
  
-   자동 ID 범위 관리는 지원되지 않습니다. 설명서에 대 한 값을 지정 해야 합니다 *identityrangemanagementoption*합니다.  
  
-   경우는 **타임 스탬프** 테이블에 있는 열에 0x08을 포함 해야 합니다 *schema_option* 열을 복제할 **타임 스탬프**합니다.  
  
-   값이 **SQL** 지정할 수 없습니다 *ins_cmd*에 *upd_cmd*, 및 *del_cmd*합니다.  
  
 자세한 내용은 [Peer-to-Peer Transactional Replication](../../relational-databases/replication/transactional/peer-to-peer-transactional-replication.md)을 참조하세요.  
  
 개체를 게시하면 해당 정의가 구독자로 복사됩니다. 하나 이상의 다른 개체에 종속된 데이터베이스 개체를 게시하는 경우 참조되는 개체를 모두 게시해야 합니다. 예를 들어 테이블에 종속된 뷰를 게시하는 경우 테이블도 게시해야 합니다.  
  
 하는 경우 *vertical_partition* 로 설정 된 **true**에 **sp_addarticle** 될 때까지 뷰 생성을 연기 [sp_articleview](../../relational-databases/system-stored-procedures/sp-articleview-transact-sql.md) 이후에 호출 됩니다 ( 마지막 [sp_articlecolumn](../../relational-databases/system-stored-procedures/sp-articlecolumn-transact-sql.md) 추가).  
  
 게시 구독 및 게시 된 테이블에 업데이트를 허용 하는 경우는 **uniqueidentifier** 열 **sp_addarticle** 추가 **uniqueidentifier** 열 테이블에 자동으로 합니다.  
  
 인스턴스가 아닌 구독자에 복제 하는 경우 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (다른 유형의 복제)만 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문이 지원 됩니다 **삽입**를 **업데이트**, 및 **삭제할** 명령입니다.  
  
 로그 판독기 에이전트가 실행 중인 경우 아티클을 피어 투 피어 게시에 추가할 경우 로그 판독기 에이전트와 아티클을 추가하는 프로세스 간에 교착 상태가 발생할 수 있습니다. 이 문제를 방지하려면 아티클을 피어 투 피어 게시에 추가하기 전에 복제 모니터를 사용하여 아티클을 추가 중인 노드에서 로그 판독기를 중지합니다. 아티클을 추가한 후 로그 판독기 에이전트를 다시 시작합니다.  
  
 설정 하는 경우 `@del_cmd = 'NONE'` 또는 `@ins_cmd = 'NONE'`에서 전파 **업데이트** 명령 또한 영향을 받을 수 없습니다 바인딩된 업데이트가 발생 하더라도 해당 명령을 전송 합니다. 바인딩된 업데이트는 구독자에 대한 DELETE/INSERT 쌍으로 복제되는 게시자의 UPDATE 문입니다.  
  
## <a name="default-schema-options"></a>기본 스키마 옵션  
 이 표에서 경우 복제를 설정한 기본값 *schema_options* 이 값 (위쪽에 표시 됨) 복제 유형 및 아티클 유형 (첫 번째 열에 표시)에 따라 달라 집니다 사용자가 지정 하지 않으면.  
  
|아티클 유형|복제 유형||  
|------------------|----------------------|------|  
||트랜잭션|스냅숏|  
|**집계 스키마만**|**0x01**|**0x01**|  
|**func 스키마만**|**0x01**|**0x01**|  
|**인덱싱된 뷰 스키마 전용**|**0x01**|**0x01**|  
|**인덱싱된 뷰 logbased**|**0x30F3**|**0x3071**|  
|**인덱싱된 뷰 밑 manualboth**|**0x30F3**|**0x3071**|  
|**logbased manualfilter 인덱싱된 뷰**|**0x30F3**|**0x3071**|  
|**logbased manualview 인덱싱된 뷰**|**0x30F3**|**0x3071**|  
|**logbased**|**0x30F3**|**0x3071**|  
|**logbased manualfilter**|**0x30F3**|**0x3071**|  
|**logbased manualview**|**0x30F3**|**0x3071**|  
|**proc exec**|**0x01**|**0x01**|  
|**프로시저 스키마 전용**|**0x01**|**0x01**|  
|**serializable proc exec**|**0x01**|**0x01**|  
|**뷰 스키마 전용**|**0x01**|**0x01**|  
  
> [!NOTE]
>  게시를 지연 업데이트를 활성화 하는 경우는 *schema_option* 의 값 **0x80** 표에 표시 된 기본값에 추가 됩니다. 기본값 *schema_option* 이외 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 게시가 **0x050D3**합니다.  
  
## <a name="valid-schema-options"></a>유효한 스키마 옵션  
 이 표에서 허용 되는 값 *schema_option* (위쪽에 표시 됨) 복제 유형 및 아티클 유형 (첫 번째 열에 표시)에 따라 합니다.  
  
|아티클 유형|복제 유형||  
|------------------|----------------------|------|  
||트랜잭션|스냅숏|  
|**logbased**|모든 옵션|모든 옵션 이지만 **0x02**|  
|**logbased manualfilter**|모든 옵션|모든 옵션 이지만 **0x02**|  
|**logbased manualview**|모든 옵션|모든 옵션 이지만 **0x02**|  
|**인덱싱된 뷰 logbased**|모든 옵션|모든 옵션 이지만 **0x02**|  
|**logbased manualfilter 인덱싱된 뷰**|모든 옵션|모든 옵션 이지만 **0x02**|  
|**logbased manualview 인덱싱된 뷰**|모든 옵션|모든 옵션 이지만 **0x02**|  
|**인덱싱된 뷰 밑 manualboth**|모든 옵션|모든 옵션 이지만 **0x02**|  
|**proc exec**|**0x01**, **0x20**, **0x2000**를 **0x400000**, **0x800000**를 **0x2000000**, **0x8000000**, **0x10000000**, **0x20000000**하십시오 **0x40000000**, 및 **0x80000000**|**0x01**, **0x20**, **0x2000**를 **0x400000**, **0x800000**를 **0x2000000**, **0x8000000**, **0x10000000**, **0x20000000**하십시오 **0x40000000**, 및 **0x80000000**|  
|**serializable proc exec**|**0x01**, **0x20**, **0x2000**를 **0x400000**, **0x800000**를 **0x2000000**, **0x8000000**, **0x10000000**, **0x20000000**하십시오 **0x40000000**, 및 **0x80000000**|**0x01**, **0x20**, **0x2000**를 **0x400000**, **0x800000**를 **0x2000000**, **0x8000000**, **0x10000000**, **0x20000000**하십시오 **0x40000000**, 및 **0x80000000**|  
|**프로시저 스키마 전용**|**0x01**, **0x20**, **0x2000**를 **0x400000**, **0x800000**를 **0x2000000**, **0x8000000**, **0x10000000**, **0x20000000**하십시오 **0x40000000**, 및 **0x80000000**|**0x01**, **0x20**, **0x2000**를 **0x400000**, **0x800000**를 **0x2000000**, **0x8000000**, **0x10000000**, **0x20000000**하십시오 **0x40000000**, 및 **0x80000000**|  
|**뷰 스키마 전용**|**0x01**, **0x010**, **0x020**를 **0x040**를 **0x0100**를 **0x2000**, **0x40000**, **0x100000**, **0x200000**합니다 **0x400000**, **0x800000**,  **0x2000000**하십시오 **0x8000000**를 **0x40000000**, 및 **0x80000000**|**0x01**, **0x010**, **0x020**를 **0x040**를 **0x0100**를 **0x2000**, **0x40000**, **0x100000**, **0x200000**합니다 **0x400000**, **0x800000**,  **0x2000000**하십시오 **0x8000000**를 **0x40000000**, 및 **0x80000000**|  
|**func 스키마만**|**0x01**, **0x20**, **0x2000**를 **0x400000**, **0x800000**를 **0x2000000**, **0x8000000**, **0x10000000**, **0x20000000**하십시오 **0x40000000**, 및 **0x80000000**|**0x01**, **0x20**, **0x2000**를 **0x400000**, **0x800000**를 **0x2000000**, **0x8000000**, **0x10000000**, **0x20000000**하십시오 **0x40000000**, 및 **0x80000000**|  
|**인덱싱된 뷰 스키마 전용**|**0x01**, **0x010**, **0x020**를 **0x040**를 **0x0100**를 **0x2000**, **0x40000**, **0x100000**, **0x200000**합니다 **0x400000**, **0x800000**,  **0x2000000**하십시오 **0x8000000**를 **0x40000000**, 및 **0x80000000**|**0x01**, **0x010**, **0x020**를 **0x040**를 **0x0100**를 **0x2000**, **0x40000**, **0x100000**, **0x200000**합니다 **0x400000**, **0x800000**,  **0x2000000**하십시오 **0x8000000**를 **0x40000000**, 및 **0x80000000**|  
  
> [!NOTE]
>  지연 업데이트 게시 합니다 *schema_option* 의 값 **0x8000** 및 **0x80** 활성화 해야 합니다. 지원 되는 *schema_option* 값 이외의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 게시 됩니다. **0x01**, **0x02**를 **0x10**를 **0x40**를 **0x80**를 **0x1000**,  **0x4000** 하 고 **0X8000**합니다.  
  
## <a name="example"></a>예제  
 [!code-sql[HowTo#sp_AddTranArticle](../../relational-databases/replication/codesnippet/tsql/sp-addarticle-transact-sql_1.sql)]  
  
## <a name="permissions"></a>사용 권한  
 멤버는 **sysadmin** 고정된 서버 역할 또는 **db_owner** 고정된 데이터베이스 역할을 실행할 수 있습니다 **sp_addarticle**합니다.  
  
## <a name="see-also"></a>관련 항목  
 [Define an Article](../../relational-databases/replication/publish/define-an-article.md)   
 [sp_articlecolumn&#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-articlecolumn-transact-sql.md)   
 [sp_articlefilter&#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-articlefilter-transact-sql.md)   
 [sp_articleview &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-articleview-transact-sql.md)   
 [sp_changearticle&#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changearticle-transact-sql.md)   
 [sp_droparticle&#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-droparticle-transact-sql.md)   
 [sp_helparticle&#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helparticle-transact-sql.md)   
 [sp_helparticlecolumns &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helparticlecolumns-transact-sql.md)   
 [복제 저장 프로시저&#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)   
 [데이터 및 데이터베이스 개체 게시](../../relational-databases/replication/publish/publish-data-and-database-objects.md)  
  
  
