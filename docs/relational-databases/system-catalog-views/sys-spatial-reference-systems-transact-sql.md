---
title: sys.spatial_reference_systems (TRANSACT-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- spatial_reference_systems_TSQL
- sys.spatial_reference_systems_TSQL
- sys.spatial_reference_systems
- spatial_reference_systems
dev_langs:
- TSQL
helpviewer_keywords:
- sys.spatial_reference_systems catalog view
- spatial_reference_systems
ms.assetid: 3c9bc120-67c3-463f-9e24-29fd623f25a0
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: c2ab77dbaf90edf1421a0d15073258c370de4c7d
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62856957"
---
# <a name="sysspatialreferencesystems-transact-sql"></a>sys.spatial_reference_systems(Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 지원되는 공간 참조 시스템(SRID)을 나열합니다.  

  
|열 이름|데이터 형식|Description|  
|-----------------|---------------|-----------------|  
|spatial_reference_id|**int**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 지원되는 SRID입니다.|  
|authority_name|**nvarchar(128)**|SRID의 인증 기관입니다.|  
|authorized_spatial_reference_id|**int**|에 명명 된 기관에 의해 지정 된 SRID **authority_name**합니다.|  
|well_known_text|**nvarchar(4000)**|SRID의 WKT 표현입니다.|  
|unit_of_measure|**nvarchar(128)**|측정 단위 이름입니다.|  
|unit_conversion_factor|**float**|미터 단위의 측정 단위 길이입니다.|  
  
## <a name="permissions"></a>사용 권한  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)]  
  
  
