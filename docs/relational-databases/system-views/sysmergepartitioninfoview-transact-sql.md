---
title: sysmergepartitioninfoview (Transact-sql) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sysmergepartitioninfoview
- sysmergepartitioninfoview_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sysmergepartitioninfoview view
ms.assetid: 714e2935-1bc7-4901-aea2-64b1bbda03d6
author: stevestein
ms.author: sstein
ms.openlocfilehash: 4b48506662283ab71516affa7665a6b0c0af9d3c
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/02/2020
ms.locfileid: "85881241"
---
# <a name="sysmergepartitioninfoview-transact-sql"></a>sysmergepartitioninfoview(Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  **Sysmergepartitioninfoview** 뷰는 테이블 아티클에 대 한 분할 정보를 제공 합니다. 이 뷰는 게시자의 게시 데이터베이스와 구독자의 구독 데이터베이스에 저장됩니다.  
  
|열 이름|데이터 형식|Description|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|아티클의 이름입니다.|  
|**type**|**tinyint**|아티클 유형을 나타내며 다음 중 하나일 수 있습니다.<br /><br /> **0x0a** = 테이블<br /><br /> **0x20** = 프로시저 스키마만 해당 합니다.<br /><br /> **0x40** = 뷰 스키마 전용 또는 인덱싱된 뷰 스키마만 해당 합니다.<br /><br /> **0x80** = 함수 스키마만 해당 합니다.|  
|**objid**|**int**|게시된 개체의 식별자입니다.|  
|**sync_objid**|**int**|동기화된 데이터 집합을 표시하는 뷰의 개체 ID입니다.|  
|**view_type**|**tinyint**|뷰의 유형:<br /><br /> **0** = 뷰가 아닙니다. 모든 기본 개체를 사용 합니다.<br /><br /> **1** = 영구 뷰입니다.<br /><br /> **2** = 임시 뷰|  
|**artid**|**uniqueidentifier**|지정된 아티클의 고유한 ID입니다.|  
|**한**|**nvarchar(255)**|아티클에 대한 간단한 설명입니다.|  
|**pre_creation_command**|**tinyint**|아티클이 구독 데이터베이스에서 생성될 때 수행할 기본 동작입니다.<br /><br /> **0** = None-구독자에 테이블이 이미 있는 경우 아무 동작도 수행 되지 않습니다.<br /><br /> **1** = Drop-테이블을 다시 만들기 전에 삭제 합니다.<br /><br /> **2** = delete-하위 집합 필터의 where 절을 기반으로 삭제를 실행 합니다.<br /><br /> **3** = Truncate-2와 동일 하지만 행 대신 페이지를 삭제 합니다. 단, WHERE 절은 사용하지 않습니다.|  
|**pubid**|**uniqueidentifier**|현재 아티클이 속한 게시의 ID입니다.|  
|**애칭**|**int**|아티클 ID에 대한 애칭 매핑입니다.|  
|**column_tracking**|**int**|아티클에 대한 열 추적이 구현되는지 여부를 나타냅니다.|  
|**status**|**tinyint**|아티클의 상태를 나타내며 다음 중 하나일 수 있습니다.<br /><br /> **1** = 동기화 됨-테이블을 게시 하는 초기 처리 스크립트가 다음에 스냅숏 에이전트 실행 될 때 실행 됩니다.<br /><br /> **2** = 활성-테이블을 게시 하는 초기 처리 스크립트가 실행 되었습니다.|  
|**conflict_table**|**sysname**|현재 아티클에 대한 충돌 기록이 들어 있는 로컬 테이블의 이름입니다. 이 테이블은 정보 제공의 목적으로만 제공되며 사용자 지정 충돌 해결 루틴에 의해서나 직접 관리자에 의해서 수정되거나 삭제될 수 있습니다.|  
|**creation_script**|**nvarchar(255)**|해당 아티클에 대한 생성 스크립트입니다.|  
|**conflict_script**|**nvarchar(255)**|해당 아티클에 대한 충돌 스크립트입니다.|  
|**article_resolver**|**nvarchar(255)**|해당 아티클에 대한 충돌 해결 프로그램입니다.|  
|**ins_conflict_proc**|**sysname**|충돌 정보를 충돌 테이블에 쓰는 데 사용하는 프로시저입니다.|  
|**insert_proc**|**sysname**|동기화하는 동안 행을 삽입하는 데 사용하는 프로시저입니다.|  
|**update_proc**|**sysname**|동기화하는 동안 행을 업데이트하는 데 사용하는 프로시저입니다.|  
|**select_proc**|**sysname**|병합 에이전트가 잠금을 수행하고 아티클에 대한 열 및 행을 찾기 위해 사용하는 자동 생성 저장 프로시저의 이름입니다.|  
|**metadata_select_proc**|**sysname**|병합 복제 시스템 테이블의 메타데이터 액세스에 사용되는 자동 생성 저장 프로시저의 이름입니다.|  
|**delete_proc**|**sysname**|동기화하는 동안 행을 삭제하는 데 사용하는 프로시저입니다.|  
|**schema_option**|**binary (8)**|지정한 아티클에 대한 스키마 생성 옵션의 비트맵입니다. 지원 되는 *schema_option* 값에 대 한 자세한 내용은 [sp_addmergearticle &#40;transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md)를 참조 하세요.|  
|**destination_object**|**sysname**|구독자에서 생성되는 테이블의 이름입니다.|  
|**destination_owner**|**sysname**|대상 개체의 소유자 이름입니다.|  
|**resolver_clsid**|**nvarchar(50)**|사용자 지정 충돌 해결 프로그램의 ID입니다. 비즈니스 논리 처리기의 경우 이 값은 NULL입니다.|  
|**subset_filterclause**|**nvarchar(1000)**|해당 아티클에 대한 필터 절입니다.|  
|**missing_col_count**|**int**|아티클에 없는 게시된 열의 수입니다.|  
|**missing_cols**|**varbinary(128)**|아티클에 없는 열을 설명하는 비트맵입니다.|  
|**excluded_cols**|**varbinary(128)**|아티클에서 제외된 열의 비트맵입니다.|  
|**excluded_col_count**|**int**|아티클에서 제외된 열의 수입니다.|  
|**세로**|**varbinary(128)**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**deleted_cols**|**varbinary(128)**|아티클에서 삭제된 열을 설명하는 비트맵입니다.|  
|**resolver_info**|**nvarchar(255)**|사용자 지정 충돌 해결 프로그램에 필요한 추가 정보의 스토리지입니다.|  
|**view_sel_proc**|**nvarchar (가 나)**|병합 에이전트가 동적으로 필터링된 게시에서 아티클의 초기 채우기를 하기 위해, 그리고 필터링된 게시에서 변경된 행을 열거하기 위해 사용하는 저장 프로시저의 이름입니다.|  
|**gen_cur**|**bigint**|아티클의 기본 테이블에 대한 로컬 변경 내용의 번호를 생성합니다.|  
|**vertical_partition**|**int**|테이블 아티클에 열 필터링 사용 여부를 지정합니다. **0** 은 세로 필터링이 없으며 모든 열을 게시 함을 나타냅니다.|  
|**identity_support**|**int**|자동 ID 범위 처리가 설정되었는지 여부를 지정합니다. **1** 은 id 범위 처리를 사용 하도록 설정 하 고 **0** 은 id 범위를 지원 하지 않음을 의미 합니다.|  
|**before_image_objid**|**int**|추적 테이블의 개체 ID입니다. 게시에 대한 파티션 변경 최적화가 활성화된 경우 추적 테이블은 특정 키 열 값을 포함합니다.|  
|**before_view_objid**|**int**|뷰 테이블의 개체 ID입니다. 뷰는 행이 삭제 또는 업데이트되기 전에 특정 구독자에 속했는지를 추적하는 테이블에 있습니다. 게시에 대해 파티션 변경 최적화가 활성화된 경우에만 적용됩니다.|  
|**verify_resolver_signature**|**int**|해결 프로그램을 병합 복제에 사용하기 전에 디지털 서명을 확인할지 여부를 지정합니다.<br /><br /> **0** = 서명이 확인 되지 않습니다.<br /><br /> **1** = 서명을 확인 하 여 신뢰할 수 있는 원본에서 가져온 것인지 확인 합니다.|  
|**allow_interactive_resolver**|**bit**|아티클에 대화형 해결 프로그램을 사용할지 여부를 지정합니다. **1** 은 대화형 해결 프로그램을 문서에서 사용할 수 있음을 의미 합니다.|  
|**fast_multicol_updateproc**|**bit**|병합 에이전트를 사용하도록 설정하여 한 UPDATE 문에서 같은 행의 여러 열에 변경 사항을 적용했는지 여부를 지정합니다.<br /><br /> **0** = 변경 된 각 열에 대해 별도의 업데이트를 발급 합니다.<br /><br /> **1** = 한 문의 여러 열에 대 한 업데이트를 발생 시키는 UPDATE 문에서 실행 됩니다.|  
|**check_permissions**|**int**|병합 에이전트가 변경 내용을 게시자에 적용할 때 확인할 테이블 수준 사용 권한의 비트맵입니다. *check_permissions* 는 다음 값 중 하나를 사용할 수 있습니다.<br /><br /> **0x00** = 사용 권한을 확인 하지 않습니다.<br /><br /> **0x10** = 구독자에서 삽입을 업로드 하기 전에 게시자에서 사용 권한을 확인 합니다.<br /><br /> **0x20** = 구독자에서 수행 된 업데이트를 업로드 하기 전에 게시자에서 사용 권한을 확인 합니다.<br /><br /> **0x40** = 구독자에서 수행 된 삭제 작업을 업로드 하기 전에 게시자에서 사용 권한을 확인 합니다.|  
|**maxversion_at_cleanup**|**int**|다음 번 병합 에이전트가 실행될 때 정리되는 최대 생성입니다.|  
|**processing_order**|**int**|병합 게시에서 아티클의 처리 순서를 나타냅니다. 여기서 값 **0** 은 아티클이 정렬 되지 않은 것을 나타내고 아티클은 가장 낮은 값에서 가장 높은 값의 순서로 처리 됩니다. 두 아티클의 값이 같으면 동시에 처리됩니다. 자세한 내용은 [병합 복제 속성 지정](../../relational-databases/replication/merge/specify-merge-replication-properties.md)을 참조하세요.|  
|**upload_options**|**tinyint**|구독자에서 변경이 수행되거나 업로드될 수 있는지 여부를 정의하며 다음 값 중 하나일 수 있습니다.<br /><br /> **0** = 구독자에서 수행 되는 업데이트에 대 한 제한은 없습니다. 모든 변경 내용이 게시자로 업로드 됩니다.<br /><br /> **1** = 구독자에서 변경이 허용 되지만 게시자로 업로드 되지 않습니다.<br /><br /> **2** = 구독자에서 변경이 허용 되지 않습니다.|  
|**published_in_tran_pub**|**bit**|병합 게시의 아티클이 트랜잭션 게시에도 게시됨을 나타냅니다.<br /><br /> **0** = 아티클이 트랜잭션 아티클에서 게시 되지 않습니다.<br /><br /> **1** = 아티클이 트랜잭션 문서에도 게시 됩니다.|  
|**lightweight**|**bit**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**procname_postfix**|**nchar(32)**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**well_partitioned_lightweight**|**bit**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**before_upd_view_objid**|**int**|업데이트 전 테이블의 뷰 ID입니다.|  
|**delete_tracking**|**bit**|삭제 내용을 복제할지 여부를 나타냅니다.<br /><br /> **0** = 삭제가 복제 되지 않습니다.<br /><br /> **1** = 병합 복제에 대 한 기본 동작인 삭제가 복제 됩니다.<br /><br /> *Delete_tracking* 값이 **0**이면 구독자에서 삭제 된 행을 게시자에서 수동으로 제거 하 고 게시자에서 삭제 된 행을 구독자에서 수동으로 제거 해야 합니다.<br /><br /> 참고: 값 **0** 은 일치 하지 않습니다.|  
|**compensate_for_errors**|**bit**|동기화 중에 오류가 발생할 경우 보정 동작이 수행될지 여부를 나타냅니다.<br /><br /> **0** = 보정 동작을 사용할 수 없습니다.<br /><br /> **1** = 구독자 또는 게시자에서 적용할 수 없는 변경 내용은 항상 보정 동작을 수행 하 여 병합 복제의 기본 동작을 실행 취소 합니다.<br /><br /> 참고: 값 **0** 은 일치 하지 않습니다.|  
|**pub_range**|**bigint**|게시자 ID의 범위 크기입니다.|  
|**range**|**bigint**|조정 시 구독자에게 할당되는 연속 ID 값의 크기입니다.|  
|**threshold**|**int**|ID 범위 임계값 비율입니다.|  
|**stream_blob_columns**|**bit**|BLOB(Binary Large Object) 열에 대한 스트리밍 최적화 사용 여부를 나타냅니다. **1** 은 최적화가 시도 됨을 의미 합니다.|  
|**preserve_rowguidcol**|**bit**|복제에 기존 rowguid 열이 사용될지 여부를 나타냅니다. 값 **1** 은 기존 ROWGUIDCOL 열이 사용 됨을 의미 합니다. **0** 은 복제가 ROWGUIDCOL 열을 추가 했음을 의미 합니다.|  
|**partition_view_id**|**int**|구독자 파티션을 정의하는 뷰를 식별합니다.|  
|**repl_view_id**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**partition_deleted_view_rule**|**sysname**|이전의 열 값을 기준으로 삭제 또는 업데이트된 각 행의 파티션 ID를 검색하기 위해 병합 복제 트리거 내에서 사용하는 문입니다.|  
|**partition_inserted_view_rule**|**Sysname 이며**|새로운 열 값을 기준으로 삽입 또는 업데이트된 각 행의 파티션 ID를 검색하기 위해 병합 복제 트리거 내에서 사용하는 문입니다.|  
|**membership_eval_proc_name**|**sysname**|[Transact-sql&#41;&#40;MSmerge_contents ](../../relational-databases/system-tables/msmerge-contents-transact-sql.md)의 행에 대 한 현재 파티션 id를 평가 하는 프로시저의 이름입니다.|  
|**column_list**|**sysname**|아티클에 게시된 열을 쉼표로 구분한 목록입니다.|  
|**column_list_blob**|**sysname**|BLOB(Binary Large Object) 열을 포함하여 아티클에 게시된 열을 쉼표로 구분한 목록입니다.|  
|**expand_proc**|**sysname**|새로 삽입된 부모 행의 모든 자식 행, 파티션이 변경된 부모 행 및 삭제된 부모 행에 대한 파티션 ID를 다시 평가하는 프로시저의 이름입니다.|  
|**logical_record_parent_nickname**|**int**|논리적 레코드에서 지정된 아티클에 대한 최상위 부모의 애칭입니다.|  
|**logical_record_view**|**int**|각 자식 rowguid에 해당하는 최상위 부모 아티클의 rowguid를 출력하는 뷰입니다.|  
|**logical_record_deleted_view_rule**|**sysname**|Update 및 delete 트리거의 "deleted" 테이블에 자식 행을 표시 한다는 점을 제외 하 고 **logical_record_view**와 유사 합니다.|  
|**logical_record_level_conflict_detection**|**bit**|충돌을 논리적 레코드 수준에서 감지할지 또는 행이나 열 수준에서 감지할지 여부를 나타냅니다.<br /><br /> **0** = 행 또는 열 수준 충돌 검색이 사용 됩니다.<br /><br /> **1** = 논리적 레코드 충돌 검색이 사용 됩니다. 게시자에서 행을 변경 하 고 별도의 행을 변경 하는 경우 구독자의 동일한 논리적 레코드가 충돌로 처리 됩니다.<br /><br /> 이 값이 1인 경우 논리적 레코드 수준의 충돌 해결만을 사용할 수 있습니다.|  
|**logical_record_level_conflict_resolution**|**bit**|충돌을 논리적 레코드 수준에서 해결할지 또는 행이나 열 수준에서 감지할지 여부를 나타냅니다.<br /><br /> **0** = 행 또는 열 수준 확인이 사용 됩니다.<br /><br /> **1** = 충돌이 발생 한 경우 적용 되는 전체 논리적 레코드가 손실 된 쪽에서 전체 논리적 레코드를 덮어씁니다.<br /><br /> 값 1은 논리적 레코드 수준의 감지 및 행 또는 열 수준의 감지 양쪽에 모두 사용할 수 있습니다.|  
|**partition_options**|**tinyint**|아티클의 데이터 분할 방식을 정의합니다. 데이터를 분할하면 모든 행이 하나의 파티션 또는 하나의 구독에만 속한 경우 성능을 최적화할 수 있습니다. *Partition_options* 는 다음 값 중 하나일 수 있습니다.<br /><br /> **0** = 아티클에 대 한 필터링이 정적 이거나 각 파티션에 대 한 고유한 데이터 하위 집합을 생성 하지 않습니다. 즉, "겹치는" 파티션입니다.<br /><br /> **1** = 파티션이 중복 되며 구독자에서 DML 업데이트를 수행 하면 행이 속한 파티션이 변경 되지 않습니다.<br /><br /> **2** = 아티클을 필터링 하면 겹치지 않는 파티션이 생성 되지만 여러 구독자가 동일한 파티션을 받을 수 있습니다.<br /><br /> **3** = 아티클에 대 한 필터링은 각 구독에 고유한 겹치지 않는 파티션을 생성 합니다.|  
|**name**|**sysname**|파티션의 이름입니다.|  
  
## <a name="see-also"></a>참고 항목  
 [매개 변수가 있는 필터를 사용 하 여 병합 게시에 대 한 파티션 관리](../../relational-databases/replication/publish/manage-partitions-for-a-merge-publication-with-parameterized-filters.md)   
 [Transact-sql&#41;&#40;복제 테이블](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Transact-sql&#41;&#40;복제 뷰](../../relational-databases/system-views/replication-views-transact-sql.md)   
 [Transact-sql&#41;sp_addmergepartition &#40;](../../relational-databases/system-stored-procedures/sp-addmergepartition-transact-sql.md)   
 [Transact-sql&#41;sp_helpmergepartition &#40;](../../relational-databases/system-stored-procedures/sp-helpmergepartition-transact-sql.md)  
  
  
