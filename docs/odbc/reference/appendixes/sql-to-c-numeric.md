---
title: 'SQL에서 C로: 숫자 | Microsoft Docs'
ms.custom: ''
ms.date: 01/19/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data conversions from SQL to C types [ODBC], numeric
- numeric data type [ODBC], converting
- converting data from SQL to C types [ODBC], numeric
ms.assetid: 76f8b5d5-4bd0-4dcb-a90a-698340e0d36e
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9abd536110222f8e30a781b6d648402335837f61
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63151285"
---
# <a name="sql-to-c-numeric"></a>SQL에서 C로: 숫자

숫자 ODBC SQL 데이터 형식에 대 한 식별자는 다음과 같습니다.

- SQL_DECIMAL  
- SQL_BIGINT  
- SQL_NUMERIC  
- SQL_REAL  
- SQL_TINYINT  
- SQL_FLOAT  
- SQL_SMALLINT  
- SQL_DOUBLE SQL_INTEGER  

다음 표에서 ODBC C 데이터 형식에는 숫자 SQL 데이터를 변환 될 수 있습니다를 보여 줍니다. 열과 테이블의 용어 설명은 참조 하세요 [SQL에서 C 데이터 형식으로 변환 데이터](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md)입니다.  

|C 형식 식별자|테스트|**TargetValuePtr*|**StrLen_or_IndPtr*|SQLSTATE|  
|-----------------------|----------|------------------------|----------------------------|--------------|  
|SQL_C_CHAR|문자 바이트 길이 < *BufferLength*<br /><br /> (소수) 달리 전체 자릿수 < *BufferLength*<br /><br /> (소수) 달리 전체 자릿수 > = *BufferLength*|data<br /><br /> 잘린된 데이터<br /><br /> 정의되지 않음|데이터의 바이트 길이<br /><br /> 데이터의 바이트 길이<br /><br /> 정의되지 않음|n/a<br /><br /> 01004<br /><br /> 22003|  
|SQL_C_WCHAR|문자 길이 < *BufferLength*<br /><br /> (소수) 달리 전체 자릿수 < *BufferLength*<br /><br /> (소수) 달리 전체 자릿수 > = *BufferLength*|data<br /><br /> 잘린된 데이터<br /><br /> 정의되지 않음|문자에서 데이터의 길이<br /><br /> 문자에서 데이터의 길이<br /><br /> 정의되지 않음|n/a<br /><br /> 01004<br /><br /> 22003|  
|SQL_C_STINYINT<br /><br /> SQL_C_UTINYINT<br /><br /> SQL_C_TINYINT<br /><br /> SQL_C_SBIGINT<br /><br /> SQL_C_UBIGINT<br /><br /> SQL_C_SSHORT<br /><br /> SQL_C_USHORT<br /><br /> SQL_C_SHORT<br /><br /> SQL_C_SLONG<br /><br /> SQL_C_ULONG<br /><br /> SQL_C_LONG<br /><br /> SQL_C_NUMERIC|[A] 잘림 없이 데이터 변환<br /><br /> 데이터 잘림 [a] 소수 자릿수를 사용 하 여 변환<br /><br /> 데이터 변환 [a] (소수) 달리 전체 자릿수 손실을 초래|data<br /><br /> 잘린된 데이터<br /><br /> 정의되지 않음|C 데이터 형식의 크기<br /><br /> C 데이터 형식의 크기<br /><br /> 정의되지 않음|n/a<br /><br /> 01S07<br /><br /> 22003|  
|SQL_C_FLOAT<br /><br /> SQL_C_DOUBLE|데이터가 숫자를 변환 하는 데이터 형식의 범위 내에서 [a]<br /><br /> 데이터 숫자를 변환 하는 데이터 형식의 범위를 벗어났습니다 [a]|data<br /><br /> 정의되지 않음|C 데이터 형식의 크기<br /><br /> 정의되지 않음|n/a<br /><br /> 22003|  
|SQL_C_BIT|데이터는 0 또는 1 [a]<br /><br /> 데이터 0, 2, 보다 작음 및 같지 않음 [a] 1 보다 큽니다.<br /><br /> 0 보다 작거나 또는 [a] 2 보다 크거나 데이터가|data<br /><br /> 잘린된 데이터<br /><br /> 정의되지 않음|1[b]<br /><br /> 1[b]<br /><br /> 정의되지 않음|n/a<br /><br /> 01S07<br /><br /> 22003|  
|SQL_C_BINARY|데이터의 바이트 길이 < = *BufferLength*<br /><br /> 데이터의 바이트 길이 > *BufferLength*|data<br /><br /> 정의되지 않음|데이터의 길이<br /><br /> 정의되지 않음|n/a<br /><br /> 22003|  
|SQL_C_INTERVAL_MONTH[c] SQL_C_INTERVAL_YEAR[c] SQL_C_INTERVAL_DAY[c] SQL_C_INTERVAL_HOUR[c] SQL_C_INTERVAL_MINUTE[c] SQL_C_INTERVAL_SECOND[c]|잘리지 데이터<br /><br /> 잘린 초 소수 부분<br /><br /> 잘릴 숫자의 정수 부분|data<br /><br /> 잘린된 데이터<br /><br /> 정의되지 않음|데이터의 바이트 길이<br /><br /> 데이터의 바이트 길이<br /><br /> 정의되지 않음|n/a<br /><br /> 01S07<br /><br /> 22015|  
|SQL_C_INTERVAL_YEAR_TO_MONTH SQL_C_INTERVAL_DAY_TO_HOUR SQL_C_INTERVAL_DAY_TO_MINUTE SQL_C_INTERVAL_DAY_TO_SECOND SQL_C_INTERVAL_HOUR_TO_MINUTE SQL_C_INTERVAL_HOUR_TO_SECOND|잘릴 숫자의 정수 부분|정의되지 않음|정의되지 않음|22015|  
  
 [a] 값 *BufferLength* 이 변환에 대해 무시 됩니다. 드라이버 가정 크기 **TargetValuePtr* C 데이터 형식의 크기입니다.  
  
 [b] C 데이터 형식에 해당 크기입니다.  
  
 [이 변환 c]이 정확한 숫자 데이터 형식 (SQL_DECIMAL, SQL_NUMERIC, SQL_TINYINT, SQL_SMALLINT, SQL_INTEGER, 및 SQL_BIGINT)에 대해서만 지원 됩니다. (SQL_REAL, SQL_FLOAT, 또는 SQL_DOUBLE) 근사치 데이터 형식에 대 한 지원 되지 않습니다.  

