---
title: '속성 (Visual C++ #import 구문 인덱스) | Microsoft Docs'
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
dev_langs:
- C++
helpviewer_keywords:
- 'Property collection [ADO], Visual C++ syntax index with #import'
ms.assetid: 80988ca7-f514-438d-bf6f-9390dfe93fc3
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 31bdc1249a82660ef7fa7c73a25fb0806c8c0744
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63027710"
---
# <a name="property-visual-c-syntax-index-with-import"></a>속성 (Visual C++ #import 구문 인덱스)
## <a name="properties"></a>속성  
  
```  
long GetAttributes( );  
void PutAttributes( long plAttributes );  
__declspec(property(get=GetAttributes,put=PutAttributes)) long  
    Attributes;  
  
_bstr_t GetName( );  
__declspec(property(get=GetName)) _bstr_t Name;  
  
enum DataTypeEnum GetType( );  
__declspec(property(get=GetType)) enum DataTypeEnum Type;  
  
_variant_t GetValue( );  
void PutValue( const _variant_t & pval );  
__declspec(property(get=GetValue,put=PutValue)) _variant_t Value;  
```  
  
## <a name="see-also"></a>관련 항목  
 [속성 개체(ADO)](../../../ado/reference/ado-api/property-object-ado.md)
