---
title: SQLConfigDataSource 함수 | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLConfigDataSource
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLConfigDataSource
helpviewer_keywords:
- SQLConfigDataSource function [ODBC]
ms.assetid: f8d6e342-c010-434e-b1cd-f5371fb50a14
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1ef74d98102c424a71ac1728d664fddbeac2296c
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63258856"
---
# <a name="sqlconfigdatasource-function"></a>SQLConfigDataSource 함수(SQLConfigDataSource Function)
**규칙**  
 도입 된 버전: ODBC 1.0  
  
 **요약**  
 **SQLConfigDataSource** 추가, 수정 또는 데이터 원본을 삭제 합니다.  
  
 기능의 **SQLConfigDataSource** 사용 하 여 액세스할 수도 있습니다 [ODBCCONF 합니다. EXE](../../../odbc/odbcconf-exe.md)합니다.  
  
## <a name="syntax"></a>구문  
  
```  
  
BOOL SQLConfigDataSource(  
     HWND     hwndParent,  
     WORD     fRequest,  
     LPCSTR   lpszDriver,  
     LPCSTR   lpszAttributes);  
```  
  
## <a name="arguments"></a>인수  
 *hwndParent*  
 [입력] 부모 창 핸들입니다. 핸들을 null 이면 함수는 모든 대화 상자 표시 되지 않습니다.  
  
 *fRequest*  
 [입력] 요청 유형입니다. 합니다 *문제점과* 인수는 다음 값 중 하나를 포함 해야 합니다.  
  
 ODBC_ADD_DSN: 새 사용자 데이터 원본을 추가 합니다.  
  
 ODBC_CONFIG_DSN: 구성 (수정) 기존 사용자 데이터 원본입니다.  
  
 ODBC_REMOVE_DSN: 기존 사용자 데이터 원본을 제거 합니다.  
  
 ODBC_ADD_SYS_DSN: 새 시스템 데이터 원본을 추가 합니다.  
  
 ODBC_CONFIG_SYS_DSN: 기존 시스템 데이터 원본을 수정 합니다.  
  
 ODBC_REMOVE_SYS_DSN: 기존 시스템 데이터 원본을 제거 합니다.  
  
 ODBC_REMOVE_DEFAULT_DSN: 시스템 정보에서 기본 데이터 원본 사양 섹션을 제거 합니다. (또한 기본 드라이버 사양 섹션에서에서 제거 시스템 정보 Odbcinst.ini 항목입니다. 이렇게 *문제점과* 사용 되지 않는 동일한 기능을 수행 **SQLRemoveDefaultDataSource** 함수입니다.) 이 옵션을 지정 하는 경우 모든 호출에서 다른 매개 변수 **SQLConfigDataSource** 무시 됩니다 하지 않은 경우 NULL을; Null 이어야 합니다.  
  
 *lpszDriver*  
 [입력] 드라이버 설명 (일반적으로 연결된 되는 DBMS의 이름) 실제 드라이버 이름 대신 사용자에 게 표시 합니다.  
  
 *lpszAttributes*  
 [입력] 키워드-값 쌍의 형태로 특성 목록을 이중 null로 종료 합니다. 자세한 내용은 [ConfigDSN](../../../odbc/reference/syntax/configdsn-function.md)합니다.  
  
## <a name="returns"></a>반환 값  
 함수가 성공적 이면 FALSE 실패 한 경우 TRUE를 반환 합니다. 이 함수가 호출 될 때 시스템 정보에 없는 항목이 있으면 함수는 FALSE를 반환 합니다.  
  
## <a name="diagnostics"></a>진단  
 때 **SQLConfigDataSource** 연결 된 FALSE를 반환  *\*pfErrorCode* 호출 하 여 값을 얻을 수 있습니다 **SQLInstallerError**합니다. 다음 표에서  *\*pfErrorCode* 에서 반환 될 수 있는 값 **SQLInstallerError** 이 함수의 컨텍스트에서 각각 설명 합니다.  
  
