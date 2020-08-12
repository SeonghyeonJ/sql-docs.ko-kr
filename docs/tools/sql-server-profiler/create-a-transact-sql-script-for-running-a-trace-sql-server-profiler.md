---
title: 추적 실행을 위한 Transact-SQL 스크립트 만들기
titleSuffix: SQL Server Profiler
description: SQL Server Profiler에서 기존 추적 파일 또는 테이블로부터 Transact-SQL 스크립트를 만드는 방법을 알아봅니다.
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
ms.assetid: 6b0e2519-998d-40d5-b8ba-5e6a773f91a6
author: markingmyname
ms.author: maghan
ms.custom: seo-lt-2019
ms.date: 03/01/2017
ms.openlocfilehash: 9f34472358f0d0cde586a25374c0de90ab708539
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85774856"
---
# <a name="create-a-transact-sql-script-for-running-a-trace-sql-server-profiler"></a>추적 실행을 위한 Transact-SQL 스크립트 만들기(SQL Server Profiler)
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  이 항목에서는 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]를 사용하여 기존 추적 파일 또는 테이블에서 Transact-SQL 스크립트를 만드는 방법에 대해 설명합니다.  
  
### <a name="to-create-a-transact-sql-script-to-run-a-trace"></a>추적을 실행하도록 Transact-SQL 스크립트를 만들려면  
  
1.  추적 파일 또는 테이블을 엽니다. 자세한 내용은 [추적 파일 열기&#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/open-a-trace-file-sql-server-profiler.md) 또는 [추적 테이블 열기&#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/open-a-trace-table-sql-server-profiler.md)에서 제공되는 사전 정의된 튜닝 템플릿을 사용합니다.  
  
2.  **파일**메뉴에서 **내보내기**, **추적 정의 스크립팅**을 차례로 가리킨 다음 추적할 서버에 해당하는 버전을 클릭합니다.  
  
3.  **다른 이름으로 저장** 대화 상자에서 스크립트 파일의 이름을 입력한 다음 **저장**을 클릭합니다.  
  
## <a name="see-also"></a>참고 항목  
 [SQL Server Profiler 템플릿 및 권한](../../tools/sql-server-profiler/sql-server-profiler-templates-and-permissions.md)   
 [SQL Server Profiler](../../tools/sql-server-profiler/sql-server-profiler.md)  
  
  
