---
description: SIGN(SSIS 식)
title: SIGN(SSIS 식) | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- positive values [Integration Services]
- SIGN function
- negative values
ms.assetid: 1547db08-4329-4781-91c2-36898ed71b15
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 88a0009b7d846adb0f12f8712c70b95109877ef1
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88477363"
---
# <a name="sign-ssis-expression"></a>SIGN(SSIS 식)

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]


  숫자 식의 양수(+1), 음수(-1) 또는 영(0) 부호를 반환합니다.  
  
## <a name="syntax"></a>구문  
  
```  
  
SIGN(numeric_expression)  
```  
  
## <a name="arguments"></a>인수  
 *numeric_expression*  
 유효한 부호 있는 숫자 식입니다. 자세한 내용은 [Integration Services Data Types](../../integration-services/data-flow/integration-services-data-types.md)을 참조하세요.  
  
## <a name="result-types"></a>결과 형식  
 DT_I4  
  
## <a name="remarks"></a>설명  
 인수가 Null이면 SIGN 결과도 Null입니다.  
  
## <a name="expression-examples"></a>식 예  
 이 예에서는 숫자 리터럴의 부호가 반환됩니다. 반환 결과는 -1입니다.  
  
```  
SIGN(-123.45)  
```  
  
 이 예에서는 **DealerPrice** 열에서 **StandardCost** 열을 뺀 결과의 부호가 반환됩니다.  
  
```  
SIGN(DealerPrice - StandardCost)  
```  
  
## <a name="see-also"></a>참고 항목  
 [함수&#40;SSIS 식&#41;](../../integration-services/expressions/functions-ssis-expression.md)  
  
  
