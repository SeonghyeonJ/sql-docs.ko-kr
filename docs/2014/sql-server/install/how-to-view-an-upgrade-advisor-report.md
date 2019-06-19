---
title: '방법: 업그레이드 관리자 보고서를 보려면 | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- displaying reports
- viewing reports
- Upgrade Advisor [SQL Server], reports
- SQL Server Upgrade Advisor, reports
- reports [Upgrade Advisor], viewing
ms.assetid: d13b38af-0ac3-4030-83cd-e7d7825dd09f
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: c0ae231e380530f11d4c97a917927ed62e99fb47
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66094803"
---
# <a name="how-to-view-an-upgrade-advisor-report"></a>방법: 업그레이드 관리자 보고서 보기
  업그레이드 관리자는 사용자가 분석하도록 선택한 각 구성 요소에 대해 보고서를 작성합니다. 이 항목에서는 업그레이드 관리자 시작 페이지에서 업그레이드 관리자 보고서를 보는 방법을 설명합니다.  
  
> [!IMPORTANT]  
>  보고서 뷰어는 표준 파일 이름을 기준으로 파일을 로드합니다. 파일의 이름이 바뀐 경우 보고서 뷰어는 해당 파일을 로드하지 않습니다.  
  
### <a name="to-view-a-report"></a>보고서를 보려면  
  
1.  클릭 **시작**, 클릭 **프로그램도**, 클릭 **[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]** 를 클릭 하 고  **[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 업그레이드 관리자**.  
  
2.  업그레이드 관리자 시작 페이지에서 클릭 **업그레이드 관리자 보고서 뷰어 시작**합니다.  
  
3.  컴퓨터의 기본 위치에 있는 보고서를 선택하려면  
  
    1.  에 **Server** 목록에서 서버를 선택 합니다.  
  
    2.  에 **인스턴스 또는 구성 요소** 목록, 구성 요소 또는 구성 요소/인스턴스 조합을 선택 합니다.  
  
     다른 위치의 보고서를 선택하려면  
  
    1.  클릭 합니다 **보고서 열기** 링크 합니다.  
  
    2.  보고서 위치를 찾은 다음 XML 파일을 두 번 클릭합니다.  
  
     업그레이드 관리자는 이전 분석에서 생성된 최대 다섯 개의 보고서를 기록으로 저장합니다. 이러한 보고서를 보려면 클릭 합니다 **보고서** 드롭다운 목록 상자 및 보고서를 선택 합니다. 보고서는 보고서가 생성될 때의 타임스탬프를 기준으로 나열됩니다.  
  
     보고서에는 검색된 모든 문제에 대해 다음과 같은 세부 정보가 포함됩니다.  
  
    -   **중요도**, 문제를 해결 하려면이 얼마나 중요 한지를 나타내는입니다.  
  
    -   **해결 시기**를 나타내는 경우 있습니다 해야 (있어야) 문제를 해결 하기 전에 또는로 업그레이드 한 후 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], 마이그레이션하기 전 / 후 응용 프로그램이 나 데이터를 언제 든 지 또는 합니다.  
  
    -   문제에 대한 간단한 설명  
  
4.  보고서에 포함된 항목이 20개를 초과하는 경우 보고서의 위 또는 아래에 있는 녹색 앞으로 화살표를 클릭하면 다음 항목 집합을 볼 수 있습니다. 이전 20개 항목을 보려면 녹색 뒤로 단추를 클릭합니다.  
  
5.  보고서를 정렬하려면 열 제목을 클릭합니다.  
  
6.  특정 항목에 대한 세부 정보를 보려면 해당 항목을 클릭합니다. 문제에 대한 설명이 다음 추가 옵션과 함께 표시됩니다.  
  
    -   이 문제가 발견 된 개체를 보려면 클릭 **표시에 영향을 받는 개체**합니다.  
  
    -   문제에 대 한 도움말을 보려면 클릭 **이 문제 및 해결 방법에 대 한 상세**합니다.  
  
    -   보고서를 다시 볼 때 문제를 숨기, 문제를 해결할 것으로 표시 하려면 선택 **이 문제가 해결 되었습니다**합니다.  
  
> [!NOTE]  
>  보고서에는 검색할 수 없는 문제에 대한 항목이 포함될 수 있습니다. 이러한 문제는 검색할 수 없는 문제, 또는 거짓 긍정 결과를 지나치게 많이 생성하는 문제입니다. 클릭 합니다 **이 문제 및 해결 방법에 대 한 상세** 구성 요소에 대 한 검색할 수 없는 문제 목록을 보려면이 링크를 합니다.  
  
## <a name="see-also"></a>관련 항목  
 [방법: 보고서 내보내기](../../../2014/sql-server/install/how-to-export-reports.md)   
 [방법: 업그레이드 관리자 분석 마법사 실행](../../../2014/sql-server/install/how-to-run-the-upgrade-advisor-analysis-wizard.md)   
 [업그레이드 문제 해결](../../../2014/sql-server/install/resolving-upgrade-issues.md)   
 [업그레이드 관리자 방법 도움말 항목](../../../2014/sql-server/install/upgrade-advisor-how-to-topics.md)   
 [업그레이드 관리자 작업](../../../2014/sql-server/install/working-with-upgrade-advisor.md)  
  
  
