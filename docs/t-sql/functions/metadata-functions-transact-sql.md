---
title: 메타데이터 함수(Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- metadata [SQL Server], functions
- functions [SQL Server], metadata
ms.assetid: a18c12a9-59ad-4711-a862-39d8f28476b0
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 05d75e3c02953c637eb338e11ceb0a92475ea352
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85681936"
---
# <a name="metadata-functions-transact-sql"></a>메타데이터 함수(Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

다음 스칼라 함수는 데이터베이스와 데이터베이스 개체에 대한 정보를 반환합니다.  
  
- [@@PROCID](../../t-sql/functions/procid-transact-sql.md)
- [APP_NAME](../../t-sql/functions/app-name-transact-sql.md)
- [APPLOCK_MODE](../../t-sql/functions/applock-mode-transact-sql.md)
- [APPLOCK_TEST](../../t-sql/functions/applock-test-transact-sql.md)
- [ASSEMBLYPROPERTY](../../t-sql/functions/assemblyproperty-transact-sql.md)
- [COL_LENGTH](../../t-sql/functions/col-length-transact-sql.md)
- [COL_NAME](../../t-sql/functions/col-name-transact-sql.md)
- [COLUMNPROPERTY](../../t-sql/functions/columnproperty-transact-sql.md)
- [DATABASE_PRINCIPAL_ID](../../t-sql/functions/database-principal-id-transact-sql.md)
- [DATABASEPROPERTYEX](../../t-sql/functions/databasepropertyex-transact-sql.md)
- [DB_ID](../../t-sql/functions/db-id-transact-sql.md)
- [DB_NAME](../../t-sql/functions/db-name-transact-sql.md)
- [FILE_ID](../../t-sql/functions/file-id-transact-sql.md)
- [FILE_IDEX](../../t-sql/functions/file-idex-transact-sql.md)
- [FILE_NAME](../../t-sql/functions/file-name-transact-sql.md)
- [FILEGROUP_ID](../../t-sql/functions/filegroup-id-transact-sql.md)
- [FILEGROUP_NAME](../../t-sql/functions/filegroup-name-transact-sql.md)
- [FILEGROUPPROPERTY](../../t-sql/functions/filegroupproperty-transact-sql.md)
- [FILEPROPERTY](../../t-sql/functions/fileproperty-transact-sql.md)
- [FULLTEXTCATALOGPROPERTY](../../t-sql/functions/fulltextcatalogproperty-transact-sql.md)
- [FULLTEXTSERVICEPROPERTY](../../t-sql/functions/fulltextserviceproperty-transact-sql.md)
- [INDEX_COL](../../t-sql/functions/index-col-transact-sql.md)  
- [INDEXKEY_PROPERTY](../../t-sql/functions/indexkey-property-transact-sql.md)  
- [INDEXPROPERTY](../../t-sql/functions/indexproperty-transact-sql.md)  
- [NEXT VALUE FOR](../../t-sql/functions/next-value-for-transact-sql.md)  
- [OBJECT_DEFINITION](../../t-sql/functions/object-definition-transact-sql.md)  
- [OBJECT_ID](../../t-sql/functions/object-id-transact-sql.md)  
- [OBJECT_NAME](../../t-sql/functions/object-name-transact-sql.md)  
- [OBJECT_SCHEMA_NAME](../../t-sql/functions/object-schema-name-transact-sql.md)  
- [OBJECTPROPERTY](../../t-sql/functions/objectproperty-transact-sql.md)  
- [OBJECTPROPERTYEX](../../t-sql/functions/objectpropertyex-transact-sql.md)  
- [ORIGINAL_DB_NAME](../../t-sql/functions/original-db-name-transact-sql.md)  
- [PARSENAME](../../t-sql/functions/parsename-transact-sql.md)  
- [SCHEMA_ID](../../t-sql/functions/schema-id-transact-sql.md)  
- [SCHEMA_NAME](../../t-sql/functions/schema-name-transact-sql.md)  
- [SCOPE_IDENTITY](../../t-sql/functions/scope-identity-transact-sql.md)  
- [SERVERPROPERTY](../../t-sql/functions/serverproperty-transact-sql.md)  
- [STATS_DATE](../../t-sql/functions/stats-date-transact-sql.md)  
- [TYPE_ID](../../t-sql/functions/type-id-transact-sql.md)  
- [TYPE_NAME](../../t-sql/functions/type-name-transact-sql.md)  
- [TYPEPROPERTY](../../t-sql/functions/typeproperty-transact-sql.md)  
- [VERSION](../../t-sql/functions/version-transact-sql-metadata-functions.md)  
  
모든 메타데이터 함수는 비결정적입니다. 이는 이러한 함수를 호출할 때마다 동일한 입력 값 집합을 사용하더라도 항상 동일한 결과가 반환되지는 않는다는 것을 의미합니다.  
  
## <a name="see-also"></a>참고 항목  
 [기본 제공 함수s&#40;Transact-SQL&#41;](~/t-sql/functions/functions.md)  
  
  

