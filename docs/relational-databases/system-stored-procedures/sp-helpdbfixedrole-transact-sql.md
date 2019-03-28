---
title: sp_helpdbfixedrole (TRANSACT-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_helpdbfixedrole
- sp_helpdbfixedrole_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_helpdbfixedrole
ms.assetid: ad87e9a0-b901-4e37-9950-aa517d680fc3
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 1f3b4416ac9c297af84240e630730b0bad855780
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/27/2019
ms.locfileid: "58527965"
---
# <a name="sphelpdbfixedrole-transact-sql"></a>sp_helpdbfixedrole(Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  고정 데이터베이스 역할의 목록을 반환합니다.  
  
 ![항목 링크 아이콘](../../database-engine/configure-windows/media/topic-link.gif "항목 링크 아이콘") [Transact-SQL 구문 규칙](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>구문  
  
```  
  
sp_helpdbfixedrole [ [ @rolename = ] 'role' ]   
```  
  
## <a name="arguments"></a>인수  
`[ @rolename = ] 'role'` 고정된 데이터베이스 역할의 이름이입니다. *역할* 됩니다 **sysname**, 기본값은 NULL입니다. 하는 경우 *역할* 는 목록 및 모든 고정된 데이터베이스 역할의 설명 되 고, 그렇지 않으면 지정 하면 해당 역할에 대 한 정보만 반환 됩니다.  
  
## <a name="return-code-values"></a>반환 코드 값  
 0(성공) 또는 1(실패)  
  
## <a name="result-sets"></a>결과 집합  
  
|열 이름|데이터 형식|Description|  
|-----------------|---------------|-----------------|  
|**DbFixedRole**|**sysname**|고정 데이터베이스 역할의 이름입니다.|  
|**설명**|**nvarchar(70)**|설명은 **DbFixedRole 합니다.**|  
  
## <a name="remarks"></a>Remarks  
 다음 표에 표시된 것과 같이 고정 데이터베이스 역할은 데이터베이스 수준에서 정의되며 특정 데이터베이스 수준의 관리 작업을 수행할 수 있는 사용 권한이 있습니다. 고정 데이터베이스 역할은 추가하거나 제거할 수 없습니다. 고정 데이터베이스 역할에 부여된 사용 권한은 변경할 수 없습니다.  
  
|고정 데이터베이스 역할|Description|  
|-------------------------|-----------------|  
|**db_owner**|데이터베이스 소유자입니다.|  
|**db_accessadmin**|데이터베이스 액세스 관리자입니다.|  
|**db_securityadmin**|데이터베이스 보안 관리자입니다.|  
|**db_ddladmin**|데이터베이스 DDL 관리자입니다.|  
|**db_backupoperator**|데이터베이스 백업 운영자입니다.|  
|**db_datareader**|데이터베이스의 데이터 판독기입니다.|  
|**db_datawriter**|데이터베이스의 데이터 기록기입니다.|  
|**db_denydatareader**|데이터베이스의 거부 데이터 판독기입니다.|  
|**db_denydatawriter**|데이터베이스의 거부 데이터 기록기입니다.|  
  
 다음 표에서는 데이터베이스 역할을 수정하는 데 사용되는 저장 프로시저를 보여 줍니다.  
  
|저장 프로시저|작업|  
|----------------------|------------|  
|**sp_addrolemember**|고정 데이터베이스 역할에 데이터베이스 사용자를 추가합니다.|  
|**sp_helprole**|고정 데이터베이스 역할의 멤버 목록을 표시합니다.|  
|**sp_droprolemember**|고정 데이터베이스 역할에서 멤버를 제거합니다.|  
  
## <a name="permissions"></a>사용 권한  
 **public** 역할의 멤버 자격이 필요합니다.  
  
 반환되는 정보는 메타데이터에 대한 액세스 제한 사항에 따라 달라집니다. 보안 주체에 사용 권한이 없는 엔터티는 나타나지 않습니다. 자세한 내용은 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)을 참조하세요.  
  
## <a name="examples"></a>예  
 다음 예에서는 모든 고정 데이터베이스 역할의 목록을 보여 줍니다.  
  
```  
EXEC sp_helpdbfixedrole;  
GO  
```  
  
## <a name="see-also"></a>관련 항목  
 [Security Stored Procedures &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [sp_addrolemember&#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addrolemember-transact-sql.md)   
 [sp_dbfixedrolepermission &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dbfixedrolepermission-transact-sql.md)   
 [sp_droprolemember &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-droprolemember-transact-sql.md)   
 [sp_helprole &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helprole-transact-sql.md)   
 [sp_helprolemember &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helprolemember-transact-sql.md)   
 [시스템 저장 프로시저&#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
