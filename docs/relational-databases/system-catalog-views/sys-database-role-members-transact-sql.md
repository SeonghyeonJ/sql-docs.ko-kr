---
title: sys.database_role_members (TRANSACT-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 01/31/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.database_role_members_TSQL
- sys.database_role_members
- database_role_members_TSQL
- database_role_members
dev_langs:
- TSQL
helpviewer_keywords:
- sys.database_role_members catalog view
ms.assetid: ed1b019d-ca48-4db3-85df-cf6d2db591cf
author: VanMSFT
ms.author: vanto
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 1bbbcf04cdb141cff25565360d82714eed1e98f1
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68079470"
---
# <a name="sysdatabaserolemembers-transact-sql"></a>sys.database_role_members(Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  각 데이터베이스 역할의 각 멤버에 대해 행을 반환합니다.  데이터베이스 사용자, 응용 프로그램 역할 및 다른 데이터베이스 역할에는 데이터베이스 역할의 멤버일 수 있습니다. 역할에 멤버를 추가 하려면 사용 합니다 [ALTER ROLE](../../t-sql/statements/alter-role-transact-sql.md) 문을 사용 하 여는 `ADD MEMBER` 옵션. 사용 하 여 조인 [sys.database_principals](../../relational-databases/system-catalog-views/sys-database-principals-transact-sql.md) 의 이름을 반환 하는 `principal_id` 값입니다.
  
|열 이름|데이터 형식|설명|  
|-----------------|---------------|-----------------|  
|**role_principal_id**|**int**|데이터베이스 역할의 보안 주체 ID입니다.|  
|**member_principal_id**|**int**|멤버의 데이터베이스 보안 주체 ID입니다.|  
  
## <a name="permissions"></a>사용 권한  
 모든 사용자는 자신의 역할 멤버 자격을 볼 수 있습니다. 멤버 자격을 보려면 다른 역할의 멤버 자격이 필요 합니다 `db_securityadmin` 고정된 데이터베이스 역할 또는 `VIEW DEFINITION` 데이터베이스에 있습니다.  
  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 자세한 내용은 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)을 참조하세요.  
  
## <a name="example"></a>예제  
 다음 쿼리는 데이터베이스 역할의 멤버를 반환합니다.  
  
```  
SELECT DP1.name AS DatabaseRoleName,   
   isnull (DP2.name, 'No members') AS DatabaseUserName   
 FROM sys.database_role_members AS DRM  
 RIGHT OUTER JOIN sys.database_principals AS DP1  
   ON DRM.role_principal_id = DP1.principal_id  
 LEFT OUTER JOIN sys.database_principals AS DP2  
   ON DRM.member_principal_id = DP2.principal_id  
WHERE DP1.type = 'R'
ORDER BY DP1.name;  
```  
  
## <a name="see-also"></a>관련 항목  
 [보안 카탈로그 뷰&#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)   
 [보안 주체&#40;데이터베이스 엔진&#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)   
 [카탈로그 뷰&#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)  
[ALTER ROLE (Transact-SQLL)](../../t-sql/statements/alter-role-transact-sql.md)      
[sys.server_role_members (TRANSACT-SQL)](../../relational-databases/system-catalog-views/sys-server-role-members-transact-sql.md)   
  


