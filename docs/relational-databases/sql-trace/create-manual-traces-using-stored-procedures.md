---
description: 저장 프로시저를 사용하여 수동 추적 만들기
title: 저장 프로시저를 사용하여 수동 추적 만들기
ms.custom: seo-dt-2019
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
ms.assetid: f6f47fa2-7c17-41d4-9f69-9be144d56832
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: d19212c30d7c9789b8e2ab3d42ccd3d4ac00bc0c
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88402709"
---
# <a name="create-manual-traces-using-stored-procedures"></a>저장 프로시저를 사용하여 수동 추적 만들기
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 는 [!INCLUDE[tsql](../../includes/tsql-md.md)] 인스턴스에 대한 추적을 만들 수 있는 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]시스템 저장 프로시저를 제공합니다. 이 시스템 저장 프로시저를 사용자의 애플리케이션에서 사용하면 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]를 사용하지 않고 추적을 수동으로 만들 수 있습니다. 따라서 각 사용자 조직의 필요에 따라 사용자 지정 애플리케이션을 쓸 수 있습니다.  
  
## <a name="in-this-section"></a>섹션 내용  
 다음 표에서는 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]인스턴스 추적을 위한 시스템 저장 프로시저를 나열합니다.  
  
|저장 프로시저|수행된 태스크|  
|----------------------|--------------------|  
|[sys.fn_trace_geteventinfo&#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-trace-geteventinfo-transact-sql.md)|추적에 포함된 이벤트에 대한 정보를 반환합니다.|  
|[sys.fn_trace_getinfo&#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-trace-getinfo-transact-sql.md)|지정한 추적이나 모든 기존 추적에 대한 정보를 반환합니다.|  
|[sp_trace_create&#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-create-transact-sql.md)|추적 정의를 만듭니다. 새 추적은 중지된 상태가 됩니다.|  
|[sp_trace_generateevent&#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-generateevent-transact-sql.md)|사용자 정의 이벤트를 만듭니다.|  
|[sp_trace_setevent&#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql.md)|추적에서 이벤트 클래스나 데이터 열을 추가 또는 제거합니다.|  
|[sp_trace_setstatus&#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-setstatus-transact-sql.md)|추적을 시작, 중지 또는 닫습니다.|  
|[sys.fn_trace_getfilterinfo&#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-trace-getfilterinfo-transact-sql.md)|추적에 적용되는 필터에 대한 정보를 반환합니다.|  
|[sp_trace_setfilter&#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-setfilter-transact-sql.md)|추적에 새 필터 또는 수정된 필터를 적용합니다.|  
  
 **저장 프로시저를 사용하여 사용자가 소유한 추적을 정의하려면**  
  
1.  **sp_trace_setevent**로 캡처할 이벤트를 지정합니다.  
  
2.  이벤트 필터를 지정합니다. 자세한 내용은 [추적 필터 설정&#40;Transact-SQL&#41;](../../relational-databases/sql-trace/set-a-trace-filter-transact-sql.md)을 참조하세요.  
  
3.  **sp_trace_create**로 캡처된 이벤트 데이터에 대한 대상을 지정합니다.  

 추적 저장 프로시저 사용에 대한 예는 [추적 만들기&#40;Transact-SQL&#41;](../../relational-databases/sql-trace/create-a-trace-transact-sql.md)를 참조하세요.  
  
 **추적 정의 기본값 설정**  
  
 [SQL Server Profiler](../../tools/sql-server-profiler/set-trace-definition-defaults-sql-server-profiler.md)  
  
 **추적 표시 기본값 설정**  
  
 [SQL Server Profiler](../../tools/sql-server-profiler/set-trace-display-defaults-sql-server-profiler.md)  
  
 **추적 만들기**  
  
 [SQL Server Profiler](../../tools/sql-server-profiler/create-a-trace-sql-server-profiler.md)  
  
 [Transact-SQL](../../relational-databases/sql-trace/create-a-trace-transact-sql.md)  
  
 **추적 템플릿에서 이벤트 추가 또는 제거**  
  
 [SQL Server Profiler](../../tools/sql-server-profiler/specify-events-and-data-columns-for-a-trace-file-sql-server-profiler.md)  
  
 [Transact-SQL](../../relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql.md)  
  
  
