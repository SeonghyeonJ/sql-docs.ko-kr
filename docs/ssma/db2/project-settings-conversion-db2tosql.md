---
title: 프로젝트 설정 (변환) (DB2ToSQL) | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 538c93cf-c5bb-43d5-b758-186d9fb00c19
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: a446fd4ce116ee19aa8b38d1ae6d8213e35c16e1
ms.sourcegitcommit: 1ab115a906117966c07d89cc2becb1bf690e8c78
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/27/2018
ms.locfileid: "52392477"
---
# <a name="project-settings-conversion-db2tosql"></a>프로젝트 설정 (변환) (DB2ToSQL)
변환 페이지의 **프로젝트 설정** 대화 상자에는 SSMA DB2 구문을 변환 하는 방법을 사용자 지정 하는 설정이 포함 되어 있습니다. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 구문입니다.  
  
변환 창에서 사용할 수는 **프로젝트 설정** 하 고 **기본 프로젝트 설정** 대화 상자:  
  
-   모든 SSMA 프로젝트에 대 한 설정을 지정 하는 **도구** 메뉴 **기본 프로젝트 설정**, 설정을 보거나에서 변경 하는 데 필요한는 마이그레이션 프로젝트 형식을 선택  **마이그레이션 대상 버전** 드롭다운 목록을 클릭 **일반** 클릭 한 다음 확인 하 고 왼쪽된 창 맨 아래에 **변환**합니다.  
  
-   현재 프로젝트에 대 한 설정을 지정 하는 **도구** 메뉴 **프로젝트 설정**, 클릭 **일반** 왼쪽된 창 맨 아래에 클릭및**변환**합니다.  
  
## <a name="conversion-messages"></a>메시지 변환  
  
### <a name="generate-messages-about-issues-applied"></a>적용 하는 문제에 대 한 메시지를 생성 합니다.  
여부를 SSMA 변환 하는 동안 정보 메시지를 생성, 출력 창에 표시 하 고 변환된 된 코드에 추가 합니다를 지정 합니다.  
  
변환 모드를 선택 하는 경우는 **모드** SSMA 상자에 다음 설정이 적용 됩니다.  
  
**기본/낙관적 모드:** 아니요  
  
**전체 모드:** 아니요  
  
## <a name="miscellaneous-options"></a>기타 옵션  
  
### <a name="cast-rownum-expressions-as-integers"></a>정수로 캐스팅 ROWNUM 식  
SSMA ROWNUM 식으로 변환, 식 TOP 절 식 뒤에 변환 됩니다. 다음 예제에서는 DB2 DELETE 문에서 ROWNUM를 보여 줍니다.  
  
`DELETE FROM Table1`  
  
`WHERE ROWNUM < expression and Field1 >= 2`  
  
다음 예제에서는 결과 [!INCLUDE[tsql](../../includes/tsql-md.md)]:  
  
`DELETE TOP (expression-1)`  
  
`FROM Table1`  
  
`WHERE Field1>=2`  
  
위쪽에 TOP 절 식이 정수에 필요 합니다. 정수가 음수 이면 문에 오류가 생성 됩니다.  
  
-   선택 하는 경우 **예**, SSMA 식을 정수로 캐스팅 합니다.  
  
-   선택 하는 경우 **No**, SSMA를 오류로 변환된 된 코드에서 모든 정수가 아닌 식이 표시 됩니다.  
  
변환 모드를 선택 하는 경우는 **모드** SSMA 상자에 다음 설정이 적용 됩니다.  
  
**기본/전체 모드:** 아니요  
  
**낙관적 모드:** 사용자 계정 컨트롤  
  
### <a name="default-schema-mapping"></a>기본 스키마 매핑  
이 설정은 DB2 스키마를 SQL Server 스키마에 매핑되는 방식을 지정 합니다. 두 옵션은이 설정을 사용할 수 있습니다.  
  
1.  **데이터베이스에 스키마:** 이 모드 DB2 스키마에서 'sch1'는 'b o '가 SQL Server 데이터베이스 스키마에 SQL Server 'sch1' 기본적으로 매핑됩니다.  
  
2.  **스키마를 스키마:** 이 모드는 DB2 스키마 'sch1' 'sch1' SQL Server 스키마에 연결 대화 상자에서 제공 하는 기본 SQL Server 데이터베이스는 기본적으로 매핑할 수 됩니다.  
  
변환 모드를 선택 하는 경우는 **모드** SSMA 상자에 다음 설정이 적용 됩니다.  
  
**기본/낙관적/전체 모드:** 데이터베이스 스키마  
  
