---
title: 추적에서 이벤트 필터링
titleSuffix: SQL Server Profiler
description: SQL Server Profiler가 추적하는 동안 캡처할 이벤트를 제한하는 필터를 설정하는 방법을 알아봅니다. 특정 필터에 필요한 형식을 확인합니다.
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
ms.assetid: 0fd63573-3b35-4f67-9e1e-ed9aabee11a8
author: markingmyname
ms.author: maghan
ms.custom: seo-lt-2019
ms.date: 03/01/2017
ms.openlocfilehash: fd8eae33f37b3e21716a0eabd894f77558ac34da
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85790008"
---
# <a name="filter-events-in-a-trace-sql-server-profiler"></a>추적에서의 이벤트 필터링(SQL Server Profiler)

 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

필터가 설정되면 추적에서 수집하는 이벤트가 제한됩니다. 필터가 설정되어 있지 않으면 선택된 이벤트 클래스의 모든 이벤트가 추적 출력에서 반환됩니다. 반드시 추적에 대한 필터를 설정해야 하는 것은 아닙니다. 그러나 필터를 설정하면 추적하는 동안 발생하는 오버헤드가 최소화됩니다.  
  
 **추적 속성** 또는 **추적 템플릿 속성** 대화 상자의 **이벤트 선택** 탭을 사용하여 추적 정의에 필터를 추가합니다.  
  
### <a name="to-filter-events-in-a-trace"></a>추적에서 이벤트를 필터링하려면  
  
1.  **추적 속성** 또는 **추적 템플릿 속성** 대화 상자에서 **이벤트 선택** 탭을 클릭합니다.  
  
     **이벤트 선택** 탭에는 표 형태 컨트롤이 있습니다. 표 형태 컨트롤은 추적 가능한 각 이벤트 클래스가 들어 있는 테이블입니다. 테이블에는 각 이벤트 클래스에 대한 행이 하나씩 포함되어 있습니다. 이벤트 클래스는 사용자가 연결된 서버의 유형 및 버전에 따라 약간 다를 수 있습니다. 이벤트 클래스는 표의 **이벤트** 열에서 식별되며 이벤트 범주별로 그룹화됩니다. 나머지 열은 각 이벤트 클래스에 대해 반환할 수 있는 데이터 열을 나열합니다.  
  
2.  **열 필터**를 클릭합니다.  
  
     **필터 편집** 대화 상자가 나타납니다. **필터 편집** 대화 상자에는 추적에서 이벤트를 필터링하는 데 사용할 수 있는 비교 연산자 목록이 있습니다.  
  
3.  필터를 적용하려면 비교 연산자를 클릭하고 필터에 사용할 값을 입력합니다.  
  
4.  **확인**을 클릭합니다.  
  
 **고려 사항:**  
  
-   이벤트 선택 탭의 **StartTime** 및 **EndTime** 데이터 열에서 필터 조건을 설정할 경우 다음 사항을 확인하십시오.  
  
    -   입력한 날짜의 다음 `YYYY/MM/DD HH:mm:sec`형식과 같아야 합니다.  
  
         또는  
  
    -   **일반 옵션** 대화 상자에서 **날짜 및 시간 값 표시에 국가별 설정 사용** 이 선택되어 있어야 합니다. **일반 옵션** 대화 상자를 보려면 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] **도구** 메뉴에서 **옵션**을 클릭합니다.  
  
         -그리고-  
  
    -   입력한 날짜가 1753년 1월 1일에서 9999년 12월 31일 사이여야 합니다.  
  
-   **osql** 유틸리티 또는 **sqlcmd** 유틸리티에서 이벤트를 추적하는 경우 항상 **%** 를 **TextData** 데이터 열의 필터에 추가합니다.  
  
## <a name="see-also"></a>참고 항목  
 [SQL Server Profiler](../../tools/sql-server-profiler/sql-server-profiler.md)  
  
  
