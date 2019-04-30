---
title: 추적 테이블에 최대 테이블 크기 설정(SQL Server Profiler) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- size [SQL Server], trace tables
- maximum table size for traces
ms.assetid: d0ae83e5-1c88-4a2e-be05-2c341280b978
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 15ef5e8621a5edd216b300a8a96f3a9656b55b12
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63267147"
---
# <a name="set-a-maximum-table-size-for-a-trace-table-sql-server-profiler"></a>추적 테이블에 최대 테이블 크기 설정(SQL Server Profiler)
  이 항목에서는 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]를 사용하여 추적 테이블의 최대 테이블 크기를 설정하는 방법에 대해 설명합니다.  
  
### <a name="to-set-a-maximum-table-size-for-a-trace-table"></a>추적 테이블에 최대 테이블 크기를 설정하려면  
  
1.  **파일** 메뉴에서 **새 추적**을 클릭한 다음 SQL Server 인스턴스에 연결합니다.  
  
     **추적 속성**대화 상자가 표시됩니다.  
  
    > [!NOTE]  
    >  **연결한 후 즉시 추적 시작**을 선택한 경우에는 **추적 속성**대화 상자가 나타나지 않고 추적이 시작됩니다. 이 설정을 해제하려면 **도구**메뉴에서 **옵션**을 클릭한 다음 **연결한 후 즉시 추적 시작** 확인란의 선택을 취소합니다.  
  
2.  **추적 이름** 입력란에 추적의 이름을 입력합니다.  
  
3.  **템플릿 이름**목록에서 추적 템플릿을 선택합니다.  
  
4.  **테이블에 저장**확인란을 선택합니다.  
  
5.  추적을 저장하려는 서버에 연결합니다.  
  
     **대상 테이블** 대화 상자가 표시됩니다.  
  
6.  **데이터베이스** 목록에서 추적할 데이터베이스를 선택합니다.  
  
7.  **테이블** 입력란에 테이블 이름을 입력하거나 선택합니다.  
  
8.  **최대 행 수 설정** 확인란을 선택하고 추적 테이블의 최대 행 수를 지정합니다.  
  
    > [!NOTE]  
    >  테이블의 행 수가 지정한 최대 값을 초과하면 추적 이벤트는 더 이상 기록되지 않습니다. 하지만 추적은 계속됩니다.  
  
## <a name="see-also"></a>관련 항목  
 [SQL Server 프로파일러](sql-server-profiler.md)   
 [SQL Server 프로파일러](sql-server-profiler.md)  
  
  
