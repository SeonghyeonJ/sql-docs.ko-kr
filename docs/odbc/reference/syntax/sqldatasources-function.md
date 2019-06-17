---
title: SQLDataSources 함수 | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLDataSources
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLDataSources
helpviewer_keywords:
- SQLDataSources function [ODBC]
ms.assetid: 3f63b1b4-e70e-44cd-96c6-6878d50d0117
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9207dde54a14e345e99d3c04d4cb66622d85972e
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/15/2019
ms.locfileid: "65537624"
---
# <a name="sqldatasources-function"></a>SQLDataSources 함수
**규칙**  
 도입 된 버전: ODBC 1.0 표준 준수 합니다. ISO 92  
  
 **요약**  
 **SQLDataSources** 데이터 원본에 대 한 정보를 반환 합니다. 이 함수에만 드라이버 관리자에 의해 구현 됩니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
  
SQLRETURN SQLDataSources(  
     SQLHENV          EnvironmentHandle,  
     SQLUSMALLINT     Direction,  
     SQLCHAR *        ServerName,  
     SQLSMALLINT      BufferLength1,  
     SQLSMALLINT *    NameLength1Ptr,  
     SQLCHAR *        Description,  
     SQLSMALLINT      BufferLength2,  
     SQLSMALLINT *    NameLength2Ptr);  
