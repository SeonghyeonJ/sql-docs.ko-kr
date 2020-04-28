---
title: 작업 중지 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- jobs [SQL Server Agent], stopping
- SQL Server Agent jobs, stopping
- stopping jobs
ms.assetid: 4249328a-24d8-4284-9d1d-7d04ed90e3d7
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: b55ca5e8f2e57e85a75f610efe4115ced0dce365
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/27/2020
ms.locfileid: "72798145"
---
# <a name="stop-a-job"></a>Stop a Job
  이 항목에서는 에이전트 작업을 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 중지 하는 방법에 대해 설명 합니다. 작업은 SQL Server 에이전트에서 수행하도록 지정된 일련의 동작입니다.  
  
-   **시작 하기 전에:** ,  
  
     [제한 사항](#Restrictions)  
  
     [보안](#Security)  
  
-   **작업을 중지하려면:**  
  
     [SQL Server Management Studio](#SSMS)  
  
     [Transact-SQL](#TSQL)  
  
     [SQL Server 관리 개체](#SMO)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> 시작하기 전에  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> 제한 사항  
  
-   작업이 현재 **CmdExec** 또는 **PowerShell**유형의 단계를 실행하고 있는 경우에는 실행 중인 프로세스(예: MyProgram.exe)가 중간에 종료됩니다. 이로 인해 프로세스가 보유하고 있던 파일이 열리는 등 예기치 않은 상황이 발생할 수 있습니다.  
  
-   다중 서버 작업의 경우 해당 작업에 대한 STOP 명령이 작업의 모든 대상 서버에 게시됩니다.  
  
###  <a name="security"></a><a name="Security"></a> 보안  
 자세한 내용은 [SQL Server 에이전트 보안 구현](implement-sql-server-agent-security.md)을 참조하세요.  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMS"></a> SQL Server Management Studio 사용  
  
#### <a name="to-stop-a-job"></a>작업을 중지하려면  
  
1.  **개체 탐색기**에서 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]의 인스턴스에 연결한 다음, 해당 인스턴스를 확장합니다.  
  
2.  **SQL Server 에이전트**, **작업**을 차례로 확장하고 중단할 작업을 마우스 오른쪽 단추로 클릭한 다음 **작업 중지**를 클릭합니다.  
  
3.  여러 작업을 중지하려면 **작업 활동 모니터**를 마우스 오른쪽 단추로 클릭한 다음 **작업 활동 보기**를 클릭합니다. 작업 활동 모니터에서 중지하려는 작업을 선택하고 선택 항목을 마우스 오른쪽 단추로 클릭한 다음 **작업 중지**를 클릭합니다.  
  
##  <a name="using-transact-sql"></a><a name="TSQL"></a> Transact-SQL 사용  
  
### <a name="to-stop-a-job"></a>작업을 중지하려면  
  
1.  **개체 탐색기**에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)]인스턴스에 연결합니다.  
  
2.  표준 도구 모음에서 **새 쿼리**를 클릭합니다.  
  
3.  다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.  
  
    ```sql
    -- stops a job named Weekly Sales Data Backup  
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_stop_job  
        N'Weekly Sales Data Backup' ;  
    GO  
    ```  
  
 자세한 내용은 [sp_stop_job &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-stop-job-transact-sql)를 참조 하세요.  
  
##  <a name="using-sql-server-management-objects"></a><a name="SMO"></a>SQL Server 관리 개체 사용  

### <a name="to-stop-a-job"></a>작업을 중지하려면
  
 Visual Basic, Visual C#, PowerShell 등 선택한 프로그래밍 언어를 사용하여 `Stop` 클래스의 `Job` 메서드를 호출합니다. 자세한 내용은 [SMO(SQL Server 관리 개체)](https://msdn.microsoft.com/library/ms162169.aspx)를 참조하세요.  
