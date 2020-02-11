---
title: 열 단위 바인딩 | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- column-wise binding [ODBC]
- result sets [ODBC], binding columns
- binding columns [ODBC]
ms.assetid: 86d37637-3a25-455d-9c82-a0d7bff8d70d
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 6f91dca1ac20173f9c10b4a52adf292e7abc45d0
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68083379"
---
# <a name="column-wise-binding"></a>열 단위 바인딩
열 단위 바인딩을 사용 하는 경우 응용 프로그램은 데이터를 반환할 각 열에 하나 또는 두 개의 배열을 바인딩합니다. 첫 번째 배열에는 데이터 값이 포함 되 고 두 번째 배열에는 길이/표시기 버퍼가 포함 됩니다. SQL_DESC_INDICATOR_PTR 및 SQL_DESC_OCTET_LENGTH_PTR 설명자 필드를 서로 다른 값으로 설정 하 여 표시기 및 길이 값을 별도의 버퍼에 저장할 수 있습니다. 이 작업이 수행 되 면 세 번째 배열이 바인딩됩니다. 각 배열에는 행 집합의 행 수 만큼의 요소가 포함 되어 있습니다.  
  
 응용 프로그램은 매개 변수 집합 버퍼와는 달리 행 집합 버퍼의 바인딩 형식을 결정 하는 SQL_ATTR_ROW_BIND_TYPE statement 특성과 함께 열 단위 바인딩을 사용 한다고 선언 합니다. 드라이버는 각 배열의 연속 요소에 있는 각 행에 대 한 데이터를 반환 합니다. 다음 그림에서는 열 단위 바인딩의 작동 방식을 보여 줍니다.  
  
 ![열&#45;세 개의 열로 이루어진 바인딩](../../../odbc/reference/develop-app/media/pr21.gif "pr21")  
  
 예를 들어 다음 코드는 10 개의 요소 배열을 OrderID, 영업 사원 및 상태 열에 바인딩합니다.  
  
```  
#define ROW_ARRAY_SIZE 10  
  
SQLUINTEGER    OrderIDArray[ROW_ARRAY_SIZE], NumRowsFetched;  
SQLCHAR        SalesPersonArray[ROW_ARRAY_SIZE][11],  
               StatusArray[ROW_ARRAY_SIZE][7];  
SQLINTEGER     OrderIDIndArray[ROW_ARRAY_SIZE],  
               SalesPersonLenOrIndArray[ROW_ARRAY_SIZE],  
               StatusLenOrIndArray[ROW_ARRAY_SIZE];  
SQLUSMALLINT   RowStatusArray[ROW_ARRAY_SIZE], i;  
SQLRETURN      rc;  
SQLHSTMT       hstmt;  
  
// Set the SQL_ATTR_ROW_BIND_TYPE statement attribute to use  
// column-wise binding. Declare the rowset size with the  
// SQL_ATTR_ROW_ARRAY_SIZE statement attribute. Set the  
// SQL_ATTR_ROW_STATUS_PTR statement attribute to point to the  
// row status array. Set the SQL_ATTR_ROWS_FETCHED_PTR statement  
// attribute to point to cRowsFetched.  
SQLSetStmtAttr(hstmt, SQL_ATTR_ROW_BIND_TYPE, SQL_BIND_BY_COLUMN, 0);  
SQLSetStmtAttr(hstmt, SQL_ATTR_ROW_ARRAY_SIZE, ROW_ARRAY_SIZE, 0);  
SQLSetStmtAttr(hstmt, SQL_ATTR_ROW_STATUS_PTR, RowStatusArray, 0);  
SQLSetStmtAttr(hstmt, SQL_ATTR_ROWS_FETCHED_PTR, &NumRowsFetched, 0);  
  
// Bind arrays to the OrderID, SalesPerson, and Status columns.  
SQLBindCol(hstmt, 1, SQL_C_ULONG, OrderIDArray, 0, OrderIDIndArray);  
SQLBindCol(hstmt, 2, SQL_C_CHAR, SalesPersonArray, sizeof(SalesPersonArray[0]),  
            SalesPersonLenOrIndArray);  
SQLBindCol(hstmt, 3, SQL_C_CHAR, StatusArray, sizeof(StatusArray[0]),  
            StatusLenOrIndArray);  
  
// Execute a statement to retrieve rows from the Orders table.  
SQLExecDirect(hstmt, "SELECT OrderID, SalesPerson, Status FROM Orders", SQL_NTS);  
  
// Fetch up to the rowset size number of rows at a time. Print the actual  
// number of rows fetched; this number is returned in NumRowsFetched.  
// Check the row status array to print only those rows successfully  
// fetched. Code to check if rc equals SQL_SUCCESS_WITH_INFO or  
// SQL_ERROR not shown.  
while ((rc = SQLFetchScroll(hstmt,SQL_FETCH_NEXT,0)) != SQL_NO_DATA) {  
   for (i = 0; i < NumRowsFetched; i++) {  
      if ((RowStatusArray[i] == SQL_ROW_SUCCESS) ||  
            (RowStatusArray[i] == SQL_ROW_SUCCESS_WITH_INFO)) {  
         if (OrderIDIndArray[i] == SQL_NULL_DATA)  
            printf(" NULL      ");  
         else  
            printf("%d\t", OrderIDArray[i]);  
         if (SalesPersonLenOrIndArray[i] == SQL_NULL_DATA)  
            printf(" NULL      ");  
         else  
            printf("%s\t", SalesPersonArray[i]);  
         if (StatusLenOrIndArray[i] == SQL_NULL_DATA)  
            printf(" NULL\n");  
         else  
            printf("%s\n", StatusArray[i]);  
      }  
   }  
}  
  
// Close the cursor.  
SQLCloseCursor(hstmt);  
```
