---
title: sys. dm_db_uncontained_entities (Transact-sql) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_db_uncontained_entities
- dm_db_uncontained_entities_TSQL
- sys.dm_db_uncontained_entities_TSQL
- dm_db_uncontained_entities
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_db_uncontained_entities dynamic management view
ms.assetid: f417efd4-8c71-4f81-bc9c-af13bb4b88ad
author: stevestein
ms.author: sstein
ms.openlocfilehash: 625c6134c91a9b452b8df2b7e235b78126c1354e
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/27/2020
ms.locfileid: "68026923"
---
# <a name="sysdm_db_uncontained_entities-transact-sql"></a>sys.dm_db_uncontained_entities (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  데이터베이스에 사용된 포함되지 않은 개체를 표시합니다. 포함되지 않은 개체는 포함된 데이터베이스의 데이터베이스 경계를 넘는 개체입니다. 이 뷰는 포함된 데이터베이스와 포함되지 않은 데이터베이스 모두에서 액세스할 수 있습니다. sys.dm_db_uncontained_entities가 비어 있는 경우에는 데이터베이스에서 포함되지 않은 엔터티를 사용하지 않습니다.  
  
 모듈이 데이터베이스 경계를 두 번 이상 교차한 경우 처음에 발견된 교차만 보고됩니다.  
  
||||  
|-|-|-|  
|**열 이름**|**Type**|**설명**|  
|*class*|**int**|1 = 개체 또는 열(모듈, XP, 뷰, 동의어 및 테이블 포함)<br /><br /> 4 = 데이터베이스 보안 주체<br /><br /> 5 = 어셈블리<br /><br /> 6 = 형식<br /><br /> 7 = 인덱스(전체 텍스트 인덱스)<br /><br /> 12 = 데이터베이스 DDL 트리거<br /><br /> 19 = 경로<br /><br /> 30 = 감사 사양|  
|*class_desc*|**nvarchar(120)**|엔터티의 클래스에 대한 설명입니다. 클래스와 일치 하는 다음 중 하나입니다.<br /><br /> **OBJECT_OR_COLUMN**<br /><br /> **DATABASE_PRINCIPAL**<br /><br /> **어셈블리**<br /><br /> **유형**<br /><br /> **인덱싱할**<br /><br /> **DATABASE_DDL_TRIGGER**<br /><br /> **ROUTE**<br /><br /> **AUDIT_SPECIFICATION**|  
|*major_id*|**int**|엔터티의 ID입니다.<br /><br /> *클래스* = 1 인 경우 object_id<br /><br /> *클래스* = 4 인 경우 database_principals. principal_id입니다.<br /><br /> *클래스* = 5 인 경우 assembly_id 합니다.<br /><br /> *클래스* = 6 인 경우에는 user_type_id 합니다.<br /><br /> *Class* = 7 인 경우 index_id 합니다.<br /><br /> *클래스* = 12 이면 object_id 합니다.<br /><br /> *클래스* = 19 인 경우에는 route_id 합니다.<br /><br /> *클래스* = 30 인 경우 sys. database_audit_specifications database_specification_id입니다.|  
|*statement_line_number*|**int**|클래스가 모듈인 경우 포함되지 않은 용도가 있는 줄 번호를 반환합니다.  그렇지 않으면 값이 Null입니다.|  
|*statement_ offset_begin*|**int**|클래스가 모듈인 경우 포함되지 않은 용도의 시작 위치(0으로 시작되는 바이트)를 나타냅니다. 그렇지 않으면 반환 값이 Null입니다.|  
|*statement_ offset_end*|**int**|클래스가 모듈인 경우 포함되지 않은 용도의 끝 위치(0으로 시작되는 바이트)를 나타냅니다. 값이 -1인 경우 모듈의 끝을 나타냅니다. 그렇지 않으면 반환 값이 Null입니다.|  
|*statement_type*|**nvarchar(512)**|문의 유형입니다.|  
|*feature_ 이름*|**nvarchar(256)**|개체의 외부 이름을 반환합니다.|  
|*feature_type_name*|**nvarchar(256)**|기능의 유형을 반환합니다.|  
  
## <a name="remarks"></a>설명  
 dm_db_uncontained_entities는 잠재적으로 데이터베이스 경계를 넘을 수 있는 엔터티를 표시 합니다. 즉, 데이터베이스 외부 개체를 사용할 가능성이 있는 사용자 엔터티를 반환합니다.  
  
 다음 기능 유형이 보고됩니다.  
  
-   알 수 없는 포함 경계(동적 SQL 또는 지연된 이름 확인)  
  
-   DBCC 명령  
  
-   시스템 저장 프로시저  
  
-   시스템 스칼라 함수  
  
-   시스템 테이블 반환 함수  
  
-   시스템 기본 제공 함수  
  
## <a name="security"></a>보안  
  
### <a name="permissions"></a>사용 권한  
 sys.dm_db_uncontained_entities는 특정 유형의 권한을 가진 사용자에 대해서만 개체를 반환합니다. 데이터베이스 포함을 완전히 평가 하려면 **sysadmin** 고정 서버 역할의 멤버 또는 **db_owner** 역할의 멤버와 같은 권한이 높은 사용자가이 함수를 사용 해야 합니다.  
  
## <a name="examples"></a>예  
 다음 예에서는 P1이라는 프로시저를 만든 다음 `sys.dm_db_uncontained_entities`쿼리를 만듭니다. 이 쿼리는 P1에서 데이터베이스 외부에 있는 **sys.endpoints** 를 사용하는 것을 보고합니다.  
  
```sql  
CREATE DATABASE Test;  
GO  
  
USE Test;  
GO  
CREATE PROC P1  
AS   
SELECT * FROM sys.endpoints ;  
GO  
SELECT SO.name, UE.* FROM sys.dm_db_uncontained_entities AS UE  
LEFT JOIN sys.objects AS SO  
    ON UE.major_id = SO.object_id;  
```  
  
## <a name="see-also"></a>참고 항목  
 [포함 된 데이터베이스](../../relational-databases/databases/contained-databases.md)  
  
  
