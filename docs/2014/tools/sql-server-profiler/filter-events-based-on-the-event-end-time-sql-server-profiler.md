---
title: 이벤트 종료 시간 기반의 이벤트 필터링(SQL Server Profiler) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- event end times [SQL Server]
- filters [SQL Server], traces
- traces [SQL Server], filters
- traces [SQL Server], events
ms.assetid: 74628f9e-2d39-496a-a443-0a3887db223d
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 48f0ada8740735e64fe57c35bc17553f59aa444c
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/03/2018
ms.locfileid: "52823847"
---
# <a name="filter-events-based-on-the-event-end-time-sql-server-profiler"></a>이벤트 종료 시간 기반의 이벤트 필터링(SQL Server Profiler)
  이 항목에서는 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]를 사용하여 이벤트 종료 시간을 기반으로 추적 이벤트를 필터링하는 방법을 설명합니다.  
  
### <a name="to-filter-events-based-on-the-event-end-time"></a>이벤트 종료 시간을 기반으로 이벤트를 필터링하려면  
  
1.  **파일** 메뉴에서 **새 추적**을 클릭한 다음 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]인스턴스에 연결합니다.  
  
     **추적 속성**대화 상자가 표시됩니다.  
  
    > [!NOTE]  
    >  **연결한 후 즉시 추적 시작**을 선택한 경우에는 **추적 속성**대화 상자가 나타나지 않고 추적이 시작됩니다. 이 설정을 해제하려면 **도구**메뉴에서 **옵션**을 클릭한 다음 **연결한 후 즉시 추적 시작** 확인란의 선택을 취소합니다.  
  
2.  **추적 속성** 대화 상자에서 **일반** 탭이 선택되어 있는지 확인하고 **추적 이름** 입력란에 이름을 입력합니다.  
  
3.  **템플릿 사용**목록에서 추적 템플릿을 선택합니다.  
  
4.  필요에 따라 추적 결과를 저장할 대상 파일이나 테이블을 지정합니다.  
  
5.  **이벤트 선택**탭에서 **EndTime** 데이터 열을 클릭하여 **필터 편집** 대화 상자를 시작합니다. 열 제목을 마우스 오른쪽 단추로 클릭한 다음 **열 필터 편집**을 선택할 수도 있습니다.  
  
6.  확장 **보다 큰** 또는 **미만**를 입력 하 고는 `datetime`비교 연산자 아래 나타나는 필드의 값.  
  
## <a name="see-also"></a>관련 항목:  
 [SQL Server 프로파일러](sql-server-profiler.md)   
 [SQL Server 프로파일러](sql-server-profiler.md)  
  
  
