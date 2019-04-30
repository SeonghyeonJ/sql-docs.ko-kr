---
title: 설치 관리자 DLL 함수 요약 | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- functions [ODBC], installer DLL functions
- installer DLL [ODBC]
ms.assetid: 666c09d3-1e10-4d89-9b42-eda2957a87f0
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ecb486f51caa97c715d54885c34575a60bfdfb83
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63231837"
---
# <a name="installer-dll-function-summary"></a>설치 관리자 DLL 함수 요약
다음 표에서 설치 관리자 DLL에서에서 함수를 설명 합니다. 구문 및 각 함수에 대 한 의미 체계에 대 한 자세한 내용은 참조 하세요. [Installer DLL API 참조](../../../odbc/reference/syntax/installer-dll-api-reference-function.md)합니다.  
  
|태스크|함수 이름|용도|  
|----------|-------------------|-------------|  
|ODBC 설치|[SQLConfigDriver](../../../odbc/reference/syntax/sqlconfigdriver-function.md)|특정 드라이버 설치 DLL을 로드합니다.|  
||[SQLGetInstalledDrivers](../../../odbc/reference/syntax/sqlgetinstalleddrivers-function.md)|설치 된 드라이버 목록을 반환합니다.|  
||[SQLInstallDriverEx](../../../odbc/reference/syntax/sqlinstalldriverex-function.md)|시스템 정보에는 드라이버를 추가합니다.|  
||[SQLInstallDriverManager](../../../odbc/reference/syntax/sqlinstalldrivermanager-function.md)|드라이버 관리자에 대 한 대상 디렉터리를 반환합니다.|  
||[SQLInstallerError](../../../odbc/reference/syntax/sqlinstallererror-function.md)|설치 관리자 기능에 대 한 오류 또는 상태 정보를 반환합니다.|  
||[SQLInstallTranslatorEx](../../../odbc/reference/syntax/sqlinstalltranslatorex-function.md)|시스템 정보에는 변환기를 추가합니다.|  
||[SQLPostInstallerError](../../../odbc/reference/syntax/sqlpostinstallererror-function.md)|드라이버 또는 translator 설치 라이브러리를 오류를 보고할 수 있습니다.|  
||[SQLRemoveDriver](../../../odbc/reference/syntax/sqlremovedriver-function.md)|시스템 정보에서 드라이버를 제거합니다.|  
||[SQLRemoveDriverManager](../../../odbc/reference/syntax/sqlremovedrivermanager-function.md)|시스템 정보에서 ODBC 핵심 구성 요소를 제거합니다.|  
||[SQLRemoveTranslator](../../../odbc/reference/syntax/sqlremovetranslator-function.md)|시스템 정보에서 변환기를 제거합니다.|  
|데이터 원본 구성|[SQLConfigDataSource](../../../odbc/reference/syntax/sqlconfigdatasource-function.md)|특정 드라이버 설치 DLL을 호출합니다.|  
||[SQLCreateDataSource](../../../odbc/reference/syntax/sqlcreatedatasource-function.md)|데이터 원본을 추가 하려면 대화 상자를 표시 합니다.|  
||[SQLGetConfigMode](../../../odbc/reference/syntax/sqlgetconfigmode-function.md)|시스템 정보에 DSN 값을 나열 하는 Odbc.ini 항목 인 나타내는 구성 모드를 검색 합니다.|  
||[SQLGetPrivateProfileString](../../../odbc/reference/syntax/sqlgetprivateprofilestring-function.md)|시스템 정보에 값을 씁니다.|  
||[SQLGetTranslator](../../../odbc/reference/syntax/sqlgettranslator-function.md)|변환기 선택 대화 상자를 표시 합니다.|  
||[SQLManageDataSources](../../../odbc/reference/syntax/sqlmanagedatasources.md)|데이터 원본 및 드라이버를 구성 하는 대화 상자를 표시 합니다.|  
||[SQLReadFileDSN](../../../odbc/reference/syntax/sqlreadfiledsn-function.md)|Dsn 파일에서 정보를 읽습니다.|  
||[SQLRemoveDefaultDataSource](../../../odbc/reference/syntax/sqlremovedefaultdatasource-function.md)|기본 데이터 원본을 제거합니다.|  
||[SQLRemoveDSNFromIni](../../../odbc/reference/syntax/sqlremovedsnfromini-function.md)|데이터 원본을 제거합니다.|  
||[SQLSetConfigMode](../../../odbc/reference/syntax/sqlsetconfigmode-function.md)|시스템 정보에 DSN 값을 나열 하는 Odbc.ini 항목 인 나타내는 구성 모드를 설정 합니다.|  
||[SQLValidDSN](../../../odbc/reference/syntax/sqlvaliddsn-function.md)|길이 데이터 원본 이름의 유효성을 검사합니다.|  
||[SQLWriteDSNToIni](../../../odbc/reference/syntax/sqlwritedsntoini-function.md)|데이터 소스를 추가합니다.|  
||[SQLWriteFileDSN](../../../odbc/reference/syntax/sqlwritefiledsn-function.md)|파일 Dsn에 정보를 씁니다.|  
||[SQLWritePrivateProfileString](../../../odbc/reference/syntax/sqlwriteprivateprofilestring-function.md)|시스템 정보에서 값을 가져옵니다.|
