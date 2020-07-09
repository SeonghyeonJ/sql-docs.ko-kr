---
title: ConvexHullAggregate(geography 데이터 형식) | Microsoft Docs
ms.custom: ''
ms.date: 07/30/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- ConvexHullAggregate_TSQL
- ConvexHullAggregate
dev_langs:
- TSQL
helpviewer_keywords:
- ConvexHullAggregate method (geography)
ms.assetid: 21784c66-2725-471b-9e2d-a8c2e3695197
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: 67980ca0f7e58a9a3051cfd28d3d120acaabeb47
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85736168"
---
# <a name="convexhullaggregate-geography-data-type"></a>ConvexHullAggregate(geography 데이터 형식)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

제공된 **geography** 개체 집합에 대한 볼록 집합(convex hull)을 반환합니다.
  
## <a name="syntax"></a>구문  
  
```  
  
ConvexHullAggregate ( geography_operand )  
```  
  
## <a name="arguments"></a>인수  
 *geography_operand*  
 **geography** 개체 집합을 나타내는 **geography** 형식 테이블 열입니다.  
  
## <a name="return-types"></a>반환 형식  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 반환 형식: **geography**  
  
## <a name="exception"></a>예외  
 유효하지 않은 입력 값이 있는 경우 `FormatException`을 발생시킵니다. [STIsValid&#40;geography 데이터 형식&#41;](../../t-sql/spatial-geography/stisvalid-geography-data-type.md) 참조  
  
## <a name="remarks"></a>설명  
 이 메서드는 입력이 비어 있거나 입력에 다른 SRID가 있는 경우 **null**을 반환합니다. [Spatial Reference Identifier&#40;SRIDs&#41;](../../relational-databases/spatial/spatial-reference-identifiers-srids.md) 참조  
  
 이 메서드는 **null** 입력을 무시합니다.  
  
> [!NOTE]  
>  이 메서드는 모든 입력 값이 **null**인 경우 **null**을 반환합니다.  
  
## <a name="examples"></a>예  
 다음 예에서는 **geography** 개체 집합의 볼록 집합(convex hull)을 반환합니다.  
  
 ```
 USE AdventureWorks2012  
 GO  
 SELECT geography::ConvexHullAggregate(SpatialLocation).ToString() AS SpatialLocation  
 FROM Person.Address  
 WHERE City LIKE ('Bothell')
 ```  
  
## <a name="see-also"></a>참고 항목  
 [확장 정적 지리 메서드](../../t-sql/spatial-geography/extended-static-geography-methods.md)  
  
  
