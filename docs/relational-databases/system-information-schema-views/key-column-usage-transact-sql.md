---
title: KEY_COLUMN_USAGE (TRANSACT-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- KEY_COLUMN_USAGE_TSQL
- KEY_COLUMN_USAGE
dev_langs:
- TSQL
helpviewer_keywords:
- INFORMATION_SCHEMA.KEY_COLUMN_USAGE view
- KEY_COLUMN_USAGE view
ms.assetid: ec1e18c2-63a1-4d2b-ba9a-c13857403782
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: d38e6ae0eaf7ed6015834052067db28993cbcccd
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67948619"
---
# <a name="keycolumnusage-transact-sql"></a>KEY_COLUMN_USAGE(Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  현재 데이터베이스에서 제약 조건이 키로 지정되어 있는 각 열에 대해 한 행씩 반환합니다. 이 정보 스키마 뷰는 현재 사용자가 사용 권한을 갖고 있는 개체에 대한 정보를 반환합니다.  
  
 이러한 뷰에서 정보를 검색할의 정규화 된 이름을 지정 **INFORMATION_SCHEMA.** _view_name_합니다.  
  
|열 이름|데이터 형식|설명|  
|-----------------|---------------|-----------------|  
|**CONSTRAINT_CATALOG**|**nvarchar(** 128 **)**|제약 조건 한정자입니다.|  
|**CONSTRAINT_SCHEMA**|**nvarchar(** 128 **)**|제약 조건이 포함된 스키마의 이름입니다.<br /><br /> <strong>\*\* 중요 \* \*</strong>  개체의 스키마를 확인 하려면 INFORMATION_SCHEMA 뷰를 사용 하지 마십시오. 개체의 스키마를 확인하는 신뢰할 수 있는 유일한 방법은 sys.objects 카탈로그 뷰를 쿼리하는 것입니다.|  
|**제약 조건 이름**|**nvarchar(** 128 **)**|제약 조건 이름입니다.|  
|**TABLE_CATALOG**|**nvarchar(** 128 **)**|테이블 한정자입니다.|  
|**TABLE_SCHEMA**|**nvarchar(** 128 **)**|테이블이 포함된 스키마의 이름입니다.<br /><br /> <strong>\*\* 중요 \* \*</strong>  개체의 스키마를 확인 하려면 INFORMATION_SCHEMA 뷰를 사용 하지 마십시오. 개체의 스키마를 확인하는 신뢰할 수 있는 유일한 방법은 sys.objects 카탈로그 뷰를 쿼리하는 것입니다.|  
|**TABLE_NAME**|**nvarchar(** 128 **)**|테이블 이름입니다.|  
|**COLUMN_NAME**|**nvarchar(** 128 **)**|열 이름입니다.|  
|**ORDINAL_POSITION**|**int**|열의 서수 위치입니다.|  
  
## <a name="see-also"></a>관련 항목  
 [시스템 뷰 &#40;TRANSACT-SQL&#41;](https://msdn.microsoft.com/library/35a6161d-7f43-4e00-bcd3-3091f2015e90)   
 [정보 스키마 뷰 &#40;TRANSACT-SQL&#41;](~/relational-databases/system-information-schema-views/system-information-schema-views-transact-sql.md)   
 [sys.columns&#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-columns-transact-sql.md)   
 [sys.indexes&#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md)   
 [sys.objects&#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md)   
 [sys.foreign_keys &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-foreign-keys-transact-sql.md)   
 [sys.key_constraints &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-key-constraints-transact-sql.md)  
  
  
