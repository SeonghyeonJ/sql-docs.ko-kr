---
title: STStartPoint(geography 데이터 형식) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- STStartPoint_TSQL
- STStartPoint (geography Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- STStartPoint method
ms.assetid: 7df18a5f-b9ee-4e36-b765-a0790c1dee3d
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: f673860664d6be588479111803c200f2903db0ca
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/30/2020
ms.locfileid: "68120787"
---
# <a name="ststartpoint-geography-data-type"></a>STStartPoint(geography 데이터 형식)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  **geography** 인스턴스의 시작 지점을 반환합니다.  
  
## <a name="syntax"></a>구문  
  
```  
  
.STStartPoint ( )  
```  
  
## <a name="return-types"></a>반환 형식  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 반환 형식: **geography**  
  
 CLR 반환 형식: **SqlGeography**  
  
 OGC(Open Geospatial Consortium) 형식: **Point**  
  
## <a name="remarks"></a>설명  
 STStartPoint()는 [STPointN](../../t-sql/spatial-geometry/stpointn-geometry-data-type.md)`(1)`과 동일합니다.  
  
## <a name="examples"></a>예  
 다음 예에서는 `LineString` 인스턴스를 만들고 `STStartPoint()`를 사용하여 인스턴스의 시작점을 검색합니다.  
  
```  
DECLARE @g geography;  
SET @g = geography::STGeomFromText('LINESTRING(-122.360 47.656, -122.343 47.656)', 4326);  
SELECT @g.STStartPoint().ToString();  
```  
  
## <a name="see-also"></a>참고 항목  
 [지리 인스턴스의 OGC 메서드](../../t-sql/spatial-geography/ogc-methods-on-geography-instances.md)  
  
  
