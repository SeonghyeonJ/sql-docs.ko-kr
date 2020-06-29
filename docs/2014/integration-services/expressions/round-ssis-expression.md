---
title: ROUND(SSIS 식) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- rounding expressions
- ROUND function [SSIS]
ms.assetid: 376f1947-4fc5-4611-ad86-823e4db1b468
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 5edad70330a5745f9d150cf8a0ad0d540132c029
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/26/2020
ms.locfileid: "85437110"
---
# <a name="round-ssis-expression"></a>ROUND(SSIS 식)
  특정 길이나 전체 자릿수로 반올림한 숫자 식을 반환합니다. 길이 매개 변수는 정수여야 합니다.  
  
## <a name="syntax"></a>구문  
  
```  
  
ROUND(numeric_expression,length)  
```  
  
## <a name="arguments"></a>인수  
 *numeric_expression*  
 유효한 숫자 유형의 식입니다. 자세한 내용은 [Integration Services Data Types](../data-flow/integration-services-data-types.md)을 참조하세요.  
  
 *length*  
 정수 식입니다. *numeric_expression* 을 반올림할 전체 자릿수입니다.  
  
## <a name="result-types"></a>결과 형식  
 *numeric*_*expression*과 동일한 형식입니다.  
  
## <a name="remarks"></a>설명  
 *length* 인수는 양의 정수이거나 0이어야 합니다.  
  
 인수가 Null이면 ROUND 결과도 Null입니다.  
  
## <a name="expression-examples"></a>식 예  
 이 예에서는 숫자 리터럴을 길이 3으로 반올림합니다. 첫 번째 반환 결과는 137.1570이고 두 번째 반환 결과는 137.1580입니다.  
  
```  
ROUND(137.1574,3)  
ROUND(137.1575,3)  
```  
  
## <a name="see-also"></a>참고 항목  
 [함수&#40;SSIS 식&#41;](functions-ssis-expression.md)  
  
  
