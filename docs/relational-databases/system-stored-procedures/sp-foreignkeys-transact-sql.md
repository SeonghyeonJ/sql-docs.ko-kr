---
title: sp_foreignkeys (Transact-sql) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_foreignkeys_TSQL
- sp_foreignkeys
dev_langs:
- TSQL
helpviewer_keywords:
- sp_foreignkeys
ms.assetid: 935fe385-19ff-41a4-8d0b-30618966991d
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 0951bd857b6fbf2e3bdc8f5bc1ff850f80c43bcd
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/05/2020
ms.locfileid: "82820488"
---
# <a name="sp_foreignkeys-transact-sql"></a>sp_foreignkeys(Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  연결된 서버의 테이블에서 기본 키를 참조하는 외래 키를 반환합니다.  
  
 ![항목 링크 아이콘](../../database-engine/configure-windows/media/topic-link.gif "항목 링크 아이콘") [Transact-SQL 구문 표기 규칙](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>구문  
  
```  
  
sp_foreignkeys [ @table_server = ] 'table_server'   
     [ , [ @pktab_name = ] 'pktab_name' ]   
     [ , [ @pktab_schema = ] 'pktab_schema' ]   
     [ , [ @pktab_catalog = ] 'pktab_catalog' ]   
     [ , [ @fktab_name = ] 'fktab_name' ]   
     [ , [ @fktab_schema = ] 'fktab_schema' ]   
     [ , [ @fktab_catalog = ] 'fktab_catalog' ]  
```  
  
## <a name="arguments"></a>인수  
`[ @table_server = ] 'table_server'`테이블 정보를 반환할 연결 된 서버의 이름입니다. *table_server* 는 **sysname**이며 기본값은 없습니다.  
  
`[ @pktab_name = ] 'pktab_name'`기본 키가 있는 테이블의 이름입니다. *pktab_name* 는 **sysname**이며 기본값은 NULL입니다.  
  
`[ @pktab_schema = ] 'pktab_schema'`기본 키가 있는 스키마의 이름입니다. *pktab_schema*는 **sysname**이며 기본값은 NULL입니다. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서는 여기에 소유자 이름이 포함됩니다.  
  
`[ @pktab_catalog = ] 'pktab_catalog'`기본 키가 있는 카탈로그의 이름입니다. *pktab_catalog*는 **sysname**이며 기본값은 NULL입니다. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서는 여기에 데이터베이스 이름이 포함됩니다.  
  
`[ @fktab_name = ] 'fktab_name'`외래 키가 있는 테이블의 이름입니다. *fktab_name*는 **sysname**이며 기본값은 NULL입니다.  
  
`[ @fktab_schema = ] 'fktab_schema'`외래 키가 있는 스키마의 이름입니다. *fktab_schema*는 **sysname**이며 기본값은 NULL입니다.  
  
`[ @fktab_catalog = ] 'fktab_catalog'`외래 키가 있는 카탈로그의 이름입니다. *fktab_catalog*는 **sysname**이며 기본값은 NULL입니다.  
  
## <a name="return-code-values"></a>반환 코드 값  
 없음  
  
## <a name="result-sets"></a>결과 집합  
 다양 한 DBMS 제품에서 테이블에 대해 세 부분으로 구성 되는 이름 (_카탈로그_)을 지원**합니다.** _스키마_**.** _테이블_)을 반환 합니다.  
  
