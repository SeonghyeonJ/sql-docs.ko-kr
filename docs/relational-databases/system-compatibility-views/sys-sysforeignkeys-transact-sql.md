---
description: sys.sysforeignkeys(Transact-SQL)
title: sys.sysforeignkeys (Transact-sql) | Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sysforeignkeys
- sys.sysforeignkeys
- sys.sysforeignkeys_TSQL
- sysforeignkeys_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sysforeignkeys system table
- sys.sysforeignkeys compatibility view
ms.assetid: 41544236-1c46-4501-be88-18c06963b6e8
author: rothja
ms.author: jroth
ms.openlocfilehash: 15a02ec0dc5b6b1e5b376876b18e36863468e59e
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88455104"
---
# <a name="syssysforeignkeys-transact-sql"></a>sys.sysforeignkeys(Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  데이터베이스의 테이블 정의에 있는 FOREIGN KEY 제약 조건에 관한 정보를 포함합니다.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssnoteCompView](../../includes/ssnotecompview-md.md)]  
  
|열 이름|데이터 형식|Description|  
|-----------------|---------------|-----------------|  
|**constid**|**int**|FOREIGN KEY 제약 조건의 ID입니다.|  
|**fkeyid**|**int**|FOREIGN KEY 제약 조건이 있는 테이블의 개체 ID입니다.|  
|**rkeyid**|**int**|FOREIGN KEY 제약 조건에서 참조되는 테이블의 개체 ID입니다.|  
|**fkey**|**smallint**|참조하는 열의 ID입니다.|  
|**rkey**|**smallint**|참조되는 열의 ID입니다.|  
|**keyno**|**smallint**|참조 열 목록에서 열의 위치입니다.|  
  
## <a name="see-also"></a>참고 항목  
 [시스템 테이블을 시스템 뷰로 매핑 &#40;Transact-sql&#41;](../../relational-databases/system-tables/mapping-system-tables-to-system-views-transact-sql.md)   
 [호환성 뷰&#40;Transact-SQL&#41;](~/relational-databases/system-compatibility-views/system-compatibility-views-transact-sql.md)  
  
  