### <a name="conversion-ways-of-merge-statement"></a>MERGE 문의 변환 방법  
  
-   선택 하는 경우 **를 사용 하 여 삽입, 업데이트, DELETE 문이**SSMA 변환 병합기 문을 삽입, 업데이트, 삭제 문입니다.  
  
-   선택 하는 경우 **를 사용 하 여 MERGE 문은**, SSMA에서 MERGE 문을 변환 병합기 문을 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]합니다.  
  
> [!WARNING]  
> 이 프로젝트 설정 옵션은 에서만 사용할 수 있습니다 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2008 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2012 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2014입니다.  
  
변환 모드를 선택 하는 경우는 **모드** SSMA 상자에 다음 설정이 적용 됩니다.  
  
**기본/낙관적/전체 모드:** MERGE 문을 사용 하 여  
  
### <a name="convert-calls-to-subprograms-that-use-default-arguments"></a>기본 인수를 사용 하는 하위 프로그램에 대 한 호출으로 변환  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 함수는 함수 호출에서 매개 변수 생략을 지원 하지 않습니다. 또한 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 함수 및 프로시저 식이 기본 매개 변수 값으로 지원 하지 않습니다.  
  
-   선택 하는 경우 **예** 매개 변수를 생략 하는 함수 호출, SSMA 키워드 삽입 **기본** 함수에 올바른 위치에서 호출 합니다. 그런 다음 경고를 사용 하 여 호출을 표시 합니다.  
  
-   선택 하는 경우 **No**, SSMA 오류로 함수 호출으로 표시 됩니다.  
  
변환 모드를 선택 하는 경우는 **모드** SSMA 상자에 다음 설정이 적용 됩니다.  
  
**기본/낙관적/전체 모드:** 사용자 계정 컨트롤  
  
### <a name="convert-count-function-to-countbig"></a>Count_big은 COUNT 함수 변환  
2는 COUNT 함수는 2,147,483,647 보다 큰 값을 반환 하는 일을 할 경우<sup>31</sup>-1 COUNT_BIG 함수를 변환 해야 합니다.  
  
-   선택 하는 경우 **예**, SSMA 수의 모든 사용 COUNT_BIG 변환 됩니다.  
  
-   선택 하는 경우 **No**, 함수 수로 유지 됩니다. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 함수 반환 값이 2 보다 크면 이면 오류가 반환 됩니다<sup>31</sup>-1입니다.  
  
변환 모드를 선택 하는 경우는 **모드** SSMA 상자에 다음 설정이 적용 됩니다.  
  
**기본/전체 모드:** 사용자 계정 컨트롤  
  
**낙관적 모드:** 아니요  
  
### <a name="convert-forall-statement-to-while-statement"></a>FORALL 문이 WHILE 변환할 문  
SSMA PL/SQL 컬렉션 요소에 FORALL 루프에서 처리 하는 방법을 정의 합니다.  
  
-   선택 하는 경우 **예**, SSMA 컬렉션 요소가 하나씩 검색된는 WHILE 루프를 만듭니다.  
  
-   선택 하는 경우 **No**, SSMA nodes () 메서드를 사용 하 여 컬렉션에서 행 집합을 생성 하 고 단일 테이블로 사용 합니다. 더 효율적 이지만 출력 코드 가독성이 떨어질 수 있습니다.  
  
변환 모드를 선택 하는 경우는 **모드** SSMA 상자에 다음 설정이 적용 됩니다.  
  
**기본/낙관적 모드:** 아니요  
  
**전체 모드:** 사용자 계정 컨트롤  
  
### <a name="convert-foreign-keys-with-set-null-referential-action-on-column-that-is-not-null"></a>Convert 외래 키 열에 SET NULL 참조 동작을 사용 하 여 NOT NULL  
DB2는 NULL 설정 작업을 하지 수행할 수 있습니다 참조 된 열에서 Null 허용 되지 않으므로 외래 키 제약 조건을 만들 수 있습니다. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 이러한 외래 키 구성을 허용 하지 않습니다.  
  
-   선택 하는 경우 **Yes**SSMA는 DB2의 경우와 같이 참조 작업을 생성 되지만 제약 조건을 로드 하기 전에 수동으로 변경 해야 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]합니다. 예를 들어, SET NULL 대신 NO ACTION을 선택할 수 있습니다.  
  
-   선택 하는 경우 **No**, 제약 조건 오류로 표시 됩니다.  
  
변환 모드를 선택 하는 경우는 **모드** SSMA 상자에 다음 설정이 적용 됩니다.  
  
**기본/낙관적/전체 모드:** 아니요  
  