|열 이름|데이터 형식|Description|  
|-----------------|---------------|-----------------|  
|**PKTABLE_CAT**|**sysname**|기본 키가 있는 테이블의 카탈로그입니다.|  
|**PKTABLE_SCHEM**|**sysname**|기본 키가 있는 테이블의 스키마입니다.|  
|**PKTABLE_NAME**|**sysname**|기본 키가 있는 테이블의 이름입니다. 이 필드는 항상 값을 반환합니다.|  
|**PKCOLUMN_NAME**|**sysname**|반환 된 **TABLE_NAME** 의 각 열에 대 한 기본 키 열의 이름입니다. 이 필드는 항상 값을 반환합니다.|  
|**FKTABLE_CAT**|**sysname**|외래 키가 있는 테이블의 카탈로그입니다.|  
|**FKTABLE_SCHEM**|**sysname**|외래 키가 있는 테이블의 스키마입니다.|  
|**FKTABLE_NAME**|**sysname**|외래 키가 있는 테이블의 이름입니다. 이 필드는 항상 값을 반환합니다.|  
|**FKCOLUMN_NAME**|**sysname**|반환되는 TABLE_NAME의 각 열에 대한 외래 키 열의 이름입니다. 이 필드는 항상 값을 반환합니다.|  
|**KEY_SEQ**|**smallint**|기본 키가 여러 열로 구성된 경우 열의 시퀀스 번호입니다. 이 필드는 항상 값을 반환합니다.|  
|**UPDATE_RULE**|**smallint**|SQL 작업이 업데이트일 때 외래 키에 적용되는 동작입니다. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]는 다음과 같은 열에 대해 0, 1 또는 2를 반환합니다.<br /><br /> 0=CASCADE는 외래 키를 변경합니다.<br /><br /> 1=NO ACTION은 외래 키가 있으면 변경합니다.<br /><br /> 2=SET_NULL. 외래 키를 NULL로 설정합니다.|  
|**DELETE_RULE**|**smallint**|SQL 작업이 삭제일 때 외래 키에 적용되는 동작입니다. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]는 다음과 같은 열에 대해 0, 1 또는 2를 반환합니다.<br /><br /> 0=CASCADE는 외래 키를 변경합니다.<br /><br /> 1=NO ACTION은 외래 키가 있으면 변경합니다.<br /><br /> 2=SET_NULL. 외래 키를 NULL로 설정합니다.|  
|**FK_NAME**|**sysname**|외래 키 식별자입니다. 데이터 원본에 적용할 수 없는 경우 NULL입니다. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]는 FOREIGN KEY 제약 조건 이름을 반환합니다.|  
|**PK_NAME**|**sysname**|기본 키 식별자입니다. 데이터 원본에 적용할 수 없는 경우 NULL입니다. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]는 PRIMARY KEY 제약 조건 이름을 반환합니다.|  
|**DEFERRABILITY**|**smallint**|제약 조건 검사를 연기할 수 있는지 여부를 나타냅니다.|  
  
 결과 집합에서 FK_NAME 및 PK_NAME 열은 항상 NULL을 반환합니다.  
  
## <a name="remarks"></a>설명  
 **sp_foreignkeys** 는 *table_server*에 해당 하는 OLE DB 공급자의 **IDBSchemaRowset** 인터페이스 FOREIGN_KEYS 행 집합을 쿼리 합니다. *Table_name*, *table_schema*, *table_catalog*및 *열* 매개 변수는 반환 되는 행을 제한 하기 위해이 인터페이스에 전달 됩니다.  
  
## <a name="permissions"></a>권한  
 스키마에 대한 SELECT 권한이 필요합니다.  
  
## <a name="examples"></a>예  
 다음 예에서는 연결된 서버 `Department`의 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 데이터베이스에 있는 `Seattle1` 테이블에 대한 외래 키 정보를 반환합니다.  
  
```  
EXEC sp_foreignkeys @table_server = N'Seattle1',   
   @pktab_name = N'Department',   
   @pktab_catalog = N'AdventureWorks2012';  
```  
  
## <a name="see-also"></a>참고 항목  
 [Transact-sql&#41;sp_catalogs &#40;](../../relational-databases/system-stored-procedures/sp-catalogs-transact-sql.md)   
 [Transact-sql&#41;sp_column_privileges &#40;](../../relational-databases/system-stored-procedures/sp-column-privileges-transact-sql.md)   
 [Transact-sql&#41;sp_indexes &#40;](../../relational-databases/system-stored-procedures/sp-indexes-transact-sql.md)   
 [Transact-sql&#41;sp_linkedservers &#40;](../../relational-databases/system-stored-procedures/sp-linkedservers-transact-sql.md)   
 [Transact-sql&#41;sp_primarykeys &#40;](../../relational-databases/system-stored-procedures/sp-primarykeys-transact-sql.md)   
 [Transact-sql&#41;sp_tables_ex &#40;](../../relational-databases/system-stored-procedures/sp-tables-ex-transact-sql.md)   
 [Transact-sql&#41;sp_table_privileges &#40;](../../relational-databases/system-stored-procedures/sp-table-privileges-transact-sql.md)   
 [시스템 저장 프로시저&#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
