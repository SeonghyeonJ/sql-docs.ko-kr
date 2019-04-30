---
title: SQLGetCursorName 함수 | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLGetCursorName
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLGetCursorName
helpviewer_keywords:
- SQLGetCursorName function [ODBC]
ms.assetid: e6e92199-7bb6-447c-8987-049a4c6ce05d
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: faa88d18a5b682b98a56b6426ba6a94ee4687cab
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63258829"
---
# <a name="sqlgetcursorname-function"></a>SQLGetCursorName 함수(SQLGetCursorName Function)
**규칙**  
 도입 된 버전: ODBC 1.0 표준 준수 합니다. ISO 92  
  
 **요약**  
 **SQLGetCursorName** 지정 된 문과 연결 된 커서 이름을 반환 합니다.  
  
## <a name="syntax"></a>구문  
  
```  
  
SQLRETURN SQLGetCursorName(  
     SQLHSTMT        StatementHandle,  
     SQLCHAR *       CursorName,  
     SQLSMALLINT     BufferLength,  
     SQLSMALLINT *   NameLengthPtr);  
```  
  
## <a name="arguments"></a>인수  
 *StatementHandle*  
 [입력] 문 핸들입니다.  
  
 *CursorName*  
 [출력] 커서 이름을 반환 하는 버퍼에 대 한 포인터입니다.  
  
 경우 *CursorName* 가 null 인 경우 *NameLengthPtr* (문자 데이터에 대 한 null 종료 문자를 제외한) 문자의 총 수를 반환 여전히가 가리키는 버퍼에서 반환할 사용 가능한 *CursorName*합니다.  
  
 *BufferLength*  
 [입력] 길이가 \* *CursorName*, 문자에서입니다. 경우 값  *\*CursorName* 는 유니코드 문자열 (호출할 때 **SQLGetCursorNameW**), *BufferLength* 인수 수는 짝수 여야 합니다.  
  
 *NameLengthPtr*  
 [출력] 문자 (null 종결 문자가 제외)의 총 수를 반환 하는 메모리에 대 한 포인터를 반환 하려면 사용 가능한 \* *CursorName*합니다. 반환할 사용 가능한 문자 개수 보다 크거나 같은 경우 *BufferLength*, 커서 이름 \* *CursorName* 잘립니다 *BufferLength*의 null 종결 문자 길이 뺀 값입니다.  
  
## <a name="returns"></a>반환 값  
 관계 없이 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR를 또는 SQL_INVALID_HANDLE 합니다.  
  
## <a name="diagnostics"></a>진단  
 때 **SQLGetCursorName** SQL_ERROR 또는 SQL_SUCCESS_WITH_INFO를 반환 합니다. 호출 하 여 연관된 된 SQLSTATE 값을 가져올 수 있습니다 **SQLGetDiagRec** 사용 하 여를 *HandleType*호출의와 *처리할* 의 *StatementHandle*합니다. 다음 표에서 일반적으로 반환한 SQLSTATE 값 **SQLGetCursorName** ;이 함수의 컨텍스트에서 각각에 설명 하 고 "(DM)" 표기법 드라이버 관리자에 의해 반환 된 Sqlstate 설명은 앞에 옵니다. 각 SQLSTATE 값과 연결 된 반환 코드를 다른 설명이 없는 경우 SQL_ERROR를 됩니다.  
  