### <a name="convert-function-calls-to-procedure-calls"></a>프로시저 호출에 대 한 함수 호출 변환  
일부 DB2 자치 트랜잭션을으로 정의 된 함수나 문을 사용할 수 없는 포함 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]합니다. 이러한 경우 SSMA 프로시저 및 함수를 프로시저에 대 한 래퍼를 만듭니다. 변환된 함수를 구현 프로시저를 호출합니다.  
  
SSMA는 프로시저에 대 한 호출으로 래퍼 함수에 대 한 호출을 변환할 수 있습니다. 보다 읽기 쉬운 코드 만들고 성능을 개선할 수 있습니다. 그러나 컨텍스트에서 항상 허용 되지 않으므로; 예를 들어, 프로시저 호출과 함께 SELECT 목록에서 함수 호출을 바꾸어야 합니다. SSMA는 일반적인 사례를 처리 하기 위해 몇 가지 옵션이 있습니다.  
  
-   선택 하는 경우 **항상**, SSMA 프로시저 호출 래퍼 함수 호출 변환 하려고 합니다. 현재 컨텍스트는이 변환을 허용 하지 않습니다, 경우에 오류 메시지가 생성 됩니다. 이 이렇게 하면 함수 호출 하지 않고 생성된 된 코드에 남아 있습니다.  
  
-   선택 하는 경우 **가능 하면**, SSMA 함수에 매개 변수를 출력 하는 경우에 프로시저 호출으로 이동 하면 됩니다. 이동 가능 하지 않은 경우에 매개 변수의 출력 특성이 제거 됩니다. 다른 모든 경우 SSMA는 함수 호출을 유지합니다.  
  
-   선택 하는 경우 **Never**, SSMA 함수 호출으로 모든 함수 호출을 종료 됩니다. 경우에 따라이 선택이 허용 가능한 수준이 아닐 성능상의 이유로 인해 합니다.  
  
변환 모드를 선택 하는 경우는 **모드** SSMA 상자에 다음 설정이 적용 됩니다.  
  
**기본/낙관적/전체 모드:** 가능한 경우  
  
### <a name="convert-lock-table-statements"></a>잠금이 TABLE 문을 변환 합니다.  
SSMA는 테이블 힌트에 잠금이 TABLE 문은 많은 변환할 수 있습니다. SSMA SUBPARTITION, 파티션을 포함 하는 모든 잠금이 TABLE 문을 변환할 수 없습니다. @dblink, NOWAIT 절 및 변환 오류 메시지를 사용 하 여 이러한 문이 표시 됩니다.  
  
-   선택 하는 경우 **예**, SSMA 테이블 힌트가 지원 되는 잠금 TABLE 문을 변환 합니다.  
  
-   선택 하는 경우 **No**, SSMA 변환 오류 메시지를 사용 하 여 모든 잠금이 TABLE 문이 표시 됩니다.  
  
다음 표에서 SSMA DB2 잠금 모드를 변환 하는 방법을 보여 줍니다.  
  
|||  
|-|-|  
|DB2 잠금 모드|SQL Server 테이블 힌트|  
|행 공유|ROWLOCK, HOLDLOCK|  
|행 제외|ROWLOCK, XLOCK, HOLDLOCK|  
|SHARE UPDATE = 행 공유|ROWLOCK, HOLDLOCK|  
|공유|TABLOCK, HOLDLOCK|  
|공유 행 제외|TABLOCK, XLOCK, HOLDLOCK|  
|전용|HOLDLOCK, TABLOCKX|  
  
변환 모드를 선택 하는 경우는 **모드** SSMA 상자에 다음 설정이 적용 됩니다.  
  
**기본/낙관적/전체 모드:** 사용자 계정 컨트롤  
  
### <a name="convert-open-for-statements-for-ref-cursor-out-parameters"></a>REF CURSOR OUT 매개 변수에 대 한 오픈 FOR 문을 변환 합니다.  
DB2의 오픈 FOR 문의 결과 하위 프로그램의 OUT REF CURSOR 형식의 매개 변수 집합을 반환 하려면 사용할 수 있습니다. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], 저장된 프로시저는 직접 SELECT 문의 결과를 반환 합니다.  
  
SSMA는 많은 오픈 FOR 문이 SELECT 문으로 변환할 수 있습니다.  
  
-   선택 하는 경우 **예**, SSMA 오픈 FOR 문 결과 집합을 클라이언트에 반환 하는 SELECT 문을 변환 합니다.  
  
-   선택 하는 경우 **No**, SSMA 출력 창에 변환된 된 코드에 오류 메시지가 생성 됩니다.  
  
