---
title: STPolyFromWKB(geometry 데이터 형식) | Microsoft Docs
ms.custom: ''
ms.date: 08/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- STPolyFromWKB_TSQL
- STPolyFromWKB (geometry Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- STPolyFromWKB (geometry Data Type)
ms.assetid: 8e8f0c41-0c62-4919-9d4c-d37c93fdd31c
author: MladjoA
ms.author: mlandzic
manager: craigg
ms.openlocfilehash: cd9e5f6fe32a3a7652a87f9ff6fe5edf849b06e0
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/15/2019
ms.locfileid: "65938286"
---
# <a name="stpolyfromwkb-geometry-data-type"></a>STPolyFromWKB(geometry 데이터 형식)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

OGC(Open Geospatial Consortium) WKB(WELL-KNOWN Binary) 표현에서 **geometryPolygon** 인스턴스를 반환합니다.
  
## <a name="syntax"></a>구문  
  
```  
  
STPolyFromWKB ( 'WKB_polygon' , SRID )  
```  
  
## <a name="arguments"></a>인수  
 *WKB_polygon*  
 반환할 **geometryPolygon** 인스턴스의 WKB 표현입니다. *WKB_polygon*은 **varbinary(max)** 식입니다.  
  
 *SRID*  
 반환하려는 **geometryPolygon** 인스턴스의 SRID(spatial reference ID)를 나타내는 **int** 식입니다.  
  
## <a name="return-types"></a>반환 형식  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 반환 형식: **geometry**  
  
 CLR 반환 형식: **SqlGeometry**  
  
 OGC 형식: **다각형**  
  
## <a name="remarks"></a>Remarks  
 이 메서드는 입력이 잘못된 경우 **FormatException**을 throw합니다.  
  
## <a name="examples"></a>예  
 다음 예에서는 `STPolyFromWKB()`를 사용하여 `geometry` 인스턴스를 만듭니다.  
  
```  
DECLARE @g geometry;   
SET @g = geometry::STPolyFromWKB(0x0103000000010000000400000000000000000014400000000000001440000000000000244000000000000014400000000000002440000000000000244000000000000014400000000000001440, 0);  
SELECT @g.STAsText();  
```  
  
## <a name="see-also"></a>참고 항목  
 [OGC 정적 기하 도형 메서드](../../t-sql/spatial-geometry/ogc-static-geometry-methods.md)  
  
  

