---
title: 'C: SQL 날짜-시간 간격 | Microsoft Docs'
ms.custom: ''
ms.date: 01/19/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- converting data from SQL to C types [ODBC], day-time intervals
- day-time intervals [ODBC]
- data conversions from SQL to C types [ODBC], day-time intervals
- intervals [ODBC], converting
ms.assetid: 8ea84d69-2292-4128-89a0-f184f68abb98
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ee08f42a4ccd7eb51f45e1654f20e264f80c49d2
ms.sourcegitcommit: 480961f14405dc0b096aa8009855dc5a2964f177
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/22/2019
ms.locfileid: "54420038"
---
# <a name="sql-to-c-day-time-intervals"></a>C: SQL 날짜-시간 간격

날짜-시간 간격 ODBC SQL 데이터 형식에 대 한 식별자는 다음과 같습니다.

- SQL_INTERVAL_DAY
- SQL_INTERVAL_DAY_TO_MINUTE
- SQL_INTERVAL_HOUR
- SQL_INTERVAL_DAY_TO_SECOND
- SQL_INTERVAL_MINUTE
- SQL_INTERVAL_HOUR_TO_MINUTE
- SQL_INTERVAL_SECOND
- SQL_INTERVAL_HOUR_TO_SECOND
- SQL_INTERVAL_DAY_TO_HOUR
- SQL_INTERVAL_MINUTE_TO_SECOND

다음 표에서 ODBC C 데이터 형식에는 날짜-시간 간격 SQL 데이터를 변환 될 수 있습니다를 보여 줍니다. 열과 테이블의 용어 설명은 참조 하세요 [SQL에서 C 데이터 형식으로 변환 데이터](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md)입니다.

|C 형식 식별자|테스트|**TargetValuePtr*|**StrLen_or_IndPtr*|SQLSTATE|  
|-----------------------|----------|------------------------|----------------------------|--------------|  
|모든 날짜-시간 C 간격 유형|잘리지 후행 필드 부분<br /><br /> 잘린 후행 필드 부분<br /><br /> 원본에서 데이터를 저장할 만큼 충분히 크지 않습니다 대상의 전체 자릿수를 유도|data<br /><br /> 잘린된 데이터<br /><br /> 정의되지 않음|데이터의 길이<br /><br /> 데이터의 길이<br /><br /> 정의되지 않음|n/a<br /><br /> 01S07<br /><br /> 22015|  
|SQL_C_STINYINT[b] SQL_C_UTINYINT[b] SQL_C_USHORT[b] SQL_C_SHORT[b] SQL_C_SLONG[b] SQL_C_ULONG[b] SQL_C_NUMERIC[b] SQL_C_BIGINT[b]|간격 정밀도 단일 필드 및 잘림 없이 데이터 변환 되었습니다.<br /><br /> 간격 정밀도 단일 필드를 되었으며 소수 잘림<br /><br /> 간격 정밀도 단일 필드 및 잘린 전체<br /><br /> 단일 필드 간격 정밀도가 없습니다.|data<br /><br /> 잘린된 데이터<br /><br /> 잘린된 데이터<br /><br /> 정의되지 않음|C 데이터 형식의 크기<br /><br /> 데이터의 길이<br /><br /> 데이터의 길이<br /><br /> C 데이터 형식의 크기|n/a<br /><br /> 01S07<br /><br /> 22003<br /><br /> 07006|  
|SQL_C_BINARY|데이터의 바이트 길이 < = *BufferLength*<br /><br /> 데이터의 바이트 길이 > *BufferLength*|data<br /><br /> 정의되지 않음|데이터의 길이<br /><br /> 정의되지 않음|n/a<br /><br /> 22003|  
|SQL_C_CHAR|문자 바이트 길이 < *BufferLength*<br /><br /> (소수) 달리 전체 자릿수 < *BufferLength*<br /><br /> (소수) 달리 전체 자릿수 > = *BufferLength*|data<br /><br /> 잘린된 데이터<br /><br /> 정의되지 않음|C 데이터 형식의 크기<br /><br /> C 데이터 형식의 크기<br /><br /> 정의되지 않음|n/a<br /><br /> 01004<br /><br /> 22003|  
|SQL_C_WCHAR|문자 길이 < *BufferLength*<br /><br /> (소수) 달리 전체 자릿수 < *BufferLength*<br /><br /> (소수) 달리 전체 자릿수 > = *BufferLength*|data<br /><br /> 잘린된 데이터<br /><br /> 정의되지 않음|C 데이터 형식의 크기<br /><br /> C 데이터 형식의 크기<br /><br /> 정의되지 않음|n/a<br /><br /> 01004<br /><br /> 22003|  
  
 SQL 형식 [a]는 날짜-시간 간격 날짜-시간 간격 C 형식으로 변환할 수 있습니다.  
  
 [b] 이면 간격 정밀도 (DAY, HOUR, MINUTE 또는 SECOND 중 하나) 단일 필드 간격 SQL 형식 (SQL_C_STINYINT, SQL_C_UTINYINT, SQL_C_USHORT, SQL_C_SHORT, SQL_C_SLONG, SQL_C_ULONG, 또는 SQL_C_NUMERIC)에 있는 정확한 숫자를 변환할 수 있습니다.  
  
기본 SQL 유형 간격의 변환이 해당 C 간격 데이터 형식입니다. 응용 프로그램이 다음 열 또는 매개 변수를 바인딩합니다 (또는 카드가의 적절 한 레코드에 SQL_DESC_DATA_PTR 필드가 설정) 초기화 SQL_INTERVAL_STRUCT 구조를 가리키도록 (합니다 로SQL_INTERVAL_STRUCT구조에대한포인터를전달하거나*TargetValuePtr* 호출에서 인수 **SQLGetData**).  
  
다음 예제에서는 DAY_TO_HOUR 간격으로 복구 되도록 SQL_INTERVAL_DAY_TO_MINUTE 형식의 열에서 데이터를 SQL_INTERVAL_STRUCT 구조로 전송 하는 방법에 설명 합니다.  

```cpp
SQL_INTERVAL_STRUCT is;  
SQLINTEGER    cbValue;  
SQLUINTEGER   days, hours;  
  
// Execute a select statement; "interval_column" is a column  
// whose data type is SQL_INTERVAL_DAY_TO_MINUTE.  
SQLExecDirect(hstmt, "SELECT interval_column FROM table", SQL_NTS);  
  
// Bind  
SQLBindCol(hstmt, 1, SQL_C_INTERVAL_DAY_TO_MINUTE, &is, sizeof(SQL_INTERVAL_STRUCT), &cbValue);  
  
// Fetch  
SQLFetch(hstmt);  
  
// Process data  
days = is.intval.day_second.day;  
hours = is.intval.day_second.hour;  
```