변환 모드를 선택 하는 경우는 **모드** SSMA 상자에 다음 설정이 적용 됩니다.  
  
**기본/낙관적/전체 모드:** 사용자 계정 컨트롤  
  
### <a name="convert-record-as-a-list-of-separates-variables"></a>레코드 구분 변수 목록으로 변환  
SSMA는 특정 구조를 사용 하 여 XML 변수 및 변수 분리에 DB2 레코드를 변환할 수 있습니다.  
  
-   선택 하는 경우 **예**, SSMA 가능 하면 구분 변수 목록으로 레코드를 변환 합니다.  
  
-   선택 하는 경우 **No**, SSMA 특정 구조를 사용 하 여 XML 변수를 레코드를 변환 합니다.  
  
변환 모드를 선택 하는 경우는 **모드** SSMA 상자에 다음 설정이 적용 됩니다.  
  
**기본/낙관적/전체 모드:** 사용자 계정 컨트롤  
  
### <a name="convert-substr-function-calls-to-substring-function-calls"></a>SUBSTR 함수 호출을 부분 문자열 함수 호출 변환  
SSMA를 DB2 SUBSTR 함수 호출을 변환할 수 있습니다 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **substring** 함수 매개 변수 수에 따라 호출 합니다. SSMA SUBSTR 함수 호출을 변환할 수 없습니다. 매개 변수의 수는 없습니다, 경우 SSMA는 사용자 지정 SSMA 함수 호출으로 SUBSTR 함수 호출을 변환 합니다.  
  
-   선택 하는 경우 **예**, SSMA에 세 개의 매개 변수를 사용 하는 SUBSTR 함수 호출 변환 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **substring**합니다. 사용자 지정 SSMA 함수를 호출 하려면 다른 SUBSTR 함수 변환 됩니다.  
  
-   선택 하는 경우 **No**합니다 SSMA 사용자 지정 SSMA 함수 호출으로 SUBSTR 함수 호출을 변환 합니다.  
  
변환 모드를 선택 하는 경우는 **모드** SSMA 상자에 다음 설정이 적용 됩니다.  
  
**기본/낙관적 모드:** 사용자 계정 컨트롤  
  
**전체 모드:** 아니요  
  
### <a name="convert-subtypes"></a>하위 형식 변환  
SSMA는 PL/SQL 하위 두 가지 방법으로 변환할 수 있습니다.  
  
-   선택 하는 경우 **예**, SSMA 만들어집니다 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 사용자 정의 하위 형식에서 입력 하 고이 하위 유형의 각 변수에 대해 사용 합니다.  
  
-   선택 하는 경우 **No**, SSMA를 기본 형식 사용 하 여 하위 유형의 모든 원본 선언을 대체 하 고 결과 일반적인 방식으로 변환 됩니다. 이 경우 추가 형식이 없습니다에에서 생성 됩니다. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
  
변환 모드를 선택 하는 경우는 **모드** SSMA 상자에 다음 설정이 적용 됩니다.  
  
**기본/낙관적/전체 모드:** 아니요  
  
### <a name="convert-synonyms"></a>동의어를 변환 합니다.  
다음 DB2 개체에 대 한 동의어로 마이그레이션할 수 있습니다 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:  
  
-   테이블 및 개체 테이블  
  
-   뷰 및 개체 보기  
  
-   저장된 프로시저 및 함수  
  
-   구체화 된 뷰  
  
다음 DB2 개체에 대 한 동의어 개체에 대 한 직접 참조 하 여 바꿀 수 있습니다.  
  
-   시퀀스  
  
-   패키지  
  
-   Java 클래스 스키마 개체  
  
-   사용자 정의 개체 형식  
  
다른 동의어를 마이그레이션할 수 없습니다. SSMA는 동의어 및 동의어가 사용 하는 모든 참조에 대 한 오류 메시지가 생성 됩니다.  
  
-   선택 하는 경우 **Yes**, SSMA 만들어집니다 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 동의어 및 이전 목록에 따라 직접 개체 참조입니다.  
  
-   선택 하는 경우 **No**, SSMA는 여기에 나열 된 모든 동의어에 대 한 직접 개체 참조를 만듭니다.  
  
변환 모드를 선택 하는 경우는 **모드** SSMA 상자에 다음 설정이 적용 됩니다.  
  
**기본/낙관적/전체 모드:** 사용자 계정 컨트롤  
  
### <a name="convert-tochardate-format"></a>(날짜, 형식) TO_CHAR 변환  
SSMA는 DB2 TO_CHAR(date, format) sysdb 데이터베이스의 프로시저를 변환할 수 있습니다.  
  
