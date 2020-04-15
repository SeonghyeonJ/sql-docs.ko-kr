---
title: 커서 사용 (ODBC) | 마이크로 소프트 문서
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, cursors
- ODBC cursors, about ODBC cursors
- ODBC applications, cursors
- cursors [ODBC]
- ODBC cursors
ms.assetid: 51322f92-0d76-44c9-9c33-9223676cf1d3
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: be512713462a9518856de2a16db749490ea24366
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306314"
---
# <a name="using-cursors-odbc"></a>커서 사용(ODBC)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  ODBC는 다음을 허용하는 커서 모델을 지원합니다.  
  
-   여러 커서 유형  
  
-   커서 내에서 스크롤 및 위치 지정  
  
-   여러 동시성 옵션  
  
-   위치 지정 업데이트  
  
 ODBC 애플리케이션은 거의 커서를 선언하여 열거나 커서 관련 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문을 사용하지 않습니다. SQL 문에서 반환된 모든 결과 집합에 대해 ODBC에서 자동으로 커서를 엽니다. 커서의 특성은 SQL 문이 실행되기 전에 [SQLSetStmtAttr로](../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md) 설정된 문 특성에 의해 제어됩니다. 결과 집합 처리를 위한 ODBC API 함수는 인출, 스크롤 및 위치 지정 업데이트를 비롯한 모든 커서 기능을 지원합니다.  
  
 다음은 [!INCLUDE[tsql](../../includes/tsql-md.md)] 스크립트와 ODBC 애플리케이션의 커서 작업 방법을 비교한 것입니다.  
  
|작업|[!INCLUDE[tsql](../../includes/tsql-md.md)]|ODBC|  
|------------|------------------------|----------|  
|커서 동작 정의|DECLARE CURSOR 매개 변수를 통해 지정|[SQLSetStmtAttr를](../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md) 사용하여 커서 특성 설정|  
|커서 열기|커서 열기 *선언 cursor_name*|**SQLExecDirect** 또는 **SQL실행**|  
|행 인출|FETCH|**SQLFetch** 또는 [SQLFetch스크롤](../../relational-databases/native-client-odbc-api/sqlfetchscroll.md)|  
|위치 지정 업데이트|UPDATE 또는 DELETE의 WHERE CURRENT OF 절|**SQLSetPos**|  
|커서 닫기|cursor_name *cursor_name* 거래 성사 성사|[SQLCloseCursor](../../relational-databases/native-client-odbc-api/sqlclosecursor.md)|  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에 구현된 서버 커서는 ODBC 커서 모델의 기능을 지원합니다. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC 드라이버는 서버 커서를 사용하여 ODBC API의 커서 기능을 지원합니다.  
  
## <a name="in-this-section"></a>섹션 내용  
  
-   [커서 구현 방법](../../relational-databases/native-client-odbc-cursors/implementation/how-cursors-are-implemented.md)  
  
-   [커서 유형](../../relational-databases/native-client-odbc-cursors/cursor-types.md)  
  
-   [커서 동작](../../relational-databases/native-client-odbc-cursors/cursor-behaviors.md)  
  
-   [커서 속성](../../relational-databases/native-client-odbc-cursors/properties/cursor-properties.md)  
  
-   [ODBC&#41;&#40;커서 프로그래밍 세부 정보](../../relational-databases/native-client-odbc-cursors/programming/cursor-programming-details-odbc.md)  
  
-   [행 스크롤 및 페치](../../relational-databases/native-client-odbc-cursors/scrolling-and-fetching-rows.md)  
  
-   [ODBC&#41;&#40;위치 업데이트](../../relational-databases/native-client-odbc-cursors/positioned-updates-odbc.md)  
  
## <a name="see-also"></a>참고 항목  
 [SQL 서버 네이티브 클라이언트 &#40;ODBC&#41;](../../relational-databases/native-client/odbc/sql-server-native-client-odbc.md)   
 [&#40;거래 SQL&#41;닫기](../../t-sql/language-elements/close-transact-sql.md)   
 [커서](../../relational-databases/cursors.md)   
 [거래 &#40;거래 SQL&#41;거래 배치](../../t-sql/language-elements/deallocate-transact-sql.md)   
 [커서 &#40;거래 SQL&#41;선언](../../t-sql/language-elements/declare-cursor-transact-sql.md)   
 [거래 SQL&#41;&#40;가져오기](../../t-sql/language-elements/fetch-transact-sql.md)   
 [OPEN&#40;Transact-SQL&#41;](../../t-sql/language-elements/open-transact-sql.md)  
  
  