```  
  
## <a name="arguments"></a>인수  
 *EnvironmentHandle*  
 [입력] 환경 핸들입니다.  
  
 *Direction*  
 [입력] 데이터 원본 드라이버 관리자 정보에 대 한 반환을 결정 합니다. 다음 값 중 하나일 수 있습니다.  
  
 SQL_FETCH_NEXT (인출할 목록의 다음 데이터 원본 이름)을, SQL_FETCH_FIRST (목록의 시작 부분에서 인출할)를, SQL_FETCH_FIRST_USER (첫 번째 인출 사용자 DSN)에 게 또는 (첫 번째 시스템 DSN 인출)를 SQL_FETCH_FIRST_SYSTEM  
  
 때 *방향을* SQL_FETCH_FIRST에 대 한 후속 호출으로 설정 된 **SQLDataSources** 사용 하 여 *방향* SQL_FETCH_NEXT로 사용자 및 시스템 Dsn을 반환 합니다. 때 *방향을* SQL_FETCH_FIRST_USER에 대 한 모든 후속 호출으로 설정 된 **SQLDataSources** 사용 하 여 *방향* SQL_FETCH_NEXT로 사용자 Dsn만 반환 합니다. 때 *방향을* SQL_FETCH_FIRST_SYSTEM에 대 한 모든 후속 호출으로 설정 된 **SQLDataSources** 사용 하 여 *방향* SQL_FETCH_NEXT로 시스템 Dsn만 반환 합니다.  
  
 *데이터 열이 추적에서 캡처되고 서버를 사용할 수 있으면*  
 [출력] 데이터 원본 이름을 반환 하는 버퍼에 대 한 포인터입니다.  
  
 경우 *ServerName* 가 null 인 경우 *NameLength1Ptr* (문자 데이터에 대 한 null 종료 문자를 제외한) 문자의 총 수를 반환 여전히가 가리키는 버퍼에서 반환할 사용 가능한 *ServerName*합니다.  
  
 *BufferLength1*  
 [입력] 길이 **ServerName* 문자에서 버퍼; SQL_MAX_DSN_LENGTH와 null 종료 문자 보다 길지 않을 것으로 필요는 없습니다.  
  
 *NameLength1Ptr*  
 [출력] 문자 (null 종결 문자가 제외)의 총 수를 반환 하는 버퍼에 대 한 포인터를 반환 하려면 사용 가능한 \* *ServerName*합니다. 반환할 사용 가능한 문자 개수 보다 크거나 같은 경우 *BufferLength1*, 데이터 원본 이름을 \* *ServerName* 잘립니다 *BufferLength1* null 종료 문자 길이 뺀 값입니다.  
  
 *설명*  
 [출력] 데이터 소스에 연결 된 드라이버의 설명을 반환 하는 버퍼에 대 한 포인터입니다. 예를 들어, dBASE 또는 SQL Server입니다.  
  
 하는 경우 *설명을* 가 null 인 경우 *NameLength2Ptr* (문자 데이터에 대 한 null 종료 문자를 제외한) 문자의 총 수를 반환 계속 됩니다 가리키는 버퍼에서 반환할 사용 가능한 *설명을*합니다.  
  
 *BufferLength2*  
 [입력] 문자 길이 **설명을* 버퍼입니다.  
  
 *NameLength2Ptr*  
 [출력] 문자 (null 종결 문자가 제외)의 총 수를 반환 하는 버퍼에 대 한 포인터를 반환 하려면 사용 가능한 \* *설명을*합니다. 반환할 사용 가능한 문자 개수 보다 크거나 같은 경우 *BufferLength2*에서 드라이버 설명을 \* *설명* 잘립니다 *BufferLength2*  null 종료 문자 길이 뺀 값입니다.  
  
## <a name="returns"></a>반환 값  
 관계 없이 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_NO_DATA, SQL_ERROR를 또는 SQL_INVALID_HANDLE 합니다.  
  
## <a name="diagnostics"></a>진단  
 때 **SQLDataSources** SQL_ERROR 또는 SQL_SUCCESS_WITH_INFO를 반환 합니다. 호출 하 여 연관된 된 SQLSTATE 값을 가져올 수 있습니다 **SQLGetDiagRec** 사용 하 여를 *HandleType*SQL_HANDLE_ENV의와 *처리할* 의 *EnvironmentHandle*합니다. 다음 표에서 일반적으로 반환한 SQLSTATE 값 **SQLDataSources** ;이 함수의 컨텍스트에서 각각에 설명 하 고 "(DM)" 표기법 드라이버 관리자에 의해 반환 된 Sqlstate 설명은 앞에 옵니다. 각 SQLSTATE 값과 연결 된 반환 코드를 다른 설명이 없는 경우 SQL_ERROR를 됩니다.  
  
|SQLSTATE|Error|Description|  
|--------------|-----------|-----------------|  
|01000|일반 경고|(DM) 드라이버 관리자 별 정보 메시지입니다. (함수는 SQL_SUCCESS_WITH_INFO를 반환합니다.)|  
|01004|문자열 데이터 오른쪽 잘림|(DM) 버퍼 \* *ServerName* 충분히 전체 데이터 원본 이름을 반환할 수 없습니다. 따라서 이름이 잘렸습니다. 전체 데이터 원본 이름의 길이가 반환 됩니다 \* *NameLength1Ptr*합니다. (함수는 SQL_SUCCESS_WITH_INFO를 반환합니다.)<br /><br /> (DM) 버퍼 \* *설명을* 전체 드라이버 설명을 반환 하는 충분히 큰 수 없습니다. 따라서 설명을 잘렸습니다. 잘리지 않은 데이터 원본 설명의 길이에서 **NameLength2Ptr*합니다. (함수는 SQL_SUCCESS_WITH_INFO를 반환합니다.)|  
|HY000|일반 오류|(DM) 오류가 발생 했습니다에 대 한 관련 없는 SQLSTATE 했습니다 및 없습니다 구현 별 SQLSTATE 정의 되었습니다. 반환 된 오류 메시지 **SQLGetDiagRec** 에  *\*MessageText* 버퍼 오류 및 해당 원인에 설명 합니다.|  
|HY001|메모리 할당 오류|(DM)의 드라이버 관리자 지원 함수 완료 또는 실행 하는 데 필요한 메모리를 할당할 수 없습니다.|  
|HY010|함수 시퀀스 오류입니다.|(DM) **SQLExecute**, **SQLExecDirect**, 또는 **SQLMoreResults** 에 대해 호출 된 합니다 *StatementHandle* SQL_PARAM_DATA_ 반환 사용할 수 있습니다. 이 함수는 모든 스트리밍된 매개 변수에 대 한 데이터를 검색 하기 전에 호출 되었습니다.|  
|HY013|메모리 관리 오류|기본 메모리 개체에 액세스할 수 없습니다, 가능한 경우 메모리 부족으로 인해 함수 호출을 처리할 수 없습니다.|  
|HY090|문자열 또는 버퍼 길이가 잘못 되었습니다.|인수에 대 한 지정 된 값 (DM) *BufferLength1* 0 보다 작습니다.<br /><br /> 인수에 대 한 지정 된 값 (DM) *BufferLength2* 0 보다 작습니다.|  
|HY103|검색 코드가 잘못 되었습니다|인수에 지정 된 값 (DM) *방향을* 가 SQL_FETCH_FIRST, SQL_FETCH_FIRST_USER, SQL_FETCH_FIRST_SYSTEM, 또는 SQL_FETCH_NEXT 없습니다.|  
|HY117|연결 알 수 없는 트랜잭션 상태로 인해 일시 중단 됩니다. 만 연결을 끊고 읽기 전용으로 함수를 사용할 수 있습니다.|(DM) 일시 중단 된 상태에 대 한 자세한 내용은 참조 하세요. [SQLEndTran 함수](../../../odbc/reference/syntax/sqlendtran-function.md)합니다.|  
  
## <a name="comments"></a>주석  
 때문에 **SQLDataSources** 구현 된 드라이버 관리자에서 특정 드라이버의 표준 준수에 관계 없이 모든 드라이버에 대 한 지원 됩니다.  
  
 응용 프로그램에서 호출할 수 있습니다 **SQLDataSources** 여러 번에 모든 데이터 원본 이름을 검색 합니다. 드라이버 관리자는 시스템 정보에서이 정보를 검색합니다. 데이터 원본 이름이 더 이상 없으면 경우 드라이버 관리자에서 SQL_NO_DATA를 반환 합니다. 하는 경우 **SQLDataSources** SQL_FETCH_NEXT 첫 번째 데이터 원본 이름을 반환 합니다 SQL_NO_DATA가 반환 된 후 즉시 호출 됩니다. 응용 프로그램에서 반환 된 정보를 사용 하는 방법에 대 한 자세한 **SQLDataSources**를 참조 하세요 [데이터 원본 또는 드라이버 선택](../../../odbc/reference/develop-app/choosing-a-data-source-or-driver.md)합니다.  
  
 SQL_FETCH_NEXT에 전달 되 면 **SQLDataSources** 처음 호출 되는 첫 번째 데이터 원본 이름을 반환 합니다.  
  
 드라이버는 데이터 원본 이름은 실제 데이터 원본에 매핑되는 방식을 결정 합니다.  
  
## <a name="related-functions"></a>관련 함수  
  
|내용|참조 항목|  
|---------------------------|---------|  
|검색 및 데이터 원본에 연결 하는 데 필요한 값을 나열|[SQLBrowseConnect 함수](../../../odbc/reference/syntax/sqlbrowseconnect-function.md)|  
|데이터 원본에 연결|[SQLConnect 함수](../../../odbc/reference/syntax/sqlconnect-function.md)|  
|연결 문자열 또는 대화 상자를 사용 하 여 데이터 원본에 연결|[SQLDriverConnect 함수](../../../odbc/reference/syntax/sqldriverconnect-function.md)|  
|드라이버 설명 및 특성을 반환합니다.|[SQLDrivers 함수](../../../odbc/reference/syntax/sqldrivers-function.md)|  
  
## <a name="see-also"></a>관련 항목  
 [ODBC API 참조](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC 헤더 파일](../../../odbc/reference/install/odbc-header-files.md)