|*\*pfErrorCode*|Error|Description|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|일반 설치 관리자 오류|오류가 발생 했습니다에 대 한 특정 설치 관리자 오류가 없습니다.|  
|ODBC_ERROR_INVALID_HWND|잘못 된 창 핸들|합니다 *hwndParent* 인수가 잘못 되었거나 NULL입니다.|  
|ODBC_ERROR_INVALID_REQUEST_TYPE|요청의 형식이 잘못 되었습니다|합니다 *문제점과* 인수 중 하나 였습니다.<br /><br /> ODBC_ADD_DSN ODBC_CONFIG_DSN ODBC_REMOVE_DSN ODBC_ADD_SYS_DSN ODBC_CONFIG_SYS_DSN ODBC_REMOVE_SYS_DSN ODBC_REMOVE_DEFAULT_DSN|  
|ODBC_ERROR_INVALID_NAME|잘못 된 드라이버 또는 변환기 이름|합니다 *lpszDriver* 인수가 잘못 되었습니다. 레지스트리에서 찾을 수 없습니다.|  
|ODBC_ERROR_INVALID_KEYWORD_VALUE|잘못 된 키워드-값 쌍|합니다 *lpszAttributes* 인수 구문 오류를 포함 합니다.|  
|ODBC_ERROR_REQUEST_FAILED|*요청* 실패|설치 관리자에서 요청한 작업을 수행할 수 없습니다는 *문제점과* 인수입니다. 에 대 한 호출 **ConfigDSN** 실패 했습니다.|  
|ODBC_ERROR_LOAD_LIBRARY_FAILED|드라이버 또는 translator 설치 라이브러리를 로드할 수 없습니다.|드라이버 설치 라이브러리를 로드할 수 없습니다.|  
|ODBC_ERROR_OUT_OF_MEM|메모리가 부족합니다.|설치 관리자의 메모리 부족으로 인해 함수를 수행할 수 있습니다.|  
  
## <a name="comments"></a>주석  
 **SQLConfigDataSource** 의 값을 사용 하 여 *lpszDriver* 시스템 정보에서 드라이버 설치 DLL의 전체 경로 읽을 수 있습니다. DLL 및 호출 로드 **ConfigDSN** 에 전달 된 동일한 인수를 사용 합니다.  
  
 **SQLConfigDataSource** 를 찾거나 설치 DLL을 로드할 수 없는 경우 또는 사용자가 대화 상자를 취소 하는 경우에 FALSE를 반환 합니다. 받은 상태를 반환 하는 고, 그렇지 **ConfigDSN**합니다.  
  
 **SQLConfigDataSource** 시스템 DSN 매핑합니다 *문제점과*사용자 DSN에 s *문제점과*(ODBC_ADD_SYS_DSN ODBC_ADD_DSN, ODBC_CONFIG_DSN, 및 ODBC_REMOVE_SYS_ ODBC_CONFIG_SYS_DSN s DSN을 하려면 ODBC_REMOVE_DSN)입니다. 사용자 및 시스템 Dsn을 구분 하기 위해 **SQLConfigDataSource** 설치 프로그램은 다음 표에 따라 구성 모드를 설정 합니다. 를 반환 하기 전에 **SQLConfigDataSource** BOTHDSN 구성 모드 다시 설정 합니다. **ConfigDSN** (드라이버에서 구현 됨)를 호출 해야 **SQLWriteDSNToIni** 하 고 **SQLWritePrivateProfileString** 시스템 DSN을 지원 하도록 합니다. 자세한 내용은 [ConfigDSN 함수](../../../odbc/reference/syntax/configdsn-function.md)합니다.  
  
|*fRequest*|구성 모드|  
|----------------|------------------------|  
|ODBC_ADD_DSN|USERDSN_ONLY|  
|ODBC_CONFIG_DSN|USERDSN_ONLY|  
|ODBC_REMOVE_DSN|USERDSN_ONLY|  
|ODBC_ADD_SYS_DSN|SYSTEMDSN_ONLY|  
|ODBC_CONFIG_SYS_DSN|SYSTEMDSN_ONLY|  
|ODBC_REMOVE_SYS_DSN|SYSTEMDSN_ONLY|  
  
## <a name="related-functions"></a>관련 함수  
  
|내용|참조 항목|  
|---------------------------|---------|  
|추가, 수정 또는 데이터 원본 제거|[ConfigDSN](../../../odbc/reference/syntax/configdsn-function.md) (에 DLL 설치)|  
|시스템 정보에서 데이터 원본 이름 제거|[SQLRemoveDSNFromIni](../../../odbc/reference/syntax/sqlremovedsnfromini-function.md)|  
|시스템 정보를 데이터 원본 이름 추가|[SQLWriteDSNToIni](../../../odbc/reference/syntax/sqlwritedsntoini-function.md)|
