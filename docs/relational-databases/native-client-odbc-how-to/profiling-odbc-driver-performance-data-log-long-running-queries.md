---
title: 장기 실행 쿼리 로그(ODBC) | 마이크로 소프트 문서
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- queries [ODBC]
ms.assetid: b9c1ddce-1dd9-409d-a414-8b544d616273
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: d1e931a24462711a742b8008eb04538e0e518d55
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305379"
---
# <a name="profiling-odbc-driver-performance-data---log-long-running-queries"></a>ODBC 드라이버 성능 데이터 프로파일링 - 장기 실행 쿼리 기록
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  이 예제에서는 장기 실행 쿼리를 로깅하기 위한 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ODBC 드라이버 관련 옵션을 보여 줍니다. 이 예제를 실행할 경우 애플리케이션에서 설정한 간격을 초과하여 실행되는 쿼리 목록이 포함된 Odbcqry.log가 만들어집니다. 이 예제는 IA64에서 지원되지 않습니다. 이 예제는 ODBC 버전 3.0 이상용으로 개발되었습니다.  
  
> [!IMPORTANT]  
>  가능하면 Windows 인증을 사용하세요. Windows 인증을 사용할 수 없으면 런타임에 사용자에게 자격 증명을 입력하라는 메시지를 표시합니다. 자격 증명은 파일에 저장하지 않는 것이 좋습니다. 자격 증명을 유지해야 하는 경우 [Win32 암호화 API를](https://go.microsoft.com/fwlink/?LinkId=64532)통해 자격 증명을 암호화해야 합니다.  
  
### <a name="to-log-long-running-queries-using-odbc-administrator"></a>ODBC 관리자를 사용하여 장기 실행 쿼리를 기록하려면  
  
1.  **제어판에서** **관리 도구를** 두 번 클릭한 다음 **ODBC(데이터 원본)를**두 번 클릭합니다. 또는 명령 프롬프트에서 odbcad32.exe를 실행할 수도 있습니다.  
  
2.  사용자 **DSN,** **시스템 DSN**또는 **파일 DSN 탭을** 클릭합니다.  
  
3.  장기 실행 쿼리를 기록할 데이터 원본을 클릭합니다.  
  
4.  **구성**을 클릭합니다.  
  
5.  Microsoft SQL Server 구성 DSN 마법사에서 **로그 파일에 장기 실행 쿼리 저장을 사용하여 페이지로**이동합니다.  
  
6.  **로그 파일에 장기 실행 쿼리 저장을 선택합니다.** 상자에서 장기 실행 쿼리를 기록할 파일 이름을 입력합니다. 선택적으로 **찾아보기를** 클릭하여 쿼리 로그에 대한 파일 시스템을 찾아봅을 클릭합니다.  
  
7.  **긴 쿼리 시간(밀리초)** 상자에서 쿼리 시간 시간 간격을 밀리초 단위로 설정합니다.  

### <a name="to-log-long-running-queries-data-programmatically"></a>장기 실행 쿼리 데이터를 프로그래밍 방식으로 기록하려면  
  
1.  [SQLSetConnectAttr에](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md) SQL_COPT_SS_PERF_QUERY_LOG 장기 실행 쿼리 로그 파일의 전체 경로 및 파일 이름을 호출합니다. 다음은 그 예입니다.  
  
    ```  
    C:\\Odbcqry.log  
    ```  
  
2.  [SQL_COPT_SS_PERF_QUERY_INTERVAL 사용하여 SQLSetConnectAttr을](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md) 호출하고 시간 시간 간격으로 밀리초 단위로 설정합니다.  
  
3.  [SQLSetConnectAttr에](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md) SQL_COPT_SS_PERF_QUERY 호출하고 SQL_PERF_START 장기 실행 쿼리로 로깅을 시작합니다.  
  
4.  SQL_COPT_SS_PERF_QUERY 및 SQL_PERF_STOP 사용하여 [SQLSetConnectAttr에](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md) 호출하여 장기 실행 쿼리로 의한 로깅을 중지합니다.  
  
## <a name="example"></a>예제  
 AdventureWorks 예제 데이터베이스를 기본 데이터베이스로 사용하는 AdventureWorks라는 ODBC 데이터 원본이 필요합니다. [(Microsoft SQL Server](https://go.microsoft.com/fwlink/?LinkID=85384) 샘플 및 커뮤니티 프로젝트 홈 페이지에서 AdventureWorks 샘플 데이터베이스를 다운로드할 수 있습니다.) 이 데이터 원본은 운영 체제에서 제공하는 ODBC 드라이버를 기반으로 해야 합니다(드라이버 이름은 "SQL Server"). 이 예제를 64비트 운영 체제에서 32비트 애플리케이션으로 작성하여 실행하려는 경우 %windir%\SysWOW64\odbcad32.exe에서 ODBC 관리자를 사용하여 ODBC 데이터 원본을 만들어야 합니다.  
  
 이 예제는 컴퓨터의 기본 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스에 연결됩니다. 명명된 인스턴스에 연결하려면 ODBC 데이터 원본의 정의를 변경하여 server\namedinstance 형식으로 인스턴스를 지정합니다. 기본적으로 [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] 는 명명된 인스턴스에 설치됩니다.  
  
 odbc32.lib를 사용하여 컴파일합니다.  
  
```  
// compile with: odbc32.lib  
#include <stdio.h>  
#include <string.h>  
#include <windows.h>  
#include <sql.h>  
#include <sqlext.h>  
#include <odbcss.h>  
  
SQLHENV henv = SQL_NULL_HENV;  
SQLHDBC hdbc1 = SQL_NULL_HDBC;       
SQLHSTMT hstmt1 = SQL_NULL_HSTMT;  
  
void Cleanup() {  
   if (hstmt1 != SQL_NULL_HSTMT)  
      SQLFreeHandle(SQL_HANDLE_STMT, hstmt1);  
  
   if (hdbc1 != SQL_NULL_HDBC) {  
      SQLDisconnect(hdbc1);  
      SQLFreeHandle(SQL_HANDLE_DBC, hdbc1);  
   }  
  
   if (henv != SQL_NULL_HENV)  
      SQLFreeHandle(SQL_HANDLE_ENV, henv);  
}  
  
int main() {  
   RETCODE retcode;  
  
   // Allocate the ODBC environment and save handle.  
   retcode = SQLAllocHandle (SQL_HANDLE_ENV, NULL, &henv);  
   if ( (retcode != SQL_SUCCESS_WITH_INFO) && (retcode != SQL_SUCCESS)) {  
      printf("SQLAllocHandle(Env) Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Notify ODBC that this is an ODBC 3.0 app.  
   retcode = SQLSetEnvAttr(henv, SQL_ATTR_ODBC_VERSION, (SQLPOINTER) SQL_OV_ODBC3, SQL_IS_INTEGER);  
   if ( (retcode != SQL_SUCCESS_WITH_INFO) && (retcode != SQL_SUCCESS)) {  
      printf("SQLSetEnvAttr(ODBC version) Failed\n\n");  
      Cleanup();  
      return(9);      
   }  
  
   // Allocate ODBC connection handle and connect.  
   retcode = SQLAllocHandle(SQL_HANDLE_DBC, henv, &hdbc1);  
   if ( (retcode != SQL_SUCCESS_WITH_INFO) && (retcode != SQL_SUCCESS)) {  
      printf("SQLAllocHandle(hdbc1) Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // sample uses Integrated Security, create SQL Server DSN using the Windows NT authentication.   
   retcode = SQLConnect(hdbc1, (UCHAR*)"AdventureWorks", SQL_NTS, (UCHAR*)"",SQL_NTS, (UCHAR*)"", SQL_NTS);  
   if ( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
      printf("SQLConnect() Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Set options to log long-running queries, including the file to use for the log.  
   retcode = SQLSetConnectAttr( hdbc1, SQL_COPT_SS_PERF_QUERY_LOG, &"odbcqry.log", SQL_NTS);  
   if ( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
      printf("SQLSetConnectAttr Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Set the long-running query interval (in milliseconds).  Note that for version 2.50 and 2.65  
   // drivers, this value is specified in seconds, not milliseconds.  
   retcode =   
      SQLSetConnectAttr( hdbc1, SQL_COPT_SS_PERF_QUERY_INTERVAL, (SQLPOINTER)3000, SQL_IS_UINTEGER);  
   if ( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
      printf("SQLSetConnectAttr Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Start the long-running query log.  
   retcode =   
      SQLSetConnectAttr( hdbc1, SQL_COPT_SS_PERF_QUERY, (SQLPOINTER)SQL_PERF_START, SQL_IS_UINTEGER);  
   if ( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
      printf("SQLSetConnectAttr Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Allocate statement handle then execute commands.  
   retcode = SQLAllocHandle(SQL_HANDLE_STMT, hdbc1, &hstmt1);  
   if ( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
      printf("SQLAllocHandle(hstmt1) Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   retcode = SQLExecDirect(hstmt1, (UCHAR*)"SELECT * FROM Purchasing.Vendor", SQL_NTS);  
   if ( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
      printf("SQLExecDirect Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Clear any result sets generated.  
   while ( ( retcode = SQLMoreResults(hstmt1) ) != SQL_NO_DATA ) {  
      if ( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
         printf("SQLMoreResults Failed\n\n");  
         Cleanup();  
           return(9);  
      }  
   }  
  
   retcode = SQLExecDirect(hstmt1, (UCHAR*)"SELECT * FROM Sales.Store", SQL_NTS);  
   if ( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
      printf("SQLExecDirect Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Clear any result sets generated.  
   while ( ( retcode = SQLMoreResults(hstmt1) ) != SQL_NO_DATA ) {  
      if ( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
         printf("SQLMoreResults Failed\n\n");  
         Cleanup();  
         return(9);  
      }  
   }  
  
   // Generate a long-running query.  
   retcode = SQLExecDirect(hstmt1, (UCHAR*)"waitfor delay '00:00:04' ", SQL_NTS);  
   if ( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
      printf("SQLExecDirect Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Clear any result sets generated.  
   while ( ( retcode = SQLMoreResults(hstmt1) ) != SQL_NO_DATA ) {  
      if ( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
         printf("SQLMoreResults Failed\n\n");  
         Cleanup();  
         return(9);  
      }  
   }  
  
   // Cleanup  
   SQLFreeHandle(SQL_HANDLE_STMT, hstmt1);  
   SQLDisconnect(hdbc1);  
   SQLFreeHandle(SQL_HANDLE_DBC, hdbc1);  
   SQLFreeHandle(SQL_HANDLE_ENV, henv);  
}  
```  
  
## <a name="see-also"></a>참고 항목  
 [ODBC 드라이버 성능 방법 &#40;ODBC&#41;프로파일링](../../relational-databases/native-client-odbc-how-to/profiling-odbc-driver-performance-odbc.md)  
  
  
