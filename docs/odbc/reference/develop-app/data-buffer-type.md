---
title: 데이터 버퍼 유형 | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data types [ODBC], buffers
- data buffers [ODBC], types
- buffers [ODBC], data
- C data types [ODBC], buffers
ms.assetid: 58bea3e9-d552-447f-b3ad-ce1dab213b72
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7e02d42d6d63608ccb70dc984e05ae11578d3160
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/28/2018
ms.locfileid: "52528859"
---
# <a name="data-buffer-type"></a>데이터 버퍼 형식
응용 프로그램에서 버퍼의 C 데이터 형식 지정 됩니다. 단일 변수를 사용 하 여이 경우 응용 프로그램 변수를 할당 합니다. 제네릭 메모리-,-void 형식의 포인터가 가리키는 메모리 경우가이 응용 프로그램 메모리를 특정 형식으로 캐스팅 합니다. 드라이버에는이 이와 같은 두 가지 방법으로 검색합니다.  
  
-   **데이터 버퍼 형식 인수입니다.** 사용 하 여 바인딩된 버퍼와 같은 매개 변수 값 및 결과 집합 데이터를 전송 하는 데 사용 되는 버퍼 *TargetValuePtr* 에 **SQLBindCol**, 같은 연결 된 형식 인수를가지고  *TargetType* 에 인수 **SQLBindCol**합니다. 이 인수를 응용 프로그램 버퍼 형식에 해당 하는 C 형식 식별자를 전달 합니다. 예를 들어, 다음에서에 호출할 **SQLBindCol**, SQL_C_TYPE_DATE 값 드라이버 지시 하는 합니다 *날짜* 버퍼가 SQL_DATE_STRUCT를:  
  
    ```  
    SQL_DATE_STRUCT Date;  
    SQLINTEGER  DateInd;  
    SQLBindCol(hstmt, 1, SQL_C_TYPE_DATE, &Date, 0, &DateInd);  
    ```  
  
     형식 식별자에 대 한 자세한 내용은 참조는 [ODBC의 데이터 형식](../../../odbc/reference/develop-app/data-types-in-odbc.md) 이 섹션의 뒷부분에 나오는 섹션입니다.  
  
-   **미리 정의 된 형식입니다.** 가리키는 버퍼를 보내고 옵션 또는 버퍼와 같은 특성을 검색 하는 데 사용 합니다 *InfoValuePtr* 에서 인수 **SQLGetInfo**, 고정 형식이 지정 된 옵션에 따라 달라 집니다. 드라이버는이 형식의 데이터 버퍼는 가정 합니다. 이러한 종류의 버퍼를 할당 해야 하는 응용 프로그램의 경우 예를 들어, 다음에서에 호출 **SQLGetInfo**, 드라이버 SQL_STRING_FUNCTIONS 옵션의 요구 사항 이므로 버퍼는 32 비트 정수를 가정 합니다.  
  
    ```  
    SQLUINTEGER StringFuncs;  
    SQLGetInfo(hdbc, SQL_STRING_FUNCTIONS, (SQLPOINTER) &StringFuncs, 0,  
                NULL);  
    ```  
  
 버퍼의 데이터를 해석 하는 C 데이터 형식을 사용 하는 드라이버.
