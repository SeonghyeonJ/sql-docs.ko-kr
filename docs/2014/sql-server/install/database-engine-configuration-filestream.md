---
title: 데이터베이스 엔진 구성-Filestream | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- FILESTREAM [SQL Server], about FILESTREAM
ms.assetid: 641a10a1-ae52-4d26-8f1c-a032a4aeff02
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: ab12b507246a3e13ac59be213813604d531d9a28
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/18/2020
ms.locfileid: "85012726"
---
# <a name="database-engine-configuration---filestream"></a>데이터베이스 엔진 구성 - Filestream
  이 페이지를 사용하여 이 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 설치에 대해 FILESTREAM을 사용하도록 설정할 수 있습니다. FILESTREAM은 `varbinary(max)` BLOB(Binary Large Object) 데이터를 파일 시스템의 파일로 저장하여 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]을 NTFS 파일 시스템과 통합합니다. [!INCLUDE[tsql](../../includes/tsql-md.md)] 문은 FILESTREAM 데이터를 삽입, 업데이트, 쿼리, 검색 및 백업할 수 있습니다. Win32 파일 시스템 인터페이스에서는 데이터에 대한 스트리밍 액세스를 제공합니다.  
  
## <a name="ui-element-list"></a>UI 요소 목록  
 **Transact-SQL 액세스에 FILESTREAM 사용**  
 [!INCLUDE[tsql](../../includes/tsql-md.md)] 액세스에 FILESTREAM을 사용하도록 설정하려면 선택합니다. 다른 컨트롤 옵션을 사용하려면 먼저 이 컨트롤을 선택해야 합니다.  
  
 **파일 I/O 스트리밍 액세스에 FILESTREAM 사용**  
 Win32 스트리밍 액세스에 FILESTREAM을 사용하도록 설정하려면 선택합니다.  
  
 **Windows 공유 이름**  
 FILESTREAM 데이터가 저장될 Windows 공유의 이름을 입력하려면 이 컨트롤을 사용합니다.  
  
 **원격 클라이언트가 FILESTREAM 데이터에 대한 스트리밍 액세스를 가질 수 있도록 허용**  
 원격 클라이언트가 이 서버의 이 FILESTREAM 데이터에 액세스할 수 있도록 허용하려면 이 컨트롤을 선택합니다.  
  
## <a name="see-also"></a>참고 항목  
 [FILESTREAM 사용 및 구성](../../relational-databases/blob/enable-and-configure-filestream.md)   
 [sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
