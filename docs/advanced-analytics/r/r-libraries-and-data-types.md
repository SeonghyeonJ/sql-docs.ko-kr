---
title: R-SQL 데이터 형식 변환
description: 데이터 과학 및 기계 학습 솔루션의 R과 SQL Server 간 암시적 및 명시적 데이터 형식 변환을 검토 합니다.
ms.prod: sql
ms.technology: machine-learning
ms.date: 12/10/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 7c829f39ee9c80d1bad3a4fb33c10635897cfb98
ms.sourcegitcommit: 321497065ecd7ecde9bff378464db8da426e9e14
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/01/2019
ms.locfileid: "68715095"
---
# <a name="data-type-mappings-between-r-and-sql-server"></a>R과 SQL Server 간의 데이터 형식 매핑
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

SQL Server Machine Learning Services의 R 통합 기능에서 실행 되는 R 솔루션의 경우 지원 되지 않는 데이터 형식 및 R 라이브러리와 SQL Server 간에 데이터가 전달 될 때 암시적으로 수행 될 수 있는 데이터 형식 변환의 목록을 검토 합니다.

## <a name="base-r-version"></a>기본 R 버전

SQL Server 2016 R 서비스 및 R과 SQL Server Machine Learning Services은 Microsoft R Open의 특정 릴리스에 맞춰져 있습니다. 예를 들어 최신 릴리스 SQL Server Machine Learning Services는 Microsoft R Open 3.3.3에서 빌드됩니다.

