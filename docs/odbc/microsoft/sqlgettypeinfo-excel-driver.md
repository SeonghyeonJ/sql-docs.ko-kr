---
title: SQLGetTypeInfo (Excel 드라이버) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLGetTypeInfo function [ODBC], Excel Driver
- Excel driver [ODBC], SQLGetTypeInfo
ms.assetid: 708845be-e6a1-4677-8113-c52819a43fa4
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ac7fe52ffdbb090e0b63a972e77c1a7f7a756446
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63034910"
---
# <a name="sqlgettypeinfo-excel-driver"></a>SQLGetTypeInfo(Excel 드라이버)
> [!NOTE]  
>  이 항목에서는 Excel 드라이버 관련 정보를 제공 합니다. 이 함수에 대 한 일반 정보에서 해당 항목을 참조 하세요 [ODBC API 참조](../../odbc/reference/syntax/odbc-api-reference.md)합니다.  
  
 (TYPE_NAME) 형식의 이름을 반환 하 여 생성 된 테이블 **SQLGetTypeInfo** 이름이 데이터 원본에서 가장 일반적으로 사용 됩니다.  
  
 SQL_ALL_EXCEPT_LIKE이 반환할 검색할 수 있는 열에 바이트에 대 한 카운터, Double, 단일 고 Long, Short 데이터 형식입니다. (다음 비교를 수행 하는 ODBC 정식 변환 함수를 사용 하 여 문자 값을 변환 하 여 LIKE 기능을 구현할 수 있습니다.)  
  
 Microsoft Excel 드라이버를 사용 하는 TYPE_NAME 열에서 반환 되는 ODBC 형식 이름이 반환 됩니다 **SQLGetTypeInfo**합니다.