|SQLSTATE|Error|Description|  
|--------------|-----------|-----------------|  
|01000|일반 경고|드라이버 관련 정보 메시지입니다. (함수는 SQL_SUCCESS_WITH_INFO를 반환합니다.)|  
|01004|문자열 데이터 오른쪽 잘림|버퍼 \* *CursorName* 충분히 커서 이름이 잘렸습니다 하므로 전체 커서 이름을 반환할 수 없습니다. 잘리지 않은 커서 이름 길이에서 **NameLengthPtr*합니다. (함수는 SQL_SUCCESS_WITH_INFO를 반환합니다.)|  
|HY000|일반 오류|오류가 없는 관련 SQLSTATE 했습니다는 및 없습니다 구현 별 SQLSTATE 정의 되었습니다. 반환 된 오류 메시지 **SQLGetDiagRec** 에  *\*MessageText* 버퍼 오류 및 해당 원인에 설명 합니다.|  
|HY001|메모리 할당 오류|드라이버 완료 함수 또는 실행을 지 원하는 데 필요한 메모리를 할당할 수 없습니다.|  
|HY010|함수 시퀀스 오류입니다.|(DM)를 비동기적으로 실행 중인 함수를 호출한 연관 된 연결 핸들에 대 한 합니다 *StatementHandle*합니다. 이 비동기 함수가 여전히 실행 시기를 **SQLGetCursorName** 함수를 호출 했습니다.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, 또는 **SQLMoreResults** 에 대해 호출 된 합니다 *StatementHandle* SQL_PARAM_DATA_ 반환 사용할 수 있습니다. 이 함수는 모든 스트리밍된 매개 변수에 대 한 데이터를 검색 하기 전에 호출 되었습니다.<br /><br /> (DM)를 비동기적으로 실행 중인 함수에 대해 호출 된 합니다 *StatementHandle* 이 함수가 호출 되었을 때 계속 실행 하 고 있습니다.<br /><br /> (DM) **SQLExecute**를 **SQLExecDirect**를 **SQLBulkOperations**, 또는 **SQLSetPos** 에 대해 호출 된는  *StatementHandle* SQL_NEED_DATA를 반환 합니다. 이 함수는 모든 실행 시 데이터 매개 변수 또는 열에 대 한 데이터를 전송 하기 전에 호출 되었습니다.|  
|HY013|메모리 관리 오류|기본 메모리 개체에 액세스할 수 없습니다, 가능한 경우 메모리 부족으로 인해 함수 호출을 처리할 수 없습니다.|  
|HY015|커서 이름이 없습니다.|(DM) 드라이버는 ODBC 2 되었습니다 *.x* 드라이버 문에서 열린 커서가 없습니다 있었습니다 및 커서 이름이 없습니다. 사용 하 여 설정 된 **SQLSetCursorName**합니다.|  
|HY090|문자열 또는 버퍼 길이가 잘못 되었습니다.|인수에 지정 된 값 (DM) *BufferLength* 0 보다 작습니다.|  
|HY117|연결 알 수 없는 트랜잭션 상태로 인해 일시 중단 됩니다. 만 연결을 끊고 읽기 전용으로 함수를 사용할 수 있습니다.|(DM) 일시 중단 된 상태에 대 한 자세한 내용은 참조 하세요. [SQLEndTran 함수](../../../odbc/reference/syntax/sqlendtran-function.md)합니다.|  
|HYT01|연결 제한 시간 만료 됨|데이터 원본 요청에 응답 하기 전에 연결 제한 시간에 만료 되었습니다. 연결 제한 시간을 통해 설정 됩니다 **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT 합니다.|  
|IM001|드라이버는이 함수를 지원 하지 않습니다.|(DM) 드라이버를 사용 하 여 연결 합니다 *StatementHandle* 함수를 지원 하지 않습니다.|  
  
## <a name="comments"></a>주석  
 커서 이름은 현재 위치 업데이트에만 사용 됩니다 및 delete 문 (예를 들어 **업데이트할** _테이블 이름_ ... **WHERE CURRENT OF** _커서 이름을_). 자세한 내용은 [배치 업데이트 및 삭제 문을](../../../odbc/reference/develop-app/positioned-update-and-delete-statements.md)합니다. 응용 프로그램을 호출 하지 않습니다 **SQLSetCursorName** 커서 이름을 정의 드라이버 이름을 생성 합니다. 이 이름은 SQL_CUR 문자로 시작합니다.  
  
> [!NOTE]
>  ODBC 2에서 *.x*했습니다. 열려 있는 커서 이름이 없는를 호출 하 여 설정 된 경우, **SQLSetCursorName**에 대 한 호출 **SQLGetCursorName** SQLSTATE HY015 반환 (커서 이름이 없습니다. 사용 가능). ODBC 3에서 *.x*,이 더 이상 true; 시기에 관계 없이 **SQLGetCursorName** 는 호출 드라이버 커서 이름을 반환 합니다.  
  
 **SQLGetCursorName** 이름을 명시적으로 또는 암시적으로 만든 여부 커서의 이름을 반환 합니다. 커서 이름을 경우 암시적으로 생성 됩니다 **SQLSetCursorName** 호출 되지 않습니다. **SQLSetCursorName** 커서가 할당 또는 준비 된 상태와 문에서 커서 이름을 바꾸려면 호출할 수 있습니다.  
  
 명시적 또는 암시적으로 설정 된 커서 이름을 설정 될 때까지 유지 합니다 *StatementHandle* 사용 하 여 연결 된 삭제를 사용 하 여 **SQLFreeHandle** 사용 하 여를 *HandleType* 호출입니다.  
  
## <a name="related-functions"></a>관련 함수  
  
|내용|참조 항목|  
|---------------------------|---------|  
|SQL 문을 실행합니다.|[SQLExecDirect 함수](../../../odbc/reference/syntax/sqlexecdirect-function.md)|  
|준비 된 SQL 문을 실행합니다.|[SQLExecute 함수](../../../odbc/reference/syntax/sqlexecute-function.md)|  
|실행할 문을 준비합니다.|[SQLPrepare 함수](../../../odbc/reference/syntax/sqlprepare-function.md)|  
|커서 이름을 설정합니다.|[SQLSetCursorName 함수](../../../odbc/reference/syntax/sqlsetcursorname-function.md)|  
  
## <a name="see-also"></a>관련 항목  
 [ODBC API 참조](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC 헤더 파일](../../../odbc/reference/install/odbc-header-files.md)