SQL Server의 특정 인스턴스와 연결 된 R 버전을 보려면 **Rgui**를 엽니다. 기본 인스턴스의 경우 경로는 다음과 같습니다.`C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\R_SERVICES\bin\x64\`

도구는 기본 R 및 기타 라이브러리를 로드 합니다. 패키지 버전 정보는 세션을 시작할 때 로드 되는 각 패키지에 대 한 알림에서 제공 됩니다. 

## <a name="r-and-sql-data-types"></a>R 및 SQL 데이터 형식

에서 수십 개의 데이터 형식을 지원하지만R에는제한된수의스칼라데이터형식(숫자,정수,복합,논리적,문자,날짜/시간및원시)이포함됩니다.[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 따라서 R 스크립트에서의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터를 사용할 때마다 데이터를 호환 되는 데이터 형식으로 암시적으로 변환할 수 있습니다. 그러나 종종 정확한 변환을 수행할 수 없으며 "처리 되지 않은 SQL 데이터 형식"과 같은 오류가 반환 됩니다.

이 섹션에서는 제공 된 암시적 변환을 나열 하 고 지원 되지 않는 데이터 형식을 나열 합니다. R과 SQL Server 간에 데이터 형식을 매핑하기 위한 몇 가지 지침이 제공 됩니다.

## <a name="implicit-data-type-conversions-between-r-and-sql-server"></a>R과 SQL Server 간 암시적 데이터 형식 변환

다음 표는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 의 데이터를 R 스크립트에 사용한 다음 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]로 반환할 때 데이터 형식 및 값의 변화를 보여줍니다.

|SQL 유형|R 클래스|RESULT SET 형식|주석|
|-|-|-|-|
|**bigint**|`numeric`|**float**||
|**binary(n)**<br /><br /> n <= 8000|`raw`|**varbinary(max)**|입력 매개 변수 및 출력으로만 허용됨|
|**bit**|`logical`|**bit**||
|**char(n)**<br /><br /> n <= 8000|`character`|**varchar(max)**||
|**datetime**|`POSIXct`|**datetime**|GMT로 표시됨|
|**date**|`POSIXct`|**datetime**|GMT로 표시됨|
|**decimal(p,s)**|`numeric`|**float**||
|**float**|`numeric`|**float**||
|**int**|`integer`|**int**||
|**money**|`numeric`|**float**||
|**numeric(p,s)**|`numeric`|**float**||
|**real**|`numeric`|**float**||
|**smalldatetime**|`POSIXct`|**datetime**|GMT로 표시됨|
|**smallint**|`integer`|**int**||
|**smallmoney**|`numeric`|**float**||
|**tinyint**|`integer`|**int**||
|**uniqueidentifier**|`character`|**varchar(max)**||
|**varbinary(n)**<br /><br /> n <= 8000|`raw`|**varbinary(max)**|입력 매개 변수 및 출력으로만 허용됨|
|**varbinary(max)**|`raw`|**varbinary(max)**|입력 매개 변수 및 출력으로만 허용됨|
|**varchar(n)**<br /><br /> n <= 8000|`character`|**varchar(max)**||


## <a name="data-types-not-supported-by-r"></a>R에서 지원되지 않는 데이터 형식

[SQL Server 형식 시스템](../../t-sql/data-types/data-types-transact-sql.md)에서 지원되는 데이터 형식의 범주 중에서 다음 형식은 R 코드에 전달될 때 문제를 일으킬 수 있습니다.

+ SQL 유형 시스템 아티클의 **다른** 섹션에 나열 된 데이터 형식: **cursor**, **timestamp**, **hierarchyid**, **uniqueidentifier**, **sql_variant**, **xml**, **테이블**
+ 모든 공간 형식
+ **image**

## <a name="data-types-that-might-convert-poorly"></a>잘못 변환될 수 있는 데이터 형식

+ **datetimeoffset**을 제외한 대부분의 datetime 형식이 작동해야 합니다. 
+ 대부분의 숫자 데이터 형식이 지원되지만 **money** 및 **smallmoney**에 대한 변환은 실패할 수 있습니다.
+ **varchar**가 지원되지만 SQL Server는 유니코드를 규칙으로 사용하므로 가능하면 **nvarchar** 및 기타 유니코드 텍스트 데이터 형식을 사용하는 것이 좋습니다.
+ RevoScaleR 라이브러리에서 접두사가 rx인 함수는 SQL 이진 데이터 형식(**binary** 및 **varbinary**)을 처리할 수 있지만 대부분의 시나리오에서는 이러한 형식에 대한 특수 처리가 필요합니다. 이진 열을 사용할 경우 대부분의 R 코드가 작동하지 않을 수 있습니다.

  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터 형식에 대한 자세한 내용은 [데이터 형식&#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)을 참조하세요.

## <a name="changes-in-data-types-between-sql-server-2016-and-earlier-versions"></a>SQL Server 2016 이하 버전 간의 데이터 형식 변경 내용

Microsoft SQL Server 2016 및 Microsoft Azure SQL Database의 데이터 형식 변환 및 여러 가지 기타 작업이 향상되었습니다. 대부분의 이러한 향상된 기능에서는 유동 소수점 형식을 처리할 때 전체 자릿수가 증가하고 클래식 **datetime** 형식에 대한 작업이 약간 변경됩니다.

이러한 향상된 기능은 모두 130 이상의 데이터베이스 호환성 수준을 사용할 경우 기본적으로 사용할 수 있습니다. 하지만 다른 호환성 수준을 사용하거나 이전 버전으로 데이터베이스에 연결하면 숫자의 전체 자릿수 또는 기타 결과에 차이가 나타날 수 있습니다. 

자세한 내용은 [SQL Server 2016 improvements in handling some data types and uncommon operations](https://support.microsoft.com/help/4010261/sql-server-2016-improvements-in-handling-some-data-types-and-uncommon-)(일부 데이터 형식 및 일반적이지 않은 작업 처리 시 SQL Server 2016의 향상된 기능)를 참조하세요.
 

## <a name="verify-r-and-sql-data-schemas-in-advance"></a>R 및 SQL 데이터 스키마 미리 확인 

일반적으로 특정 데이터 형식 또는 데이터 구조가 R에서 어떻게 사용되는지 잘 모를 경우  `str()` 함수를 사용하여 R개체의 내부 구조와 형식을 가져옵니다. 함수 결과는 R 콘솔에 인쇄되며 **의** 메시지 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]탭에서 쿼리 결과로도 확인할 수 있습니다. 

R 코드에서 사용할 데이터베이스에서 데이터를 검색할 때는 항상 R에서 사용할 수 없는 열을 제거 하 고, 분석에 유용 하지 않은 열 (예: GUID (uniqueidentifier), 감사에 사용 되는 타임 스탬프 및 기타 열)을 제거 해야 합니다. ETL 프로세스에 의해 생성 된 정보입니다. 

불필요한 열을 포함하면, 특히 카디널리티가 높은 열이 요소로 사용될 경우 R 코드의 성능이 크게 저하될 수 있습니다. 따라서 SQL Server 시스템 저장 프로시저 및 정보 뷰를 사용하여 지정된 테이블에 대한 데이터 형식을 미리 가져오고 호환되지 않는 열을 제거하거나 변환하는 것이 좋습니다. 자세한 내용은 [시스템 정보 스키마 뷰(TRANSACT-SQL)](../../relational-databases/system-information-schema-views/system-information-schema-views-transact-sql.md)를 참조하세요.

R에서 특정 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터 형식을 지원하지 않지만 R 스크립트에서 데이터 열을 사용해야 하는 경우 [CAST 및 CONVERT&#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md) 함수를 사용하여 R 스크립트에서 데이터를 사용하기 전에 데이터 형식 변환이 의도한 대로 시행되었는지 확인하는 것이 좋습니다.  

> [!WARNING]
> 데이터를 이동하는 동안 **rxDataStep**을 사용하여 호환되지 않는 열을 삭제할 경우 **RxSqlServerData** 데이터 원본 형식에는 인수 _varsToKeep_ 및 _varsToDrop_이 지원되지 않습니다.


## <a name="examples"></a>예

### <a name="example-1-implicit-conversion"></a>예제 1: 암시적 변환

다음 예제에서는 SQL Server와 R 간에 왕복을 수행할 때 데이터를 변환하는 방법을 보여 줍니다.

이 쿼리는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 테이블에서 일련의 값을 가져오며 [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md) 저장 프로시저를 사용 하 여 R 런타임을 사용 하 여 값을 출력 합니다.

```sql
CREATE TABLE MyTable (    
 c1 int,    
 c2 varchar(10),    
 c3 uniqueidentifier    
);    
go    
INSERT MyTable VALUES(1, 'Hello', newid());    
INSERT MyTable VALUES(-11, 'world', newid());    
SELECT * FROM MyTable;    
  
