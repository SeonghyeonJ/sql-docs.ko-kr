---
title: 커서 동시성 (ODBC) | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- concurrency [ODBC]
- cursors [ODBC], concurrency
- ODBC cursors, concurrency
ms.assetid: 68228ece-cbf1-4f19-bfdc-053884c1af48
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: b5c11ee87fe49e13bddd1a4331258a412916373b
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63014225"
---
# <a name="cursor-concurrency-odbc"></a>커서 동시성(ODBC)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  커서 작업은 커서 유형처럼 응용 프로그램에서 설정한 동시성 옵션의 영향을 받습니다. SQL_ATTR_CONCURRENCY 옵션을 사용 하 여 동시성 옵션 설정이 [SQLSetStmtAttr](../../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md)합니다. 동시성 유형은 다음과 같습니다.  
  
-   읽기 전용(SQL_CONCUR_READONLY)  
  
-   값(SQL_CONCUR_VALUES)  
  
-   행 버전(SQL_CONCUR_ROWVER)  
  
-   잠금(SQL_CONCUR_LOCK)  
  
## <a name="see-also"></a>관련 항목  
 [커서 속성](../../../relational-databases/native-client-odbc-cursors/properties/cursor-properties.md)  
  
  
