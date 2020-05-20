---
title: 테이블 백업 및 복원 (Transact-sql) | Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- system tables [SQL Server], backup tables
- backup system tables [SQL Server]
- system tables [SQL Server], restore tables
- restore system tables [SQL Server]
ms.assetid: aa615add-54e6-40f5-8b55-3728b26884ee
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 9bd366cc3d78887959e7eb08d0a63aba156cb780
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/05/2020
ms.locfileid: "82827351"
---
# <a name="backup-and-restore-tables-transact-sql"></a>테이블 백업 및 복원(Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  이 섹션의 항목에서는 데이터베이스 백업 및 복원 작업에서 사용하는 정보를 저장하는 시스템 테이블에 대해 설명합니다.  
  
## <a name="in-this-section"></a>섹션 내용  
 [backupfile](../../relational-databases/system-tables/backupfile-transact-sql.md)  
 데이터베이스의 각 데이터 또는 로그 파일마다 하나의 행을 포함합니다.  
  
 [backupfilegroup](../../relational-databases/system-tables/backupfilegroup-transact-sql.md)  
 백업 당시 데이터베이스의 각 파일 그룹마다 하나의 행을 포함합니다.  
  
 [backupmediafamily](../../relational-databases/system-tables/backupmediafamily-transact-sql.md)  
 각 미디어 패밀리마다 하나의 행을 포함합니다.  
  
 [backupmediaset](../../relational-databases/system-tables/backupmediaset-transact-sql.md)  
 각 백업 미디어 세트에 대해 한 행을 포함합니다.  
  
 [backupset](../../relational-databases/system-tables/backupset-transact-sql.md)  
 각 백업 세트마다 하나의 행을 포함합니다.  
  
 [logmarkhistory](../../relational-databases/system-tables/logmarkhistory-transact-sql.md)  
 표시되어 있는 각각의 커밋된 트랜잭션에 대해 하나의 행을 포함합니다.  
  
 [restorefile](../../relational-databases/system-tables/restorefile-transact-sql.md)  
 복원된 각 파일 그룹에 대해 하나의 행을 포함합니다. 여기에는 파일 그룹 이름에 의해 간접적으로 복원된 파일이 포함됩니다.  
  
 [restorefilegroup](../../relational-databases/system-tables/restorefilegroup-transact-sql.md)  
 복원된 각 파일 그룹에 대해 하나의 행을 포함합니다.  
  
 [restorehistory](../../relational-databases/system-tables/restorehistory-transact-sql.md)  
 각 복원 작업에 대해 하나의 행을 포함합니다.  
  
 [suspect_pages](../../relational-databases/system-tables/suspect-pages-transact-sql.md)  
 824 오류가 발생하여 실패한 페이지당 하나의 행을 포함합니다(최대 1,000개 행까지).  
  
 [sysopentapes](../../relational-databases/system-tables/sysopentapes-transact-sql.md)  
 현재 열려 있는 각 테이프 디바이스에 대해 한 행을 포함합니다.  
  
  