-   선택 하는 경우 **함수를 사용 하 여 TO_CHAR_DATE**, SSMA (날짜, 형식) TO_CHAR TO_CHAR_DATE 함수를 사용 하 여 영어의 변환에 변환 합니다.  
  
-   선택 하는 경우 **를 사용 하 여 TO_CHAR_DATE_LS 함수 (NLS 주의)**, SSMA (날짜, 형식) TO_CHAR TO_CHAR_DATE_LS 함수를 사용 하 여 세션 언어의 변환에 대 한 변환  
  
변환 모드를 선택 하는 경우는 **모드** SSMA 상자에 다음 설정이 적용 됩니다.  
  
**기본/낙관적 모드:** TO_CHAR_DATE 함수를 사용 하 여  
  
**전체 모드:** TO_CHAR_DATE_LS 함수 (NLS 주의)를 사용 하 여  
  
### <a name="convert-transaction-processing-statements"></a>트랜잭션 처리 문을 변환 합니다.  
SSMA는 DB2 트랜잭션 처리 문을 변환할 수 있습니다.  
  
-   선택 하는 경우 **예**, SSMA DB2 트랜잭션 처리 문을 변환 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 문입니다.  
  
-   선택 하는 경우 **No**, SSMA 문을 변환 오류로 처리 트랜잭션을 표시 합니다.  
  
> [!NOTE]  
> DB2는 트랜잭션을 암시적으로 열립니다. 이 동작을 에뮬레이트하기 위해 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]를 수동으로 추가 해야 BEGIN TRANSACTION 문 시작에 트랜잭션을 저장할 합니다. 또는 세션의 시작 부분에 SET IMPLICIT_TRANSACTIONS ON 명령을 실행할 수 있습니다. SSMA 자치 트랜잭션 사용 하 여 서브루틴을 변환 하는 경우 SET IMPLICIT_TRANSACTIONS ON을 자동으로 추가 합니다.  
  
변환 모드를 선택 하는 경우는 **모드** SSMA 상자에 다음 설정이 적용 됩니다.  
  
**기본/낙관적/전체 모드:** 사용자 계정 컨트롤  
  
### <a name="emulate-db2-null-behavior-in-order-by-clauses"></a>ORDER BY 절에서 null 동작 DB2 에뮬레이션  
NULL 값에서 다르게 정렬 됩니다 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 및 DB2:  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], NULL 값은 정렬 된 목록에서 가장 낮은 값입니다. 된 오름차순 목록에 NULL 값이 먼저 표시 됩니다.  
  
-   DB2의 경우 NULL 값은 정렬 된 목록에서 가장 높은 값입니다. 기본적으로 NULL 값을 오름차순 순서 목록에서 마지막 표시 됩니다.  
  
-   DB2는 DB2 null 값을 정렬 하는 방법을 변경할 수 있도록 NULL 첫 번째 및 마지막 NULL 절에 있습니다.  
  
SSMA는 NULL 값을 검사 하 여 DB2 ORDER BY 동작을 에뮬레이트할 수 있습니다. 다음 먼저 정렬에서 지정 된 순서 대로 주문을 다른 값으로 NULL 값으로.  
  
-   선택 하는 경우 **예**, SSMA DB2 문을 DB2 ORDER BY 동작을 에뮬레이션 하는 방식으로 변환 됩니다.  
  
-   선택 하는 경우 **No**, SSMA DB2 규칙 무시 되며 NULL 첫 번째 및 마지막 NULL 절을 발견할 경우 오류 메시지를 생성 합니다.  
  
변환 모드를 선택 하는 경우는 **모드** SSMA 상자에 다음 설정이 적용 됩니다.  
  
**기본/낙관적 모드:** 아니요  
  
**전체 모드:** 사용자 계정 컨트롤  
  
### <a name="emulate-row-count-exceptions-in-select"></a>선택에서 행 개수 예외 에뮬레이트  
INTO 절을 사용 하 여 SELECT 문의 모든 행을 반환 하지 않으면 DB2 NO_DATA_FOUND 예외를 발생 시킵니다. 문이 두 개 이상의 행을 반환 하는 경우 TOO_MANY_ROWS 예외가 발생 합니다. 변환된 된 문이 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 행 수가 하나에서 다른 경우 모든 예외를 발생 하지 않습니다.  
  
