---
title: 작업 단계 로그 삭제 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- job steps [SQL Server Agent]
- deleting job step logs
- logs [SQL Server], jobs
- removing job step logs
ms.assetid: ee20c6cd-0258-4550-bdb0-71e86a0fb330
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: cd6cefd41ea223b91445042ff3cee9090074feeb
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2020
ms.locfileid: "72783190"
---
# <a name="delete-a-job-step-log"></a>Delete a Job Step Log
  이 항목에서는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 작업 단계 로그를 삭제하는 방법에 대해 설명합니다.  
  
-   **시작하기 전 주의 사항:**  
  
     [제한 사항](#Restrictions)  
  
     [보안](#Security)  
  
-   **다음을 사용 하 여 SQL Server 에이전트 작업 단계 로그를 삭제 합니다.**  
  
     [SQL Server Management Studio](#SSMS)  
  
     [Transact-SQL](#TSQL)  
  
     [SQL Server 관리 개체](#SMO)  
  
##  <a name="BeforeYouBegin"></a> 시작하기 전에  
  
###  <a name="Restrictions"></a> 제한 사항  
 작업 단계를 삭제하면 해당 출력 로그가 자동으로 삭제됩니다.  
  
###  <a name="Security"></a> 보안  
  
####  <a name="Permissions"></a> 권한  
 
  **sysadmin** 고정 서버 역할의 멤버가 아닌 경우 자신이 소유한 작업만 수정할 수 있습니다.  
  
##  <a name="SSMS"></a> SQL Server Management Studio 사용  
  
#### <a name="to-delete-a-sql-server-agent-job-step-log"></a>SQL Server 에이전트 작업 단계 로그를 삭제하려면  
  
1.  
  **개체 탐색기** 에서 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]의 인스턴스에 연결한 다음 해당 인스턴스를 확장합니다.  
  
2.  
  **SQL Server 에이전트**, **작업**을 차례로 확장한 다음 수정할 작업을 마우스 오른쪽 단추로 클릭하고 **속성**을 클릭합니다.  
  
3.  
  **작업 속성** 대화 상자에서 선택한 작업 단계를 삭제합니다.  
  
##  <a name="TSQL"></a> Transact-SQL 사용  
  
#### <a name="to-delete-a-sql-server-agent-job-step-log"></a>SQL Server 에이전트 작업 단계 로그를 삭제하려면  
  
1.  **개체 탐색기**에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)]인스턴스에 연결합니다.  
  
2.  표준 도구 모음에서 **새 쿼리**를 클릭합니다.  
  
3.  다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.  
  
    ```sql
    -- removes the job step log for step 2 in the job Weekly Sales Data Backup  
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_delete_jobsteplog  
        @job_name = N'Weekly Sales Data Backup',  
        @step_id = 2;  
    GO  
    ```  
  
 자세한 내용은 [sp_delete_jobsteplog &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-delete-jobsteplog-transact-sql)를 참조 하세요.  
  
##  <a name="SMO"></a>SQL Server 관리 개체 사용  
 Visual Basic, Visual C#, PowerShell 등 선택한 프로그래밍 언어를 사용하여 `DeleteJobStepLogs` 클래스의 `Job` 메서드를 사용합니다. 자세한 내용은[SMO(SQL Server 관리 개체)](https://msdn.microsoft.com/library/ms162169.aspx)를 참조하세요.  
  
```powershell
# Delete all job step log files that have ID values larger than 5.  
$srv = New-Object Microsoft.SqlServer.Management.Smo.Server("(local)")  
$jb = $srv.JobServer.Jobs["Test Job"]  
$jb.DeleteJobStepLogs(5)  
```
