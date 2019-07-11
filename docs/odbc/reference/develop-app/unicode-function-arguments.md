---
title: 유니코드 함수 인수 | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Unicode [ODBC], functions
- functions [ODBC], Unicode functions
ms.assetid: eafe8c7e-f6d2-44d7-99ee-cf2148a30f4f
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 83cb2faad86268c3270e9386ca10b25e4807e030
ms.sourcegitcommit: 56b963446965f3a4bb0fa1446f49578dbff382e0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67793754"
---
# <a name="unicode-function-arguments"></a>유니코드 함수 인수
ODBC 3.5 (또는 이상) 드라이버 관리자는 해당 인수에 문자열 또는 대 SQLPOINTER에 대 한 포인터를 허용 하는 모든 함수의 ANSI 및 유니코드 버전을 지원 합니다. 유니코드 함수 함수로 구현 됩니다 (의 접미사로 *W*) 아니라 매크로입니다. ANSI 함수 (접미사 없이 호출할 수 *는*)는 현재 ODBC API 함수를 사용 하 여 동일 합니다.  
  
## <a name="remarks"></a>설명  
 항상 반환 하거나 문자열 또는 길이 인수를 사용 하는 유니코드 함수는 문자 수로 전달 됩니다. 서버 데이터에 대 한 길이 정보를 반환 하는 함수에 대 한 디스플레이 크기 및 전체 자릿수를 문자 수에 설명 되어 있습니다. 문자열 또는 문자열이 아닌 데이터 길이 (데이터 전송 크기)를 참조할 수, 하는 경우 8 진수 길이 길이 설명 합니다. 예를 들어 **SQLGetInfoW** 바이트의 수와 길이가 걸립니다 여전히 있지만 **SQLExecDirectW** 문자 수를 사용 합니다.  
  
 문자 수 (8 진수) ANSI 함수에 대 한 바이트 수와 유니코드 함수에 대 한 WCHAR (16 비트 단어)의 수를 나타냅니다. 특히, 여러 바이트를 더블 바이트 문자 시퀀스 (DBCS) 또는 멀티 바이트 문자 시퀀스 (MBCS)을 구성할 수 있습니다. 여러 WCHARs의 utf-16 유니코드 문자 시퀀스를 구성할 수 있습니다.  
  
 다음은 유니코드 (W) 및 ANSI (A) 버전을 지 원하는 ODBC API 함수 목록입니다.  
  
|||  
|-|-|  
|**SQLBrowseConnect**|**SQLGetDiagField**|  
|**SQLColAttribute**|**SQLGetDiagRec**|  
|**SQLColAttributes**|**SQLGetInfo**|  
|**SQLColumnPrivileges**|**SQLGetStmtAttr**|  
|**SQLColumns**|**SQLNativeSQL**|  
|**SQLConnect**|**SQLPrepare**|  
|**SQLDataSources**|**SQLPrimaryKeys**|  
|**SQLDescribeCol**|**SQLProcedureColumns**|  
|**SQLDriverConnect**|**SQLProcedures**|  
|**SQLDrivers**|**SQLSetConnectAttr**|  
|**SQLError**|**SQLSetConnectOption**|  
|**SQLExecDirect**|**SQLSetCursorName**|  
|**SQLForeignKeys**|**SQLSetDescField**|  
|**SQLGetConnectAttr**|**SQLSetStmtAttr**|  
|**SQLGetConnectOption**|**SQLSpecialColumns**|  
|**SQLGetCursorName**|**SQLStatistics**|  
|**SQLGetDescField**|**SQLTablePrivileges**|  
|**SQLGetDescRec**|**SQLTables**|  
  
 다음은 유니코드 (W) 및 ANSI (A) 버전을 지 원하는 ODBC 설치 관리자 및 ODBC 변환기 함수 목록.  
  
|||  
|-|-|  
|**SQLConfigDataSource**|**SQLInstallDriverManager**|  
|**SQLCreateDataSource**|**SQLInstallerError**|  
|**SQLDataSourceToDriver**|**SQLInstallODBC**|  
|**SQLDriverToDataSource**|**SQLReadFileDSN**|  
|**SQLGetAvailableDrivers**|**SQLRemoveDSNFromINI**|  
|**SQLGetInstalledDrivers**|**SQLValidDSN**|  
|**SQLGetTranslator**|**SQLWriteDSNToINI**|  
|**SQLInstallDriver**||  
  
> [!NOTE]
>  사용 되지 않는 함수는 유니코드에서 ANSI로 매핑을 지원 하므로 ODBC *3.x* 드라이버 관리자가 지 원하는 ODBC 다시 컴파일하지 *2.x* 유니코드를 사용 하 여 응용 프로그램 **#define**.  
  
 이 섹션에서는 다음 항목을 다룹니다.  
  
-   [유니코드 애플리케이션](../../../odbc/reference/develop-app/unicode-applications.md)  
  
-   [유니코드 드라이버](../../../odbc/reference/develop-app/unicode-drivers.md)  
  
-   [드라이버 관리자의 함수 매핑](../../../odbc/reference/develop-app/function-mapping-in-the-driver-manager.md)
