---
title: 저장된 추적 보기(Transact-SQL) | Microsoft 문서
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- traces [SQL Server], viewing
- displaying traces
- viewing traces
ms.assetid: 3a95a816-aa89-4d5f-858c-968a9cb3ee87
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 4118a30ffe84210bd7829522d50dc0f163e88639
ms.sourcegitcommit: cff8dd63959d7a45c5446cadf1f5d15ae08406d8
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/05/2019
ms.locfileid: "67582397"
---
# <a name="view-a-saved-trace-transact-sql"></a>저장된 추적 보기(Transact-SQL)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  이 항목에서는 기본 제공 함수를 사용하여 저장된 추적을 보는 방법에 대해 설명합니다.  
  
### <a name="to-view-a-specific-trace"></a>특정 추적을 보려면  
  
1.  필요한 정보에 대한 추적 ID를 지정하여 **fn_trace_getinfo** 를 실행합니다. 이 함수는 추적, 추적 속성, 속성 정보가 들어 있는 테이블을 반환합니다.  

[!INCLUDE[freshInclude](../../includes/paragraph-content/fresh-note-steps-feedback.md)]

     Invoke the function this way:  
  
    ```  
    SELECT *  
    FROM ::fn_trace_getinfo(trace_id)  
    ```  
  
### <a name="to-view-all-existing-traces"></a>기존 추적을 모두 보려면  
  
1.  **이나** 를 지정하여 `0` fn_trace_getinfo `default`를 실행합니다. 이 함수는 모든 추적, 추적 속성, 속성 정보가 들어 있는 테이블을 반환합니다.  
  
     다음과 같이 함수를 호출하십시오.  
  
    ```  
    SELECT *  
    FROM ::fn_trace_getinfo(default)  
    ```  
  
## <a name="net-framework-security"></a>.NET Framework 보안  
 기본 제공 함수 **fn_trace_getinfo**를 실행하려면 사용자에게 다음과 같은 사용 권한이 있어야 합니다.  
  
 서버에 대한 ALTER TRACE  
  
## <a name="see-also"></a>참고 항목  
 [sys.fn_trace_getinfo&#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-trace-getinfo-transact-sql.md)   
 [SQL Server Profiler를 사용하여 추적 보기 및 분석](../../tools/sql-server-profiler/view-and-analyze-traces-with-sql-server-profiler.md)  
  
  
