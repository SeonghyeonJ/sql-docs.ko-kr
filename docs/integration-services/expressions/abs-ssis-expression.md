---
description: ABS(SSIS 식)
title: ABS(SSIS 식) | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- ABS function
- absolute positive value
ms.assetid: 156747f6-e016-44cf-9a9f-ae8e4a1b4f17
author: chugugrace
ms.author: chugu
ms.openlocfilehash: cc19d31e89795ab2af731deac610656e61f61062
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88391339"
---
# <a name="abs-ssis-expression"></a>ABS(SSIS 식)

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]


  숫자 식의 절대값을 양수로 반환합니다.  
  
## <a name="syntax"></a>구문  
  
```  
  
ABS(numeric_expression)  
```  
  
## <a name="arguments"></a>인수  
 *numeric_expression*  
 부호 있는 숫자 식이거나 부호 없는 숫자 식입니다.  
  
## <a name="result-types"></a>결과 형식  
 함수에 전달된 숫자 식의 데이터 형식입니다.  
  
## <a name="remarks"></a>설명  
 인수가 Null이면 ABS 결과도 Null입니다.  
  
## <a name="expression-examples"></a>식 예  
 이 예에서는 ABS 함수를 양수와 음수에 적용합니다. 둘 다 1.23을 반환합니다.  
  
```  
ABS(-1.23)  
ABS(1.23)  
```  
  
 이 예에서는 변수 **HighTemperature** 와 **LowTempature**의 값을 빼는 식에 ABS 함수를 적용합니다.  
  
```  
ABS(@HighTemperature - @LowTemperature)  
```  
  
## <a name="see-also"></a>참고 항목  
 [함수&#40;SSIS 식&#41;](../../integration-services/expressions/functions-ssis-expression.md)  
  
  
