---
title: EXP(SSIS 식) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- exponential functions
- EXP function
ms.assetid: 4cd96d3c-58c9-4a67-a6f6-b72758232912
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 00aea33b9ee240229cc399650f4c227e86f19507
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/03/2018
ms.locfileid: "52752107"
---
# <a name="exp-ssis-expression"></a>EXP(SSIS 식)
  밑이 e인 숫자 식의 지수를 반환합니다. EXP 함수는 LN 함수의 동작을 보완하며 역대수라고도 합니다.  
  
## <a name="syntax"></a>구문  
  
```  
  
EXP(numeric_expression)  
```  
  
## <a name="arguments"></a>인수  
 *numeric_expression*  
 유효한 숫자 식입니다.  
  
## <a name="result-types"></a>결과 형식  
 DT_R8  
  
## <a name="remarks"></a>Remarks  
 숫자 식은 지수를 계산하기 전에 DT_R8 데이터 형식으로 캐스팅됩니다. 자세한 내용은 [Integration Services Data Types](../data-flow/integration-services-data-types.md)을 참조하세요.  
  
 반환 결과는 항상 양수입니다.  
  
## <a name="expression-examples"></a>식 예  
 이 예에서는 양수, 음수 및 0에 EXP 함수를 적용합니다.  
  
```  
EXP(74)  
```  
  
 1.373382979540176E+32를 반환합니다.  
  
```  
EXP(-27)  
```  
  
 1.879528816539083E-12를 반환합니다.  
  
```  
EXP(0)  
```  
  
 1을 반환합니다.  
  
## <a name="see-also"></a>관련 항목  
 [LOG&#40;SSIS 식&#41;](log-ssis-expression.md)   
 [함수&#40;SSIS 식&#41;](functions-ssis-expression.md)  
  
  
