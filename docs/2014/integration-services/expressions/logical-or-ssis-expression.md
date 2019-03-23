---
title: '||(논리적 OR)(SSIS 식) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- OR operator
- logical OR (||)
- '|| (logical OR)'
ms.assetid: a3c07c09-f121-4187-9617-b01adcf843c4
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: e4be7f70d568fd705847d3529fadd28181a71352
ms.sourcegitcommit: 5a8678bf85f65be590676745a7fe4fcbcc47e83d
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2019
ms.locfileid: "58376102"
---
# <a name="-logical-or-ssis-expression"></a>||(논리적 OR)(SSIS 식)
  논리적 OR 연산을 수행합니다. 두 조건 중 하나 또는 둘 다가 TRUE이면 식도 TRUE가 됩니다.  
  
## <a name="syntax"></a>구문  
  
```  
  
boolean_expression1 || boolean_expression2  
```  
  
## <a name="arguments"></a>인수  
 *boolean_expression1, boolean_expression2*  
 TRUE, FALSE 또는 NULL로 계산되는 임의의 유효한 식입니다.  
  
## <a name="result-types"></a>결과 형식  
 DT_BOOL  
  
## <a name="remarks"></a>Remarks  
 다음 표에서는 || 연산자의 결과를 보여 줍니다.  
  
|결과|식|식|  
|------------|----------------|----------------|  
|TRUE|TRUE|TRUE|  
|TRUE|TRUE|FALSE|  
|FALSE|FALSE|FALSE|  
|NULL|NULL|NULL|  
|TRUE|NULL|TRUE|  
|NULL|NULL|FALSE|  
  
## <a name="ssis-expression-examples"></a>SSIS 식 예  
 이 예에서는 **StandardCost** 열과 **ListPrice** 열을 사용합니다. **StandardCost** 열의 값이 300보다 작거나 **ListPrice** 열의 값이 500보다 크면 TRUE가 됩니다.  
  
```  
StandardCost < 300 || ListPrice > 500  
```  
  
 이 예에서는 숫자 리터럴 대신 변수 **SPrice** 와 **LPrice** 를 사용합니다.  
  
```  
StandardCost < @SPrice || ListPrice > @LPrice  
```  
  
## <a name="see-also"></a>관련 항목  
 [&#124;&#40;포괄적 비트 OR&#41;&#40;SSIS 식&#41;](bitwise-inclusive-or-ssis-expression.md)   
 [^&#40;배타적 비트 OR&#41;&#40;SSIS 식&#41;](bitwise-exclusive-or-ssis-expression.md)   
 [연산자 우선 순위 및 계산 방향](operator-precedence-and-associativity.md)   
 [연산자&#40;SSIS 식&#41;](operators-ssis-expression.md)  
  
  
