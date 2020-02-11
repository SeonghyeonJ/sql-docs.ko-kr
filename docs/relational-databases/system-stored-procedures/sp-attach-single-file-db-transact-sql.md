---
title: sp_attach_single_file_db (Transact-sql) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_attach_single_file_db
- sp_attach_single_file_db_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_attach_single_file_db
ms.assetid: 13bd1044-9497-4293-8390-1f12e6b8e952
author: stevestein
ms.author: sstein
ms.openlocfilehash: b285b5032c1ccde03ef8bd3f287d6b7f60eb0ffc
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68046173"
---
# <a name="sp_attach_single_file_db-transact-sql"></a>sp_attach_single_file_db(Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  데이터 파일이 한 개만 있는 데이터베이스를 현재 서버에 연결합니다. **sp_attach_single_file_db** 는 여러 데이터 파일과 함께 사용할 수 없습니다.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]대신 CREATE DATABASE *database_name* 를 사용 하 여 연결 하는 것이 좋습니다. 자세한 내용은 [CREATE DATABASE&#40;SQL Server Transact-SQL&#41;](../../t-sql/statements/create-database-sql-server-transact-sql.md)를 참조하세요. 복제 데이터베이스에는 이 프로시저를 사용하지 마십시오.  
  
> [!IMPORTANT]  
>  알 수 없거나 신뢰할 수 없는 출처의 데이터베이스는 연결 또는 복원하지 않는 것이 좋습니다. 이러한 데이터베이스에 포함된 악성 코드가 의도하지 않은 [!INCLUDE[tsql](../../includes/tsql-md.md)] 코드를 실행하거나 스키마 또는 물리적 데이터베이스 구조를 수정하여 오류가 발생할 수 있습니다. 출처를 알 수 없거나 신뢰할 수 없는 데이터베이스를 사용 하기 전에 비프로덕션 서버의 데이터베이스에서 [DBCC CHECKDB](../../t-sql/database-console-commands/dbcc-checkdb-transact-sql.md) 를 실행 하 고 데이터베이스의 코드 (예: 저장 프로시저 또는 다른 사용자 정의 코드)도 검사 합니다.  
  
 ![항목 링크 아이콘](../../database-engine/configure-windows/media/topic-link.gif "항목 링크 아이콘") [Transact-SQL 구문 표기 규칙](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>구문  
  
```  
  
sp_attach_single_file_db [ @dbname= ] 'dbname'  
    , [ @physname= ] 'physical_name'  
```  
  
## <a name="arguments"></a>인수  
`[ @dbname = ] 'dbname'`서버에 연결할 데이터베이스의 이름입니다. 이름은 고유해야 합니다. *dbname* 은 **sysname**이며 기본값은 NULL입니다.  
  
`[ @physname = ] 'physical_name'`경로를 포함 한 데이터베이스 파일의 물리적 이름입니다. *physical_name* 은 **nvarchar (260)** 이며 기본값은 NULL입니다.  
  
> [!NOTE]  
>  이 인수는 CREATE DATABASE 문의 FILENAME 매개 변수에 매핑됩니다. 자세한 내용은 [CREATE DATABASE&#40;SQL Server Transact-SQL&#41;](../../t-sql/statements/create-database-sql-server-transact-sql.md)를 참조하세요.  
  
 
  [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 서버 인스턴스에 전체 텍스트 카탈로그 파일이 포함된 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 데이터베이스를 연결할 경우 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]에서와 같이 다른 데이터베이스 파일과 함께 이전 위치에서 카탈로그 파일이 연결됩니다. 자세한 내용은 [전체 텍스트 검색 업그레이드](../../relational-databases/search/upgrade-full-text-search.md)를 참조하세요.  
  
## <a name="return-code-values"></a>반환 코드 값  
 0(성공) 또는 1(실패)  
  
## <a name="result-sets"></a>결과 집합  
 None  
  
## <a name="remarks"></a>설명  
 명시적 **sp_detach_db** 작업을 사용 하 여 서버에서 이전에 분리 된 데이터베이스나 복사 된 데이터베이스 에서만 **sp_attach_single_file_db** 를 사용 합니다.  
  
 **sp_attach_single_file_db** 는 단일 로그 파일이 있는 데이터베이스 에서만 작동 합니다. **Sp_attach_single_file_db** 데이터베이스를 서버에 연결 하는 경우 새 로그 파일을 작성 합니다. 데이터베이스가 읽기 전용이면 이전 위치에 로그 파일이 만들어집니다.  
  
> [!NOTE]  
>  데이터베이스 스냅샷은 분리하거나 연결할 수 없습니다.  
  
 복제 데이터베이스에는 이 프로시저를 사용하지 마십시오.  
  
## <a name="permissions"></a>사용 권한  
 데이터베이스가 연결 될 때 사용 권한이 처리 되는 방법에 대 한 자세한 내용은 [CREATE database &#40;SQL Server transact-sql&#41;](../../t-sql/statements/create-database-sql-server-transact-sql.md)를 참조 하세요.  
  
## <a name="examples"></a>예  
 다음 예에서는 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]를 분리한 다음 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]의 파일 하나를 현재 서버에 연결합니다.  
  
```  
USE master;  
GO  
EXEC sp_detach_db @dbname = 'AdventureWorks2012';  
EXEC sp_attach_single_file_db @dbname = 'AdventureWorks2012',   
    @physname =   
N'C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\Data\AdventureWorks2012_Data.mdf';  
```  
  
## <a name="see-also"></a>참고 항목  
 [데이터베이스 분리 및 연결 &#40;SQL Server&#41;](../../relational-databases/databases/database-detach-and-attach-sql-server.md)   
 [Transact-sql&#41;sp_detach_db &#40;](../../relational-databases/system-stored-procedures/sp-detach-db-transact-sql.md)   
 [Transact-sql&#41;sp_helpfile &#40;](../../relational-databases/system-stored-procedures/sp-helpfile-transact-sql.md)   
 [시스템 저장 프로시저&#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
