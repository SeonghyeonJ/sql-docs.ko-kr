---
description: sp_enum_sqlagent_subsystems(Transact-SQL)
title: sp_enum_sqlagent_subsystems (Transact-sql) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_enum_sqlagent_subsystems
- sp_enum_sqlagent_subsystems_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_enum_sqlagent_subsystems
ms.assetid: 019a3c9d-bac3-495b-a70a-2c19f1d2e20e
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: af59c399d1d87c75bd78dd16cc57e98f835982f0
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88447211"
---
# <a name="sp_enum_sqlagent_subsystems-transact-sql"></a>sp_enum_sqlagent_subsystems(Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 하위 시스템을 나열합니다.  
  
 ![항목 링크 아이콘](../../database-engine/configure-windows/media/topic-link.gif "항목 링크 아이콘") [Transact-SQL 구문 표기 규칙](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>구문  
  
```  
  
sp_enum_sqlagent_subsystems  
```  
  
## <a name="arguments"></a>인수  
 None  
  
## <a name="return-code-values"></a>반환 코드 값  
 **0** (성공) 또는 **1** (실패)  
  
## <a name="result-sets"></a>결과 집합  
  
|열 이름|데이터 형식|Description|  
|-----------------|---------------|-----------------|  
|**하위**|**nvarchar(40)**|하위 시스템의 이름입니다.|  
|**description**|**nvarchar(512)**|하위 시스템에 대한 설명입니다.|  
|**subsystem_dll**|**nvarchar (510)**|하위 시스템을 포함하는 DLL 모듈입니다.|  
|**agent_exe**|**nvarchar (510)**|하위 시스템이 사용하는 실행 모듈입니다.|  
|**start_entry_point**|**nvarchar(30)**|작업 단계 실행 중 SQL Server 에이전트가 호출하는 프로시저입니다.|  
|**event_entry_point**|**nvarchar(30)**|작업 단계 실행 중 SQL Server 에이전트가 호출하는 프로시저입니다.|  
|**stop_entry_point**|**nvarchar(30)**|작업 단계 실행 중 SQL Server 에이전트가 호출하는 프로시저입니다.|  
|**max_worker_threads**|**int**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트가 이 하위 시스템에 대해 시작할 최대 스레드 수입니다.|  
|**subsystem_id**|**int**|하위 시스템에 대한 식별자입니다.|  
  
## <a name="remarks"></a>설명  
 이 프로시저는 인스턴스에 사용할 수 있는 하위 시스템을 나열합니다.  
  
## <a name="permissions"></a>사용 권한  
 기본적으로 **sysadmin** 고정 서버 역할의 멤버는 이 저장 프로시저를 실행할 수 있습니다. 다른 사용자는 **msdb** 데이터베이스의 **SQLAgentOperatorRole** 고정 데이터베이스 역할을 부여 받아야 합니다.  
  
 **SQLAgentOperatorRole**에 대 한 자세한 내용은 [고정 데이터베이스 역할 SQL Server 에이전트](../../ssms/agent/sql-server-agent-fixed-database-roles.md)을 참조 하세요.  
  
## <a name="see-also"></a>참고 항목  
 [SQL Server 에이전트 보안 구현](../../ssms/agent/implement-sql-server-agent-security.md)   
 [sp_add_jobstep&#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-jobstep-transact-sql.md)  
  
  
