---
title: 교착 상태 그래프 저장(SQL Server Profiler) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- deadlocks [SQL Server], saving deadlock graphs
- graphs [SQL Server]
- saving deadlock graphs
ms.assetid: bf1fc906-abd6-4a89-842e-da0d66b2defe
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 33757ad1f8085ce141b8e206f2c3fd99c7dcba90
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/26/2020
ms.locfileid: "63150699"
---
# <a name="save-deadlock-graphs-sql-server-profiler"></a>교착 상태 그래프 저장(SQL Server Profiler)
  이 항목에서는 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]를 사용하여 교착 상태 그래프를 저장하는 방법에 대해 설명합니다. 교착 상태 그래프는 XML 파일로 저장됩니다.  
  
### <a name="to-save-deadlock-graph-events-separately"></a>교착 상태 그래프 이벤트를 별도로 저장하려면  
  
1.  **파일** 메뉴에서 **새 추적**을 클릭한 다음 SQL Server 인스턴스에 연결합니다.  
  
     **추적 속성**대화 상자가 표시됩니다.  
  
    > [!NOTE]  
    >  **연결한 후 즉시 추적 시작** 을 선택한 경우에는 **추적 속성**대화 상자가 나타나지 않고 추적이 시작됩니다. 이 설정을 해제하려면 **도구**메뉴에서 **옵션**을 클릭한 다음 **연결한 후 즉시 추적 시작** 확인란의 선택을 취소합니다.  
  
2.  추적 속성 대화 상자에서**추적 이름** 입력란에 추적의 이름을 입력합니다.  
  
3.  **템플릿 사용** 목록에서 추적의 기반이 되는 추적 템플릿을 선택하거나 템플릿을 사용하지 않을 경우 **비어 있음** 을 선택합니다.  
  
4.  다음 중 하나를 수행합니다.  
  
    -   추적을 데이터베이스 테이블에 캡처하려면**파일에 저장** 확인란을 선택하면 추적이 파일에 캡처됩니다. **최대 파일 크기 설정**에 대한 값을 지정합니다.  
  
         필요에 따라 **파일 롤오버 사용** 과 **서버에서 추적 데이터 처리**를 선택합니다.  
  
    -   추적을 데이터베이스 테이블에 캡처하려면 **테이블에 저장** 확인란을 선택합니다.  
  
         필요에 따라 **최대 행 설정**을 클릭 하 고 값을 지정 합니다.  
  
5.  필요에 따라 **추적 중지 시간 설정** 확인란을 선택하여 중지 날짜 및 시간을 지정합니다.  
  
6.  **이벤트 선택**탭을 클릭합니다.  
  
7.  **이벤트**데이터 열에서 **잠금**이벤트 범주를 확장한 다음 **교착 상태 그래프**확인란을 선택합니다. Locks 이벤트 범주가 나타나지 않는 경우 **모든 이벤트 표시** 를 선택하여 이 범주를 표시합니다.  
  
     **이벤트 추출 설정**탭이 **추적 속성**대화 상자에 추가됩니다.  
  
8.  **이벤트 추출 설정**탭에서 **별도로 교착 상태 XML 이벤트 저장**을 클릭합니다.  
  
9. **다른 이름으로 저장** 대화 상자에 교착 상태 그래프 이벤트를 저장할 파일의 이름을 입력합니다.  
  
10. **모든 교착 상태 XML 일괄 처리를 단일 파일로 저장** 을 클릭하여 모든 교착 상태 그래프 이벤트를 단일 XML 파일로 저장하거나 **각 교착 상태 XML 일괄 처리를 개별 파일로 저장**을 클릭하여 각 교착 상태 그래프에 대해 새 XML 파일을 만듭니다.  
  
 교착 상태 파일을 저장한 다음 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]에서 파일을 열 수 있습니다. 자세한 내용은 [&#41;SQL Server Management Studio &#40;교착 상태 파일 열기, 보기 및 인쇄 ](open-view-and-print-a-deadlock-file-sql-server-management-studio.md)를 참조 하세요.  
  
## <a name="see-also"></a>참고 항목  
 [SQL Server Profiler를 사용하여 교착 상태 분석](../../tools/sql-server-profiler/analyze-deadlocks-with-sql-server-profiler.md)  
  
  
