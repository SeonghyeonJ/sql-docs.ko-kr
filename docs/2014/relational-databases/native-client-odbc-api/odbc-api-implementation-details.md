---
title: ODBC API 구현 정보 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- ODBC, functions
- SQL Server Native Client ODBC driver, SQL Server-specific behaviors
- ODBC, SQL Server-specific behaviors
- functions [ODBC]
ms.assetid: dca92489-f179-4b1f-997c-adcc46aa17a3
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a8370db6cfcf3d410e563a0134221d0d48da09a8
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62715090"
---
# <a name="odbc-api-implementation-details"></a>ODBC API 구현 정보
  이 섹션에서는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC 드라이버와 함께 사용할 경우 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 관련 동작을 수행하는 ODBC 함수에 대해 설명합니다. 여기에서 모든 ODBC 함수를 설명하는 것은 아닙니다. 개별 항목에서는 ODBC 함수의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 관련 문제에 대해서만 설명합니다. 즉 ODBC 함수에 대한 완전한 참조 자료가 아닙니다.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC 드라이버는 ODBC 3.51 사양을 준수하며, 사용자가 Windows 7 SDK를 사용하고 있는 경우 ODBC 3.8 사양을 준수합니다. 포괄적인 ODBC 참조를 확인 합니다 [ODBC 프로그래머 참조](https://go.microsoft.com/fwlink/?LinkId=45250) 온라인입니다.  
  
## <a name="in-this-section"></a>섹션 내용  
  
-   [SQLBindCol](sqlbindcol.md)  
  
-   [SQLBindParameter](sqlbindparameter.md)  
  
-   [SQLBrowseConnect](sqlbrowseconnect.md)  
  
-   [SQLCancel](sqlcancel.md)  
  
-   [SQLCloseCursor](sqlclosecursor.md)  
  
-   [SQLColAttribute](sqlcolattribute.md)  
  
-   [SQLColumnPrivileges](sqlcolumnprivileges.md)  
  
-   [SQLColumns](sqlcolumns.md)  
  
-   [SQLConfigDataSource](sqlconfigdatasource.md)  
  
-   [SQLConnect](sqlconnect.md)  
  
-   [SQLDescribeCol](sqldescribecol.md)  
  
-   [SQLDescribeParam](sqldescribeparam.md)  
  
-   [SQLDriverConnect](sqldriverconnect.md)  
  
-   [SQLDrivers](sqldrivers.md)  
  
-   [SQLEndTran](sqlendtran.md)  
  
-   [SQLExecDirect](sqlexecdirect.md)  
  
-   [SQLExecute](sqlexecute.md)  
  
-   [SQLFetch](sqlfetch.md)  
  
-   [SQLFetchScroll](sqlfetchscroll.md)  
  
-   [SQLForeignKeys](sqlforeignkeys.md)  
  
-   [SQLFreeHandle](sqlfreehandle.md)  
  
-   [SQLFreeStmt](sqlfreestmt.md)  
  
-   [SQLGetConnectAttr](sqlgetconnectattr.md)  
  
-   [SQLGetCursorName](sqlgetcursorname.md)  
  
-   [SQLGetData](sqlgetdata.md)  
  
-   [SQLGetDescField](sqlgetdescfield.md)  
  
-   [SQLGetDescRec](sqlgetdescrec.md)  
  
-   [SQLGetDiagField](sqlgetdiagfield.md)  
  
-   [SQLGetFunctions](sqlgetfunctions.md)  
  
-   [SQLGetInfo](sqlgetinfo.md)  
  
-   [SQLGetStmtAttr](sqlgetstmtattr.md)  
  
-   [SQLGetTypeInfo](sqlgettypeinfo.md)  
  
-   [SQLMoreResults](sqlmoreresults.md)  
  
-   [SQLNativeSql](sqlnativesql.md)  
  
-   [SQLNumParams](sqlnumparams.md)  
  
-   [SQLNumResultCols](sqlnumresultcols.md)  
  
-   [SQLParamData](sqlparamdata.md)  
  
-   [SQLPrimaryKeys](sqlprimarykeys.md)  
  
-   [SQLProcedureColumns](sqlprocedurecolumns.md)  
  
-   [SQLProcedures](sqlprocedures.md)  
  
-   [SQLPutData](sqlputdata.md)  
  
-   [SQLRowCount](sqlrowcount.md)  
  
-   [SQLSetConnectAttr](sqlsetconnectattr.md)  
  
-   [SQLSetDescField](sqlsetdescfield.md)  
  
-   [SQLSetDescRec](sqlsetdescrec.md)  
  
-   [SQLSetEnvAttr](sqlsetenvattr.md)  
  
-   [SQLSetStmtAttr](sqlsetstmtattr.md)  
  
-   [SQLSpecialColumns](sqlspecialcolumns.md)  
  
-   [SQLStatistics](../statistics/statistics.md)  
  
-   [SQLTablePrivileges](sqltableprivileges.md)  
  
-   [SQLTables](sqltables.md)  
  
## <a name="see-also"></a>관련 항목  
 [SQL Server Native Client &#40;ODBC&#41; 참조](../../database-engine/dev-guide/sql-server-native-client-odbc-reference.md)   
 [SQL Server Native Client를 사용하여 응용 프로그램 빌드](../native-client/applications/building-applications-with-sql-server-native-client.md)  
  
  
