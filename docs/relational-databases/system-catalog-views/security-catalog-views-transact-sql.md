---
title: 보안 카탈로그 뷰 (TRANSACT-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 02/27/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- cryptography [SQL Server], catalog views
- encryption [SQL Server], catalog views
- catalog views [SQL Server], security
- security catalog views [SQL Server]
ms.assetid: 4d5cf1bf-09a7-4ee0-9dbb-5c584750fc67
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: 9681edb9cc020294673f5697286714a17819747a
ms.sourcegitcommit: 561cee96844b82ade6cf543a228028ad5c310768
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66506568"
---
# <a name="security-catalog-views-transact-sql"></a>보안 카탈로그 뷰(Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  보안 정보는 성능과 효용을 위해 최적화된 카탈로그 뷰에서 제공됩니다. 가능하면 다음 카탈로그 뷰를 사용하여 카탈로그 메타데이터에 액세스합니다.  
  
## <a name="database-level-views"></a>데이터베이스 수준 뷰  
  
|||  
|-|-|  
|[sys.database_permissions](../../relational-databases/system-catalog-views/sys-database-permissions-transact-sql.md)|[sys.database_scoped_credentials](../../relational-databases/system-catalog-views/sys-database-scoped-credentials-transact-sql.md) |  
|[sys.database_principals](../../relational-databases/system-catalog-views/sys-database-principals-transact-sql.md)|[sys.master_key_passwords](../../relational-databases/system-catalog-views/sys-master-key-passwords-transact-sql.md) |  
|[sys.database_role_members](../../relational-databases/system-catalog-views/sys-database-role-members-transact-sql.md)|[sys.user_token](../../relational-databases/system-catalog-views/sys-user-token-transact-sql.md) |  
|[sys.sql_feature_restrictions](sys-sql-feature-restrictions.md)|
  
## <a name="server-level-views"></a>서버 수준 뷰  
  
|||  
|-|-|  
|[sys.credentials](../../relational-databases/system-catalog-views/sys-credentials-transact-sql.md)|[sys.server_principals](../../relational-databases/system-catalog-views/sys-server-principals-transact-sql.md)|  
|[sys.login_token](../../relational-databases/system-catalog-views/sys-login-token-transact-sql.md)|[sys.server_role_members](../../relational-databases/system-catalog-views/sys-server-role-members-transact-sql.md)|  
|[sys.securable_classes](../../relational-databases/system-catalog-views/sys-securable-classes-transact-sql.md)|[sys.sql_logins](../../relational-databases/system-catalog-views/sys-sql-logins-transact-sql.md)|  
|[sys.server_permissions](../../relational-databases/system-catalog-views/sys-server-permissions-transact-sql.md)|[sys.system_components_surface_area_configuration](../../relational-databases/system-catalog-views/sys-system-components-surface-area-configuration-transact-sql.md)|  
  
## <a name="encryption-views"></a>암호화 뷰  
  
|||  
|-|-|  
|[sys.asymmetric_keys](../../relational-databases/system-catalog-views/sys-asymmetric-keys-transact-sql.md)|[sys.cryptographic_providers](../../relational-databases/system-catalog-views/sys-cryptographic-providers-transact-sql.md)|  
|[sys.certificates](../../relational-databases/system-catalog-views/sys-certificates-transact-sql.md)|[sys.key_encryptions](../../relational-databases/system-catalog-views/sys-key-encryptions-transact-sql.md)|  
|[sys.column_encryption_key_values](../../relational-databases/system-catalog-views/sys-column-encryption-key-values-transact-sql.md)|[sys.openkeys](../../relational-databases/system-catalog-views/sys-openkeys-transact-sql.md)|  
|[sys.column_encryption_keys](../../relational-databases/system-catalog-views/sys-column-encryption-keys-transact-sql.md)|[sys.security_policies &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-security-policies-transact-sql.md)|  
|[sys.column_master_key_definitions](../../relational-databases/system-catalog-views/sys-column-master-keys-transact-sql.md)|[sys.security_predicates&#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-security-predicates-transact-sql.md)|  
|[sys.crypt_properties](../../relational-databases/system-catalog-views/sys-crypt-properties-transact-sql.md)|[sys.symmetric_keys](../../relational-databases/system-catalog-views/sys-symmetric-keys-transact-sql.md)|  
  
## <a name="sql-server-audit-views"></a>SQL Server 감사 뷰  
  
|||  
|-|-|  
|[sys.server_audits](../../relational-databases/system-catalog-views/sys-server-audits-transact-sql.md)|[sys.server_file_audits](../../relational-databases/system-catalog-views/sys-server-file-audits-transact-sql.md)|  
|[sys.server_audit_specifications](../../relational-databases/system-catalog-views/sys-server-audit-specifications-transact-sql.md)|[sys.server_audit_specifications_details](../../relational-databases/system-catalog-views/sys-server-audit-specification-details-transact-sql.md)|  
|[sys.database_ audit_specifications](../../relational-databases/system-catalog-views/sys-database-audit-specifications-transact-sql.md)|[sys.audit_database_specification_details](../../relational-databases/system-catalog-views/sys-database-audit-specification-details-transact-sql.md)|  
  
## <a name="permissions"></a>사용 권한  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 자세한 내용은 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)을 참조하세요.  
  
## <a name="see-also"></a>관련 항목  
 [SQL Server 데이터베이스 엔진 및 Azure SQL 데이터베이스에 대한 보안 센터](../../relational-databases/security/security-center-for-sql-server-database-engine-and-azure-sql-database.md)   
 [보안 관련 동적 관리 뷰 및 함수&#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/security-related-dynamic-management-views-and-functions-transact-sql.md)  
  
  
