---
title: SQLColAttributes (텍스트 파일 드라이버) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- text file driver [ODBC], SQLColAttributes
- SQLColAttribute function [ODBC], Text File Driver
ms.assetid: 132fd1c0-1921-4a7d-910e-aedf1bff5453
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8bb242dcaf34f8fe7fad2886b13ddf5209c20c18
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62666087"
---
# <a name="sqlcolattributes-text-file-driver"></a>SQLColAttributes(텍스트 파일 드라이버)
> [!NOTE]  
>  이 항목에서는 텍스트 파일 드라이버 관련 정보를 제공 합니다. 이 함수에 대 한 일반 정보에서 해당 항목을 참조 하세요 [ODBC API 참조](../../odbc/reference/syntax/odbc-api-reference.md)합니다.  
  
|attribute|주석|  
|---------------|--------------|  
|SQL_COLUMN_DISPLAY_SIZE|LONGVARBINARY 데이터용 SQL_COLUMN_DISPLAY_SIZE 없습니다 2 시간 열의 최대 길이 열의 최대 길이입니다.|  
|SQL_OWNER_NAME|빈 문자열 ("") 소유자 이름입니다. 지원 되지 않으므로이 열에 반환 됩니다.|  
|SQL_QUALIFIER_NAME|디렉터리 경로가 반환 됩니다.|  
|SQL_COLUMN_SEARCHABLE|LONGVARCHAR 및 LONGVARBINARY 열 SQL_UNSEARCHABLE로 보고 됩니다.<br /><br /> 고정 길이 및 가변 길이 이진 및 문자 데이터 형식 LONGVARCHAR 및 LONGVARBINARY 하지 않더라도 검색할 수 됩니다.|
