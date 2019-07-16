---
title: sp_dbmmonitorupdate (TRANSACT-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_dbmmonitorupdate
- sp_dbmmonitorupdate_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_dbmmonitorupdate
- database mirroring [SQL Server], monitoring
ms.assetid: 9ceb9611-4929-44ee-a406-c39ba2720fd5
author: stevestein
ms.author: sstein
ms.openlocfilehash: 190b4f0598afa6d434b5dada8c8464cb8209dac7
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68061258"
---
# <a name="spdbmmonitorupdate-transact-sql"></a>sp_dbmmonitorupdate(Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  각 미러된 데이터베이스에 대한 새 테이블 행을 삽입하여 데이터베이스 미러링 모니터 상태 테이블을 업데이트하고 현재 보존 기간보다 오래된 행을 자릅니다. 기본 보존 기간은 7일(168시간)입니다. 테이블을 업데이트할 때 **sp_dbmmonitorupdate** 성능 메트릭을 평가 합니다.  
  
> [!NOTE]  
>  처음 **sp_dbmmonitorupdate** 실행 데이터베이스 미러링 상태 테이블을 만들면 및 **dbm_monitor** 고정된 데이터베이스 역할은 **msdb** 데이터베이스.  
  
 ![항목 링크 아이콘](../../database-engine/configure-windows/media/topic-link.gif "항목 링크 아이콘") [Transact-SQL 구문 규칙](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>구문  
  
```  
  
sp_dbmmonitorupdate [ database_name ]  
```  
  
## <a name="arguments"></a>인수  
 *database_name*  
 미러링 상태를 업데이트할 데이터베이스의 이름입니다. 하는 경우 *database_name* 지정 하지 않으면 프로시저는 서버 인스턴스의 모든 미러된 데이터베이스에 대 한 상태 테이블을 업데이트 합니다.  
  
## <a name="return-code-values"></a>반환 코드 값  
 없음  
  
## <a name="result-sets"></a>결과 집합  
 없음  
  
## <a name="remarks"></a>설명  
 **sp_dbmmonitorupdate** 의 컨텍스트에서만 실행할 수 있습니다 합니다 **msdb** 데이터베이스입니다.  
  
 상태 테이블의 열이 파트너의 역할에 적용되지 않는 경우 해당 파트너에 대한 값은 NULL이 됩니다. 장애 조치(Failover) 또는 서버 다시 시작 중과 같이 관련 정보를 사용할 수 없는 경우에도 열 값이 NULL이 됩니다.  
  
 후 **sp_dbmmonitorupdate** 만듭니다 합니다 **dbm_monitor** 고정된 데이터베이스 역할을 **msdb** 데이터베이스의 멤버는 **sysadmin** 고정된 서버 역할에 임의의 사용자를 추가할 수는 **dbm_monitor** 고정된 데이터베이스 역할. 합니다 **dbm_monitor** 역할에 해당 멤버 데이터베이스 미러링 상태를 보고 하지만 하지 업데이트 하지만 하지 보기 또는 구성 데이터베이스 미러링 이벤트를 사용 하도록 설정 합니다.  
  
 데이터베이스 미러링 상태를 업데이트 하는 경우 **sp_dbmmonitorupdate** 경고 임계값을 지정 된는 모든 미러링 성능 메트릭의 최신 값을 검사 합니다. 이 값이 임계값을 초과하면 프로시저는 이벤트 로그에 정보 이벤트를 추가합니다. 모든 속도는 마지막 업데이트 이후의 평균입니다. 자세한 내용은 [미러링 성능 메트릭에 대해 경고 임계값 및 경고 사용&#40;SQL Server&#41;](../../database-engine/database-mirroring/use-warning-thresholds-and-alerts-on-mirroring-performance-metrics-sql-server.md)을 참조하세요.  
  
## <a name="permissions"></a>사용 권한  
 **sysadmin** 고정 서버 역할의 멤버 자격이 필요합니다.  
  
## <a name="examples"></a>예  
 다음 예에서는 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 데이터베이스에 대한 미러링 상태만 업데이트합니다.  
  
```  
USE msdb;  
EXEC sp_dbmmonitorupdate AdventureWorks2012 ;  
```  
  
## <a name="see-also"></a>관련 항목  
 [데이터베이스 미러링 모니터링&#40;SQL Server&#41;](../../database-engine/database-mirroring/monitoring-database-mirroring-sql-server.md)   
 [sp_dbmmonitorchangealert &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dbmmonitorchangealert-transact-sql.md)   
 [sp_dbmmonitorchangemonitoring &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dbmmonitorchangemonitoring-transact-sql.md)   
 [sp_dbmmonitordropalert &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dbmmonitordropalert-transact-sql.md)   
 [sp_dbmmonitorhelpalert &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dbmmonitorhelpalert-transact-sql.md)   
 [sp_dbmmonitorhelpmonitoring &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dbmmonitorhelpmonitoring-transact-sql.md)   
 [sp_dbmmonitorresults&#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dbmmonitorresults-transact-sql.md)  
  
  
