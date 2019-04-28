---
title: SQL 적합성 수준 | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- conformance levels [ODBC], SQL
- SQL conformance levels [ODBC]
- data sources [ODBC], conformance levels
- ODBC drivers [ODBC], conformance levels
ms.assetid: 3529df2c-a09b-4c16-9c60-eae7a06d903a
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c2e8ce5aeeb94a4f7a33b22054adc8067e0654ac
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62690203"
---
# <a name="sql-conformance-levels"></a>SQL 적합성 수준
드라이버에서 지 원하는 SQL-92 문법의 수준에 대 한 호출에서 반환한 값으로 표시 됩니다 **SQLGetInfo** SQL_SQL_CONFORMANCE 정보 형식을 사용 하 여 합니다. SQL-92에 정의 된 항목, FIPS 전환, 중간 또는 전체 수준으로 드라이버를 준수 하는지 여부를 나타냅니다.  
  
 모든 ODBC 드라이버에 설명 된 최소 SQL 문법을 지원 해야 합니다 [SQL 최소 문법](../../../odbc/reference/appendixes/sql-minimum-grammar.md) 부록 c: SQL 문법입니다. 이 문법에는 SQL-92 항목 수준의 일부입니다. 드라이버는 추가 SQL을 지원 하 고와 호환 되는 SQL-92 항목, 중간 또는 전체 수준 또는 FIPS 127-2 전환 수준 수 수 있습니다. 지정된 된 수준의 SQL-92 또는 FIPS 127-2를 준수 하는 드라이버의 더 높은 수준에서 추가 기능을 지원 하면서 완전히 해당 수준에 부합 되지 수 있습니다. 기능이 지원 되는지 여부를 확인 하려면 응용 프로그램 호출 해야 **SQLGetInfo** 적절 한 정보 형식을 사용 하 여 합니다. SQL 기능을의 규칙 수준은 해당 정보 유형을 설명 합니다. (참조를 [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md) 함수 설명 합니다.)