EXECUTE sp_execute_external_script    
 @language = N'R'    
 , @script = N'    
inputDataSet["cR"] <- c(4, 2)    
str(inputDataSet)    
outputDataSet <- inputDataSet'    
 , @input_data_1 = N'SELECT c1, c2, c3 FROM MyTable'    
 , @input_data_1_name = N'inputDataSet'    
 , @output_data_1_name = N'outputDataSet'    
 WITH RESULT SETS((C1 int, C2 varchar(max), C3 varchar(max), C4 float));  
```

**결과**

||||||
|-|-|-|-|-|
||C1|C2|C3|C4|
|1|1|Hello|6e225611-4b58-4995-a0a5-554d19012ef1|4|
|1|-11|world|6732ea46-2d5d-430b-8ao1-86e7f3351c3e|2|

R에서 `str` 함수를 사용할 경우 출력 데이터의 스키마를 가져옵니다. 이 함수는 다음 정보를 반환합니다.

<code>'data.frame':2 obs. of  4 variables:</code>
<code> $ c1: int  1 -11</code>
<code> $ c2: Factor w/ 2 levels "Hello","world": 1 2</code>
<code> $ c3: Factor w/ 2 levels "6732EA46-2D5D-430B-8A01-86E7F3351C3E",..: 2 1</code>
<code> $ cR: num  4 2</code>

여기에서 이 쿼리의 일환으로 다음의 데이터 형식 변환이 암시적으로 실행된 것을 볼 수 있습니다.

-   **열 C1**: 이 열은 **ssNoversion** 에서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], R에서 `integer` , 출력 결과 집합에서 **ssNoversion** 로 표시됩니다.  
  
     형식 변환은 실행되지 않았습니다.  
  
-   **열 C2**: 이 열은 **ssNoversion** 에서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], R에서 `factor` , 출력 결과 집합에서 **varchar(max)** 로 표시됩니다.  
  
     출력이 어떻게 달라지는지 확인하십시오. R의 문자열(인수 또는 일반 문자열)은 문자열의 길이와 상관없이 **varchar(max)** 로 표시됩니다.  
  
-   **열 C3**:  이 열은 **ssNoversion** 에서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], R에서 `character` , 출력 결과 집합에서 **varchar(max)** 로 표시됩니다.
  
     여기서 실행된 데이터 형식 변환을 주목하십시오. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 는 **ssNoversion** 를 지원하지만 R은 그렇지 않습니다. 따라서 식별자는 문자열로 표시됩니다.
  
-   **열 C4**: 이 열에는 R 스크립트에서 생성된 값이 포함되며 원본 데이터에 표시되지 않습니다.


## <a name="example-2-dynamic-column-selection-using-r"></a>예제 2: R을 사용 하 여 동적 열 선택

다음 예제에서는 R 코드를 사용하여 잘못된 열 형식이 있는지 확인하는 방법을 보여 줍니다. SQL Server 시스템 뷰를 사용하여 지정된 테이블의 스키마를 가져오고 지정된 잘못된 형식이 포함된 열을 제거합니다.

```R
connStr <- "Server=.;Database=TestDB;Trusted_Connection=Yes"
data <- RxSqlServerData(connectionString = connStr, sqlQuery = "SELECT COLUMN_NAME FROM TestDB.INFORMATION_SCHEMA.COLUMNS WHERE TABLE_NAME = N'testdata' AND DATA_TYPE <> 'image';")
columns <- rxImport(data)
columnList <- do.call(paste, c(as.list(columns$COLUMN_NAME), sep = ","))
sqlQuery <- paste("SELECT", columnList, "FROM testdata")
```

## <a name="see-also"></a>참조

