---
title: 파일에 추적 결과 저장
titleSuffix: SQL Server Profiler
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
ms.assetid: ac528747-0c19-4f3d-96f5-44c762a4abed
author: markingmyname
ms.author: maghan
ms.custom: seo-lt-2019
ms.date: 03/14/2017
ms.openlocfilehash: dc77ef698496e79e56d818ab00a63f38e0ad7c38
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/29/2020
ms.locfileid: "75307453"
---
# <a name="save-trace-results-to-a-file-sql-server-profiler"></a>추적 결과를 파일에 저장(SQL Server Profiler)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

이 항목에서는 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]를 사용하여 추적 결과를 파일에 저장하는 방법에 대해 설명합니다.  
  
### <a name="to-save-trace-results-to-a-file"></a>파일에 추적 결과를 저장하려면  
  
1.  **파일** 메뉴에서 **새 추적**을 클릭한 다음 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]인스턴스에 연결합니다.  
  
     **추적 속성**대화 상자가 표시됩니다.  
  
    > [!NOTE]  
    >  **연결한 후 즉시 추적 시작**을 선택한 경우에는 **추적 속성**대화 상자가 나타나지 않고 추적이 시작됩니다. 이 설정을 해제하려면 **도구**메뉴에서 **옵션**을 클릭한 다음 **연결한 후 즉시 추적 시작** 확인란의 선택을 취소합니다.  
  
2.  **추적 이름** 입력란에 추적의 이름을 입력합니다.  
  
3.  **파일에 저장** 확인란을 선택합니다.  
  
     **다른 이름으로 저장**대화 상자가 나타납니다.  
  
4.  **다른 이름으로 저장**대화 상자에 경로와 파일 이름을 지정합니다. **저장**을 클릭합니다.  
  
    > [!NOTE]  
    >  SQL Server 서비스는 지정된 디렉터리에 있는 파일에 대한 쓰기 권한이 있어야 합니다.  
  
5.  **추적 속성** 대화 상자에서 **최대 파일 크기 설정(MB)** 입력란에 최대 파일 크기를 입력합니다. 기본값은 5MB입니다.  
  
6.  필요에 따라 다음 옵션을 지정합니다.  
  
    -   최대 파일 크기에 도달했을 때 **가 추적 데이터용으로 새 파일을 만들도록 하려면** 파일 롤오버 사용 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 확인란을 선택합니다. 이 옵션은 기본적으로 선택되어 있습니다.  
  
    -   서버가 각 추적 이벤트를 기록하도록 하려면 **서버에서 추적 데이터 처리** 확인란을 선택합니다.  
  
        > [!NOTE]  
        >  **서버에서 추적 데이터 처리**가 선택되지 않은 경우 이벤트 기록으로 인해 성능이 크게 저하되면 서버는 이벤트를 기록하지 않습니다.  
  
## <a name="see-also"></a>참고 항목  
 [SQL Server Profiler](../../tools/sql-server-profiler/sql-server-profiler.md)  
  
  