-   선택 하는 경우 **예**, SSMA 각 SELECT 문은 다음 sysdb 프로시저 db_error_exact_one_row_check 호출을 추가 합니다. 이 절차는 NO_DATA_FOUND 및 TOO_MANY_ROWS 예외를 에뮬레이트합니다. 기본값이 며와 최대한 가깝게 DB2 동작을 재현할 수 있습니다. 항상 선택 해야 **예** 소스 코드에 이러한 오류를 처리 하는 예외 처리기를 포함 하는 경우. 저장된 프로시저, 저장된 프로시저를 실행 하기 때문에이 모듈 변환할 수는 SELECT 문은 사용자 정의 함수 내에서 발생 하는 경우 및 호환 되지 않는 예외를 발생 시키는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 함수 컨텍스트.  
  
-   선택 하는 경우 **No**, 예외가 생성 됩니다. SSMA 변환 하는 사용자 정의 함수에서 함수를 유지 하려는 경우 유용할 수 있는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
  
변환 모드를 선택 하는 경우는 **모드** SSMA 상자에 다음 설정이 적용 됩니다.  
  
**기본/낙관적/전체 모드:** 사용자 계정 컨트롤  
  
### <a name="generate-error-for-dbmssqlparse"></a>DBMS_SQL에 대 한 오류를 생성 합니다. 구문 분석  
  
-   선택 하는 경우 **오류**, SSMA DBMS_SQL 변환에서 오류를 생성 합니다. 구문 분석 합니다.  
  
-   선택 하는 경우 **경고**, SSMA DBMS_SQL 변환에서 경고를 생성 합니다. 구문 분석 합니다.  
  
변환 모드를 선택 하는 경우는 **모드** SSMA 상자에 다음 설정이 적용 됩니다.  
  
**기본/낙관적/전체 모드:** Error  
  
### <a name="generate-rowid-column"></a>행 ID 열 생성  
SSMA에서 테이블을 만들 경우 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], 행 ID 열을 만들 수 있습니다. 데이터를 마이그레이션할 때 각 행에 newid () 함수에 의해 생성 된 새 UNIQUEIDENTIFIER 값을 가져옵니다.  
  
-   선택 하는 경우 **Yes**, ROWID 열은 모든 테이블에서 생성 및 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 값을 삽입 하면 Guid를 생성 합니다. 언제 든 지 선택할 **예** SSMA 테스터를 사용 하려는 경우.  
  
-   선택 하는 경우 **No**, ROWID 열 테이블에 추가 되지 않습니다.  
  
-   **트리거가 있는 테이블의 행 ID 열을 추가** 트리거를 포함 하는 테이블에 대 한 ROWID를 추가 합니다.  
  
> [!WARNING]  
> SQL Server 2005, SQL Server 2008 및 SQL Server 2012 및 2014의 경우 기본 설정은 **트리거가 있는 테이블에 대 한 추가 ROWID 열**합니다.  
  
변환 모드를 선택 하는 경우는 **모드** SSMA 상자에 다음 설정이 적용 됩니다.  
  
**기본/낙관적 모드:** 트리거가 있는 테이블의 행 ID 열 추가  
  
**전체 모드:** 사용자 계정 컨트롤  
  
### <a name="generate-unique-index-on-rowid-column"></a>행 ID 열에 고유 인덱스를 생성 합니다.  
여부 SSMA ROWID 생성 된 열에 고유 인덱스 열을 생성 하는지 여부를 지정 합니다. 고유 인덱스가 생성 되는 옵션을 "예"로 설정 하는 경우 하 고 "아니요"로 설정 된 경우 고유 인덱스 행 ID 열에는 생성 되지 않습니다.  
  
변환 모드를 선택 하는 경우는 **모드** SSMA 상자에 다음 설정이 적용 됩니다.  
  
**기본/낙관적/전체 모드:** 사용자 계정 컨트롤  
  
### <a name="local-modules-conversion"></a>로컬 모듈 변환  
중첩 된 DB2 하위 프로그램 (독립 실행형 저장 프로시저나 함수에서 선언 됨) 변환 유형을 정의합니다.  
  
-   선택 하는 경우 **인라인**, 중첩 된 하위 프로그램 호출 본문으로 대체 됩니다.  
  
-   선택 하는 경우 **저장 프로시저**, SQL Server 저장 프로시저에 중첩 된 하위 프로그램 변환 되 고이 프로시저 호출에서 해당 호출을 바뀝니다.  
  
변환 모드를 선택 하는 경우는 **모드** SSMA 상자에 다음 설정이 적용 됩니다.  
  
**기본/낙관적/전체 모드:** 인라인  
  
### <a name="use-isnull-in-string-concatenation"></a>문자열 연결에 ISNULL 사용  
DB2 및 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] NULL 값을 포함 하는 문자열 연결 하는 경우 다른 결과 반환 합니다. DB2 빈 문자 집합을 같은 NULL 값을 처리합니다. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] NULL을 반환합니다.  
  
