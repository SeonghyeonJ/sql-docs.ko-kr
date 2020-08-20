---
description: sp_helpdistributor_properties(Transact-SQL)
title: sp_helpdistributor_properties (Transact-sql) | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_helpdistributor_properties_TSQL
- sp_helpdistributor_properties
helpviewer_keywords:
- sp_helpdistributor_properties
ms.assetid: ee267724-3244-49eb-84c9-f38dbefdd639
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 5760625f8316eeddaa9cf1d3dd429e91932e0d4e
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88474065"
---
# <a name="sp_helpdistributor_properties-transact-sql"></a>sp_helpdistributor_properties(Transact-SQL)
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]

  배포자 속성을 반환합니다. 이 저장 프로시저는 배포 데이터베이스의 배포자에서 실행됩니다.  
  
 ![항목 링크 아이콘](../../database-engine/configure-windows/media/topic-link.gif "항목 링크 아이콘") [Transact-SQL 구문 표기 규칙](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>구문  
  
```  
  
sp_helpdistributor_properties   
```  
  
## <a name="result-set"></a>결과 집합  
  
|열 이름|데이터 형식|Description|  
|-----------------|---------------|-----------------|  
|**heartbeat_interval**|**int**|진행률 메시지를 기록하지 않고 에이전트를 실행할 수 있는 최대 시간(분)입니다.|  
  
## <a name="return-code-values"></a>반환 코드 값  
 **0** (성공) 또는 **1** (실패)  
  
## <a name="remarks"></a>설명  
 **sp_helpdistributor_properties** 은 모든 유형의 복제에 사용 됩니다.  
  
## <a name="permissions"></a>사용 권한  
 **Sysadmin** 고정 서버 역할의 멤버, 배포 데이터베이스에 대 한 **db_owner** 또는 **replmonitor** 고정 데이터베이스 역할의 멤버 및이 배포자를 사용 하는 게시에 대 한 PAL (게시 액세스 목록)의 사용자만 **sp_helpdistributor_properties**을 실행할 수 있습니다.  
  
## <a name="see-also"></a>참고 항목  
 [Transact-sql&#41;sp_changedistributor_property &#40;](../../relational-databases/system-stored-procedures/sp-changedistributor-property-transact-sql.md)  
  
  
