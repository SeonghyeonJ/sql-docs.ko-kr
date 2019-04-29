---
title: sp_bindefault (TRANSACT-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 11/25/2015
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_bindefault
- sp_bindefault_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_bindefault
ms.assetid: 3da70c10-68d0-4c16-94a5-9e84c4a520f6
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 715387bcb15e27b0d53a7f000b0f97c2be5a4bbe
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62996289"
---
# <a name="spbindefault-transact-sql"></a>sp_bindefault(Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  열 또는 별칭 데이터 형식에 기본값을 바인딩합니다.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] DEFAULT 키워드를 사용 하 여 기본 정의 만드는 것이 좋습니다 합니다 [ALTER TABLE](../../t-sql/statements/alter-table-transact-sql.md) 하거나 [CREATE TABLE](../../t-sql/statements/create-table-transact-sql.md) 문 대신 합니다.  
  
 ![항목 링크 아이콘](../../database-engine/configure-windows/media/topic-link.gif "항목 링크 아이콘") [Transact-SQL 구문 규칙](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>구문  
  
```  
  
sp_bindefault [ @defname = ] 'default' ,   
    [ @objname = ] 'object_name'   
    [ , [ @futureonly = ] 'futureonly_flag' ]   
```  
  
## <a name="arguments"></a>인수  
`[ @defname = ] 'default'` CREATE DEFAULT 문으로 작성 되는 기본값의 이름이입니다. *기본* 됩니다 **nvarchar(776)**, 기본값은 없습니다.  
  
`[ @objname = ] 'object_name'` 기본값이 바인딩될 별칭 데이터 형식 또는 테이블과 열의 이름이입니다. *object_name* 됩니다 **nvarchar(776)** 기본값은 없습니다. *object_name* 으로 정의할 수 없습니다 합니다 **varchar (max)** 를 **nvarchar (max)** 를 **varbinary (max)** 를 **xml**, 또는 CLR 사용자 정의 형식입니다.  
  
 하는 경우 *object_name* 은 한 부분으로 이루어진 이름, 별칭 데이터 형식으로 확인 됩니다. 두 부분이나 세 부분으로 된 이름이면 먼저 테이블 및 열로 확인된 다음 확인이 실패하면 별칭 데이터 형식으로 확인됩니다. 기본적으로 별칭 데이터 형식의 기존 열을 상속 *기본*열에 직접 바인딩된 기본값 되지 않은 경우. 에 기본값을 바인딩할 수 없습니다는 **텍스트**를 **ntext**를 **이미지**를 **varchar (max)** 를 **nvarchar (max)**, **varbinary (max)**, **xml**하십시오 **타임 스탬프**, 또는 CLR 사용자 정의 형식 열, IDENTITY 속성이 있는 열, 계산된 열 또는 열은 DEFAULT 제약 조건이 이미 있습니다.  
  
> [!NOTE]  
>  *object_name* 대괄호를 포함할 수 있습니다 **[]** 구분된 식별자로. 자세한 내용은 [Database Identifiers](../../relational-databases/databases/database-identifiers.md)을 참조하세요.  
  
`[ @futureonly = ] 'futureonly_flag'` 별칭 데이터 형식에 기본값 바인딩 하는 경우에 사용 됩니다. *futureonly_flag* 됩니다 **varchar(15)** 이며 기본값은 NULL입니다. 이 매개 변수로 설정 되 면 **futureonly**, 해당 데이터 형식의 기존 열에 새 기본값을 상속할 수 없습니다. 이 매개 변수는 열에 기본값을 바인딩할 때는 절대 사용되지 않습니다. 하는 경우 *futureonly_flag* 가 null 인 경우는 현재 기본값이 없거나 별칭 데이터 형식의 기존 기본값을 사용 하는 별칭 데이터 형식의 열에는 새 기본값이 바인딩됩니다.  
  
## <a name="return-code-values"></a>반환 코드 값  
 0(성공) 또는 1(실패)  
  
## <a name="remarks"></a>Remarks  
 사용할 수 있습니다 **sp_bindefault** 바인딩할 새 기본 열에 DEFAULT 제약 조건을 사용 하는 것이 좋습니다, 있지만 또는 별칭 데이터 형식에 기존 기본값의 바인딩을 해제 하지 않고도 합니다. 이전의 기본값은 무시됩니다. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 시스템 데이터 형식 또는 CLR 사용자 정의 형식에는 기본값을 바인딩할 수 없습니다. 기본값을 바인딩한 열과 기본값이 호환되지 않는 경우에는 바인딩할 때가 아니라 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]가 기본값을 삽입하려고 시도할 때 오류 메시지를 반환합니다.  
  
 별칭 데이터 형식의 기존 열에 직접 바인딩된 기본값이 하지 않는 한 새 기본값을 상속 하거나 *futureonly_flag* 으로 지정 됩니다 **futureonly**합니다. 별칭 데이터 형식의 새 열은 항상 기본값을 상속합니다.  
  
 관련된 정보는 추가할 열에는 기본값을 바인딩하는 경우는 **sys.columns** 카탈로그 뷰에 있습니다. 관련된 정보에 추가 됩니다을 기본 별칭 데이터 형식에 바인딩하는 경우는 **sys.types** 카탈로그 뷰.  
  
## <a name="permissions"></a>사용 권한  
 사용자 테이블을 소유 하거나의 멤버 여야 합니다 **sysadmin** 고정 서버 역할 또는 **db_owner** 하 고 **db_ddladmin** 고정 데이터베이스 역할.  
  
## <a name="examples"></a>예  
  
### <a name="a-binding-a-default-to-a-column"></a>1. 열에 기본값 바인딩  
 `today`라는 기본값이 CREATE DEFAULT에 의해 현재 데이터베이스에 정의되었으며, 다음 예에서는 이 기본값을 `HireDate` 테이블의 `Employee` 열에 바인딩합니다. `Employee` 열의 데이터가 제공되지 않은 채로 `HireDate` 테이블에 행이 추가될 때마다 열은 `today`라는 기본값을 할당받게 됩니다.  
  
```  
USE master;  
GO  
EXEC sp_bindefault 'today', 'HumanResources.Employee.HireDate';  
```  
  
### <a name="b-binding-a-default-to-an-alias-data-type"></a>2. 별칭 데이터 형식에 기본값 바인딩  
 `def_ssn`이라는 이름의 기본값과 `ssn`이라는 이름의 별칭 데이터 형식이 이미 존재합니다. 다음 예에서는 기본값 `def_ssn`을 `ssn`에 바인딩합니다. 테이블을 작성할 때 별칭 데이터 형식인 `ssn`으로 할당된 모든 열은 기본값을 상속합니다. 형식의 기존 열 **ssn** 도 기본값을 상속 **def_ssn 이라는**경우가 아니면 **futureonly** 에 대해 지정 된 *futureonly_flag* 값 또는 열에 직접 바인딩된 기본값이 없는 경우. 열에 바인딩된 기본값은 데이터 형식에 바인딩된 값보다 항상 우선합니다.  
  
```  
USE master;  
GO  
EXEC sp_bindefault 'def_ssn', 'ssn';  
```  
  
### <a name="c-using-the-futureonlyflag"></a>3. futureonly_flag 사용  
 다음 예에서는 기본값 `def_ssn`을 별칭 데이터 형식 `ssn`에 바인딩합니다. 때문에 **futureonly** 지정 된 형식의 기존 열이 없습니다 `ssn` 영향을 받습니다.  
  
```  
USE master;  
GO  
EXEC sp_bindefault 'def_ssn', 'ssn', 'futureonly';  
```  
  
### <a name="d-using-delimited-identifiers"></a>4. 구분 식별자 사용  
 다음 예제에서는 구분된 식별자를 사용 하 여 보여 줍니다 `[t.1]`의 *object_name*합니다.  
  
```  
USE master;  
GO  
CREATE TABLE [t.1] (c1 int);   
-- Notice the period as part of the table name.  
EXEC sp_bindefault 'default1', '[t.1].c1' ;  
-- The object contains two periods;   
-- the first is part of the table name,   
-- and the second distinguishes the table name from the column name.  
```  
  
## <a name="see-also"></a>관련 항목  
 [데이터베이스 엔진 저장 프로시저 &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [CREATE DEFAULT&#40;Transact-SQL&#41;](../../t-sql/statements/create-default-transact-sql.md)   
 [DROP DEFAULT &#40;Transact-SQL&#41;](../../t-sql/statements/drop-default-transact-sql.md)   
 [sp_unbindefault &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-unbindefault-transact-sql.md)   
 [시스템 저장 프로시저&#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
