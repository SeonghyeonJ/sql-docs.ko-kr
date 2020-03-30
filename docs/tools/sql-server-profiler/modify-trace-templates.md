---
title: 추적 템플릿 수정
titleSuffix: SQL Server Profiler
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
ms.assetid: 75b62a54-8d16-4599-bd2d-c42cfcc209f4
author: markingmyname
ms.author: maghan
ms.custom: seo-lt-2019
ms.date: 07/12/2017
ms.openlocfilehash: 71716d1a9a50a29e1f574fb292d078d21e34a9a6
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/29/2020
ms.locfileid: "75307167"
---
# <a name="modify-trace-templates"></a>추적 템플릿 수정
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 가 실행 중인 로컬 컴퓨터에서 파일에 저장된 템플릿을 수정할 수 있습니다. 이런 파일에서 파생된 템플릿도 수정할 수 있습니다. 기존 템플릿을 수정할 때 **추적 속성** 대화 상자의 **이벤트 선택** 탭에서 속성이 원래 설정된 순서와 동일한 순서대로 이벤트 클래스나 데이터 열 같은 템플릿 속성을 편집합니다. 이벤트 클래스 및 데이터 열을 추가 또는 제거할 수도 있고 필터도 같은 방법으로 변경할 수 있습니다. 템플릿을 수정하면 사용자 특정 템플릿이 만들어지고 원래 시스템 템플릿은 그대로 남습니다. 자세한 내용은 [추적 및 추적 템플릿 저장](../../tools/sql-server-profiler/save-traces-and-trace-templates.md)을 참조하세요.  
  
 추적을 만들 때 사용한 원래 템플릿을 기억할 수 없거나 나중에 같은 추적을 실행하려는 경우 기존 추적 파일에서 템플릿을 파생해야 합니다. 기존의 추적으로 작업하면 속성을 볼 수는 있지만 수정할 수는 없습니다. 속성을 수정하려면 추적을 시작하거나 일시 중지하십시오. 자세한 내용은 [추적 파일 또는 추적 테이블에서 템플릿 파생&#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/derive-a-template-from-a-trace-file-or-trace-table-sql-server-profiler.md) 및 [실행 중인 추적으로부터 템플릿 파생&#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/derive-a-template-from-a-running-trace-sql-server-profiler.md)을 참조하세요.  
  
## <a name="to-modify-a-trace-template"></a>추적 템플릿을 수정하려면  
  
1.  **파일** 메뉴에서 **템플릿**- **템플릿 편집**을 클릭합니다.  
  
2.  **추적 템플릿 속성** 대화 상자의 **일반** 탭에서 서버 유형과 템플릿 이름을 수정하거나 서버 유형에 맞는 기본 템플릿을 사용하도록 선택합니다.  
  
3.  **이벤트 선택** 탭에서 표 형태 컨트롤을 사용하여 다음과 같이 추적 파일에서 이벤트와 데이터 열을 추가하거나 제거할 수 있습니다.  
  
    -   이벤트를 추가하려면 **이벤트** 열의 해당 이벤트 범주를 확장한 다음 이벤트 이름을 선택합니다.  
  
    -   이벤트를 추가할 때는 관련된 모든 데이터 열이 기본적으로 포함됩니다. 추적에서 이벤트에 대한 데이터 열을 제거하려면 해당 이벤트에 대한 데이터 열의 확인란 선택을 취소합니다.  
  
    -   필터를 추가하려면 데이터 열 이름을 클릭하고 **필터 편집** 대화 상자에 필터 조건을 지정합니다. 또한 데이터 열 이름을 마우스 오른쪽 단추로 클릭하고 **열 필터 편집** 을 클릭하여 **필터 편집** 대화 상자를 실행할 수 있습니다. **확인** 을 클릭하여 필터를 추가합니다.  
  
4.  **저장** 또는 **다른 이름으로 저장**을 클릭하여 추적 템플릿을 저장합니다.  
  
## <a name="next-steps"></a>다음 단계  
[추적 시작](../../tools/sql-server-profiler/start-a-trace.md)  
[추적 만들기](../../tools/sql-server-profiler/create-a-trace-sql-server-profiler.md)  
[Transact-SQL을 사용하여 기존 추적 수정](../../relational-databases/sql-trace/modify-an-existing-trace-transact-sql.md)  
[SQL Server Profiler를 사용하여 추적에 대한 이벤트 및 데이터 열 지정](../../tools/sql-server-profiler/specify-events-and-data-columns-for-a-trace-file-sql-server-profiler.md)  
[sp-trace-setevent-transact-sql](../../relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql.md)  
  
