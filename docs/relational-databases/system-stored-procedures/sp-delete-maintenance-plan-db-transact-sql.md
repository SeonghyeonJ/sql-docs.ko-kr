---
title: sp_delete_maintenance_plan_db (TRANSACT-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_delete_maintenance_plan_db_TSQL
- sp_delete_maintenance_plan_db
dev_langs:
- TSQL
helpviewer_keywords:
- sp_delete_maintenance_plan_db
- maintenance plans [SQL Server], deleting
- removing maintenance plan
- disassociating maintenance plan
ms.assetid: d1e8afb5-12ee-492b-a770-ba708ed7c8a4
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 8a260e68064b0a9218da07a8a65cf6b584382b4b
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/27/2019
ms.locfileid: "58528645"
---
# <a name="spdeletemaintenanceplandb-transact-sql"></a>sp_delete_maintenance_plan_db(Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  지정된 데이터베이스에서 지정된 유지 관리 계획을 분리합니다.  
  
> [!NOTE]  
>  이 저장 프로시저는 데이터베이스 유지 관리 계획에 사용됩니다. 이 기능은 이러한 저장 프로시저를 사용하지 않는 유지 관리 계획으로 바뀌었습니다. 이 프로시저를 사용하여 이전 버전의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 업그레이드된 설치에 대한 데이터베이스 유지 관리 계획을 유지할 수 있습니다.  
  
 [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]  
  
 ![항목 링크 아이콘](../../database-engine/configure-windows/media/topic-link.gif "항목 링크 아이콘") [Transact-SQL 구문 규칙](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>구문  
  
```  
  
sp_delete_maintenance_plan_db [ @plan_id = ] 'plan_id' ,   
     [ @db_name = ] 'database_name'   
```  
  
## <a name="arguments"></a>인수  
`[ @plan_id = ] 'plan\_id'` 유지 관리 계획 ID를 지정합니다. *plan_id* 됩니다 **uniqueidentifier**합니다.  
  
`[ @db_name = ] 'database\_name'` 유지 관리 계획에서 삭제할 데이터베이스 이름을 지정 합니다. *database_name*은 **sysname**입니다.  
  
## <a name="return-code-values"></a>반환 코드 값  
 0(성공) 또는 1(실패)  
  
## <a name="remarks"></a>Remarks  
 **sp_delete_maintenance_plan_db** 에서 실행 해야 합니다 **msdb** 데이터베이스입니다.  
  
 합니다 **sp_delete_maintenance_plan_db** ; 유지 관리 계획 및 지정된 된 데이터베이스 간의 연결을 제거 하는 저장된 프로시저를 삭제 하거나 데이터베이스를 삭제 하지 않습니다.  
  
 때 **sp_delete_maintenance_plan_db** 유지 관리 계획에서 마지막 데이터베이스를 제거, 저장된 프로시저도 유지 관리 계획을 삭제 합니다.  
  
## <a name="permissions"></a>사용 권한  
 멤버는 **sysadmin** 고정된 서버 역할을 실행할 수 있습니다 **sp_delete_maintenance_plan_db**합니다.  
  
## <a name="examples"></a>예  
 유지 관리 계획을 삭제 합니다 **AdventureWorks2012** 데이터베이스에 사용 하 여 이전에 추가한 **sp_add_maintenance_plan_db**합니다.  
  
```  
EXECUTE   sp_delete_maintenance_plan_db N'FAD6F2AB-3571-11D3-9D4A-00C04FB925FC', N'AdventureWorks2012';  
```  
  
## <a name="see-also"></a>관련 항목  
 [유지 관리 계획](../../relational-databases/maintenance-plans/maintenance-plans.md)   
 [데이터베이스 유지 관리 계획 저장 프로시저 &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/database-maintenance-plan-stored-procedures-transact-sql.md)  
  
  
