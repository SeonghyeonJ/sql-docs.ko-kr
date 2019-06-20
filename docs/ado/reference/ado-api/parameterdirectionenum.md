---
title: ParameterDirectionEnum | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- ParameterDirectionEnum
helpviewer_keywords:
- ParameterDirectionEnum enumeration [ADO]
ms.assetid: c66aa6e6-d4f0-4f0f-9640-e08ae6cfdef3
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 3f62d2119764466cabb542d26849712d733453ba
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66703270"
---
# <a name="parameterdirectionenum"></a>ParameterDirectionEnum
지정 여부는 [매개 변수](../../../ado/reference/ado-api/parameter-object.md) 는 입력된 매개 변수, 출력 매개 변수, 두 입력은 출력 매개 변수 또는 저장된 프로시저에서 반환 값 및.  
  
|상수|값|Description|  
|--------------|-----------|-----------------|  
|**adParamInput**|1|기본. 매개 변수는 입력된 매개 변수를 나타냅니다.|  
|**adParamInputOutput**|3|매개 변수는 입력 및 출력 매개 변수를 나타냅니다.|  
|**adParamOutput**|2|매개 변수는 출력 매개 변수를 나타냅니다.|  
|**adParamReturnValue**|4|매개 변수는 반환 값을 나타냅니다.|  
|**adParamUnknown**|0|매개 변수 방향은 알려진 임을 나타냅니다.|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC 해당  
 Package: **com.ms.wfc.data**  
  
|상수|  
|--------------|  
|AdoEnums.ParameterDirection.INPUT|  
|AdoEnums.ParameterDirection.INPUTOUTPUT|  
|AdoEnums.ParameterDirection.OUTPUT|  
|AdoEnums.ParameterDirection.RETURNVALUE|  
|AdoEnums.ParameterDirection.UNKNOWN|  
  
## <a name="applies-to"></a>적용 대상  
  
|||  
|-|-|  
|[CreateParameter 메서드(ADO)](../../../ado/reference/ado-api/createparameter-method-ado.md)|[Direction 속성](../../../ado/reference/ado-api/direction-property.md)|
