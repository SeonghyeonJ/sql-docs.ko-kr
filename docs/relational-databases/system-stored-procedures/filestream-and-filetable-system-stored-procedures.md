---
description: Filestream 및 FileTable 시스템 저장 프로시저(Transact-SQL)
title: Filestream 및 FileTable 시스템 저장 프로시저 (Transact-sql) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- FileTables [SQL Server], catalog views
ms.assetid: 2c83a4a7-720b-4435-a3b5-788c29f56949
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 4b16bd28de1b6166cfcea3634c02d48ab8bdc400
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88489786"
---
# <a name="filestream-and-filetable-system-stored-procedures-transact-sql"></a>Filestream 및 FileTable 시스템 저장 프로시저 (Transact-sql)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  이 섹션에서는 FileTable 및 Filestream 기능에 대 한 시스템 저장 프로시저에 대해 설명 합니다.  

## <a name="filestream-and-filetable-system-stored-procedures"></a>Filestream 및 Filetable 시스템 저장 프로시저
  [sp_filestream_force_garbage_collection(Transact-SQL)](filestream-and-filetable-sp-filestream-force-garbage-collection.md)

   FILESTREAM 가비지 수집기를 실행하고 불필요한 FILESTREAM 파일을 삭제합니다.

  [sp_kill_filestream_non_transacted_handles(Transact-SQL)](filestream-and-filetable-sp-kill-filestream-non-transacted-handles.md)

  FileTable 데이터에 대한 비트랜잭션 핸들 파일을 닫습니다.


## <a name="see-also"></a>참조
[Filestream](../../relational-databases/blob/filestream-sql-server.md)
<br>[Filetable](../../relational-databases/blob/filetables-sql-server.md)
<br>[Filestream 및 FileTable 동적 관리 뷰(Transact-SQL)](../system-dynamic-management-views/filestream-and-filetable-dynamic-management-views-transact-sql.md)
<br>[Filestream 및 FileTable 카탈로그 뷰(Transact-SQL)](../system-catalog-views/filestream-and-filetable-catalog-views-transact-sql.md)
  
  
