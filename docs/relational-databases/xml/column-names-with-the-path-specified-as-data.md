---
title: 경로가 data()로 지정된 열 이름 | Microsoft 문서
description: 경로가 data()로 지정된 열 이름이 포함된 XML 쿼리에 대해 알아봅니다.
ms.custom: fresh2019may
ms.date: 05/22/2019
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- names [SQL Server], columns with
ms.assetid: 0b738e44-6108-4417-a9a4-abeb7680d899
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 71cddb62a7277d32d9f43f499c83f3df9e9f69d6
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85775595"
---
# <a name="column-names-with-the-path-specified-as-data"></a>경로가 data()로 지정된 열 이름

[!INCLUDE [SQL Server Azure SQL Database](../../includes/applies-to-version/sql-asdb.md)]

열 이름으로 지정된 경로가 "data()"일 경우 생성된 XML에서 해당 값이 원자 값으로 처리됩니다. 직렬화의 다음 항목도 원자성 값이면 공백 문자가 XML에 추가됩니다. 이 특징은 목록 유형의 요소와 특성 값을 만들 때 유용합니다. 다음 쿼리는 제품 모델 ID, 이름 및 해당 제품 모델에 속한 제품 목록을 검색합니다.  
  
```sql
USE AdventureWorks2012;  
GO  
SELECT ProductModelID       AS "@ProductModelID",  
       Name                 AS "@ProductModelName",  
      (SELECT ProductID AS "data()"  
       FROM   Production.Product  
       WHERE  Production.Product.ProductModelID =   
              Production.ProductModel.ProductModelID  
      FOR XML PATH (''))    AS "@ProductIDs"  
FROM  Production.ProductModel  
WHERE ProductModelID= 7   
FOR XML PATH('ProductModelData');  
```  
  
 중첩 SELECT가 제품 ID 목록을 검색합니다. "data()"를 제품 ID에 대한 열 이름으로 지정합니다. PATH 모드에서는 행 요소 이름에 빈 문자열을 지정하므로 행 요소가 생성되지 않습니다. 대신 부모 SELECT의 `<ProductModelData>` 행 요소에 대한 ProductID 특성에 할당된 대로 값이 반환됩니다. 다음은 결과입니다.  

```sql
<ProductModelData
  ProductModelID="7"
  ProductModelName="HL Touring Frame"
  ProductIDs="885 887 888 889 890 891 892 893"
/>
```

## <a name="see-also"></a>참고 항목  
 [FOR XML에서 PATH 모드 사용](../../relational-databases/xml/use-path-mode-with-for-xml.md)  
  
  
