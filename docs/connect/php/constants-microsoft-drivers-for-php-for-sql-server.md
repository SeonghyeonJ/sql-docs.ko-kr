---
title: 상수(Microsoft Drivers for PHP for SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 02/11/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- constants
ms.assetid: 9727c944-b645-48d6-9012-18dbde35ee3c
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 4081e9db30e3607d783de40a71d9d7b2e7599c76
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/29/2020
ms.locfileid: "67993696"
---
# <a name="constants-microsoft-drivers-for-php-for-sql-server"></a>상수(Microsoft Drivers for PHP for SQL Server)
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

이 항목에서는 [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]에서 정의된 상수를 설명합니다.  
  
## <a name="pdo_sqlsrv-driver-constants"></a>PDO_SQLSRV 드라이버 상수  
[PDO 웹 사이트](https://php.net/manual/book.pdo.php)에 나열된 상수는 [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]에서 유효합니다.  
  
다음은 PDO_SQLSRV 드라이버의 Microsoft 관련 상수를 설명합니다.  
  
### <a name="transaction-isolation-level-constants"></a>트랜잭션 격리 수준 상수  
**TransactionIsolation** 키로, [PDO::__construct](../../connect/php/pdo-construct.md)와 함께 사용되며 다음 상수 중 하나를 허용합니다.  
  
-   PDO::SQLSRV_TXN_READ_UNCOMMITTED  
  
-   PDO::SQLSRV_TXN_READ_COMMITTED  
  
-   PDO::SQLSRV_TXN_REPEATABLE_READ  
  
-   PDO::SQLSRV_TXN_SNAPSHOT  
  
-   PDO::SQLSRV_TXN_SERIALIZABLE  
  
**TransactionIsolation** 키에 대한 자세한 내용은 [Connection Options](../../connect/php/connection-options.md)를 참조하세요.  
  
### <a name="encoding-constants"></a>인코딩 상수  
PDO::SQLSRV_ATTR_ENCODING 특성은 [PDOStatement::setAttribute](../../connect/php/pdostatement-setattribute.md), [PDO::setAttribute](../../connect/php/pdo-setattribute.md), [PDO::prepare](../../connect/php/pdo-prepare.md), [PDOStatement::bindColumn](../../connect/php/pdostatement-bindcolumn.md) 및 [PDOStatement::bindParam](../../connect/php/pdostatement-bindparam.md)에 전달될 수 있습니다.  
  
PDO::SQLSRV_ATTR_ENCODING에 전달할 수 있는 값은 다음과 같습니다.  
  
|PDO_SQLSRV 드라이버 상수|Description|  
|-------------------------------|---------------|  
|PDO::SQLSRV_ENCODING_BINARY|데이터는 인코딩 또는 변환을 수행하지 않고 서버에서 반환되는 원시 바이트 스트림입니다.<br /><br />PDO::setAttribute에 유효하지 않습니다.|  
|PDO::SQLSRV_ENCODING_SYSTEM|데이터는 시스템에 설정된 Windows 로캘의 코드 페이지에 지정된 8비트 문자입니다. 모든 멀티바이트 문자 또는 이 코드 페이지에 매핑되지 않는 문자는 싱글바이트 물음표(?) 문자로 대체됩니다.|  
|PDO::SQLSRV_ENCODING_UTF8|데이터는 UTF-8 인코딩 형식입니다. 이는 기본 인코딩입니다.|  
|PDO::SQLSRV_ENCODING_DEFAULT|연결하는 동안 지정된 경우 PDO::SQLSRV_ENCODING_SYSTEM을 사용합니다.<br /><br />prepare 문에 지정된 경우 연결의 인코딩을 사용합니다.|  
  
### <a name="query-timeout"></a>쿼리 제한 시간  
PDO::SQLSRV_ATTR_QUERY_TIMEOUT 특성은 시간 제한 기간(초)을 나타내는 음수가 아닌 정수입니다. 0이 기본값이며 시간 제한이 없다는 것입니다.  
  
[PDOStatement::setAttribute](../../connect/php/pdostatement-setattribute.md), [PDO::setAttribute](../../connect/php/pdo-setattribute.md) 및 [PDO::prepare](../../connect/php/pdo-prepare.md)를 사용하여 PDO::SQLSRV_ATTR_QUERY_TIMEOUT 특성을 지정할 수 있습니다.  
  
### <a name="direct-or-prepared-execution"></a>직접 또는 준비된 실행  
PDO::SQLSRV_ATTR_DIRECT_QUERY 특성을 사용하여 직접 쿼리 실행 또는 준비된 문 실행을 선택할 수 있습니다. PDO::SQLSRV_ATTR_DIRECT_QUERY는 [PDO::prepare](../../connect/php/pdo-prepare.md) 또는 [PDO::setAttribute](../../connect/php/pdo-setattribute.md)를 사용하여 설정될 수 있습니다. PDO::SQLSRV_ATTR_DIRECT_QUERY에 대한 자세한 내용은 [PDO_SQLSRV 드라이버에서 직접 명령문 실행 및 준비된 명령문 실행](../../connect/php/direct-statement-execution-prepared-statement-execution-pdo-sqlsrv-driver.md)을 참조하세요.  

### <a name="handling-numeric-fetches"></a>숫자 페치 처리
PDO::SQLSRV_ATTR_FETCHES_NUMERIC_TYPE 특성은 숫자 SQL 형식(bit, integer, smallint, tinyint, float, real)을 사용하여 열에서 숫자 페치를 처리하는 데 사용할 수 있습니다. PDO::SQLSRV_ATTR_FETCHES_NUMERIC_TYPE가 true로 설정되면 정수 열의 결과는 int로 표시되는 반면 SQL 부동 소수점 수 및 실수는 float로 표시됩니다. 이 특성은 [PDOStatement::setAttribute](../../connect/php/pdostatement-setattribute.md)를 사용하여 설정할 수 있습니다. 

PDO::SQLSRV_ATTR_FORMAT_DECIMALS 및 PDO::SQLSRV_ATTR_DECIMAL_PLACES 특성을 사용하여 기본 10진수 서식 지정 동작을 수정할 수 있습니다. 이러한 특성의 동작은 출력 매개 변수가 서식 지정에 지원되지 않는다는 점을 제외하고 SQLSRV 쪽 해당 옵션(**FormatDecimals** 및 **DecimalPlaces**)과 동일합니다. 이러한 특성은 [PDO::setAttribute](../../connect/php/pdo-setattribute.md) 또는 [PDOStatement::setAttribute](../../connect/php/pdostatement-setattribute.md)를 사용하여 연결 또는 문 수준에서 설정할 수 있지만 모든 문 특성은 해당 연결 특성을 재정의합니다. 자세한 내용은 [Formatting Decimal Strings and Money Values (PDO_SQLSRV Driver)](../../connect/php/formatting-decimals-pdo-sqlsrv-driver.md)(10진수 문자열 및 Money 값 서식 지정(PDO_SQLSRV 드라이버))를 참조하세요.

### <a name="handling-date-and-time-fetches"></a>날짜 및 시간 페치 처리

PDO::SQLSRV_ATTR_FETCHES_DATETIME_TYPE는 날짜 및 시간 형식을 [PHP DateTime](http://php.net/manual/en/class.datetime.php) 개체로 검색할지 여부를 지정합니다. false로 유지하면 기본적으로 문자열로 반환됩니다. 이러한 특성은 [PDO::setAttribute](../../connect/php/pdo-setattribute.md) 또는 [PDOStatement::setAttribute](../../connect/php/pdostatement-setattribute.md)를 사용하여 연결 또는 문 수준에서 설정할 수 있지만 문 특성은 해당 연결 특성을 재정의합니다. 자세한 내용은 [방법: PDO_SQLSRV 드라이버를 사용하여 날짜 및 시간 형식을 PHP DateTime 개체로 검색](../../connect/php/how-to-retrieve-datetime-objects-using-pdo-sqlsrv-driver.md)을 참조하세요.

## <a name="sqlsrv-driver-constants"></a>SQLSRV 드라이버 상수  
다음 섹션에서는 SQLSRV 드라이버에서 사용되는 상수를 나열합니다.  
  
### <a name="err-constants"></a>ERR 상수  
다음 표는 [sqlsrv_errors](../../connect/php/sqlsrv-errors.md)가 오류, 경고 또는 둘 다 반환하는지 여부를 지정하는 데 사용되는 상수를 나열합니다.  
  
|값|Description|  
|---------|---------------|  
|SQLSRV_ERR_ALL|마지막 **sqlsrv** 함수 호출 시 생성된 오류 및 경고가 반환됩니다. 이것은 기본값입니다.|  
|SQLSRV_ERR_ERRORS|마지막 **sqlsrv** 함수 호출 시 생성된 오류가 반환됩니다.|  
|SQLSRV_ERR_WARNINGS|마지막 **sqlsrv** 함수 호출 시 생성된 경고가 반환됩니다.|  
  
### <a name="fetch-constants"></a>FETCH 상수  
다음 표는 [sqlsrv_fetch_array](../../connect/php/sqlsrv-fetch-array.md)에서 반환된 배열 유형을 지정하는 데 사용되는 상수를 나열합니다.  
  
|SQLSRV 상수|Description|  
|-------------------|---------------|  
|SQLSRV_FETCH_ASSOC|**sqlsrv_fetch_array** 는 데이터의 다음 행을 결합형 배열로 반환합니다.|  
|SQLSRV_FETCH_BOTH|**sqlsrv_fetch_array** 는 데이터의 다음 행을 숫자와 결합형 키를 모두 가진 배열로 반환합니다. 이것은 기본값입니다.|  
|SQLSRV_FETCH_NUMERIC|**sqlsrv_fetch_array** 는 데이터의 다음 행을 숫자로 인덱싱된 배열로 반환합니다.|  
  
### <a name="logging-constants"></a>로깅 상수  
이 섹션에서는 [sqlsrv_configure](../../connect/php/sqlsrv-configure.md)를 사용하여 로깅 설정을 변경하는 데 사용되는 상수를 나열합니다. 로깅 작업에 대한 자세한 내용은 [Logging Activity](../../connect/php/logging-activity.md)을 참조하세요.  
  
다음 표는 **LogSubsystems** 설정에 대한 값으로 사용할 수 있는 상수를 나열합니다.  
  
|SQLSRV 상수(괄호 안의 정수)|Description|  
|----------------------------------------------------------|---------------|  
|SQLSRV_LOG_SYSTEM_ALL(-1)|모든 하위 시스템의 로깅을 설정합니다.|  
|SQLSRV_LOG_SYSTEM_CONN(2)|연결 작업의 로깅을 설정합니다.|  
|SQLSRV_LOG_SYSTEM_INIT(1)|초기화 작업의 로깅을 설정합니다.|  
|SQLSRV_LOG_SYSTEM_OFF(0)|로깅을 해제합니다.|  
|SQLSRV_LOG_SYSTEM_STMT(4)|문 작업의 로깅을 설정합니다.|  
|SQLSRV_LOG_SYSTEM_UTIL(8)|오류 함수 작업(예: **handle_error** 및 **handle_warning**)의 로깅을 설정합니다.|  
  
다음 표는 **LogSeverity** 설정에 대한 값으로 사용할 수 있는 상수를 나열합니다.  
  
|SQLSRV 상수(괄호 안의 정수)|Description|  
|----------------------------------------------------------|---------------|  
|SQLSRV_LOG_SEVERITY_ALL(-1)|오류, 경고 및 알림이 기록된다는 것을 지정합니다.|  
|SQLSRV_LOG_SEVERITY_ERROR(1)|오류가 기록된다는 것을 지정합니다.|  
|SQLSRV_LOG_SEVERITY_NOTICE(4)|알림이 기록된다는 것을 지정합니다.|  
|SQLSRV_LOG_SEVERITY_WARNING(2)|경고가 기록된다는 것을 지정합니다.|  
  
### <a name="nullable-constants"></a>Null을 허용하는 상수  
다음 표는 열이 Null을 허용하는지 여부 또는 이 정보를 사용할 수 있는지 여부를 확인하는 데 사용할 수 있는 상수를 나열합니다. 열의 null 허용 상태를 확인하려면 **sqlsrv_field_metadata** 에서 반환되는 [Nullable](../../connect/php/sqlsrv-field-metadata.md) 키의 값을 비교하면 됩니다.  
  
|SQLSRV 상수(괄호 안의 정수)|Description|  
|----------------------------------------------------------|---------------|  
|SQLSRV_NULLABLE_YES(0)|열이 Null을 허용합니다.|  
|SQLSRV_NULLABLE_NO(1)|열이 Null을 허용하지 않습니다.|  
|SQLSRV_NULLABLE_UNKNOWN(2)|열이 Null을 허용하는지 여부를 알 수 없습니다.|  
  
### <a name="param-constants"></a>PARAM 상수  
다음 목록에는 [sqlsrv_query](../../connect/php/sqlsrv-query.md) 또는 [sqlsrv_prepare](../../connect/php/sqlsrv-prepare.md)를 호출할 때 매개 변수 방향을 지정하기 위한 상수가 들어 있습니다.  
  
|SQLSRV 상수|Description|  
|-------------------|---------------|  
|SQLSRV_PARAM_IN|입력 매개 변수를 나타냅니다.|  
|SQLSRV_PARAM_INOUT|양방향 매개 변수를 나타냅니다.|  
|SQLSRV_PARAM_OUT|출력 매개 변수를 나타냅니다.|  
  
### <a name="phptype-constants"></a>PHPTYPE 상수  
다음 표는 PHP 데이터 형식을 설명하는 데 사용되는 상수를 나열합니다. PHP 데이터 형식에 대한 자세한 내용은 [PHP 형식](https://php.net/manual/en/language.types.php)을 참조하세요.  
  
|SQLSRV 상수|PHP 데이터 형식|  
|-------------------|-----------------|  
|SQLSRV_PHPTYPE_INT|정수|  
|SQLSRV_PHPTYPE_DATETIME|DateTime|  
|SQLSRV_PHPTYPE_FLOAT|Float|  
|SQLSRV_PHPTYPE_STREAM($encoding<sup>1</sup>)|STREAM|  
|SQLSRV_PHPTYPE_STRING($encoding<sup>1</sup>)|String|  
  
1. **SQLSRV_PHPTYPE_STREAM** 및 **SQLSRV_PHPTYPE_STRING**은 스트림 인코딩을 지정하는 매개 변수를 수락합니다. 다음 표에는 허용 가능한 매개 변수인 SQLSRV 상수 및 해당 인코딩에 대한 설명이 있습니다.  
  
|SQLSRV 상수|Description|  
|-------------------|---------------|  
|SQLSRV_ENC_BINARY|데이터는 인코딩 또는 변환을 수행하지 않은 원시 바이트 스트림으로 서버에서 반환됩니다.|  
|SQLSRV_ENC_CHAR|데이터는 시스템에 설정된 Windows 로캘의 코드 페이지에 지정된 8비트 문자로 반환됩니다. 모든 멀티바이트 문자 또는 이 코드 페이지에 매핑되지 않는 문자는 싱글바이트 물음표(?) 문자로 대체됩니다.<br /><br />이는 기본 인코딩입니다.|  
|"UTF-8"|데이터는 UTF-8 인코딩으로 반환됩니다. 이 상수가 [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]의 버전 1.1에 추가되었습니다. UTF-8 지원에 대한 자세한 내용은 [방법: 기본 제공 UTF-8 지원을 사용하여 UTF-8 데이터를 보내기 및 검색](../../connect/php/how-to-send-and-retrieve-utf-8-data-using-built-in-utf-8-support.md)을 참조하세요.|  
  
> [!NOTE]  
> **SQLSRV_PHPTYPE_STREAM** 또는 **SQLSRV_PHPTYPE_STRING**을 사용하는 경우 인코딩이 지정되어야 합니다. 매개 변수가 제공되지 않으면 오류가 반환됩니다.  
  
이러한 상수에 대한 자세한 내용은 [방법: PHP 데이터 형식 지정](../../connect/php/how-to-specify-php-data-types.md), [방법: SQLSRV 드라이버를 사용하여 스트림으로 문자 데이터 가져오기](../../connect/php/how-to-retrieve-character-data-as-a-stream-using-the-sqlsrv-driver.md)를 참조하세요.  
  
### <a name="sqltype-constants"></a>SQLTYPE 상수  
다음 표는 SQL Server 데이터 형식을 설명하는 데 사용되는 상수를 나열합니다. 일부 상수는 함수와 유사하며 전체 자릿수, 소수 자릿수 및/또는 길이에 해당하는 매개 변수를 사용할 수 있습니다.  매개 변수를 바인딩하는 경우 함수 형태 상수를 사용해야 합니다. 형식 비교의 경우 표준(비함수 형식) 상수가 필요합니다. SQL Server 데이터 형식에 대한 자세한 내용은 [데이터 형식(Transact-SQL)](../../t-sql/data-types/data-types-transact-sql.md)을 참조하세요. 전체 자릿수, 소수 자릿수 및 길이에 대한 자세한 내용은 [전체 자릿수, 소수 자릿수 및 길이(Transact-SQL)](../../t-sql/data-types/precision-scale-and-length-transact-sql.md)를 참조하세요.  
  
|SQLSRV 상수|SQL Server 데이터 형식|  
|-------------------|------------------------|  
|SQLSRV_SQLTYPE_BIGINT|bigint|  
|SQLSRV_SQLTYPE_BINARY|binary|  
|SQLSRV_SQLTYPE_BIT|bit|  
|SQLSRV_SQLTYPE_CHAR|char<sup>5</sup>|  
|SQLSRV_SQLTYPE_CHAR($charCount)|char|  
|SQLSRV_SQLTYPE_DATE|date<sup>4</sup>|  
|SQLSRV_SQLTYPE_DATETIME|Datetime|  
|SQLSRV_SQLTYPE_DATETIME2|datetime2<sup>4</sup>|  
|SQLSRV_SQLTYPE_DATETIMEOFFSET|datetimeoffset<sup>4</sup>|  
|SQLSRV_SQLTYPE_DECIMAL|decimal<sup>5</sup>|
|SQLSRV_SQLTYPE_DECIMAL($precision, $scale)|decimal|  
|SQLSRV_SQLTYPE_FLOAT|float|  
|SQLSRV_SQLTYPE_IMAGE|image<sup>1</sup>|  
|SQLSRV_SQLTYPE_INT|int|  
|SQLSRV_SQLTYPE_MONEY|money| 
|SQLSRV_SQLTYPE_NCHAR|nchar<sup>5</sup>|   
|SQLSRV_SQLTYPE_NCHAR($charCount)|nchar|  
|SQLSRV_SQLTYPE_NUMERIC|numeric<sup>5</sup>|
|SQLSRV_SQLTYPE_NUMERIC($precision, $scale)|numeric|  
|SQLSRV_SQLTYPE_NVARCHAR|nvarchar<sup>5</sup>|  
|SQLSRV_SQLTYPE_NVARCHAR($charCount)|nvarchar|  
|SQLSRV_SQLTYPE_NVARCHAR('max')|nvarchar(MAX)|  
|SQLSRV_SQLTYPE_NTEXT|ntext<sup>2</sup>|  
|SQLSRV_SQLTYPE_REAL|real|  
|SQLSRV_SQLTYPE_SMALLDATETIME|smalldatetime|  
|SQLSRV_SQLTYPE_SMALLINT|smallint|  
|SQLSRV_SQLTYPE_SMALLMONEY|smallmoney|  
|SQLSRV_SQLTYPE_TEXT|text<sup>3</sup>|  
|SQLSRV_SQLTYPE_TIME|time<sup>4</sup>|  
|SQLSRV_SQLTYPE_TIMESTAMP|timestamp|  
|SQLSRV_SQLTYPE_TINYINT|tinyint|  
|SQLSRV_SQLTYPE_UNIQUEIDENTIFIER|uniqueidentifier|  
|SQLSRV_SQLTYPE_UDT|UDT|  
|SQLSRV_SQLTYPE_VARBINARY|varbinary<sup>5</sup>|  
|SQLSRV_SQLTYPE_VARBINARY($byteCount)|varbinary|  
|SQLSRV_SQLTYPE_VARBINARY('max')|varbinary(MAX)|  
|SQLSRV_SQLTYPE_VARCHAR|varchar<sup>5</sup>|  
|SQLSRV_SQLTYPE_VARCHAR($charCount)|varchar|  
|SQLSRV_SQLTYPE_VARCHAR('max')|varchar(MAX)|  
|SQLSRV_SQLTYPE_XML|Xml|  
  
1.  varbinary(max) 형식에 매핑되는 레거시 형식입니다.  
  
2.  최신 nvarchar 형식에 매핑되는 레거시 형식입니다.  
  
3.  최신 varchar 형식에 매핑되는 레거시 형식입니다.  
  
4.  이 형식에 대한 지원이 [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]의 버전 1.1에 추가되었습니다.  

5.  이러한 상수는 형식 비교 연산에서 사용해야 하며 함수 유형 상수를 유사한 구문으로 바꾸지 않습니다. 매개 변수를 바인딩하는 경우 함수 형태 상수를 사용해야 합니다.

  
다음 표는 매개 변수 및 매개 변수에 허용되는 값 범위를 수락하는 SQLTYPE 상수를 나열합니다.  
  
|SQLTYPE|매개 변수|매개 변수에 대한 허용 범위|  
|-----------|-------------|---------------------------------|  
|SQLSRV_SQLTYPE_CHAR,<br /><br />SQLSRV_SQLTYPE_VARCHAR|charCount|1 - 8000|  
|SQLSRV_SQLTYPE_NCHAR,<br /><br />SQLSRV_SQLTYPE_NVARCHAR|charCount|1 - 4000|  
|SQLSRV_SQLTYPE_BINARY,<br /><br />SQLSRV_SQLTYPE_VARBINARY|byteCount|1 - 8000|  
|SQLSRV_SQLTYPE_DECIMAL,<br /><br />SQLSRV_SQLTYPE_NUMERIC|자릿수|1 - 38|  
|SQLSRV_SQLTYPE_DECIMAL,<br /><br />SQLSRV_SQLTYPE_NUMERIC|소수 자릿수|1 - 전체 자릿수|  
  
### <a name="transaction-isolation-level-constants"></a>트랜잭션 격리 수준 상수  
**TransactionIsolation** 키로, [sqlsrv_connect](../../connect/php/sqlsrv-connect.md)와 함께 사용되며 다음 상수 중 하나를 허용합니다.  
  
-   SQLSRV_TXN_READ_UNCOMMITTED  
  
-   SQLSRV_TXN_READ_COMMITTED  
  
-   SQLSRV_TXN_REPEATABLE_READ  
  
-   SQLSRV_TXN_SNAPSHOT  
  
-   SQLSRV_TXN_SERIALIZABLE  
  
### <a name="cursor-and-scrolling-constants"></a>커서 및 스크롤 가능 상수  
다음 상수는 결과 집합에서 사용할 수 있는 커서의 종류를 지정합니다.  
  
-   SQLSRV_CURSOR_FORWARD  
  
-   SQLSRV_CURSOR_STATIC  
  
-   SQLSRV_CURSOR_DYNAMIC  
  
-   SQLSRV_CURSOR_KEYSET  
  
-   SQLSRV_CURSOR_CLIENT_BUFFERED  
  
다음 상수는 결과 집합에서 선택할 행을 지정합니다.  
  
-   SQLSRV_SCROLL_NEXT  
  
-   SQLSRV_SCROLL_PRIOR  
  
-   SQLSRV_SCROLL_FIRST  
  
-   SQLSRV_SCROLL_LAST  
  
-   SQLSRV_SCROLL_ABSOLUTE  
  
-   SQLSRV_SCROLL_RELATIVE  
  
이러한 상수를 사용하는 방법에 대한 자세한 내용은 [Specifying a Cursor Type and Selecting Rows](../../connect/php/specifying-a-cursor-type-and-selecting-rows.md)을 참조하세요.  
  
## <a name="see-also"></a>참고 항목  
[SQLSRV 드라이버 API 참조](../../connect/php/sqlsrv-driver-api-reference.md)  
  
