---
title: '예: &lt;행&gt; 요소 이름 바꾸기 | Microsoft Docs'
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- RAW mode, renaming <row> example
ms.assetid: b042292a-0b6e-40a3-b254-71c06e626706
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6c7d9e578badd12f1b6eb4eb794846431c8c4b0e
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62635721"
---
# <a name="example-renaming-the-ltrowgt-element"></a>예: &lt;행&gt; 요소 이름 바꾸기
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  결과 집합의 각 행에 대해 RAW 모드는 `<row>`요소를 생성합니다. 이 쿼리에 표시된 것과 같이 RAW 모드에 선택적 인수를 지정하여 선택적으로 이 요소에 다른 이름을 지정할 수 있습니다. 이 쿼리는 행 집합의 각 행에 대해 <`ProductModel`> 요소를 반환합니다.  
  
## <a name="example"></a>예제  
  
```  
SELECT ProductModelID, Name   
FROM Production.ProductModel  
WHERE ProductModelID=122  
FOR XML RAW ('ProductModel'), ELEMENTS  
GO  
```  
  
 다음은 결과입니다. 쿼리에 `ELEMENTS` 지시어가 추가되었기 때문에 결과는 요소 중심입니다.  
  
```  
<ProductModel>  
  <ProductModelID>122</ProductModelID>  
  <Name>All-Purpose Bike Stand</Name>  
</ProductModel>   
```  
  
## <a name="see-also"></a>참고 항목  
 [FOR XML에서 RAW 모드 사용](../../relational-databases/xml/use-raw-mode-with-for-xml.md)  
  
  
