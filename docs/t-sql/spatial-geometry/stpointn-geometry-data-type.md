---
title: STPointN(geometry 데이터 형식) | Microsoft Docs
ms.custom: ''
ms.date: 08/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- STPointN_TSQL
- STPointN (geometry Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- STPointN (geometry Data Type)
ms.assetid: 8f0bb3b7-5cd9-42c2-b9f8-f04628653bd0
author: MladjoA
ms.author: mlandzic
manager: craigg
ms.openlocfilehash: f7bbaf25715275b14deda0f2a510b40934c6f33e
ms.sourcegitcommit: 57c3b07cba5855fc7b4195a0586b42f8b45c08c2
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/20/2019
ms.locfileid: "65938377"
---
# <a name="stpointn-geometry-data-type"></a>STPointN(geometry 데이터 형식)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

**geometry** 인스턴스의 지정된 점을 반환합니다.
  
## <a name="syntax"></a>구문  
  
```  
  
.STPointN ( expression )  
```  
  
## <a name="arguments"></a>인수  
 *expression*  
 1과 **geometry** 인스턴스에 있는 점 개수 사이의 **int** 식입니다.  
  
## <a name="return-types"></a>반환 형식  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 반환 형식: **geometry**  
  
 CLR 반환 형식: **SqlGeometry**  
  
 OGC(Open Geospatial Consortium) 형식: **Point**  
  
## <a name="remarks"></a>Remarks  
 사용자가 **geometry** 인스턴스를 만든 경우 `STPointN()`은 *expression*을 통해 지정된 점을 원래 입력된 순서대로 정렬하여 반환합니다.  
  
 시스템에서 **geometry** 인스턴스를 생성한 경우 `STPointN()`은 *expression*을 통해 지정한 점을 모두 출력 순서와 동일하게 geometry, geometry의 링(해당되는 경우), 이 링 내의 점 순서로 정렬하여 반환합니다. 이 순서는 결정적입니다.  
  
 1보다 작은 값을 사용하여 이 메서드를 호출하면 이 메서드는 **ArgumentOutOfRangeException**을 throw합니다.  
  
 인스턴스에 있는 점 개수보다 큰 값을 사용하여 이 메서드를 호출하면 이 메서드는 Null을 반환합니다.  
  
## <a name="examples"></a>예  
 다음 예에서는 `LineString` 인스턴스를 만들고 `STPointN()`을 사용하여 인스턴스의 설명에 있는 두 번째 점을 검색합니다.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('LINESTRING(0 0, 2 2, 1 0)', 0);  
SELECT @g.STPointN(2).ToString();  
```  
  
## <a name="see-also"></a>참고 항목  
 [geometry 인스턴스의 OGC 메서드](../../t-sql/spatial-geometry/ogc-methods-on-geometry-instances.md)  
  
  

