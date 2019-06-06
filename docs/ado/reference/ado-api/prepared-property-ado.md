---
title: 속성 (ADO)를 준비 합니다. | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Command15::Prepared
helpviewer_keywords:
- Prepared property [ADO]
ms.assetid: 11ca8825-765e-4bb4-a6ce-3f6564ad8755
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: c762de42fd12509a56fcc22584b4afa57be2eaa5
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/05/2019
ms.locfileid: "66703132"
---
# <a name="prepared-property-ado"></a>준비된 속성(ADO)
컴파일된 버전을 저장할지 여부를 나타냅니다는 [명령](../../../ado/reference/ado-api/command-object-ado.md) 실행 하기 전에 합니다.  
  
## <a name="settings-and-return-values"></a>설정 및 반환 값  
 설정 하거나 반환을 **부울** 값,로 **True**, 명령을 준비할는 나타냅니다.  
  
## <a name="remarks"></a>Remarks  
 사용 하 여는 **Prepared** 는 공급자가 준비 된 (또는 컴파일된) 버전에 지정 된 쿼리를 저장 하는 속성을 [CommandText](../../../ado/reference/ado-api/commandtext-property-ado.md) 하기 전에 속성을 [명령](../../../ado/reference/ado-api/command-object-ado.md) 개체의 첫 번째 실행 합니다. 명령의 첫 번째 실행을 저하 될 수 있습니다이 있지만 공급자는 성능이 향상 됩니다. 후속 실행에 대 한 명령의 컴파일된 버전을 사용 공급자 명령을 컴파일한 후 합니다.  
  
 속성이 **False**, 공급자 실행될지를 **명령** 컴파일된 버전을 만들지 않고 직접 개체입니다.  
  
 이 속성 설정 된 경우 오류를 반환 합니다 공급자 명령 준비를 지원 하지 않는 경우 **True**합니다. 명령 및 집합을 준비 하려면 요청 공급자 오류를 반환 하지 않으면 무시 하기만 합니다 **Prepared** 속성을 **False**.  
  
## <a name="applies-to"></a>적용 대상  
 [명령 개체(ADO)](../../../ado/reference/ado-api/command-object-ado.md)  
  
## <a name="see-also"></a>관련 항목  
 [Prepared 속성 예제 (VB)](../../../ado/reference/ado-api/prepared-property-example-vb.md)   
 [Prepared 속성 예제(VC++)](../../../ado/reference/ado-api/prepared-property-example-vc.md)   