-   선택 하는 경우 **예**, SSMA DB2 연결 문자 (|)를 사용 하 여 대체 된 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 연결 문자 (+). SSMA는 또한 NULL 값에 대 한 연결의 양쪽에 있는 식을 확인합니다.  
  
-   선택 하는 경우 **No**, SSMA 연결 문자를 대체 하지만 NULL 값을 확인 하지 않습니다.  
  
변환 모드를 선택 하는 경우는 **모드** SSMA 상자에 다음 설정이 적용 됩니다.  
  
### <a name="use-isnull-in-replace-function-calls"></a>REPLACE 함수 호출의 ISNULL 사용  
ISNULL 문이 REPLACE 함수 호출에서 DB2 동작을 에뮬레이트하는 데 사용 됩니다. 다음 옵션은이 설정에 대해 존재 합니다.  
  
-   YES  
  
-   아니요  
  
변환 모드를 선택 하는 경우는 **모드** SSMA 상자에 다음 설정이 적용 됩니다.  
  
**기본/낙관적 모드:** 아니요  
  
**전체 모드:** 사용자 계정 컨트롤  
  
### <a name="use-isnull-in-concat-function-calls"></a>CONCAT 함수 호출의 ISNULL 사용  
ISNULL 문이 CONCAT 함수 호출에서 DB2 동작을 에뮬레이트하는 데 사용 됩니다. 다음 옵션은이 설정에 대해 존재 합니다.  
  
-   YES  
  
-   아니요  
  
변환 모드를 선택 하는 경우는 **모드** SSMA 상자에 다음 설정이 적용 됩니다.  
  
**기본/낙관적 모드:** 아니요  
  
**전체 모드:** 사용자 계정 컨트롤  
  
### <a name="use-native-convert-function-when-possible"></a>가능 하면 네이티브 convert 함수를 사용 합니다.  
  
-   선택 하는 경우 **예**, SSMA 가능한 경우 기본 변환 함수 (날짜, 형식) TO_CHAR 변환 합니다.  
  
-   선택 하는 경우 **No**, SSMA 변환 (날짜, 형식) TO_CHAR TO_CHAR_DATE 또는 TO_CHAR_DATE_LS ("TO_CHAR(date, format) 변환" 옵션으로 정의 됩니다).  
  
변환 모드를 선택 하는 경우는 **모드** SSMA 상자에 다음 설정이 적용 됩니다.  
  
**기본/낙관적 모드:** 사용자 계정 컨트롤  
  
**전체 모드:** 아니요  
  
### <a name="use-selectfor-xml-when-converting-selectinto-for-record-variable"></a>SELECT를 사용 하는 중... FOR XML 변환 하는 경우 다음을 선택 하는 중... 레코드 변수의 INTO  
레코드 변수를 선택 하면 설정 XML 결과 생성할지 여부를 지정 합니다.  
  
-   선택 하는 경우 **예**, SELECT 문은 XML을 반환 합니다.  
  
-   선택 하는 경우 **No**, SELECT 문의 결과 집합을 반환 합니다.  
  
변환 모드를 선택 하는 경우는 **모드** SSMA 상자에 다음 설정이 적용 됩니다.  
  
**기본/낙관적/전체 모드:** 아니요  
  
## <a name="returning-clause-conversion"></a>절 변환을 반환합니다.  
  
### <a name="convert-returning-clause-in-delete-statement-to-output"></a>DELETE 문에 RETURNING 절을 출력으로 변환  
DB2는 RETURNING 절을 즉시 삭제 된 값을 얻는 방법을 제공 합니다. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] OUTPUT 절을 사용 하 여 해당 기능을 제공합니다.  
  
-   선택 하는 경우 **예**, SSMA RETURNING 절 DELETE 문에서 OUTPUT 절에 변환 됩니다. 반환된 된 값에서 다를 수 있습니다 트리거 테이블에서 값을 변경할 수, 있으므로 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] DB2 에서보다 합니다.  
  
-   선택 하는 경우 **No**, SSMA SELECT 문에서 반환 된 값을 검색 하려면 DELETE 문 앞에 생성 됩니다.  
  
변환 모드를 선택 하는 경우는 **모드** SSMA 상자에 다음 설정이 적용 됩니다.  
  
**기본/낙관적/전체 모드:** 사용자 계정 컨트롤  
  
### <a name="convert-returning-clause-in-insert-statement-to-output"></a>INSERT 문의 RETURNING 절을 출력으로 변환  
DB2는 RETURNING 절을 바로 삽입 된 값을 얻는 방법을 제공 합니다. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] OUTPUT 절을 사용 하 여 해당 기능을 제공합니다.  
  
