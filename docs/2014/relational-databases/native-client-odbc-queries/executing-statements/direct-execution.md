---
title: 직접 실행 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- ODBC applications, statements
- direct execution [ODBC]
- SQLExecDirect function
- statements [ODBC], direct execution
ms.assetid: fa36e1af-ed98-4abc-97c1-c4cc5d227b29
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 4e912ac2dd63fa63ce57647f0c4e95e6702a22ed
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/15/2019
ms.locfileid: "68207073"
---
# <a name="direct-execution"></a>직접 실행
  직접 실행은 가장 기본적인 문 실행 방법입니다. 응용 프로그램 빌드에 포함 된 문자열을 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 문을 사용 하 여 실행에 대 한 전송 및 합니다 **SQLExecDirect** 함수입니다. 서버에서 문이 수신되면 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]가 문을 실행 계획으로 컴파일한 다음 실행 계획을 즉시 실행합니다.  
  
 직접 실행은 런타임에 문을 작성하고 실행하는 응용 프로그램에 많이 사용되며, 한 번 실행되는 문에 가장 효율적인 실행 방법입니다. 반면 실행할 때마다 SQL 문을 구문 분석하고 컴파일해야 하기 때문에 문을 여러 번 실행하는 경우 오버헤드가 증가한다는 점이 많은 데이터베이스에서 단점이 됩니다.  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]에서는 다중 사용자 환경에서 자주 실행되는 문의 직접 실행 성능이 크게 향상되었으며, 자주 실행되는 SQL 문에 대한 매개 변수 표식과 SQLExecDirect를 함께 사용하여 준비된 실행의 효율성을 높일 수 있습니다.  
  
 인스턴스에 연결할 때 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC 드라이버를 사용 하 여 [sp_executesql](/sql/relational-databases/system-stored-procedures/sp-executesql-transact-sql) SQL 문 또는 일괄 처리에 지정 된 전송할 **SQLExecDirect**합니다. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 신속 하 게 하는 경우 SQL 문을 확인 하기 위한 논리가 했거나이 사용 하 여 일괄 처리 실행 **sp_executesql** 문 또는 메모리에 이미 존재 하는 실행 계획을 생성 하는 일괄 처리와 일치 합니다. 일치하는 경우 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]는 새 계획을 컴파일하는 대신 기존 계획을 다시 사용합니다. 이 즉, 일반적으로 사용 하 여 실행 하는 SQL 문을 실행할 **SQLExecDirect** 여러 사용자가 있는 시스템에서 이익을 많은 저장 프로시저 의이전버전에서사용할수있는계획다시사용혜택[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 실행 계획을 다시 사용하는 데 따른 이러한 이점은 여러 사용자가 동일한 SQL 문 또는 일괄 처리를 실행하는 경우에만 얻을 수 있습니다. 여러 클라이언트에서 실행되는 SQL 문에서 실행 계획의 다시 사용 가능성을 높이려면 다음 코딩 규칙을 따르십시오.  
  
-   SQL 문에 데이터 상수를 포함하지 않습니다. 대신 프로그램 변수에 바인딩된 매개 변수 표식을 사용합니다. 자세한 내용은 [문 매개 변수를 사용 하 여](../using-statement-parameters.md)입니다.  
  
-   정규화된 개체 이름을 사용합니다. 개체 이름이 정규화되어 있지 않으면 실행 계획이 다시 사용되지 않습니다.  
  
-   응용 프로그램 연결에 공통 연결 및 문 옵션을 사용할 수 있도록 합니다. 하나의 옵션 집합(예: ANSI_NULLS)을 사용하는 연결에 대해 생성되는 실행 계획은 다른 옵션 집합이 추가로 사용된 연결에 다시 사용되지 않습니다. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC 드라이버와 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB 공급자는 이러한 옵션에 대한 기본 설정이 동일합니다.  
  
 모든 문을 실행 하는 경우 **SQLExecDirect** 은 이러한 규칙을 사용 하 여 코딩 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 에서 기회가 있을 때 실행 계획을 재사용할 수 있습니다.  
  
## <a name="see-also"></a>관련 항목  
 [문 실행 &#40;ODBC&#41;](executing-statements-odbc.md)  
  
  
