---
title: SQLGetInfo (Excel 드라이버) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Excel driver [ODBC], SQLGetInfo
- SQLGetInfo function [ODBC], Excel Driver
ms.assetid: fed4aea2-6d3d-4199-a5db-3d033eb63927
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a2524c51f1b4b9297b6e3483a27fd78e6c1836e9
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63301992"
---
# <a name="sqlgetinfo-excel-driver"></a>SQLGetInfo(Excel 드라이버)
> [!NOTE]  
>  이 항목에서는 Excel 드라이버 관련 정보를 제공 합니다. 이 함수에 대 한 일반 정보에서 해당 항목을 참조 하세요 [ODBC API 참조](../../odbc/reference/syntax/odbc-api-reference.md)합니다.  
  
 **SQLGetInfo** SQL_FILE_USAGE 정보 유형을 지원 합니다. 반환된 값은 드라이버 파일을 데이터 원본에서 직접 처리 하는 방법을 나타내는 16 비트 정수.  
  
-   SQL_FILE_NOT_SUPPORTED-드라이버는 단일 계층 드라이버 없습니다.  
  
-   SQL_FILE_TABLE-단일 계층 드라이버 파일 데이터 원본에서 테이블로 처리합니다.  
  
-   단일 계층 드라이버 SQL_FILE_QUALIFIER-파일 데이터 원본에 한정자로 처리합니다.  
  
 ODBC 드라이버는 각 파일 테이블 이므로 theMicrosoft Exceldriver에 대 한 SQL_FILE_TABLE를 반환 합니다.  
  
## <a name="sqldbmsver"></a>SQL_DBMS_VER  
  
|ISAM|버전|버전 번호의 형식|  
|----------|-------------|-------------------------------|  
|Microsoft Excel|3.0|03.00.0000|  
||4.0|04.00.0000|  
||5.0/7.0|05.00.0000|  
||97/2000|08.00.0000|  
  
## <a name="sqlfileusage"></a>SQL_FILE_USAGE  
 SQL_FILE_TABLE (Excel 3.0/4.0)  
  
 SQL_FILE_CATALOG (Excel 5.0/7.0)  
  
## <a name="sqlmaxcharliterallen"></a>SQL_MAX_CHAR_LITERAL_LEN  
 255 (Excel 3.0/4.0/5.0/7.0)  
  
 65535 (Excel 97)  
  
## <a name="sqlmaxcolumnnamelen"></a>SQL_MAX_COLUMN_NAME_LEN  
 30 (Excel 3.0/4.0)  
  
 64 (Excel 5.0/7.0/97)  
  
## <a name="sqlmaxtablenamelen"></a>SQL_MAX_TABLE_NAME_LEN  
 12 (Excel 3.0/4.0)  
  
 31 (Excel 5.0/7.0/97)  
  
## <a name="sqlcatalognameseparator"></a>SQL_CATALOG_NAME_SEPARATOR  
 "\\" (Excel 3.0/4.0)  
  
 "." (5.0/7.0/97 excel)  
  
## <a name="sqlcatalogterm"></a>SQL_CATALOG_TERM  
 "Directory" (Excel 3.0/4.0)  
  
 "통합" (Excel 5.0/7.0/97)  
  
## <a name="sqlcatalogusage"></a>SQL_CATALOG_USAGE  
 SQL_QU_DML_STATEMENTS &#124; SQL_QU_TABLE_DEFINITION  
  
## <a name="sqltimedatefunctions"></a>SQL_TIMEDATE_FUNCTIONS  
 SQL_FN_TD_CURDATE &AMP;#124; SQL_FN_TD_CURTIME &AMP;#124; SQL_FN_TD_DAYOFMONTH &AMP;#124; SQL_FN_TD_DAYOFWEEK &AMP;#124; SQL_FN_TD_DAYOFYEAR &AMP;#124; SQL_FN_TD_HOUR &AMP;#124; SQL_FN_TD_MINUTE &AMP;#124; SQL_FN_TD_MONTH &AMP;#124; SQL_FN_TD_NOW &AMP;#124; SQL_FN_TD_SECOND &AMP;#124; SQL_FN_TD_WEEK &AMP;#124; SQL_FN_TD_YEAR
