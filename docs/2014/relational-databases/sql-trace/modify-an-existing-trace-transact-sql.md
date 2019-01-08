---
title: 기존 추적 수정(Transact-SQL) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- traces [SQL Server], modifying
- modifying traces
ms.assetid: 8792b43f-2510-44e3-9239-e73ad8227b89
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 56d4f7d922c0c229b1e2126f93611670adf7c702
ms.sourcegitcommit: 37310da0565c2792aae43b3855bd3948fd13e044
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/18/2018
ms.locfileid: "53591847"
---
# <a name="modify-an-existing-trace-transact-sql"></a>기존 추적 수정(Transact-SQL)
  이 항목에서는 저장 프로시저를 사용하여 기존 추적을 수정하는 방법에 대해 설명합니다.  
  
### <a name="to-modify-an-existing-trace"></a>기존 추적을 수정하려면  
  
1.  추적이 이미 실행 중이면 **@status = 0**을 지정하고 **sp_trace_setstatus**를 실행하여 추적을 중지합니다.  
  
2.  추적 이벤트를 수정하려면 매개 변수를 통해 변경 내용을 지정하는 **sp_trace_setevent** 를 실행합니다. 순서대로 나열된 매개 변수는 다음과 같습니다.  
  
    -   **@traceid** (추적 ID)  
  
    -   **@eventid** (이벤트 ID)  
  
    -   **@columnid** (열 ID)  
  
    -   **@on** (ON)  
  
     **@on** 매개 변수를 수정할 경우 이 매개 변수가 **@columnid** 매개 변수와 상호 작용한다는 점에 유의하세요.  
  
    |ON|열 ID|결과|  
    |--------|---------------|------------|  
    |ON(**1**)|NULL|이벤트가 활성화됩니다. 모든 열이 지워집니다.|  
    ||NOT NULL|지정된 이벤트에 대해 열이 활성화됩니다.|  
    |OFF(**0**)|NULL|이벤트가 해제됩니다. 모든 열이 지워집니다.|  
    ||NOT NULL|지정된 이벤트에 대해 열이 해제됩니다.|  
  
> [!IMPORTANT]
>  일반적인 저장된 프로시저의 모든 매개 변수가 달리 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 저장 프로시저 (<strong>sp_trace_*xx*</strong>)는 엄격 하 게 형식이 며 데이터 형식 자동 변환을 지원 하지 않습니다. 이러한 매개 변수를 인수 설명에 지정된 올바른 입력 매개 변수 데이터 형식으로 호출하지 않으면 저장 프로시저가 오류를 반환합니다.  

## <a name="see-also"></a>관련 항목  
 [sp_trace_setevent&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql)   
 [sp_trace_setstatus&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setstatus-transact-sql)   
 [시스템 저장 프로시저&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/system-stored-procedures-transact-sql)   
 [SQL Server Profiler 저장 프로시저&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sql-server-profiler-stored-procedures-transact-sql)  
  
  
