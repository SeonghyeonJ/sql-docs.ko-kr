---
title: 추적에서 스크립트 추출(SQL Server Profiler) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- scripts [SQL Server], traces
- extracting script from trace [SQL Server]
ms.assetid: 431126a6-ff91-4818-8763-4442152bd571
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 178fba1888c84471b8cc568c77abd9ed797d1b6c
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/03/2018
ms.locfileid: "52768285"
---
# <a name="extract-a-script-from-a-trace-sql-server-profiler"></a>추적에서 스크립트 추출(SQL Server Profiler)
  이 항목에서는 [!INCLUDE[tsql](../../includes/tsql-md.md)] 를 사용하여 추적 파일이나 테이블에서 [!INCLUDE[tsql](../../includes/tsql-md.md)] 이벤트를 추출하고 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]스크립트 파일로 저장하는 방법에 대해 설명합니다.  
  
### <a name="to-extract-a-transact-sql-script-from-a-trace-file-or-table"></a>추적 파일이나 테이블에서 Transact-SQL 스크립트를 추출하려면  
  
1.  [!INCLUDE[tsql](../../includes/tsql-md.md)] 스크립트 파일로 저장할 [!INCLUDE[tsql](../../includes/tsql-md.md)] 이벤트를 포함하는 추적 파일이나 테이블을 엽니다. 자세한 내용은 [추적 파일 열기&#40;SQL Server Profiler&#41;](open-a-trace-file-sql-server-profiler.md) 또는 [추적 테이블 열기&#40;SQL Server Profiler&#41;](open-a-trace-table-sql-server-profiler.md)에서 제공되는 사전 정의된 튜닝 템플릿을 사용합니다.  
  
2.  **파일** 메뉴에서 **내보내기**, **SQL Server 이벤트 추출**을 차례로 가리킨 다음 **Transact-SQL 이벤트 추출**을 클릭합니다.  
  
3.  **다른 이름으로 저장** 대화 상자에서 [!INCLUDE[tsql](../../includes/tsql-md.md)] 파일의 이름을 입력한 다음 **저장**을 클릭합니다.  
  
## <a name="see-also"></a>관련 항목:  
 [SQL Server 프로파일러](sql-server-profiler.md)  
  
  