-   선택 하는 경우 **예**, SSMA RETURNING 절을 INSERT 문에서 출력 변환 됩니다. 반환된 된 값에서 다를 수 있습니다 트리거 테이블에서 값을 변경할 수, 있으므로 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] DB2 에서보다 합니다.  
  
-   선택 하는 경우 **No**, SSMA를 삽입 한 다음 참조 테이블에서 값을 선택 하 여 DB2 기능을 에뮬레이션 합니다.  
  
변환 모드를 선택 하는 경우는 **모드** SSMA 상자에 다음 설정이 적용 됩니다.  
  
**기본/낙관적/전체 모드:** 사용자 계정 컨트롤  
  
### <a name="convert-returning-clause-in-update-statement-to-output"></a>UPDATE 문이 RETURNING 절을 출력으로 변환  
DB2는 RETURNING 절을 즉시 업데이트 된 값을 얻는 방법을 제공 합니다. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] OUTPUT 절을 사용 하 여 해당 기능을 제공합니다.  
  
-   선택 하는 경우 **예**, SSMA RETURNING 절 UPDATE 문에서 OUTPUT 절에 변환 됩니다. 반환된 된 값에서 다를 수 있습니다 트리거 테이블에서 값을 변경할 수, 있으므로 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] DB2 에서보다 합니다.  
  
-   선택 하는 경우 **No**, SSMA 반환 값을 검색 하려면 UPDATE 문을 후 SELECT 문을 생성 됩니다.  
  
변환 모드를 선택 하는 경우는 **모드** SSMA 상자에 다음 설정이 적용 됩니다.  
  
**기본/낙관적/전체 모드:** 사용자 계정 컨트롤  
  
## <a name="sequence-conversion"></a>시퀀스 변환  
  
### <a name="convert-sequence-generator"></a>시퀀스 생성기를 변환 합니다.  
DB2의 고유 식별자를 생성 하는 시퀀스를 사용할 수 있습니다.  
  
SSMA는 다음에 시퀀스를 변환할 수 있습니다.  
  
-   (이 옵션은만 사용할 수 있는 SQL Server 2012 및 SQL Server 2014를 변환 하는 경우)는 SQL Server 시퀀스 생성기를 사용 합니다.  
  
-   SSMA 시퀀스 생성기를 사용합니다.  
  
-   열 id를 사용 하 여 합니다.  
  
SQL Server 2012 또는 SQL Server 2014를 변환 하는 경우 기본 옵션을 SQL Server 시퀀스 생성기를 사용 하는 것입니다. 그러나 SQL Server 2012 및 SQL Server 2014 지원 하지 않습니다 (예: DB2 시퀀스 currval 메서드는) 현재 시퀀스 값 가져오기. DB2 시퀀스 currval 메서드를 마이그레이션에 대 한 지침은 SSMA 팀 블로그 사이트를 참조 하십시오.  
  
SSMA는 또한 DB2 시퀀스 SSMA 시퀀스 에뮬레이터를 변환 하는 옵션을 제공 합니다. SQL Server 2012 이전의 변환할 때 이것이 기본 옵션  
  
마지막으로, SQL Server id 값을 테이블의 열에 할당 된 시퀀스를 변환할 수 있습니다. DB2에서 id 열에 시퀀스 간의 매핑을 지정 해야 합니다 **테이블** 탭  
  
### <a name="convert-currval-outside-triggers"></a>외부 트리거 CURRVAL 변환  
변환할 시퀀스 생성기로 설정 된 경우에 표시 **identity 열을 사용 하 여**입니다. DB2 시퀀스는 테이블에서 별도 개체를 생성 하 고 새 시퀀스 값을 삽입 트리거를 사용 하는 시퀀스를 사용 하는 여러 테이블. SSMA 이러한 문을 주석으로 처리 하거나 주석 처리 아웃 오류를 생성 하는 경우 오류로 표시 합니다.  
  
-   선택 하는 경우 **예**, SSMA에서 변환 된 트리거 외부 CURRVAL 경고를 사용 하 여 시퀀스에 대 한 모든 참조 표시 됩니다.  
  
-   선택 하는 경우 **No**, SSMA에서 변환 된 트리거 외부 CURRVAL 오류가 발생 하 여 시퀀스에 대 한 모든 참조 표시 됩니다.  
  
## <a name="see-also"></a>관련 항목  
[사용자 인터페이스 참조 &#40;DB2ToSQL&#41;](../../ssma/db2/user-interface-reference-db2tosql.md)  
  
