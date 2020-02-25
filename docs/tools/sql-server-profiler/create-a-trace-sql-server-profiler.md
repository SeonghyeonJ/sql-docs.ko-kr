---
title: 추적 만들기
titleSuffix: SQL Server Profiler
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
ms.assetid: 0302fa6d-d2b5-43fe-ad70-7a337575b112
author: markingmyname
ms.author: maghan
ms.custom: seo-lt-2019
ms.date: 08/01/2016
ms.openlocfilehash: 5a5c004bbc7e93720f18df998b989c46ced0188e
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/31/2020
ms.locfileid: "75307338"
---
# <a name="create-a-trace-sql-server-profiler"></a>추적 만들기(SQL Server Profiler)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

이 항목에서는 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 를 사용하여 추적을 만드는 방법에 대해 설명합니다.  
  
### <a name="to-create-a-trace"></a>추적 만들기  
  
1.  **파일** 메뉴에서 **새 추적**을 클릭한 다음 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]인스턴스에 연결합니다.  
  
     **추적 속성** 대화 상자가 나타납니다.  
  
    > **참고:** **연결한 후 즉시 추적 시작** 을 선택한 경우에는 **추적 속성** 대화 상자가 나타나지 않고 추적이 시작됩니다. 이 설정을 해제하려면 *도구  *메뉴에서 **옵션**을 클릭한 다음, 연결하고 즉시 추적 시작 확인란의 선택을 취소합니다.  
  
2.  **추적 이름** 입력란에 추적의 이름을 입력합니다.  
  
3.  **템플릿 사용** 목록에서 추적의 기반이 되는 추적 템플릿을 선택하거나 템플릿을 사용하지 않을 경우 **비어 있음** 을 선택합니다.  
  
4.  추적 결과를 저장하려면 다음 중 하나를 수행합니다.  
  
    -   **파일에 저장** 을 클릭하면 추적이 파일에 캡처됩니다. **최대 파일 크기 설정**에 대한 값을 지정합니다. 기본값은 5MB입니다.  
  
         **파일 롤오버 사용** 을 선택하여 최대 파일 크기에 도달할 때 자동으로 새 파일을 만들 수도 있습니다. **서버에서 추적 데이터 처리**를 선택하면 클라이언트 애플리케이션 대신 추적을 실행하는 서비스에서 추적 데이터를 처리하게 됩니다. 서버에서 추적 데이터를 처리하는 경우 스트레스 상태에서도 이벤트를 건너뛰지 않지만 서버 성능은 저하될 수 있습니다.  
  
    -   **테이블에 저장** 을 클릭하여 추적을 데이터베이스 테이블에 캡처합니다.  
  
         필요에 따라 **최대 행 수 설정**을 클릭하고 값을 지정합니다.  
  
    > **주의** 추적 결과를 파일이나 테이블에 저장하지 않아도 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 가 열려 있으면 추적을 표시할 수 있습니다. 그러나 추적을 중지하고 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]를 닫으면 추적 결과가 손실됩니다. 이런 방식으로 추적 결과가 손실되는 것을 방지하려면 **를 닫기 전에** 파일 **메뉴에서** 저장 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]을 클릭합니다.  
  
5.  필요에 따라 **추적 중지 시간 설정** 확인란을 선택하여 중지 날짜 및 시간을 지정합니다.  
  
6.  이벤트, 데이터 열 또는 필터를 추가하거나 제거하려면 **이벤트 선택**  탭을 클릭합니다. 자세한 내용은 다음을 참조하세요. [추적 파일에 대해 이벤트 및 데이터 열 지정&#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/specify-events-and-data-columns-for-a-trace-file-sql-server-profiler.md)  
  
7.  **실행** 을 클릭하여 추적을 시작합니다.  
  
## <a name="see-also"></a>참고 항목  
 [SQL Server 프로파일러 실행에 필요한 권한](../../tools/sql-server-profiler/permissions-required-to-run-sql-server-profiler.md)   
 [SQL Server Profiler 템플릿 및 권한](../../tools/sql-server-profiler/sql-server-profiler-templates-and-permissions.md)   
 [SQL Server 프로파일러](../../tools/sql-server-profiler/sql-server-profiler.md)   
 [추적과 Windows 성능 로그 데이터의 상관 관계 지정&#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/correlate-a-trace-with-windows-performance-log-data-sql-server-profiler.md)  
  
  
