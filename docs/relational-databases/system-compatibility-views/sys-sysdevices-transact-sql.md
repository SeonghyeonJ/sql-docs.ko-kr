---
title: sysdevices (Transact-sql) | Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sysdevices
- sysdevices_TSQL
- sys.sysdevices
- sys.sysdevices_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sysdevices compatibility view
- sysdevices system table
ms.assetid: ac5bcaf4-8fb6-4855-8856-d7643f469361
author: rothja
ms.author: jroth
ms.openlocfilehash: 9cbd14a7ce8dd1cfb1571874a83a615065200014
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/27/2020
ms.locfileid: "68053526"
---
# <a name="syssysdevices-transact-sql"></a>sys.sysdevices(Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  각 디스크 백업 파일, 테이프 백업 파일 및 데이터베이스 파일에 대한 행을 하나씩 포함합니다.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssnoteCompView](../../includes/ssnotecompview-md.md)]  
  
|열 이름|데이터 형식|Description|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|백업 파일 또는 데이터베이스 파일의 논리적 이름입니다.|  
|**size**|**int**|2KB 페이지 단위로 표시한 파일 크기입니다.|  
|**거의**|**int**|이전 버전과의 호환성을 위해서만 유지됩니다.|  
|**high**|**int**|이전 버전과의 호환성을 위해서만 유지됩니다.|  
|**status**|**smallint**|디바이스 유형을 표시하는 비트맵입니다.<br /><br /> 1 = 기본 디스크<br /><br /> 2 = 물리적 디스크<br /><br /> 4 = 논리적 디스크<br /><br /> 8 = 머리글 건너뛰기<br /><br /> 16 = 백업 파일<br /><br /> 32 = 순차 쓰기<br /><br /> 4096 = 읽기 전용|  
|**cntrltype**|**smallint**|컨트롤러 종류입니다.<br /><br /> 0 = CD-ROM이 아닌 데이터베이스 파일<br /><br /> 2 = 디스크 백업 파일<br /><br /> 3 - 4 = 디스켓 백업 파일<br /><br /> 5 = 테이프 백업 파일<br /><br /> 6 = 명명된 파이프 파일|  
|**phyname**|**nvarchar(260)**|물리적 파일의 이름입니다.|  
  
## <a name="see-also"></a>참고 항목  
 [시스템 테이블을 시스템 뷰로 매핑 &#40;Transact-sql&#41;](../../relational-databases/system-tables/mapping-system-tables-to-system-views-transact-sql.md)   
 [호환성 뷰&#40;Transact-SQL&#41;](~/relational-databases/system-compatibility-views/system-compatibility-views-transact-sql.md)  
  
  
