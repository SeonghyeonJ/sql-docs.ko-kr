---
description: STY(geometry 데이터 형식)
title: STY(geometry 데이터 형식) | Microsoft Docs
ms.custom: ''
ms.date: 08/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- STY_TSQL
- STY (geometry Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- STY (geometry Data Type)
ms.assetid: f72e0eaa-7d1d-4052-88fd-a172d8cb0d71
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: ae260a3587e3f0f9ea08829a89bfe78901cfb0e2
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88472395"
---
# <a name="sty-geometry-data-type"></a>STY(geometry 데이터 형식)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

**Point** 인스턴스의 Y 좌표 속성입니다.
  
## <a name="syntax"></a>구문  
  
```  
  
.STY  
```  
  
[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="return-types"></a>반환 형식
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 형식: **float**  
  
 CLR 유형: **SqlDouble**  
  
## <a name="remarks"></a>설명  
 **geometry** 인스턴스가 점인 경우 이 속성의 값은 Null입니다. 이 속성은 읽기 전용입니다.  
  
## <a name="examples"></a>예제  
 다음 예에서는 `Point` 인스턴스를 만들고 `STY`를 사용하여 인스턴스의 Y 좌표를 검색합니다.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('POINT(3 8)', 0);  
SELECT @g.STY;  
```  
  
## <a name="see-also"></a>참고 항목  
 [STX&#40;geometry 데이터 형식&#41;](../../t-sql/spatial-geometry/stx-geometry-data-type.md)   
 [STSrid&#40;geometry 데이터 형식&#41;](../../t-sql/spatial-geometry/stsrid-geometry-data-type.md)   
 [geometry 인스턴스의 OGC 메서드](../../t-sql/spatial-geometry/ogc-methods-on-geometry-instances.md)  
  
  

