---
title: sys.dm_database_encryption_keys (TRANSACT-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/27/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_database_encryption_keys
- sys.dm_database_encryption_keys_TSQL
- dm_database_encryption_keys
- dm_database_encryption_keys_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_database_encryption_keys dynamic management view
ms.assetid: 56fee8f3-06eb-4fff-969e-abeaa0c4b8e4
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: c041ea8aff23a3b601695236681fda3081def1fa
ms.sourcegitcommit: 2db83830514d23691b914466a314dfeb49094b3c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/27/2019
ms.locfileid: "58494081"
---
# <a name="sysdmdatabaseencryptionkeys-transact-sql"></a>sys.dm_database_encryption_keys(Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  연결된 데이터베이스 암호화 키 및 데이터베이스의 암호화 상태에 대한 정보를 반환합니다. 데이터 암호화에 대한 자세한 내용은 [Transparent Data Encryption &#40;TDE&#41;](../../relational-databases/security/encryption/transparent-data-encryption.md)를 참조하십시오.  
 
|열 이름|데이터 형식|Description|  
|-----------------|---------------|-----------------|  
|database_id|**int**|데이터베이스의 ID입니다.|  
|encryption_state|**int**|데이터베이스가 암호화되었는지 여부를 나타냅니다.<br /><br /> 0 = 데이터베이스 암호화 키가 없고 암호화되지 않음<br /><br /> 1 = 암호화되지 않음<br /><br /> 2 = 암호화 진행 중<br /><br /> 3 = 암호화됨<br /><br /> 4 = 키 변경 진행 중<br /><br /> 5 = 해독 진행 중<br /><br /> 6 = 보호 변경 진행 중. 데이터베이스 암호화 키를 암호화하는 인증서 또는 비대칭 키를 변경하고 있습니다.|  
|create_date|**datetime**|날짜 표시 하는 암호화 키가 만들어진 (UTC)에 있습니다.|  
|regenerate_date|**datetime**|날짜 (UTC)에 암호화 키를 다시 생성 합니다.|  
|modify_date|**datetime**|날짜 (UTC)에 암호화 키를 수정 했습니다.|  
|set_date|**datetime**|날짜 (UTC)에 암호화 키를 데이터베이스에 적용 되었습니다.|  
|opened_date|**datetime**|(UTC)에 데이터베이스 키를 마지막으로 열었던 면 표시 됩니다.|  
|key_algorithm|**nvarchar(32)**|키에 사용된 알고리즘을 표시합니다.|  
|key_length|**int**|키의 길이를 표시합니다.|  
|encryptor_thumbprint|**varbinary(20)**|암호기의 손도장을 표시합니다.|  
|encryptor_type|**nvarchar(32)**|**적용 대상**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] ~ [현재 버전](https://go.microsoft.com/fwlink/p/?LinkId=299658)).<br /><br /> 암호기를 설명합니다.|  
|percent_complete|**real**|데이터베이스 암호화 상태 변경의 완료 비율입니다. 상태 변경이 없으면 0이 됩니다.|
|encryption_state_desc|**nvarchar(32)**|**적용 대상**: [!INCLUDE[sql-server-2019](../../includes/sssqlv15-md.md)] 이상.<br><br> 데이터베이스의 암호화 되지 않은 암호화 여부를 나타내는 문자열입니다.<br><br>없음<br><br>암호화 되지 않은<br><br>암호화<br><br>DECRYPTION_IN_PROGRESS<br><br>ENCRYPTION_IN_PROGRESS<br><br>KEY_CHANGE_IN_PROGRESS<br><br>PROTECTION_CHANGE_IN_PROGRESS|
|encryption_scan_state|**int**|**적용 대상**: [!INCLUDE[sql-server-2019](../../includes/sssqlv15-md.md)] 이상.<br><br>암호화 검색의 현재 상태를 나타냅니다. <br><br>0 = 아니요 검사가 시작 되었습니다, TDE를 사용 하지 않습니다<br><br>1 = 검색 진행에서 중입니다.<br><br>2 = 검색 진행 중 일시 중단 된 하지만 사용자를 다시 시작할 수 있습니다.<br><br>3 = 검색을 성공적으로 완료 한 TDE를 사용 하 고 암호화가 완료 합니다.<br><br>4 = 이유로 검색이 중단 되었습니다, 수동 개입이 필요 합니다. 자세한 내용은 Microsoft 지원에 문의 합니다.|
|encryption_scan_state_desc|**nvarchar(32)**|**적용 대상**: [!INCLUDE[sql-server-2019](../../includes/sssqlv15-md.md)] 이상.<br><br>암호화 검색의 현재 상태를 나타내는 문자열입니다.<br><br> 없음<br><br>RUNNING<br><br>SUSPENDED<br><br>완료<br><br>ABORTED|
|encryption_scan_modify_date|**datetime**|**적용 대상**: [!INCLUDE[sql-server-2019](../../includes/sssqlv15-md.md)] 이상.<br><br> 날짜 (UTC) 암호화 검사 상태를 마지막으로 수정 된 합니다.|
  
## <a name="permissions"></a>사용 권한

온 [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], 필요한 `VIEW SERVER STATE` 권한.   
온 [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)], 필요를 `VIEW DATABASE STATE` 데이터베이스의 권한.   

## <a name="see-also"></a>관련 항목  

 [보안 관련 동적 관리 뷰 및 함수&#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/security-related-dynamic-management-views-and-functions-transact-sql.md)   
 [투명한 데이터 암호화&#40;TDE&#41;](../../relational-databases/security/encryption/transparent-data-encryption.md)   
 [SQL Server 암호화](../../relational-databases/security/encryption/sql-server-encryption.md)   
 [SQL Server 및 데이터베이스 암호화 키&#40;데이터베이스 엔진&#41;](../../relational-databases/security/encryption/sql-server-and-database-encryption-keys-database-engine.md)   
 [암호화 계층](../../relational-databases/security/encryption/encryption-hierarchy.md)   
 [ALTER DATABASE SET 옵션&#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-set-options.md)   
 [CREATE DATABASE ENCRYPTION KEY &#40;Transact-SQL&#41;](../../t-sql/statements/create-database-encryption-key-transact-sql.md)   
 [ALTER DATABASE ENCRYPTION KEY &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-encryption-key-transact-sql.md)   
 [DROP DATABASE ENCRYPTION KEY&#40;Transact-SQL&#41;](../../t-sql/statements/drop-database-encryption-key-transact-sql.md)  
  
  
