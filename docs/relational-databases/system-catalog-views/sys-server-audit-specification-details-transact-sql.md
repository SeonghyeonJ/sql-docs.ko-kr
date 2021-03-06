---
description: sys.server_audit_specification_details(Transact-SQL)
title: sys. server_audit_specification_details (Transact-sql) | Microsoft Docs
ms.custom: ''
ms.date: 04/05/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- server_audit_specification_details
- sys.server_audit_specification_details_TSQL
- server_audit_specification_details_TSQL
- sys.server_audit_specification_details
dev_langs:
- TSQL
helpviewer_keywords:
- sys.server_audit_specification_details catalog view
ms.assetid: 792724dc-402e-4b17-9f2c-029d910bf88e
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 20f119f3db641ebffd61ba4465abeea3c99515e5
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89550451"
---
# <a name="sysserver_audit_specification_details-transact-sql"></a>sys.server_audit_specification_details(Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  서버 인스턴스에 있는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Audit의 서버 감사 사양 세부 정보(동작)를 포함합니다. 자세한 내용은 [SQL Server Audit&#40;데이터베이스 엔진&#41;](../../relational-databases/security/auditing/sql-server-audit-database-engine.md)을 참조하세요. 모든 audit_action_id 및 해당 이름 목록을 보려면 [transact-sql&#41;&#40;dm_audit_actions ](../../relational-databases/system-dynamic-management-views/sys-dm-audit-actions-transact-sql.md)를 쿼리 합니다.  
  
|열 이름|데이터 형식|Description|  
|-----------------|---------------|-----------------|  
|server_specification_id|**int**|감사 서버 사양의 ID입니다.|  
|audit_action_id|**int**|감사 동작의 ID입니다.|  
|audit_action_name|**sysname**|그룹 또는 감사 동작의 이름입니다.|  
|class|**tinyint**|예약됨|  
|class_desc|**nvarchar(60)**|예약됨|  
|major_id|**int**|예약됨|  
|minor_id|**int**|예약됨|  
|audited_principal_id|**int**|예약됨|  
|audited_result|**nvarchar(60)**|감사된 결과:<br /><br /> - SUCCESS AND FAILURE<br /><br /> - SUCCESS<br /><br /> - FAILURE|  
|is_group|**bit**|감사된 개체의 그룹 여부:<br /><br /> 0 - 그룹 아님<br /><br /> 1 - 그룹임|  
  
## <a name="permissions"></a>사용 권한  
 **ALTER ANY SERVER AUDIT** 또는 **VIEW any DEFINITION** 권한이 있는 보안 주체가이 카탈로그 뷰에 액세스할 수 있습니다. 또한 보안 주체는 **VIEW ANY DEFINITION** 권한을 거부 해서는 안 됩니다.  
  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 자세한 내용은 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)을 참조하세요.  
  
## <a name="see-also"></a>참고 항목  
 [보안 카탈로그 뷰&#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)   
 [CREATE SERVER AUDIT &#40;Transact-SQL&#41;](../../t-sql/statements/create-server-audit-transact-sql.md)   
 [ALTER SERVER AUDIT  &#40;Transact-SQL&#41;](../../t-sql/statements/alter-server-audit-transact-sql.md)   
 [DROP SERVER AUDIT  &#40;Transact-SQL&#41;](../../t-sql/statements/drop-server-audit-transact-sql.md)   
 [CREATE SERVER AUDIT SPECIFICATION &#40;Transact-SQL&#41;](../../t-sql/statements/create-server-audit-specification-transact-sql.md)   
 [ALTER SERVER AUDIT SPECIFICATION &#40;Transact-SQL&#41;](../../t-sql/statements/alter-server-audit-specification-transact-sql.md)   
 [DROP SERVER AUDIT SPECIFICATION &#40;Transact-SQL&#41;](../../t-sql/statements/drop-server-audit-specification-transact-sql.md)   
 [CREATE DATABASE AUDIT SPECIFICATION &#40;Transact-SQL&#41;](../../t-sql/statements/create-database-audit-specification-transact-sql.md)   
 [ALTER DATABASE AUDIT SPECIFICATION &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-audit-specification-transact-sql.md)   
 [DROP DATABASE AUDIT SPECIFICATION &#40;Transact-SQL&#41;](../../t-sql/statements/drop-database-audit-specification-transact-sql.md)   
 [ALTER AUTHORIZATION &#40;Transact-SQL&#41;](../../t-sql/statements/alter-authorization-transact-sql.md)   
 [sys.fn_get_audit_file &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-get-audit-file-transact-sql.md)   
 [sys.server_audits &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-server-audits-transact-sql.md)   
 [sys.server_file_audits &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-server-file-audits-transact-sql.md)   
 [sys.server_audit_specifications &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-server-audit-specifications-transact-sql.md)   
 [sys.database_audit_specifications &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-audit-specifications-transact-sql.md)   
 [sys.database_audit_specification_details &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-audit-specification-details-transact-sql.md)   
 [sys.dm_server_audit_status &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-server-audit-status-transact-sql.md)   
 [sys.dm_audit_actions &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-audit-actions-transact-sql.md)   
 [sys.dm_audit_class_type_map &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-audit-class-type-map-transact-sql.md)   
 [서버 감사 및 서버 감사 사양 만들기](../../relational-databases/security/auditing/create-a-server-audit-and-server-audit-specification.md)  
  
  
