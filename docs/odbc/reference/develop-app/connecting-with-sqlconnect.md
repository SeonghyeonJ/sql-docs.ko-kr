---
title: SQLConnect로 연결 | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data sources [ODBC], connection functions
- connecting to driver [ODBC], SQLConnect
- functions [ODBC], data source or driver connections
- SQLConnect function [ODBC], connecting
- connecting to data source [ODBC], SQLConnect
- connecting to data source [ODBC], functions
- connecting to driver [ODBC], functions
- connection functions [ODBC]
- ODBC drivers [ODBC], connection functions
ms.assetid: b16319d2-2c2c-4341-abb5-caa9e17362b4
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d89825bcfc9f885d4339874c870cbc5a29938062
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63042743"
---
# <a name="connecting-with-sqlconnect"></a>SQLConnect로 연결
**SQLConnect** 는 가장 단순한 연결 함수입니다. 데이터 원본 이름이 필요 하 고 선택적 사용자 ID 및 암호를 허용 합니다. 하드 코드는 데이터 원본 이름 및 사용자 ID 또는 암호가 필요 하지 않은 응용 프로그램에 대 한 잘 작동 합니다. 또한 하려는 응용 프로그램 제어 "모양 및 느낌" 자체 또는 사용자 인터페이스에 대해 잘 작동 합니다. 이러한 응용 프로그램에 사용 하 여 데이터 원본 목록을 빌드할 수 있습니다 **SQLDataSources**고, 데이터 원본, 사용자 ID와 암호를 묻는 메시지를 호출 하 **SQLConnect**합니다.  
  
 다음 예제에서는 northwind DSN을 사용 하 여 Northwind 데이터베이스에 연결 하 고 모든 직원 테이블의 레코드에서 모든 이름 및 성 필드를 검색 합니다.  
  
```  
// Connecting_with_SQLConnect.cpp  
// compile with: user32.lib odbc32.lib  
#include <windows.h>  
#include <sqlext.h>  
#include <mbstring.h>  
#include <stdio.h>  
  
#define MAX_DATA 100  
#define MYSQLSUCCESS(rc) ((rc == SQL_SUCCESS) || (rc == SQL_SUCCESS_WITH_INFO) )  
  
class direxec {  
   RETCODE rc; // ODBC return code  
   HENV henv; // Environment     
   HDBC hdbc; // Connection handle  
   HSTMT hstmt; // Statement handle  
  
   unsigned char szData[MAX_DATA]; // Returned data storage  
   SDWORD cbData; // Output length of data  
   unsigned char chr_ds_name[SQL_MAX_DSN_LENGTH]; // Data source name  
  
public:  
   direxec(); // Constructor  
   void sqlconn(); // Allocate env, stat, and conn  
   void sqlexec(unsigned char *); // Execute SQL statement  
   void sqldisconn(); // Free pointers to env, stat, conn, and disconnect  
   void error_out(); // Displays errors  
};  
  
// Constructor initializes the string chr_ds_name with the data source name.  
// "Northwind" is an ODBC data source (odbcad32.exe) name whose default is the Northwind database  
direxec::direxec() {  
   _mbscpy_s(chr_ds_name, SQL_MAX_DSN_LENGTH, (const unsigned char *)"Northwind");  
}  
  
// Allocate environment handle and connection handle, connect to data source, and allocate statement handle.  
void direxec::sqlconn() {  
   SQLAllocEnv(&henv);  
   SQLAllocConnect(henv, &hdbc);  
   rc = SQLConnect(hdbc, chr_ds_name, SQL_NTS, NULL, 0, NULL, 0);  
  
   // Deallocate handles, display error message, and exit.  
   if (!MYSQLSUCCESS(rc)) {  
      SQLFreeConnect(henv);  
      SQLFreeEnv(henv);  
      SQLFreeConnect(hdbc);  
      if (hstmt)  
         error_out();  
      exit(-1);  
   }  
  
   rc = SQLAllocStmt(hdbc, &hstmt);  
}  
  
// Execute SQL command with SQLExecDirect() ODBC API.  
void direxec::sqlexec(unsigned char * cmdstr) {  
   rc = SQLExecDirect(hstmt, cmdstr, SQL_NTS);  
   if (!MYSQLSUCCESS(rc)) {  //Error  
      error_out();  
      // Deallocate handles and disconnect.  
      SQLFreeStmt(hstmt,SQL_DROP);  
      SQLDisconnect(hdbc);  
      SQLFreeConnect(hdbc);  
      SQLFreeEnv(henv);  
      exit(-1);  
   }  
   else {  
      for ( rc = SQLFetch(hstmt) ; rc == SQL_SUCCESS ; rc=SQLFetch(hstmt) ) {  
         SQLGetData(hstmt, 1, SQL_C_CHAR, szData, sizeof(szData), &cbData);  
         // In this example, the data is sent to the console; SQLBindCol() could be called to bind   
         // individual rows of data and assign for a rowset.  
         printf("%s\n", (const char *)szData);  
      }  
   }  
}  
  
// Free the statement handle, disconnect, free the connection handle, and free the environment handle.  
void direxec::sqldisconn() {  
   SQLFreeStmt(hstmt,SQL_DROP);  
   SQLDisconnect(hdbc);  
   SQLFreeConnect(hdbc);  
   SQLFreeEnv(henv);  
}  
  
// Display error message in a message box that has an OK button.  
void direxec::error_out() {  
   unsigned char szSQLSTATE[10];  
   SDWORD nErr;  
   unsigned char msg[SQL_MAX_MESSAGE_LENGTH + 1];  
   SWORD cbmsg;  
  
   while (SQLError(0, 0, hstmt, szSQLSTATE, &nErr, msg, sizeof(msg), &cbmsg) == SQL_SUCCESS) {  
      sprintf_s((char *)szData, sizeof(szData), "Error:\nSQLSTATE=%s, Native error=%ld, msg='%s'", szSQLSTATE, nErr, msg);  
      MessageBox(NULL, (const char *)szData, "ODBC Error", MB_OK);  
   }  
}  
  
int main () {  
   direxec x;   // Declare an instance of the direxec object.  
   x.sqlconn();   // Allocate handles, and connect.  
   x.sqlexec((UCHAR FAR *)"SELECT FirstName, LastName FROM employees");   // Execute SQL command  
   x.sqldisconn();   // Free handles and disconnect  
}  
```
