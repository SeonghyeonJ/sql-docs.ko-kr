---
title: LineSeparator 속성 (ADO) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Stream::LineSeparator
helpviewer_keywords:
- LineSeparator property [ADO]
ms.assetid: 0b20fbb8-6b83-48ec-b442-f96c8a4bafbb
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 0343954f549f2cba4b535b8ab4ebafec5a842015
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67918281"
---
# <a name="lineseparator-property-ado"></a>LineSeparator 속성(ADO)
텍스트에서 줄 구분 기호로 사용할 문자를 이진 나타냅니다 [Stream](../../../ado/reference/ado-api/stream-object-ado.md) 개체입니다.  
  
## <a name="settings-and-return-values"></a>설정 및 반환 값  
 설정 하거나 반환을 [LineSeparatorsEnum](../../../ado/reference/ado-api/lineseparatorsenum.md) 에 사용 되는 줄 구분 기호 문자를 나타내는 값을 **Stream**합니다. 기본값은 **adCRLF**합니다.  
  
## <a name="remarks"></a>설명  
 **LineSeparator** 줄의 텍스트 콘텐츠를 읽을 때 해석 하는 데 사용 됩니다 **Stream**합니다. 줄을 사용 하 여 건너뛸 수는 [SkipLine](../../../ado/reference/ado-api/skipline-method.md) 메서드.  
  
 **LineSeparator** 텍스트만 되 **Stream** 개체 ([형식](../../../ado/reference/ado-api/type-property-ado-stream.md) 은 **adTypeText**). 하는 경우이 속성은 무시 됩니다 **형식** 됩니다 **adTypeBinary**합니다.  
  
## <a name="applies-to"></a>적용 대상  
 [스트림 개체(ADO)](../../../ado/reference/ado-api/stream-object-ado.md)  
  
## <a name="see-also"></a>관련 항목  
 [스트림 개체(ADO)](../../../ado/reference/ado-api/stream-object-ado.md)
