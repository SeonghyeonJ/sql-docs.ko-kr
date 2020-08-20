---
description: UPPER(SSIS 식)
title: UPPER(SSIS 식) | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- UPPER function
- converting lowercase to uppercase
- uppercase characters [Integration Services]
- lowercase characters
ms.assetid: d33985f7-1048-4023-83e4-274090acda78
author: chugugrace
ms.author: chugu
ms.openlocfilehash: bd1a7c2d716f3043693840097dd832dec143cd70
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88484372"
---
# <a name="upper-ssis-expression"></a>UPPER(SSIS 식)

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]


  소문자를 대문자로 변환한 후에 문자 식을 반환합니다.  
  
## <a name="syntax"></a>구문  
  
```  
  
UPPER(character_expression)  
```  
  
## <a name="arguments"></a>인수  
 *character_expression*  
 대문자로 변환할 문자 식입니다.  
  
## <a name="result-types"></a>결과 형식  
 DT_WSTR  
  
## <a name="remarks"></a>설명  
 UPPER는 DT_WSTR 데이터 형식에서만 실행됩니다. 문자열 리터럴이나 DT_STR 데이터 형식의 데이터 열인 *character_expression* 인수는 UPPER이 연산을 수행하기 전에 DT_WSTR 데이터 형식으로 암시적으로 캐스팅됩니다. 다른 데이터 형식은 DT_WSTR 데이터 형식으로 명시적으로 캐스팅되어야 합니다. 자세한 내용은 [Integration Services 데이터 형식](../../integration-services/data-flow/integration-services-data-types.md) 및 [캐스트&#40;SSIS 식&#41;](../../integration-services/expressions/cast-ssis-expression.md)를 참조하세요.  
  
 인수가 Null이면 UPPER 결과도 Null입니다.  
  
## <a name="expression-examples"></a>식 예  
 이 예에서는 문자열 리터럴을 대문자로 변환합니다. 반환 결과는 "HELLO"입니다.  
  
```  
UPPER("hello")  
```  
  
 이 예에서는 **FirstName** 열의 첫 문자를 대문자로 변환합니다. **FirstName** 이 anna이면 반환 결과는 "A"입니다. 자세한 내용은 [SUBSTRING&#40;SSIS 식&#41;](../../integration-services/expressions/substring-ssis-expression.md)을 참조하세요.  
  
```  
UPPER(SUBSTRING(FirstName, 1, 1))  
```  
  
 이 예에서는 **PostalCode** 변수 값을 대문자로 변환합니다. **PostalCode** 이 k4b1s2이면 반환 결과는 "K4B1S2"입니다.  
  
```  
UPPER(@PostalCode)  
```  
  
## <a name="see-also"></a>참고 항목  
 [LOWER&#40;SSIS 식&#41;](../../integration-services/expressions/lower-ssis-expression.md)   
 [함수&#40;SSIS 식&#41;](../../integration-services/expressions/functions-ssis-expression.md)  
  
  
