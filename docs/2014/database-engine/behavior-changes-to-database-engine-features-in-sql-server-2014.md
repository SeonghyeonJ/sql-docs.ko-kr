---
title: SQL Server 2014의 데이터베이스 엔진 기능에 대 한 동작 변경 내용 Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- behavior changes [SQL Server]
- Database Engine [SQL Server], what's new
- Transact-SQL behavior changes
ms.assetid: 65eaafa1-9e06-4264-b547-cbee8013c995
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: b9d174bb43388af9ea3fe02d839c7a3fcfec202c
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/27/2020
ms.locfileid: "77646320"
---
# <a name="behavior-changes-to-database-engine-features-in-sql-server-2014"></a>SQL Server 2014 데이터베이스 엔진 기능의 동작 변경 내용
  이 항목에서는 [!INCLUDE[ssDE](../includes/ssde-md.md)]의 동작 변경 내용에 대해 설명합니다. 동작 변경 내용은 이전 버전의 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] 와 비교해서 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]의 기능이 작동하고 상호 작용하는 방법에 영향을 줍니다.  
  
## <a name="behavior-changes-in-sssql14"></a><a name="SQL14"></a>의 동작 변경 내용[!INCLUDE[ssSQL14](../includes/sssql14-md.md)]  
 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]의 이전 버전에서 특정 길이(4,020자 초과) 이상의 문자열을 포함하는 XML 문서에 대한 쿼리는 잘못된 결과를 반환할 수 있습니다. [!INCLUDE[ssSQL14](../includes/sssql14-md.md)]에서는 이러한 쿼리가 올바른 결과를 반환합니다.  
  
## <a name="behavior-changes-in-sssql11"></a><a name="Denali"></a>의 동작 변경 내용[!INCLUDE[ssSQL11](../includes/sssql11-md.md)]  
  
### <a name="metadata-discovery"></a>메타데이터 검색  
 [!INCLUDE[ssDE](../includes/ssde-md.md)] 부터의 향상 된 기능 [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] 으로 인해 SQLDescribeCol는 이전 버전의 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]에서 SQLDescribeCol에 의해 반환 된 결과 보다 더 정확한 결과를 얻을 수 있습니다. 자세한 내용은 [메타데이터 검색](../relational-databases/native-client/features/metadata-discovery.md)을 참조하세요.  
  
 쿼리를 실제로 실행 하지 않고 응답 형식을 결정 하는 [SET FMTONLY](/sql/t-sql/statements/set-fmtonly-transact-sql) 옵션은 transact-sql sp_describe_undeclared_parameters [&#41;&#40;sp_describe_first_result_set ](/sql/relational-databases/system-stored-procedures/sp-describe-first-result-set-transact-sql) [&#40;](/sql/relational-databases/system-stored-procedures/sp-describe-undeclared-parameters-transact-sql)transact-sql&#41;, [dm_exec_describe_first_result_set &#40;transact-sql&#41;, dm_exec_describe_first_result_set_for_object ](/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-describe-first-result-set-transact-sql) [&#40;transact-sql&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-describe-first-result-set-for-object-transact-sql)로 대체 됩니다.  
  
### <a name="changes-to-behavior-in-scripting-a-sql-server-agent-task"></a>SQL Server 에이전트 태스크의 스크립팅 동작 변경 내용  
[!INCLUDE[ssSQL11](../includes/sssql11-md.md)]부터 기존 작업에서 스크립트를 복사 하 여 새 작업을 만드는 경우 새 작업은 기존 작업에 실수로 영향을 줄 수 있습니다. 기존 작업의 스크립트를 사용 하 여 새 작업을 만들려면 일반적으로 기존 작업에서 작업 일정을 만드는 섹션의 마지막 매개 변수 * \@schedule_uid* 매개 변수를 수동으로 삭제 합니다. 이렇게 하면 기존 작업에 영향을 주지 않고 새 작업의 독립적인 새 스케줄을 만들 수 있습니다.  
  
### <a name="constant-folding-for-clr-user-defined-functions-and-methods"></a>CLR 사용자 정의 함수 및 메서드를 위한 상수 폴딩  
[!INCLUDE[ssSQL11](../includes/sssql11-md.md)]부터는 이제 다음과 같은 사용자 정의 CLR 개체가 폴딩 가능 됩니다.  

-   결정적 스칼라 반환 CLR 사용자 정의 함수  
-   CLR 사용자 정의 형식의 결정적 메서드  
  
 이러한 개선 사항은 동일한 인수를 사용하여 이러한 함수 또는 메서드를 두 번 이상 호출할 때 성능을 향상시키기 위한 것입니다. 그러나 오류에서 비결정적 함수 또는 메서드가 결정적으로 표시된 경우에는 이러한 변경으로 인해 예기치 않은 결과가 발생할 수 있습니다. CLR 함수 또는 메서드의 결정성은 `IsDeterministic` 또는 `SqlFunctionAttribute`의 `SqlMethodAttribute` 속성 값으로 표시됩니다.  
  
### <a name="behavior-of-stenvelope-method-has-changed-with-empty-spatial-types"></a>빈 공간 형식을 사용하는 STEnvelope() 메서드의 동작이 변경됨  
 이제 빈 개체를 사용하는 `STEnvelope` 메서드의 동작이 다른 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 공간 메서드의 동작과 일치합니다.  
  
 [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)]에서는 빈 개체를 사용하여 호출하는 경우 `STEnvelope` 메서드에서 다음과 같은 결과를 반환했습니다.  
  
