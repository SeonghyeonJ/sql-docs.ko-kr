---
title: Point(geometry 데이터 형식) | Microsoft Docs
ms.custom: ''
ms.date: 08/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- Point
- Point_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- Point (geometry Data Type)
ms.assetid: 7a2e593a-4d4c-4214-b0c5-02d1ac46bc66
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: 3a0c9f31f0e724c56c22a46653eb56d51f2616fe
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/01/2020
ms.locfileid: "68101033"
---
# <a name="point-geometry-data-type"></a>Point(geometry 데이터 형식)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

해당 X 값, Y 값 및 SRID의 **Point** 인스턴스를 나타내는 **geometry** 인스턴스를 생성합니다.
  
## <a name="syntax"></a>구문  
  
```  
  
Point ( X, Y, SRID )  
```  
  
## <a name="arguments"></a>인수  
 *X*  
 생성할 **Point**의 X 좌표를 나타내는 **float** 식입니다.  
  
 *예*  
 생성할 **Point**의 Y 좌표를 나타내는 **float** 식입니다.  
  
 *SRID*  
 반환하려는 **geometry** 인스턴스의 SRID(Spatial Reference ID)를 나타내는 **int** 식입니다.  
  
## <a name="return-types"></a>반환 형식  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 반환 형식: **geometry**  
  
 CLR 반환 형식: **SqlGeometry**  
  
## <a name="remarks"></a>설명  
  
## <a name="examples"></a>예  
 다음 예에서는 `Point()`를 사용하여 `geometry` 인스턴스를 만듭니다.  
  
```  
DECLARE @g geometry;   
SET @g = geometry::Point(1, 10, 0);  
SELECT @g.ToString();  
```  
  
## <a name="see-also"></a>참고 항목  
 [확장 정적 기하 도형 메서드](../../t-sql/spatial-geometry/extended-static-geometry-methods.md)  
  
  

