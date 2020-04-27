---
title: SQL Server 식별자 이스케이프 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: scripting
ms.topic: conceptual
ms.assetid: 8a73e945-daa6-4e5d-93da-10f000f1f3a2
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 17196f4e9a6deaadca09e77e94e2cf393f4af237
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/26/2020
ms.locfileid: "62922899"
---
# <a name="escape-sql-server-identifiers"></a>SQL Server 식별자 이스케이프
  Windows PowerShell 역따옴표 이스케이프 문자(`)를 사용하여 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 구분 식별자에는 허용되고 Windows PowerShell 경로 이름에는 허용되지 않는 문자를 이스케이프 처리할 수도 있습니다. 하지만 이스케이프 처리되지 않는 문자도 있습니다. 예를 들어 Windows PowerShell에서 콜론 문자(:)는 이스케이프 처리할 수 없습니다. 해당 문자가 포함된 식별자는 인코딩해야 합니다. 인코딩은 모든 문자에 대해 작동하므로 이스케이프 처리보다 안정적입니다.  
  
## <a name="before-you-begin"></a>시작하기 전에  
 역따옴표 문자(`) 키는 일반적으로 키보드 왼쪽 위에서 ESC 키 아래에 있습니다.  
  
## <a name="examples"></a>예  
 다음은 # 문자를 이스케이프 처리하는 예입니다.  
  
```  
cd SQLSERVER:\SQL\MyComputer\MyInstance\MyDatabase\MySchema\`#MyTempTable  
```  
  
 다음은 (local)을 컴퓨터 이름으로 지정하는 경우 괄호를 이스케이프 처리하는 예입니다.  
  
```  
Set-Location SQLSERVER:\SQL\`(local`)\DEFAULT  
```  
  
## <a name="see-also"></a>참고 항목  
 [PowerShell에서 SQL Server 식별자](sql-server-identifiers-in-powershell.md)   
 [SQL Server PowerShell 공급자](sql-server-powershell-provider.md)   
 [SQL Server PowerShell](sql-server-powershell.md)  
  
  
