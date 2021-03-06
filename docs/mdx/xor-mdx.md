---
description: XOR(MDX)
title: XOR (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: b74d4ec3d92469dc0372218bfe66375c0844384e
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88421877"
---
# <a name="xor-mdx"></a>XOR(MDX)


  두 숫자 식에 대해 논리 제외를 수행합니다.  
  
## <a name="syntax"></a>구문  
  
```  
  
Expression1 XOR Expression2  
  
```  
  
#### <a name="parameters"></a>매개 변수  
 *Expression1*  
 숫자 값을 반환하는 유효한 MDX 식입니다.  
  
 *Expression2*  
 숫자 값을 반환하는 유효한 MDX 식입니다.  
  
## <a name="return-value"></a>반환 값  
 하나의 인수만 **true**로 평가 되는 경우 **true** 를 반환 하는 부울 값입니다. 그렇지 않으면 **false**입니다.  
  
## <a name="remarks"></a>설명  
 **XOR** 연산자는 연산자가 논리적 **제외를 수행**하기 전에 두 매개 변수를 모두 부울 값 (0, 0, 0, 0, 0)으로 처리 **합니다.** 다음 표에서는 **XOR** 연산자가 논리적 제외를 수행 하는 방법을 보여 줍니다.  
  
|*Expression1*|*Expression2*|반환 값|  
|-------------------|-------------------|------------------|  
|**true**|**true**|**false**|  
|**true**|**false**|**true**|  
|**false**|**true**|**true**|  
|**false**|**false**|**false**|  
  
## <a name="see-also"></a>참고 항목  
 [Mdx 연산자 참조 &#40;MDX&#41;](../mdx/mdx-operator-reference-mdx.md)  
  
  
