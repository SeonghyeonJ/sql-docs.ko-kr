---
title: SQLSetScrollOptions 함수 | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLSetScrollOptions
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLSetScrollOptions
helpviewer_keywords:
- SQLSetScrollOptions function [ODBC]
ms.assetid: 2a825ba7-7942-4c23-bcdb-c80dc12f8c86
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9e0c2a9c367df9cd71d68d73ff676c8df915237b
ms.sourcegitcommit: 56b963446965f3a4bb0fa1446f49578dbff382e0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67793880"
---
# <a name="sqlsetscrolloptions-function"></a>SQLSetScrollOptions 함수
**규칙**  
 도입 된 버전: ODBC 1.0 표준 준수 합니다. 사용되지 않음  
  
 **요약**  
 Odbc에서 *3.x*, ODBC 2.0 함수 **SQLSetScrollOptions** 에 대 한 호출으로 대체 되었습니다 **SQLGetInfo** 고 **SQLSetStmtAttr**합니다.  
  
> [!NOTE]
>  새로운 드라이버 관리자는이 함수를 경우 맵을 ODBC에 대 한 자세한 *2.x* ODBC를 사용 하 여 응용 프로그램이 작동 *3.x* 드라이버를 참조 하세요. [사용 되지 않는 함수 매핑](../../../odbc/reference/appendixes/mapping-deprecated-functions.md)부록 g: 이전 버전과 호환성에 대 한 드라이버 지침입니다.  
> 
> [!NOTE]
>  때 드라이버 관리자 매핑합니다 **SQLSetScrollOptions** ODBC를 사용 하 여 작업 하는 응용 프로그램에 대 한 *3.x* 지원 하지 않는 드라이버 **SQLSetScrollOptions**, 드라이버 관리자에 not SQL_ATTR_ROW_ARRAY_SIZE 문 특성 SQL_ROWSET_SIZE 문 옵션을 설정 합니다는 *RowsetSize* 에서 인수 **SQLSetScrollOption**합니다. 따라서 **SQLSetScrollOptions** 를 호출 하 여 여러 행을 인출할 때 응용 프로그램에서 사용할 수 없습니다 **SQLFetch** 하거나 **SQLFetchScroll**합니다. 호출 하 여 행을 가져오는 여러 경우에 사용할 수 있습니다 **SQLExtendedFetch**합니다.  
  
## <a name="remarks"></a>설명  
 를 64 비트 운영 체제에서 응용 프로그램를 실행 하는 경우 참조 [ODBC 64-Bit 정보](../../../odbc/reference/odbc-64-bit-information.md)합니다.  
  
## <a name="see-also"></a>관련 항목  
 [ODBC API 참조](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC 헤더 파일](../../../odbc/reference/install/odbc-header-files.md)
