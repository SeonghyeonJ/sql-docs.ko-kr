---
title: Paradox 데이터 형식 | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC desktop database drivers [ODBC], Paradox driver
- desktop database drivers [ODBC], Paradox driver
- Paradox data types [ODBC]
- Jet-based ODBC drivers [ODBC], Paradox driver
- data types [ODBC], Paradox driver
- Paradox driver [ODBC], data types
ms.assetid: 0c9e5d21-9321-49f8-a055-69459e1c9c85
author: MightyPen
ms.author: genemi
ms.openlocfilehash: e8478e80ae2ebd19a3e0f2aa8307e0985b2c092d
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68043695"
---
# <a name="paradox-data-types"></a>Paradox 데이터 형식
ODBC Paradox 드라이버 Paradox 데이터 형식을 ODBC SQL 데이터 형식을 매핑합니다. 다음 표에서 모든 Paradox 데이터 형식을 나열 하 고 ODBC SQL 데이터 형식에 매핑되는지를 보여 줍니다.  
  
|Paradox 데이터 형식|ODBC 데이터 형식|  
|-----------------------|--------------------|  
|ALPHANUMERIC|SQL_VARCHAR|  
|AUTOINCREMENT [1]|SQL_INTEGER|  
|BCD[1]|SQL_DOUBLE|  
|바이트 [1]|SQL_BINARY|  
|DATE|SQL_DATE|  
|IMAGE[2]|SQL_LONGVARBINARY|  
|논리 [1]|SQL_BIT|  
|장기 [1]|SQL_INTEGER|  
|[2] 메모|SQL_LONGVARCHAR|  
|MONEY [1]|SQL_DOUBLE|  
|NUMBER|SQL_DOUBLE|  
|짧은|SQL_SMALLINT|  
|시간 [1]|SQL_TIMESTAMP|  
|TIMESTAMP[1]|SQL_TIMESTAMP|  
  
 Paradox 버전 5에만 유효 [1]입니다. *x*합니다.  
  
 Paradox 버전 4에 대해서만 유효 [2]. *x* 5. *x*합니다.  
  
> [!NOTE]  
>  **SQLGetTypeInfo** ODBC SQL 데이터 형식을 반환 합니다. 부록 D의 모든 변환 합니다 *ODBC 프로그래머 참조* 이 항목의 앞부분에 나열 된 ODBC SQL 데이터 형식에 대해 지원 됩니다.  
  
 다음 표에서 Paradox 데이터 형식의 제한 사항 보여 줍니다.  
  
|데이터 형식|설명|  
|---------------|-----------------|  
|ALPHANUMERIC|0의 영숫자 열 만들기 또는 실제로 지정 되지 않은 길이 255 바이트 열을 반환 합니다.|  
|BYTES|Paradox5 드라이버를 사용 하 여 이진 열에 NULL을 삽입 하면 0으로 변경 됩니다.|  
|LONG|Paradox 5의 Long 데이터 형식에 대해 Paradox 드라이버에서 지 원하는 최대 음수 값입니다. *x* 아닙니다-2 ^31 (-2147483648), ODBC 데이터에 긴 매핑됩니다 이후 것 처럼 입력 SQL_INTEGER 합니다. 장기에 대 한 지원 되는 최대 음수 값은 실제로-2 ^31 + 1 (-2147483647).|  
|timestamp|값은 Paradox 드라이버에 의해 타임 스탬프 열에 삽입 한 다음 이후에 열에서 검색 하는 경우 검색된 된 값 따라 다를 수 삽입된 된 값에서 1 초 만큼 반올림으로 인해 합니다.|  
  
 데이터 형식에 대 한 자세한 제한에서 찾을 수 있습니다 [데이터 형식 제한 사항](../../odbc/microsoft/data-type-limitations.md)합니다.
