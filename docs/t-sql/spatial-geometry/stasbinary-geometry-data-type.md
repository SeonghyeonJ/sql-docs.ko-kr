---
title: STAsBinary(geometry 데이터 형식) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- STAsBinary_TSQL
- STAsBinary (geometry Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- STAsBinary (geometry Data Type)
ms.assetid: 65353777-e3e6-461c-9504-ea4d83312692
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: aa0bc1c078e476fbf888f632f583179c6066e1e8
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85748802"
---
# <a name="stasbinary-geometry-data-type"></a>STAsBinary(geometry 데이터 형식)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

  geometry 인스턴스의 OGC(Open Geospatial Consortium) WKB(Well-Known Binary) 표현을 반환합니다.  
 
## <a name="syntax"></a>구문  
  
```  
  
.STAsBinary ( )  
```  
  
## <a name="return-types"></a>반환 형식  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 반환 형식: **varbinary(max)**  
  
 CLR 반환 형식: **SqlBytes**  
  
## <a name="examples"></a>예  
 다음 예에서는 텍스트에서 `LineString` geometry 인스턴스((0,0) - (2,3))를 만듭니다. `STAsBinary()`는 결과를 텍스트로 반환합니다.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('LINESTRING(0 0, 2 3)', 0);  
SELECT @g.STAsBinary();  
```  
  
## <a name="see-also"></a>참고 항목  
 [geometry 인스턴스의 OGC 메서드](../../t-sql/spatial-geometry/ogc-methods-on-geometry-instances.md)  
  
  
