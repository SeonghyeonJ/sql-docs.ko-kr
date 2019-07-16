---
title: sys.master_key_passwords (TRANSACT-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.master_key_passwords_TSQL
- master_key_passwords_TSQL
- sys.master_key_passwords
- master_key_passwords
dev_langs:
- TSQL
helpviewer_keywords:
- sys.master_key_passwords catalog view
ms.assetid: b8e18cff-a9e6-4386-98ce-1cd855506e03
author: stevestein
ms.author: sstein
ms.openlocfilehash: 87bb4a97db318330f253d068febb1309e4eda12a
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68102398"
---
# <a name="sysmasterkeypasswords-transact-sql"></a>sys.master_key_passwords(Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  사용 하 여 추가 된 각 데이터베이스 마스터 키 암호에 대 한 행을 반환 합니다 **sp_control_dbmasterkey_password** 저장 프로시저입니다. 마스터 키를 보호하는 데 사용된 암호는 자격 증명 저장소에 저장됩니다. 자격 증명 이름은: # # DBMKEY_ < database_family_guid > _ < random_password_guid > # #. 암호는 자격 증명 암호로 저장됩니다. 사용 하 여 추가 된 각 암호 **sp_control_dbmasterkey_password**에서 행이 **sys.credentials**합니다.  
  
 이 뷰의 각 행에 표시를 **credential_id** 하며 **family_guid** 는 마스터 키 자격 증명을 사용 하 여 연결 된 암호로 보호 되는 데이터베이스의 합니다. 조인이 **sys.credentials** 에 **credential_id** 와 같은 유용한 필드가 반환 됩니다는 **create_date** 및 자격 증명 이름입니다.  
  
|열 이름|데이터 형식|설명|  
|-----------------|---------------|-----------------|  
|**credential_id**|**int**|암호가 속한 자격 증명의 ID입니다. 이 ID는 서버 인스턴스 내에서 고유합니다.|  
|**family_guid**|**uniqueidentifier**|생성 시 원래 데이터베이스의 고유 ID입니다. 이 GUID는 데이터베이스를 복원하거나 연결한 경우뿐만 아니라 데이터베이스 이름을 변경한 경우에도 동일하게 유지됩니다.<br /><br /> 서비스 마스터 키 자동 암호 해독에 실패 하면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 사용 합니다 **family_guid** 데이터베이스 마스터 키를 보호 하는 데 사용한 암호를 포함할 수 있는 자격 증명을 식별 합니다.|  
  
## <a name="permissions"></a>사용 권한  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 자세한 내용은 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)을 참조하세요.  
  
## <a name="see-also"></a>관련 항목  
 [카탈로그 뷰&#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [sp_control_dbmasterkey_password&#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-control-dbmasterkey-password-transact-sql.md)   
 [보안 카탈로그 뷰&#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)   
 [CREATE SYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/create-symmetric-key-transact-sql.md)   
 [암호화 계층](../../relational-databases/security/encryption/encryption-hierarchy.md)  
  
  
