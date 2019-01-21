---
title: LIKE (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- ESCAPE
- LIKE
- ESCAPE_TSQL
- LIKE_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- ESCAPE keyword
- '% (wildcard - character(s) to match)'
- ASCII pattern matching
- pattern searching [SQL Server]
- wildcard characters [SQL Server]
- literals [SQL Server], using wildcards
- character strings [SQL Server], LIKE
- exact matches [SQL Server]
- Boolean functions
- LIKE comparisons
- matching patterns [SQL Server]
- NOT LIKE keyword
ms.assetid: 581fb289-29f9-412b-869c-18d33a9e93d5
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: e7d8bfaf8e2b07bd34843893a67a823e6841b6d6
ms.sourcegitcommit: 96032813f6bf1cba680b5e46d82ae1f0f2da3d11
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/15/2019
ms.locfileid: "54299990"
---
# <a name="like-transact-sql"></a>LIKE(Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  > [!div class="nextstepaction"]
  > [SQL Docs 목차에 대한 피드백을 공유하세요!](https://aka.ms/sqldocsurvey)

  특정 문자열이 지정된 패턴과 일치하는지를 확인합니다. 패턴은 일반 문자와 와일드카드 문자를 포함할 수 있습니다. 패턴 일치에서 일반 문자는 문자열에 지정된 문자와 정확하게 일치해야 합니다. 그러나 와일드카드 문자는 문자열에서 어느 한 부분만 일치하면 됩니다. LIKE 연산자에 와일드카드 문자를 사용할 경우 = 및 != 문자열 비교 연산자를 사용하는 것보다 훨씬 융통성이 있습니다. 문자열 데이터 형식의 인수가 하나라도 있을 경우 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]에서는 가능한 한 이를 문자열 데이터 형식으로 변환합니다.  
  
 ![항목 링크 아이콘](../../database-engine/configure-windows/media/topic-link.gif "항목 링크 아이콘") [Transact-SQL 구문 규칙](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>구문  
  
```  
-- Syntax for SQL Server and Azure SQL Database  
  
match_expression [ NOT ] LIKE pattern [ ESCAPE escape_character ]  
```  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
match_expression [ NOT ] LIKE pattern  
```  
  
## <a name="arguments"></a>인수  
 *match_expression*  
 문자 데이터 형식의 유효한 [식](../../t-sql/language-elements/expressions-transact-sql.md)입니다.  
  
 *pattern*  
 *match_expression*에서 검색할 특정 문자열이며 다음과 같은 유효한 와일드카드 문자를 포함할 수 있습니다. *pattern*은 최대 8,000바이트까지 지정할 수 있습니다.  
  
|와일드카드 문자|설명|예제|  
|------------------------|-----------------|-------------|  
|%|0개 이상의 문자를 가진 문자열|WHERE title LIKE '%computer%'는 책 제목에 'computer' 단어가 있는 모든 책 제목을 찾습니다.|  
|_ (밑줄)|단일 문자|WHERE au_fname LIKE '_ean'은 ean으로 끝나는 모든 4문자 이름을 찾습니다(Dean, Sean 등).|  
|[ ]|지정된 범위([a-f]) 또는 집합([abcdef])에 있는 단일 문자|WHERE au_lname LIKE '[C-P]arsen'은 arsen으로 끝나고 C와 P 사이의 단일 문자로 시작하는 저자의 성을 찾습니다. 예를 들면 Carsen, Larsen, Karsen 등입니다. 범위 검색에서 범위에 포함되는 문자는 데이터 정렬의 정렬 규칙에 따라 다를 수 있습니다.|  
|[^]|지정된 범위([^a-f]) 또는 집합([^abcdef])에 없는 단일 문자|WHERE au_lname LIKE 'de[^l]%'은 de로 시작하고 이어지는 문자가 l이 아닌 저자의 성을 모두 찾습니다.|  
  
 *escape_character*  
 와일드카드 문자 앞에 입력하여 와일드카드가 일반 문자로 해석되도록 하는 문자입니다. *escape_character*는 기본값이 없는 문자 식이며 하나의 문자만을 반환해야 합니다.  
  
## <a name="result-types"></a>결과 형식  
 **Boolean**  
  
## <a name="result-value"></a>결과 값  
 LIKE는 *match_expression*이 지정된 *pattern*과 일치하면 TRUE를 반환합니다.  
  
## <a name="remarks"></a>Remarks  
 LIKE를 사용하여 문자열 비교를 수행할 때는 패턴 문자열의 모든 문자가 의미를 가지며 여기에는 선행 및 후행 공백 역시 포함됩니다. 쿼리에서 비교의 결과로 'abc '(abc 다음에 단일 공백이 옴) 문자열이 있는 행을 모두 반환해야 하면 그 열의 값이 abc인 행(공백 없는 abc)은 반환되지 않습니다. 그러나 패턴과 일치되는 식에 있는 후행 공백은 무시됩니다. 쿼리에서 비교의 결과로 'abc'(공백 없는 abc) 문자열이 있는 행을 모두 반환해야 하면 abc로 시작하고 후행 공백이 0개 이상인 행이 모두 반환됩니다.  
  
 **char** 및 **varchar** 데이터를 포함하는 패턴을 사용하는 문자열 비교에서는 데이터의 저장 방식으로 인해 LIKE 비교가 성공하지 못할 수도 있습니다. 각 데이터 형식의 저장 방식과 LIKE 비교가 실패할 수 있는 상황을 이해하는 것이 중요합니다. 다음 예에서는 로컬 **char** 변수를 저장 프로시저에 전달한 다음, 패턴 일치를 사용하여 지정된 문자 집합으로 시작하는 성을 가진 모든 직원을 찾는 방법을 보여 줍니다.  
  
```sql
-- Uses AdventureWorks  
  
CREATE PROCEDURE FindEmployee @EmpLName char(20)  
AS  
SELECT @EmpLName = RTRIM(@EmpLName) + '%';  
SELECT p.FirstName, p.LastName, a.City  
FROM Person.Person p JOIN Person.Address a ON p.BusinessEntityID = a.AddressID  
WHERE p.LastName LIKE @EmpLName;  
GO  
EXEC FindEmployee @EmpLName = 'Barb';  
GO  
```  
  
 `FindEmployee` 프로시저는 이름의 문자가 20개 미만일 때 **char** 변수(`@EmpLName`)에 후행 공백을 포함하므로 일치하는 행을 반환하지 못합니다. 반면에 `LastName` 열은 **varchar**이므로 후행 공백을 포함하지 않습니다. 이 프로시저에서는 후행 공백이 의미를 가지므로 실패합니다.  
  
 그러나 다음 예에서는 **varchar** 변수에 후행 공백을 추가하지 않으므로 성공합니다.  
  
```sql
-- Uses AdventureWorks  
  
CREATE PROCEDURE FindEmployee @EmpLName varchar(20)  
AS  
SELECT @EmpLName = RTRIM(@EmpLName) + '%';  
SELECT p.FirstName, p.LastName, a.City  
FROM Person.Person p JOIN Person.Address a ON p.BusinessEntityID = a.AddressID  
WHERE p.LastName LIKE @EmpLName;  
GO  
EXEC FindEmployee @EmpLName = 'Barb';  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```
 FirstName      LastName            City
 ----------     -------------------- --------------- 
 Angela         Barbariol            Snohomish
 David          Barber               Snohomish
 (2 row(s) affected)  
 ``` 
 
## Pattern Matching by Using LIKE  
 LIKE supports ASCII pattern matching and Unicode pattern matching. When all arguments (*match_expression*, *pattern*, and *escape_character*, if present) are ASCII character data types, ASCII pattern matching is performed. If any one of the arguments are of Unicode data type, all arguments are converted to Unicode and Unicode pattern matching is performed. When you use Unicode data (**nchar** or **nvarchar** data types) with LIKE, trailing blanks are significant; however, for non-Unicode data, trailing blanks are not significant. Unicode LIKE is compatible with the ISO standard. ASCII LIKE is compatible with earlier versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 The following is a series of examples that show the differences in rows returned between ASCII and Unicode LIKE pattern matching.  
  
```sql  
-- ASCII pattern matching with char column  
CREATE TABLE t (col1 char(30));  
INSERT INTO t VALUES ('Robert King');  
SELECT *   
FROM t   
WHERE col1 LIKE '% King';   -- returns 1 row  
  
-- Unicode pattern matching with nchar column  
CREATE TABLE t (col1 nchar(30));  
INSERT INTO t VALUES ('Robert King');  
SELECT *   
FROM t   
WHERE col1 LIKE '% King';   -- no rows returned  
  
-- Unicode pattern matching with nchar column and RTRIM  
CREATE TABLE t (col1 nchar (30));  
INSERT INTO t VALUES ('Robert King');  
SELECT *   
FROM t   
WHERE RTRIM(col1) LIKE '% King';   -- returns 1 row  
```  
  
> [!NOTE]  
>  LIKE 비교는 데이터 정렬의 영향을 받습니다. 자세한 내용은 [COLLATE&#40;Transact-SQL&#41;](~/t-sql/statements/collations.md)를 참조하세요.  
  
## <a name="using-the--wildcard-character"></a>% 와일드카드 문자 사용  
 LIKE '5%' 기호를 지정하면 [!INCLUDE[ssDE](../../includes/ssde-md.md)]은 숫자 5 다음 0개 이상의 문자가 이어지는 문자열을 검색합니다.  
  
 예를 들어 다음 쿼리는 모두 `dm` 문자로 시작하므로 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 데이터베이스에서 모든 동적 관리 뷰를 보여 줍니다.  
  
```sql  
-- Uses AdventureWorks  
  
SELECT Name  
FROM sys.system_views  
WHERE Name LIKE 'dm%';  
GO  
```  
  
 동적 관리 뷰가 아닌 모든 개체를 보려면 `NOT LIKE 'dm%'`를 사용하세요. 총 32개의 개체가 있고 LIKE로 패턴과 일치하는 이름을 13개 찾는다면 NOT LIKE는 LIKE 패턴과 일치하지 않는 19개의 개체를 찾습니다.  
  
 `LIKE '[^d][^m]%'`와 같은 패턴으로는 항상 동일한 이름을 찾지 못할 수 있습니다. 이 패턴에서는 19개의 이름이 아니라 첫 번째 문자가 `d`이거나 두 번째 문자가 `m`인 이름을 제외하고 동적 관리 뷰 이름도 아닌 14개의 이름을 찾게 됩니다. 이것은 부정적인 와일드카드 문자가 있는 일치 문자열은 하나의 와일드카드씩 단계별로 평가되기 때문입니다. 평가 중에 일치되지 않는 항목은 제거됩니다.  
  
## <a name="using-wildcard-characters-as-literals"></a>와일드카드 문자를 리터럴로 사용  
 와일드카드 패턴 일치 문자를 리터럴 문자로 사용할 수 있습니다. 와일드카드 문자를 리터럴 문자로 사용하려면 와일드카드 문자를 대괄호로 묶으세요. 다음 표에서는 LIKE 키워드와 [ ] 와일드카드 문자를 사용하는 여러 가지 예를 보여 줍니다.  
  
|기호|의미|  
|------------|-------------|  
|LIKE '5[%]'|5%|  
|LIKE '[_]n'|_n|  
|LIKE '[a-cdf]'|a, b, c, d 또는 f|  
|LIKE '[-acdf]'|-, a, c, d 또는 f|  
|LIKE '[ [ ]'|[|  
|LIKE ']'|]|  
|LIKE 'abc[_]d%'|abc_d 및 abc_de|  
|LIKE 'abc[def]'|abcd, abce 및 abcf|  
  
## <a name="pattern-matching-with-the-escape-clause"></a>ESCAPE 절을 사용한 패턴 일치  
 하나 이상의 특수 와일드카드 문자를 포함하는 문자열을 검색할 수 있습니다. 예를 들어 customers 데이터베이스의 discounts 테이블은 백분율 기호(%)를 포함하는 할인 값을 저장할 수 있습니다. 백분율 기호를 와일드카드 문자가 아닌 일반 문자로 취급하여 검색하려면 ESCAPE 키워드와 이스케이프 문자를 제공해야 합니다. 예를 들어 예제 데이터베이스에는 30%라는 텍스트를 포함하는 comment 열이 있습니다. comment 열의 어느 위치든 30%라는 문자열이 있는 모든 행을 검색하려면 `WHERE comment LIKE '%30!%%' ESCAPE '!'`와 같은 WHERE 절을 지정합니다. ESCAPE 및 이스케이프 문자를 지정하지 않은 경우 [!INCLUDE[ssDE](../../includes/ssde-md.md)]은 30이라는 문자열이 있는 모든 행을 반환합니다.  
  
 LIKE 패턴에서 이스케이프 문자 뒤에 문자가 없는 경우 해당 패턴은 유효하지 않으며 LIKE는 FALSE를 반환합니다. 이스케이프 문자 뒤에 오는 문자가 와일드카드 문자가 아닌 경우 이스케이프 문자는 무시되고 이스케이프 다음에 오는 문자는 패턴 내의 일반 문자로 처리됩니다. 양쪽 대괄호([ ])로 묶여 있는 백분율 기호(%), 밑줄(_) 및 왼쪽 대괄호([) 와일드카드 문자가 여기에 포함됩니다. 또한 양쪽 대괄호 문자([ ]) 안에서 이스케이프 문자를 사용할 수 있으며 캐럿(^), 하이픈(-) 및 오른쪽 대괄호(])를 이스케이프 처리할 수 있습니다.  
  
 0x0000(**char(0)**)은 Windows 데이터 정렬에서 정의되지 않은 문자이며 LIKE에 포함할 수 없습니다.  
  
## <a name="examples"></a>예  
  
### <a name="a-using-like-with-the--wildcard-character"></a>1. LIKE와 % 와일드카드 문자 사용  
 다음 예에서는 `415` 테이블에서 지역 번호가 `PersonPhone`인 모든 전화 번호를 찾는 방법을 보여 줍니다.  
  
```sql  
-- Uses AdventureWorks  
  
SELECT p.FirstName, p.LastName, ph.PhoneNumber  
FROM Person.PersonPhone AS ph  
INNER JOIN Person.Person AS p  
ON ph.BusinessEntityID = p.BusinessEntityID  
WHERE ph.PhoneNumber LIKE '415%'  
ORDER by p.LastName;  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
 
 ```
 FirstName             LastName             Phone
 -----------------     -------------------  ------------
 Ruben                 Alonso               415-555-124  
 Shelby                Cook                 415-555-0121  
 Karen                 Hu                   415-555-0114  
 John                  Long                 415-555-0147  
 David                 Long                 415-555-0123  
 Gilbert               Ma                   415-555-0138  
 Meredith              Moreno               415-555-0131  
 Alexandra             Nelson               415-555-0174  
 Taylor                Patterson            415-555-0170  
 Gabrielle              Russell             415-555-0197  
 Dalton                 Simmons             415-555-0115  
 (11 row(s) affected)  
 ``` 
 
### B. Using NOT LIKE with the % wildcard character  
 The following example finds all telephone numbers in the `PersonPhone` table that have area codes other than `415`.  
  
```sql  
-- Uses AdventureWorks  
  
SELECT p.FirstName, p.LastName, ph.PhoneNumber  
FROM Person.PersonPhone AS ph  
INNER JOIN Person.Person AS p  
ON ph.BusinessEntityID = p.BusinessEntityID  
WHERE ph.PhoneNumber NOT LIKE '415%' AND p.FirstName = 'Gail'  
ORDER BY p.LastName;  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
 
 ```
FirstName              LastName            Phone
---------------------- -------------------- -------------------
Gail                  Alexander            1 (11) 500 555-0120  
Gail                  Butler               1 (11) 500 555-0191  
Gail                  Erickson             834-555-0132  
Gail                  Erickson             849-555-0139  
Gail                  Griffin              450-555-0171  
Gail                  Moore                155-555-0169  
Gail                  Russell              334-555-0170  
Gail                  Westover             305-555-0100  
(8 row(s) affected)  
```  

### C. Using the ESCAPE clause  
 The following example uses the `ESCAPE` clause and the escape character to find the exact character string `10-15%` in column `c1` of the `mytbl2` table.  
  
```sql
USE tempdb;  
GO  
IF EXISTS(SELECT TABLE_NAME FROM INFORMATION_SCHEMA.TABLES  
      WHERE TABLE_NAME = 'mytbl2')  
   DROP TABLE mytbl2;  
GO  
USE tempdb;  
GO  
CREATE TABLE mytbl2  
(  
 c1 sysname  
);  
GO  
INSERT mytbl2 VALUES ('Discount is 10-15% off'), ('Discount is .10-.15 off');  
GO  
SELECT c1   
FROM mytbl2  
WHERE c1 LIKE '%10-15!% off%' ESCAPE '!';  
GO  
```  
  
### <a name="d-using-the---wildcard-characters"></a>D. [ ] 와일드카드 문자 사용  
 다음 예에서는 `Person` 테이블에서 이름이 `Cheryl` 또는 `Sheryl`인 직원을 찾습니다.  
  
```sql  
-- Uses AdventureWorks  
  
SELECT BusinessEntityID, FirstName, LastName   
FROM Person.Person   
WHERE FirstName LIKE '[CS]heryl';  
GO  
```  
  
 다음 예에서는 `Person` 테이블에서 성이 `Zheng` 또는 `Zhang`인 직원의 행을 찾습니다.  
  
```sql  
-- Uses AdventureWorks  
  
SELECT LastName, FirstName  
FROM Person.Person  
WHERE LastName LIKE 'Zh[ae]ng'  
ORDER BY LastName ASC, FirstName ASC;  
GO  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>예제: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] 및 [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="e-using-like-with-the--wildcard-character"></a>E. LIKE와 % 와일드카드 문자 사용  
 다음 예에서는 `DimEmployee` 테이블에서 전화 번호가 `612`로 시작하는 모든 직원을 찾습니다.  
  
```sql  
-- Uses AdventureWorks  
  
SELECT FirstName, LastName, Phone  
FROM DimEmployee  
WHERE phone LIKE '612%'  
ORDER by LastName;  
```  
  
### <a name="f-using-not-like-with-the--wildcard-character"></a>F. NOT LIKE와 % 와일드카드 문자 사용  
 다음 예에서는 `DimEmployee` 테이블에서 `612`로 시작하지 않는 모든 전화번호를 찾습니다.  의 인스턴스에 액세스할 때마다 SQL Server 로그인을 제공할 필요가 없습니다.  
  
```sql  
-- Uses AdventureWorks  
  
SELECT FirstName, LastName, Phone  
FROM DimEmployee  
WHERE phone NOT LIKE '612%'  
ORDER by LastName;  
```  
  
### <a name="g-using-like-with-the--wildcard-character"></a>G. LIKE와 _ 와일드 카드 문자 사용  
 다음 예제에서는 `DimEmployee` 테이블에서 지역 코드가 `6`으로 시작해 `2`로 끝나는 모든 전화 번호를 찾습니다. 지역 코드가 전화 번호의 첫 부분이며 추가 문자는 열 값 다음에 존재하므로 % 와일드 카드 문자는 검색 패턴의 마지막에도 포함됩니다.  
  
```sql  
-- Uses AdventureWorks  
  
SELECT FirstName, LastName, Phone  
FROM DimEmployee  
WHERE phone LIKE '6_2%'  
ORDER by LastName;   
```  
  
## <a name="see-also"></a>참고 항목  
 [PATINDEX&#40;Transact-SQL&#41;](../../t-sql/functions/patindex-transact-sql.md)   
 [식&#40;Transact-SQL&#41;](../../t-sql/language-elements/expressions-transact-sql.md)   
 [기본 제공 함수s&#40;Transact-SQL&#41;](~/t-sql/functions/functions.md)   
 [SELECT&#40;Transact-SQL&#41;](../../t-sql/queries/select-transact-sql.md)   
 [WHERE&#40;Transact-SQL&#41;](../../t-sql/queries/where-transact-sql.md)  
 
