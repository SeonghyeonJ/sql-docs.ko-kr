---
title: 여러 행 집합 결과를 생성하는 명령 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- multiple rowsets
- rowsets [OLE DB], multiple
- SQL Server Native Client OLE DB provider, commands
- SQL Server Native Client OLE DB provider, multiple rowsets
- commands [OLE DB]
- multiple-rowset results
ms.assetid: 4567668d-35fd-4162-b61f-f7536862cdcb
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 04a7db670171f6f890f55a89e2da987ef2309f0e
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/26/2020
ms.locfileid: "62657683"
---
# <a name="commands-generating-multiple-rowset-results"></a>여러 행 집합 결과를 생성하는 명령
  Native [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Client OLE DB 공급자는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 문에서 여러 행 집합을 반환할 수 있습니다. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 문은 다음과 같은 조건에서 여러 행 집합 결과를 반환합니다.  
  
-   일괄 처리되는 SQL 문이 단일 명령으로 제출된 경우  
  
-   저장 프로시저가 SQL 문의 일괄 처리를 구현하는 경우  
  
## <a name="batches"></a>Batch  
 Native [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Client OLE DB 공급자는 세미콜론 문자를 SQL 문에 대 한 일괄 처리 구분 기호로 인식 합니다.  
  
```  
WCHAR*       wSQLString = L"SELECT * FROM Categories; "  
                          L"SELECT * FROM Products";  
```  
  
 여러 SQL 문을 하나의 일괄 처리로 보내는 것이 각 SQL 문을 별도로 실행하는 것보다 효율적입니다. 하나의 일괄 처리를 보내는 경우 클라이언트에서 서버로의 네트워크 왕복 수가 줄어듭니다.  
  
## <a name="stored-procedures"></a>저장 프로시저  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]는 저장 프로시저의 각 문에 대해 하나의 결과 집합을 반환하므로 대부분의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 저장 프로시저는 여러 결과 집합을 반환합니다.  
  
## <a name="in-this-section"></a>섹션 내용  
  
-   [IMultipleResults를 사용하여 여러 결과 집합 처리](using-imultipleresults-to-process-multiple-result-sets.md)  
  
## <a name="see-also"></a>참고 항목  
 [명령](commands.md)  
  
  
