---
title: dbo.sysproxysubsystem (TRANSACT-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dbo.sysproxysubsystem_TSQL
- dbo.sysproxysubsystem
- sysproxysubsystem_TSQL
- sysproxysubsystem
dev_langs:
- TSQL
helpviewer_keywords:
- sysproxysubsystem system table
ms.assetid: 6d7713f5-1253-4a19-b1fb-635c377c95c1
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: e6fa0ff8c90f4532d87191f827e0815de8636033
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62470675"
---
# <a name="dbosysproxysubsystem-transact-sql"></a>dbo.sysproxysubsystem(Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  각 프록시 계정에서 사용하는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 하위 시스템을 기록합니다. 이 테이블에 저장 되는 **msdb** 데이터베이스입니다.  
  
|열 이름|데이터 형식|Description|  
|-----------------|---------------|-----------------|  
|**subsystem_id**|**int**|하위 시스템의 ID입니다. 이 값에 해당 합니다 **subsystem_id** 열에는 **syssubsystems** 테이블입니다.|  
|**proxy_id**|**int**|프록시 계정의 ID입니다. 이 값에 해당 합니다 **proxy_id** 열에는 **sysproxies** 테이블입니다.|  
  
## <a name="remarks"></a>Remarks  
 멤버는 **sysadmin** 고정된 서버 역할이이 테이블에 액세스할 수 있습니다.  
  
## <a name="see-also"></a>관련 항목  
 [dbo.syssubsystems &#40;TRANSACT-SQL&#41;](../../relational-databases/system-tables/dbo-syssubsystems-transact-sql.md)   
 [dbo.sysproxies &#40;TRANSACT-SQL&#41;](../../relational-databases/system-tables/dbo-sysproxies-transact-sql.md)  
  
  
