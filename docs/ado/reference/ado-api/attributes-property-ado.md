---
title: 특성 속성 (ADO) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Connection15::Attributes
- Field20::Attributes
- _Parameter::Attributes
helpviewer_keywords:
- Attributes property [ADO]
ms.assetid: acc15d40-68a6-4ba9-85bd-12d331aecaa6
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 91425029546402edbd5bde7df45586c77e38d83b
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/05/2019
ms.locfileid: "66696388"
---
# <a name="attributes-property-ado"></a>Attributes 속성(ADO)
개체의 하나 이상의 특성을 나타냅니다.  
  
## <a name="settings-and-return-values"></a>설정 및 반환 값  
 설정 하거나 반환 된 **긴** 값입니다.  
  
 에 [연결](../../../ado/reference/ado-api/connection-object-ado.md) 개체를 **특성** 속성은 읽기/쓰기가 가능 하 고 해당 값에는 하나 이상의 합 될 수 있습니다 [XactAttributeEnum](../../../ado/reference/ado-api/xactattributeenum.md) 값. 기본값은 0입니다.  
  
 에 [매개 변수](../../../ado/reference/ado-api/parameter-object.md) 개체를 **특성** 속성은 읽기/쓰기가 가능 하 고 해당 값에는 하나 이상의의 합 될 수 있습니다 [ParameterAttributesEnum](../../../ado/reference/ado-api/parameterattributesenum.md) 값. 기본값은 **adParamSigned**합니다.  
  
 에 [필드](../../../ado/reference/ado-api/field-object.md) 개체를 **특성** 속성에는 하나 이상의 합 될 수 있습니다 [파생](../../../ado/reference/ado-api/fieldattributeenum.md) 값. 일반적으로 읽기 전용 이며 그러나에 대 한 새 **필드** 에 추가 된 개체를 [필드](../../../ado/reference/ado-api/fields-collection-ado.md) 의 컬렉션을 [레코드](../../../ado/reference/ado-api/record-object-ado.md)를 **특성** 만 읽기/쓰기 후는 [값](../../../ado/reference/ado-api/value-property-ado.md) 에 대 한 속성을 **필드** 지정 된 및 새로운 **필드** 를호출하여데이터공급자가성공적으로추가되었습니다[ 업데이트](../../../ado/reference/ado-api/update-method.md) 메서드를 **필드** 컬렉션입니다.  
  
 에 [속성](../../../ado/reference/ado-api/property-object-ado.md) 개체를 **특성** 속성은 읽기 전용 이며 해당 값의 하나 이상의 합계를 수 있습니다 [PropertyAttributesEnum](../../../ado/reference/ado-api/propertyattributesenum.md) 값입니다.  
  
## <a name="remarks"></a>Remarks  
 사용 하 여는 **특성** 속성을 설정 하거나 특성을 반환할 **연결** 개체를 **매개 변수** 개체를 **필드** 개체 또는 **속성** 개체입니다.  
  
 여러 특성을 설정 하는 경우 적절 한 상수 합계를 계산할 수 있습니다. 호환 되지 않는 상수를 포함 하 여 합계를 속성 값을 설정 하는 경우 오류가 발생 했습니다.  
  
> [!NOTE]
>  **원격 데이터 서비스 사용** 이 속성은 클라이언트 쪽에서 사용할 수 없습니다 **연결** 개체입니다.  
  
## <a name="applies-to"></a>적용 대상  
  
|||  
|-|-|  
|[연결 개체(ADO)](../../../ado/reference/ado-api/connection-object-ado.md)|[Field 개체](../../../ado/reference/ado-api/field-object.md)|  
|[Parameter 개체](../../../ado/reference/ado-api/parameter-object.md)|[속성 개체(ADO)](../../../ado/reference/ado-api/property-object-ado.md)|  
  
## <a name="see-also"></a>관련 항목  
 [Attributes 및 Name 속성 예제 (VB)](../../../ado/reference/ado-api/attributes-and-name-properties-example-vb.md)   
 [Attributes 및 Name 속성 예제 (VC + +)](../../../ado/reference/ado-api/attributes-and-name-properties-example-vc.md)   
 [AppendChunk 메서드 (ADO)](../../../ado/reference/ado-api/appendchunk-method-ado.md)   
 [BeginTrans, CommitTrans 및 RollbackTrans 메서드 (ADO)](../../../ado/reference/ado-api/begintrans-committrans-and-rollbacktrans-methods-ado.md)   
 [GetChunk 메서드(ADO)](../../../ado/reference/ado-api/getchunk-method-ado.md)
