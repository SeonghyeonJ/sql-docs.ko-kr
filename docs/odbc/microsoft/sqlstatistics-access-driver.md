---
title: SQLStatistics (Access 드라이버) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Access driver [ODBC], SQLStatistics
- SQLStatistics function [ODBC], Access Driver
ms.assetid: 6117ac77-1020-4f0c-8eed-e671c34c1f21
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: bc5a354aeaf186b4baeabd96e7424939fe463bfb
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62687127"
---
# <a name="sqlstatistics-access-driver"></a>SQLStatistics(Access 드라이버)
> [!NOTE]  
>  이 항목에서는 액세스 드라이버 관련 정보를 제공 합니다. 이 함수에 대 한 일반 정보에서 해당 항목을 참조 하세요 [ODBC API 참조](../../odbc/reference/syntax/odbc-api-reference.md)합니다.  
  
|Column|주석|  
|------------|--------------|  
|TABLE_QUALIFIER|Microsoft Access 데이터베이스 파일의 경로를 반환 됩니다.<br /><br /> 패턴 일치에서 지원 되지 않습니다 합니다 *szTableQualifier* 인수입니다.|  
|TABLE_OWNER|소유자 이름입니다. 지원 되지 않으므로이 열에 NULL이 반환 됩니다.|  
|TABLE_NAME|구분 되지 않은 테이블 이름입니다.<br /><br /> 패턴 일치에서 지원 되지 않습니다 합니다 *szTableName* 인수입니다.|  
|INDEX_QUALIFIER|항상 NULL이 반환 됩니다.|  
|INDEX_NAME|인덱스에 따라 다릅니다.|  
|TYPE|형식에 대 한 SQL_TABLE_STAT 또는 SQL_INDEX_OTHER만 반환 됩니다.|  
|SEQ_IN_INDEX|인덱스에 따라 다릅니다.|  
|COLUMN_NAME|인덱스에 따라 다릅니다.|  
|COLLATION|인덱스에 따라 다릅니다.|  
|CARDINALITY|Microsoft access만 반환 합니다.|  
|PAGES|항상 NULL이 반환 됩니다.|  
  
 고유성 기반으로 필터링 (합니다 *fUnique* 인수). 합니다 *fAccuracy* 매개 변수가 무시 됩니다.
