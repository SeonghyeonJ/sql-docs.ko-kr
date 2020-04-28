---
title: SQL Server PowerShell 경로 작업 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: scripting
ms.topic: conceptual
ms.assetid: f31d8e2c-8d59-4fee-ac2a-324668e54262
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 5ca7d915b940296e6de6689e666401b0c3534c9d
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/27/2020
ms.locfileid: "72782727"
---
# <a name="work-with-sql-server-powershell-paths"></a>SQL Server PowerShell 경로 작업
  [!INCLUDE[ssDE](../includes/ssde-md.md)] 공급자 경로의 노드로 이동한 후에는 노드에 연결된 [!INCLUDE[ssDE](../includes/ssde-md.md)] 관리 개체에서 메서드 및 속성을 사용하여 작업을 수행하거나 정보를 검색할 수 있습니다.  
  
1.  [시작하기 전에](#BeforeYouBegin)  
  
2.  **경로 노드에서 작업하려면**  [메서드 및 속성 나열](#ListPropMeth), [메서드 및 속성 사용](#UsePropMeth)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> 시작하기 전에  
 [!INCLUDE[ssDE](../includes/ssde-md.md)] 공급자 경로의 노드로 이동한 후에는 다음 두 가지 동작을 수행할 수 있습니다.  
  
-   **Rename-Item**과 같이 노드에서 작동하는 Windows PowerShell cmdlet을 실행할 수 있습니다.  
  
-   SMO와 같은 관련 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 관리 개체 모델에서 메서드를 호출할 수 있습니다. 예를 들어 경로에서 Databases 노드로 이동하는 경우 <xref:Microsoft.SqlServer.Management.Smo.Database> 클래스의 메서드와 속성을 사용할 수 있습니다.  
  
 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 공급자는 [!INCLUDE[ssDE](../includes/ssde-md.md)]인스턴스의 개체를 관리하는 데 사용됩니다. 데이터베이스의 데이터 작업에는 사용되지 않습니다. 테이블 또는 뷰로 이동한 경우에는 공급자를 사용하여 데이터에 대한 선택, 삽입, 업데이트 또는 삭제 작업을 수행할 수 없습니다. Windows PowerShell 환경에서 테이블 및 뷰의 데이터를 쿼리하거나 변경하려면 **Invoke-Sqlcmd** cmdlet을 사용하세요. 자세한 내용은 [Invoke-Sqlcmd cmdlet](../database-engine/invoke-sqlcmd-cmdlet.md)을 참조하세요.  
  
##  <a name="listing-methods-and-properties"></a><a name="ListPropMeth"></a>메서드 및 속성 나열
  
 특정 개체 또는 개체 클래스에 사용할 수 있는 메서드 및 속성을 보려면 **Get-Member** cmdlet을 사용합니다.  
  
### <a name="examples-listing-methods-and-properties"></a>예: 메서드 및 속성 나열  
 이 예에서는 Windows PowerShell 변수를 SMO <xref:Microsoft.SqlServer.Management.Smo.Database> 클래스로 설정하고 메서드 및 속성을 나열합니다.  
  
```powershell
$MyDBVar = New-Object Microsoft.SqlServer.Management.SMO.Database  
$MyDBVar | Get-Member -Type Methods  
$MyDBVar | Get-Member -Type Properties  
```  
  
 또한 **Get-Member** 를 사용하여 Windows PowerShell 경로의 끝 노드와 관련된 메서드 및 속성을 나열할 수 있습니다.  
  
 이 예에서는 SQLSERVER: 경로의 Databases 노드로 이동하고 컬렉션 속성을 나열합니다.  
  
```powershell
Set-Location SQLSERVER:\SQL\localhost\DEFAULT\Databases  
Get-Item . | Get-Member -Type Properties  
```  
  
 이 예에서는 SQLSERVER: 경로의 AdventureWorks2012 노드로 이동하고 개체 속성을 나열합니다.  
  
```powershell
Set-Location SQLSERVER:\SQL\localhost\DEFAULT\Databases\AdventureWorks2012  
Get-Item . | Get-Member -Type Properties  
```  
  
##  <a name="using-smo-methods-and-properties"></a><a name="UsePropMeth"></a>SMO 메서드 및 속성 사용  
  
 [!INCLUDE[ssDE](../includes/ssde-md.md)] 공급자 경로에서 개체에 대한 작업을 수행하려면 SMO 메서드 및 속성을 사용할 수 있습니다.  
  
### <a name="examples-using-methods-and-properties"></a>예: 메서드 및 속성 사용  
 이 예에서는 SMO **Schema** 속성을 사용하여 AdventureWorks2012의 Sales 스키마에서 테이블 목록을 가져옵니다.  
  
```powershell
Set-Location SQLSERVER:\SQL\localhost\DEFAULT\Databases\AdventureWorks2012\Tables  
Get-ChildItem | Where {$_.Schema -eq "Sales"}  
```  
  
 이 예에서는 SMO **script** 메서드를 사용 하 여 AdventureWorks2012에서 뷰를 `CREATE VIEW` 다시 만드는 데 필요한 문이 포함 된 스크립트를 생성 합니다.  
  
```powershell
Remove-Item C:\PowerShell\CreateViews.sql  
Set-Location SQLSERVER:\SQL\localhost\DEFAULT\Databases\AdventureWorks2012\Views  
foreach ($Item in Get-ChildItem) { $Item.Script() | Out-File -Filepath C:\PowerShell\CreateViews.sql -append }  
```  
  
 이 예에서는 SMO **Create** 메서드를 사용하여 데이터베이스를 만든 다음 **State** 속성을 사용하여 데이터베이스의 유무를 표시합니다.  
  
```powershell
Set-Location SQLSERVER:\SQL\localhost\DEFAULT\Databases  
$MyDBVar = New-Object Microsoft.SqlServer.Management.SMO.Database  
$MyDBVar.Parent = (Get-Item ..)  
$MyDBVar.Name = "NewDB"  
$MyDBVar.Create()  
$MyDBVar.State  
```  
  
## <a name="see-also"></a>참고 항목  
 [SQL Server PowerShell 공급자](sql-server-powershell-provider.md)   
 [SQL Server PowerShell 경로 탐색](navigate-sql-server-powershell-paths.md)   
 [Urn를 SQL Server 공급자 경로로 변환](../database-engine/convert-urns-to-sql-server-provider-paths.md)   
 [SQL Server PowerShell](sql-server-powershell.md)  
  
  
