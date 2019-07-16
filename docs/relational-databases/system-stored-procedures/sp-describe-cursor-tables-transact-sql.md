---
title: sp_describe_cursor_tables (TRANSACT-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_describe_cursor_tables_TSQL
- sp_describe_cursor_tables
dev_langs:
- TSQL
helpviewer_keywords:
- sp_describe_cursor_tables
ms.assetid: 02c0f81a-54ed-4ca4-aa4f-bb7463a9ab9a
author: stevestein
ms.author: sstein
ms.openlocfilehash: 5c005ff603f21dca387215cafd9dff572db53960
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68053092"
---
# <a name="spdescribecursortables-transact-sql"></a>sp_describe_cursor_tables(Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  서버 커서가 참조하는 개체 또는 기본 테이블을 보고합니다.  
  
 ![항목 링크 아이콘](../../database-engine/configure-windows/media/topic-link.gif "항목 링크 아이콘") [Transact-SQL 구문 규칙](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>구문  
  
```  
  
sp_describe_cursor_tables   
     [ @cursor_return = ] output_cursor_variable OUTPUT   
     { [ , [ @cursor_source = ] N'local'  
     , [ @cursor_identity = ] N'local_cursor_name' ]   
   | [ , [ @cursor_source = ] N'global'  
     , [ @cursor_identity = ] N'global_cursor_name' ]   
   | [ , [ @cursor_source = ] N'variable'  
     , [ @cursor_identity = ] N'input_cursor_variable' ]   
     }   
[;]  
```  
  
## <a name="arguments"></a>인수  
 [ @cursor_return=] *output_cursor_variable*출력  
 커서 출력을 수신하기 위해 선언된 커서 변수의 이름입니다. *output_cursor_variable* 됩니다 **커서**없습니다 기본적 이며 반드시 sp_describe_cursor_tables가 호출 시 모든 커서와도 연결 수 없습니다. 반환된 커서는 스크롤할 수 있으며 동적인 읽기 전용 커서입니다.  
  
 [ @cursor_source=] {N'local' | N'global' | N'variable'}  
 보고할 커서를 로컬 커서, 전역 커서 또는 커서 변수의 이름 중 어느 것을 사용하여 지정할지 결정합니다. 매개 변수가 **nvarchar(30)** 합니다.  
  
 [ @cursor_identity=] N'*local_cursor_name*'  
 LOCAL 키워드를 갖거나 LOCAL이 기본값인 DECLARE CURSOR 문에 의해 생성된 커서의 이름입니다. *local_cursor_name* 됩니다 **nvarchar (128)** 합니다.  
  
 [ @cursor_identity=] N'*global_cursor_name*'  
 GLOBAL 키워드를 갖거나 GLOBAL이 기본값인 DECLARE CURSOR 문에 의해 생성된 커서의 이름입니다. *global_cursor_name* SQLSetCursorName를 호출 하 여 커서를 명명할 ODBC 응용 프로그램에 의해 열린 API 서버 커서의 이름일 수도 있습니다. *global_cursor_name* 됩니다 **nvarchar (128)** 합니다.  
  
 [ @cursor_identity=] N'*input_cursor_variable*'  
 열린 커서와 연관된 커서 변수의 이름입니다. *input_cursor_variable* 됩니다 **nvarchar (128)** 합니다.  
  
## <a name="return-code-values"></a>반환 코드 값  
 없음  
  
## <a name="cursors-returned"></a>반환되는 커서  
 sp_describe_cursor_tables 변수로 해당 보고서를 캡슐화를 [!INCLUDE[tsql](../../includes/tsql-md.md)] **커서** 매개 변수를 출력 합니다. 이로 인해 [!INCLUDE[tsql](../../includes/tsql-md.md)] 일괄 처리, 저장 프로시저 및 한 번에 하나의 행만 출력 작업을 하는 트리거가 허용됩니다. 이는 API 함수에서 바로 프로시저를 호출할 수 없음을 의미하기도 합니다. 합니다 **커서** 출력 매개 변수를 프로그램 변수에 바인딩되어야 하지만 Api 바인딩을 지원 하지 않습니다 **커서** 매개 변수 또는 변수입니다.  
  
 다음 표에서는 sp_describe_cursor_tables에 의해 반환된 커서의 형식을 보여 줍니다.  
  
|열 이름|데이터 형식|설명|  
|-----------------|---------------|-----------------|  
|table owner|**sysname**|테이블 소유자의 사용자 ID입니다.|  
|Table_name|**sysname**|개체 또는 기본 테이블의 이름입니다. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 서버 커서는 항상 기본 테이블이 아닌 사용자 지정 개체를 반환합니다.|  
|Optimizer_hints|**smallint**|다음 중 하나 이상으로 구성된 비트맵입니다.<br /><br /> 1 = 행 수준 잠금(ROWLOCK)<br /><br /> 4 = 페이지 수준 잠금(PAGELOCK)<br /><br /> 8 = 테이블 잠금(TABLOCK)<br /><br /> 16 = 배타적 테이블 잠금(TABLOCKX)<br /><br /> 32 = 업데이트 잠금(UPDLOCK)<br /><br /> 64 = 잠금 없음(NOLOCK)<br /><br /> 128 = 빠른 첫째 행 옵션(FASTFIRST)<br /><br /> 4096 = DECLARE CURSOR(HOLDLOCK)와 함께 사용된 경우 반복적인 의미 체계를 읽습니다.<br /><br /> 여러 가지 옵션이 제공되는 경우 시스템은 가장 제한적인 것을 사용합니다. 단, sp_describe_cursor_tables는 쿼리에서 지정된 플래그를 표시합니다.|  
|lock_type|**smallint**|해당 커서의 기초가 되는 각 기본 테이블에 대해 명시적 또는 암시적으로 요청된 스크롤 잠금 유형입니다. 값은 다음 중 하나일 수 있습니다.<br /><br /> 0 = 없음<br /><br /> 1 = 공유<br /><br /> 3 = 업데이트|  
|server_name|**sysname, null 허용**|테이블이 있는 연결된 서버의 이름입니다. OPENQUERY 또는 OPENROWSET가 사용된 경우에는 NULL입니다.|  
|Objectid|**int**|테이블의 개체 ID입니다. OPENQUERY 또는 OPENROWSET가 사용된 경우에는 0입니다.|  
|dbid|**int**|테이블이 있는 데이터베이스의 ID입니다. OPENQUERY 또는 OPENROWSET가 사용된 경우에는 0입니다.|  
|dbname|**sysname**, **null 허용**|테이블이 있는 데이터베이스의 이름입니다. OPENQUERY 또는 OPENROWSET가 사용된 경우에는 NULL입니다.|  
  
## <a name="remarks"></a>설명  
 sp_describe_cursor_tables는 서버 커서가 참조하는 기본 테이블을 설명합니다. 커서가 반환한 결과 집합의 특성 설명을 보려면 sp_describe_cursor_columns를 사용합니다. 스크롤 및 업데이트 허용 여부 등 커서의 전역 특성에 대한 설명을 보려면 sp_describe_cursor를 사용합니다. 연결 시 표시될 [!INCLUDE[tsql](../../includes/tsql-md.md)] 서버 커서의 보고서를 가져오려면 sp_cursor_list를 사용합니다.  
  
## <a name="permissions"></a>사용 권한  
 public 역할의 멤버 자격이 필요합니다.  
  
## <a name="examples"></a>예  
 다음 예에서는 전역 커서를 열고 `sp_describe_cursor_tables`를 사용하여 커서에 의해 참조되는 테이블을 보고합니다.  
  
```  
USE AdventureWorks2012;  
GO  
-- Declare and open a global cursor.  
DECLARE abc CURSOR KEYSET FOR  
SELECT LastName  
FROM Person.Person  
WHERE LastName LIKE 'S%';  
  
OPEN abc;  
GO  
-- Declare a cursor variable to hold the cursor output variable  
-- from sp_describe_cursor_tables.  
DECLARE @Report CURSOR;  
  
-- Execute sp_describe_cursor_tables into the cursor variable.  
EXEC master.dbo.sp_describe_cursor_tables  
      @cursor_return = @Report OUTPUT,  
      @cursor_source = N'global', @cursor_identity = N'abc';  
  
-- Fetch all the rows from the sp_describe_cursor_tables output cursor.  
FETCH NEXT from @Report;  
WHILE (@@FETCH_STATUS <> -1)  
BEGIN  
   FETCH NEXT from @Report;  
END  
  
-- Close and deallocate the cursor from sp_describe_cursor_tables.  
CLOSE @Report;  
DEALLOCATE @Report;  
GO  
  
-- Close and deallocate the original cursor.  
CLOSE abc;  
DEALLOCATE abc;  
GO  
```  
  
## <a name="see-also"></a>관련 항목  
 [커서](../../relational-databases/cursors.md)   
 [CURSOR_STATUS &#40;TRANSACT-SQL&#41;](../../t-sql/functions/cursor-status-transact-sql.md)   
 [DECLARE CURSOR&#40;Transact-SQL&#41;](../../t-sql/language-elements/declare-cursor-transact-sql.md)   
 [sp_cursor_list &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-cursor-list-transact-sql.md)   
 [sp_describe_cursor &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-describe-cursor-transact-sql.md)   
 [sp_describe_cursor_columns &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-describe-cursor-columns-transact-sql.md)   
 [시스템 저장 프로시저&#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
