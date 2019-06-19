---
title: 'C에서 SQL로: 연도-월 간격 | Microsoft Docs'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- converting data from c to SQL types [ODBC], year-month intervals
- intervals [ODBC], converting
- year-month intervals [ODBC]
- data conversions from C to SQL types [ODBC], year-month intervals
ms.assetid: a0eb7b55-9db0-4375-9210-bddec4593880
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d12727f9298eb63fe10b44c48b9d3b7996a839d5
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63159284"
---
# <a name="c-to-sql-year-month-intervals"></a>C에서 SQL로: 연-월 간격
년-월 간격 ODBC C 데이터 형식에 대 한 식별자 다음과 같습니다.  
  
 SQL_C_INTERVAL_MONTH SQL_C_INTERVAL_YEAR SQL_C_INTERVAL_YEAR_TO_MONTH  
  
 다음 표에서 ODBC SQL 데이터 형식은 연도-월 간격 C 데이터를 변환 될 수 있습니다를 보여 줍니다. 열과 테이블의 용어 설명은 참조 하세요 [C에서 SQL 데이터 형식으로 변환 데이터](../../../odbc/reference/appendixes/converting-data-from-c-to-sql-data-types.md)입니다.  
  
|SQL 유형 식별자|테스트|SQLSTATE|  
|-------------------------|----------|--------------|  
|SQL_CHAR[a]<br /><br /> SQL_VARCHAR[a]<br /><br /> SQL_LONGVARCHAR[a]|열의 바이트 길이 > = 문자 바이트 길이<br /><br /> 열의 바이트 길이 < 문자 바이트 길이 [a]<br /><br /> 데이터 값은 리터럴 유효한 간격이 아닙니다.|n/a<br /><br /> 22001<br /><br /> 22015|  
|SQL_WCHAR[a]<br /><br /> SQL_WVARCHAR[a]<br /><br /> SQL_WLONGVARCHAR[a]|열의 문자 길이 > 데이터의 문자 길이 =<br /><br /> 열의 문자 길이 < [a] 데이터의 길이 문자<br /><br /> 데이터 값은 리터럴 유효한 간격이 아닙니다.|n/a<br /><br /> 22001<br /><br /> 22015|  
|SQL_TINYINT[b]<br /><br /> SQL_SMALLINT[b]<br /><br /> SQL_INTEGER[b]<br /><br /> SQL_BIGINT[b]<br /><br /> SQL_NUMERIC[b]<br /><br /> SQL_DECIMAL[b]|변환 된 단일 필드 간격의 전체 자릿수는 잘림이 발생 하지<br /><br /> 변환 결과 전체 자릿수는 잘림이 발생 했습니다.|n/a<br /><br /> 22003|  
|SQL_INTERVAL_MONTH<br /><br /> SQL_INTERVAL_YEAR<br /><br /> SQL_INTERVAL_YEAR_TO_MONTH|필드의 잘림 없이 데이터 값이 변환 된<br /><br /> 변환 중 데이터 값의 하나 이상의 필드를 잘렸습니다.|n/a<br /><br /> 22015|  
  
 [a] 모든 C는 interval 데이터 형식은 문자 데이터 형식으로 변환할 수 있습니다.  
  
 [b] 이면 간격 구조에 유형 필드는 간격 (SQL_YEAR 또는 SQL_MONTH) 단일 필드는 같은 C 간격 유형으로 변환할 수 있는 정확한 숫자 (SQL_TINYINT, SQL_SMALLINT, SQL_INTEGER, SQL_BIGINT, SQL_DECIMAL, 또는 SQL_NUMERIC).  
  
 기본 C 형식 간격의 변환이 해당 연도-월 간격 SQL 형식입니다.  
  
 드라이버 C 간격 데이터 형식에서 데이터를 변환할 때 길이/표시기 값을 무시 하 고 데이터 버퍼의 크기가 C 간격 데이터 형식의 크기를 가정 합니다. 길이/표시기 값이 전달 합니다 *StrLen_or_Ind* 인수에 **SQLPutData** 에 지정 된 버퍼는 *StrLen_or_IndPtr* 에서인수**SQLBindParameter**합니다. 지정 된 데이터 버퍼를 *DataPtr* 에서 인수 **SQLPutData** 및 *ParameterValuePtr* 인수에서 **SQLBindParameter**.
