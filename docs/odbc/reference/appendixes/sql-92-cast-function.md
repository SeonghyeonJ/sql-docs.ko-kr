---
title: SQL-92 CAST 함수 | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- functions [ODBC], SQL-92 functions
- SQL-92 functions [ODBC]
- CAST function [ODBC]
ms.assetid: 982f09e5-8205-41b9-98b3-8f898e24743f
author: MightyPen
ms.author: genemi
ms.openlocfilehash: c6682ae98f2da64f6936049bee96fe2fff2a84db
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68057063"
---
# <a name="sql-92-cast-function"></a>SQL-92 CAST 함수
**캐스트** SQL-92에 정의 된 함수는 동일 합니다 **변환** ODBC에 정의 된 함수입니다. 해당 함수의 구문은 다음과 같습니다.  
  
```  
{ fn CONVERT (value-exp, data-type) } /* ODBC  
CAST (value-exp AS data-type) /* SQL92  
```  
  
 SQL-92 **캐스트** 함수는 다른 데이터 형식으로 변환할 수 있는 데이터 형식을 규정 합니다. (자세한 내용은 SQL-92 사양 참조). 합니다 **캐스트** FIPS 전환 수준 함수는 지원 합니다.  
  
 응용 프로그램에 대 한 지원을 확인할 수 있습니다 합니다 **캐스트** 다음과 같이 작동 합니다.  
  
1.  호출 **SQLGetInfo** SQL_SQL_CONFORMANCE 정보 형식을 사용 하 여 합니다. 정보 유형에 대 한 반환 값이 SQL_SC_FIPS127_2_TRANSITIONAL, SQL_SC_SQL92_INTERMEDIATE, 또는 SQL_SC_SQL92_FULL, 합니다 **캐스트** 함수는 지원 합니다.  
  
2.  SQL_SQL_CONFORMANCE 정보 형식의 반환 값 SQL_SC_ENTRY_LEVEL 또는 0 이면 호출 **SQLGetInfo** SQL_SQL92_VALUE_EXPRESSIONS 정보 형식을 사용 하 여 합니다. SQL_SVE_CAST 비트가 설정 된 경우는 **캐스트** 함수는 지원 합니다.
