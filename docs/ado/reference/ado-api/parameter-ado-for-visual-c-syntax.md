---
title: 매개 변수 (시각적 개체에 대 한 ADO C++ 구문) | Microsoft Docs
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
- Parameter collection [ADO], ADO for Visual C++ syntax
ms.assetid: 74801dc1-cf0f-4a6e-960b-5990fe55e30d
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 291ef7f063ef8c5fb0769ea8430eacef946797bc
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63240437"
---
# <a name="parameter-ado-for-visual-c-syntax"></a>매개 변수(Visual C++ 구문에 대한 ADO)
## <a name="methods"></a>메서드  
  
```  
AppendChunk(VARIANT Val)  
```  
  
## <a name="properties"></a>속성  
  
```  
get_Attributes(LONG *plParmAttribs)  
put_Attributes(LONG lParmAttribs)  
get_Direction(ParameterDirectionEnum *plParmDirection)  
put_Direction(ParameterDirectionEnum lParmDirection)  
get_Name(BSTR *pbstr)  
put_Name(BSTR bstr)  
get_NumericScale(BYTE *pbScale)  
put_NumericScale(BYTE bScale)  
get_Precision(BYTE *pbPrecision)  
put_Precision(BYTE bPrecision)  
get_Size(long *pl)  
put_Size(long l)  
get_Type(DataTypeEnum *psDataType)  
put_Type(DataTypeEnum sDataType)  
get_Value(VARIANT *pvar)  
put_Value(VARIANT val)  
```  
  
## <a name="see-also"></a>관련 항목  
 [Parameter 개체](../../../ado/reference/ado-api/parameter-object.md)