## <a name="sqlcnumeric-and-sqlsetdescfield"></a>SQL_C_NUMERIC 및 SQLSetDescField

 합니다 [SQLSetDescField 함수](../../../odbc/reference/syntax/sqlsetdescfield-function.md) SQL_C_NUMERIC 값을 사용 하 여 수동 바인딩을 수행 해야 합니다. (ODBC 3.0에서 SQLSetDescField가 추가 되었는지 참고). 수동 바인딩으로 수행 하려면 먼저 설명자 핸들을 가져와야 합니다.  

```cpp
if (fCType == SQL_C_NUMERIC) {   
   // special processing required for NUMERIC to get right scale & precision  
   // Modify the fields in the implicit application parameter descriptor  
   SQLHDESC hdesc=NULL;  
  
   // Use SQL_ATTR_APP_ROW_DESC for calls to SQLBindCol()  
   // Use SQL_ATTR_APP_PARAM_DESC for calls to SQLBindParameter()  
   //  
   // retcode = SQLGetStmtAttr(hstmt, SQL_ATTR_APP_ROW_DESC, &hdesc, 0, NULL);  
   retcode = SQLGetStmtAttr(hstmt, SQL_ATTR_APP_PARAM_DESC, &hdesc, 0, NULL);  
   if (!ODBC_CALL_SUCCESS(retcode)) {  
      printf ("\nSQLGetStmtAttr failed");  
      i = 1;  
      sqlstate[7] = '\0';  
      while (SQLGetDiagRec(SQL_HANDLE_STMT, hstmt, i, sqlstate, &NativeError, wrkbuf, sizeof(wrkbuf), &len) != SQL_NO_DATA) {  
         printf("\niTestCase = %d Failed...Precision = %d, Scale = %d\nNativeError=%d, State=%s, \n  Message=%s",   
            iTestCase, Precision, Scale, NativeError, sqlstate, wrkbuf);  
         i++;  
      }  
      continue;  
   }  
   retcode = SQLSetDescField(hdesc, iCol, SQL_DESC_TYPE, (SQLPOINTER) SQL_C_NUMERIC, 0);  
   if (!ODBC_CALL_SUCCESS(retcode))  
      goto error;  
   retcode = SQLSetDescField(hdesc, iCol, SQL_DESC_PRECISION, (SQLPOINTER)num.precision, 0);  
   if (!ODBC_CALL_SUCCESS(retcode))  
      goto error;  
   retcode = SQLSetDescField(hdesc, iCol, SQL_DESC_SCALE, (SQLPOINTER)num.scale, 0);  
   if (!ODBC_CALL_SUCCESS(retcode))  
      goto error;  
   retcode = SQLSetDescField(hdesc, iCol, SQL_DESC_DATA_PTR, (SQLPOINTER) &(num), sizeof(num));  
```