```sql  
SELECT geometry::Parse('POINT EMPTY').STEnvelope().ToString()  
-- returns POINT EMPTY  
SELECT geometry::Parse('LINESTRING EMPTY').STEnvelope().ToString()  
-- returns LINESTRING EMPTY  
SELECT geometry::Parse('POLYGON EMPTY').STEnvelope().ToString()  
-- returns POLYGON EMPTY  
```  
  
 이제 [!INCLUDE[ssSQL11](../includes/sssql11-md.md)]에서는 빈 개체를 사용하여 호출하는 경우 `STEnvelope` 메서드에서 다음과 같은 결과를 반환합니다.  
  
```sql  
SELECT geometry::Parse('POINT EMPTY').STEnvelope().ToString()  
-- returns GEOMETRYCOLLECTION EMPTY  
SELECT geometry::Parse('LINESTRING EMPTY').STEnvelope().ToString()  
-- returns GEOMETRYCOLLECTION EMPTY  
SELECT geometry::Parse('POLYGON EMPTY').STEnvelope().ToString()  
-- returns GEOMETRYCOLLECTION EMPTY  
```  
  
 공간 개체가 비어 있는지 확인 하려면 [STIsEmpty &#40;Geometry 데이터 형식&#41;](/sql/t-sql/spatial-geometry/stisempty-geometry-data-type) 메서드를 호출 합니다.  
  
### <a name="log-function-has-new-optional-parameter"></a>로그 함수에 새로운 선택적 매개 변수 포함  
 이제 `LOG` 함수에 선택적 *기본* 매개 변수가 있습니다. 자세한 내용은 [LOG &#40;transact-sql&#41;](/sql/t-sql/functions/log-transact-sql)를 참조 하세요.  
  
### <a name="statistics-computation-during-partitioned-index-operations-has-changed"></a>분할된 인덱스 작업 중의 통계 계산이 변경됨  
[!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]에서는 분할된 인덱스를 만들거나 다시 작성할 때 테이블의 모든 행을 검색하여 통계를 작성하지 않습니다. 대신 쿼리 최적화 프로그램에서 기본 샘플링 알고리즘을 사용 하 여 통계를 생성 합니다. 분할된 인덱스로 데이터베이스를 업그레이드한 후 인덱스에 대한 히스토그램 데이터가 달라집니다. 이 동작 변경이 쿼리 성능에는 영향을 주지 않을 수 있습니다. 테이블의 모든 행을 검사하여 분할된 인덱스에 대한 통계를 얻으려면 `FULLSCAN` 절에서 `CREATE STATISTICS` 또는 `UPDATE STATISTICS`를 사용합니다.  
  
### <a name="data-type-conversion-by-the-xml-value-method-has-changed"></a>XML 값 메서드에 의한 데이터 형식 변환이 변경됨  
`value` 데이터 형식의 `xml` 메서드에 대한 내부 동작이 변경되었습니다. 이 메서드는 XML에 대해 XQuery를 수행하고 지정된 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 데이터 형식의 스칼라 값을 반환합니다. xs 형식은 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 데이터 형식으로 변환해야 합니다. 이전에는 `value` 메서드가 원본 값을 xs:string으로 내부적으로 변환한 다음 xs:string을 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 데이터 형식으로 변환했습니다. [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]에서는 다음과 같은 경우에 xs:string으로의 변환이 생략됩니다.  
  
|원본 XS 데이터 형식|대상 SQL Server 데이터 형식|  
|-------------------------|--------------------------------------|  
|byte<br /><br /> short<br /><br /> int<br /><br /> integer<br /><br /> long<br /><br /> unsignedByte<br /><br /> unsignedShort<br /><br /> unsignedInt<br /><br /> unsignedLong<br /><br /> positiveInteger<br /><br /> nonPositiveInteger<br /><br /> negativeInteger<br /><br /> nonNegativeInteger|tinyint<br /><br /> smallint<br /><br /> int<br /><br /> bigint<br /><br /> decimal<br /><br /> numeric|  
|decimal|decimal<br /><br /> numeric|  
|float|real|  
|double|float|  
  
 중간 변환을 건너뛸 수 있는 경우 새로운 동작으로 인해 성능이 향상됩니다. 그러나 데이터 형식 변환에 실패하는 경우 중간 xs:string 값에서 변환할 때 발생했던 오류 메시지와 다른 메시지가 표시됩니다. 예를 들어 value 메서드에서 `int` 값 100000을 `smallint`로 변환하는 데 실패한 경우 이전에 표시된 오류 메시지는 다음과 같습니다.  
  
 `The conversion of the nvarchar value '100000' overflowed an INT2 column. Use a larger integer column.`  
  
 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]에서는 xs:string으로의 중간 변환 없이 다음과 같은 오류 메시지가 표시됩니다.  
  
 `Arithmetic overflow error converting expression to data type smallint.`  
  
### <a name="sqlcmdexe-behavior-change-in-xml-mode"></a>XML 모드에서의 sqlcmd.exe 동작 변경 내용  
 SELECT * from T FOR XML ...을 실행할 때 XML 모드 (: XML ON 명령)에서 sqlcmd를 사용 하는 경우 동작이 변경 됩니다.  
  
### <a name="dbcc-checkident-revised-message"></a>DBCC CHECKIDENT 수정 메시지  
 [!INCLUDE[ssSQL11](../includes/sssql11-md.md)]에서 DBCC CHECKIDENT 명령을 통해 반환되는 메시지는 해당 명령을 RESEED *new_reseed_value*  에 사용하는 경우에만 현재 ID 값을 변경하도록 변경되었습니다. 새 메시지는 *"id 정보 확인: 현재 id 값 '\<현재 id 값> '"* 입니다. DBCC 실행이 완료되었습니다. DBCC에서 오류 메시지를 출력하면 시스템 관리자에게 문의하세요."  
  
 이전 버전에서 메시지는 *"id 정보 확인:\<현재 id 값 ' 현재 id 값> ', 현재 열 값 '\<현재 열 값> '입니다. DBCC 실행이 완료 되었습니다. DBCC에서 오류 메시지를 출력 하면 시스템 관리자에 게 문의 하십시오. "* 이 지정 된 경우 `DBCC CHECKIDENT` 두 번째 매개 변수 `NORESEED`를 사용 하지 않거나 초기값을 지정 하지 않고 메시지는 변경 되지 않습니다. 자세한 내용은 [DBCC CHECKIDENT&#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-checkident-transact-sql)를 참조하세요.  
  
### <a name="behavior-of-exist-function-on-xml-datatype-has-changed"></a>XML 데이터 형식에서의 exist() 함수 동작이 변경됨  
 Null 값이 있는 `exist()` XML 데이터 형식을 0 (영)으로 비교할 때 함수의 동작이 변경 되었습니다. 다음 예제를 참조하세요.  
  
```sql  
DECLARE @test XML;  
SET @test = null;  
SELECT COUNT(1) WHERE @test.exist('/dogs') = 0;  
```  
  
 이전 버전에서는 이러한 비교 시 1(true)이 반환되었는데 이제는 0(false)이 반환됩니다.  
  
 다음 비교는 변경되지 않았습니다.  
  
```sql  
DECLARE @test XML;  
SET @test = null;  
SELECT COUNT(1) WHERE @test.exist('/dogs') = 1; -- 0 expected, 0 returned  
SELECT COUNT(1) WHERE @test.exist('/dogs') IS NULL; -- 1 expected, 1 returned  
```  
  
## <a name="see-also"></a>참고 항목  
 [SQL Server 2014의 데이터베이스 엔진 기능에 대 한 주요 변경 내용](breaking-changes-to-database-engine-features-in-sql-server-2016.md)   
 [SQL Server 2014에서 사용 되지 않는 데이터베이스 엔진 기능](deprecated-database-engine-features-in-sql-server-2016.md)   
 [SQL Server 2014에서 지원 되지 않는 데이터베이스 엔진 기능](discontinued-database-engine-functionality-in-sql-server-2016.md)   
 [ALTER DATABASE 호환성 수준&#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-compatibility-level)  
  
  
