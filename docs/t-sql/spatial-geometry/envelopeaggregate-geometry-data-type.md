---
title: EnvelopeAggregate(geometry 데이터 형식) | Microsoft Docs
ms.custom: ''
ms.date: 08/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- EnvelopeAggregate method (geometry)
ms.assetid: c4c15abe-0fe9-441d-9d42-6572e264869c
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: aec6618297f0ed38bfea5e730a452d4ccc9fae9b
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/30/2020
ms.locfileid: "68081186"
---
# <a name="envelopeaggregate-geometry-data-type"></a>EnvelopeAggregate(geometry 데이터 형식)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

지정된 **geometry** 개체 집합에 대한 경계 상자를 반환합니다.
  
## <a name="syntax"></a>구문  
  
```  
  
EnvelopeAggregate ( geometry_operand )  
```  
  
## <a name="arguments"></a>인수  
 *geometry_operand*  
 **geometry** 개체 집합을 나타내는 **geometry** 형식 테이블 열입니다.  
  
## <a name="return-types"></a>반환 형식  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 반환 형식: **geometry**  
  
## <a name="exceptions"></a>예외  
 유효하지 않은 입력 값이 있는 경우 `FormatException`을 발생시킵니다. [STIsValid &#40;geometry 데이터 형식&#41;](../../t-sql/spatial-geometry/stisvalid-geometry-data-type.md) 참조  
  
## <a name="remarks"></a>설명  
 이 메서드는 입력이 비어 있거나 입력에 다른 SRID가 있는 경우 **null**을 반환합니다. [Spatial Reference Identifier&#40;SRIDs&#41;](../../relational-databases/spatial/spatial-reference-identifiers-srids.md) 참조  
  
 이 메서드는 **null** 입력을 무시합니다.  
  
> [!NOTE]  
>  이 메서드는 모든 입력 값이 **null**인 경우 **null**을 반환합니다.  
  
## <a name="examples"></a>예  
 다음 예에서는 테이블 변수 열에 있는 개체 집합에 대한 경계 상자를 반환합니다.  
  
 ```
 -- Setup table variable for EnvelopeAggregate example 
DECLARE @Geom TABLE 
( 
shape geometry, 
shapeType nvarchar(50) 
) 
INSERT INTO @Geom(shape,shapeType) VALUES('CURVEPOLYGON(CIRCULARSTRING(2 3, 4 1, 6 3, 4 5, 2 3))', 'Circle'), 
('POLYGON((1 1, 4 1, 4 5, 1 5, 1 1))', 'Rectangle'); 
-- Perform EnvelopeAggregate on @Geom.shape column 
SELECT geometry::EnvelopeAggregate(shape).ToString() 
FROM @Geom;
 ```  
  
## <a name="see-also"></a>참고 항목  
 [확장 정적 기하 도형 메서드](../../t-sql/spatial-geometry/extended-static-geometry-methods.md)  
  
  

