---
title: REPLACE(SSIS 식) | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- replacing string expression
- REPLACE function
ms.assetid: a6837043-ea70-4c6a-9c7a-6868b02b2adc
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 8ef16c9c83419d6b404affc49e7200a739ab65f7
ms.sourcegitcommit: c8e1553ff3fdf295e8dc6ce30d1c454d6fde8088
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/22/2020
ms.locfileid: "86919067"
---
# <a name="replace-ssis-expression"></a>REPLACE(SSIS 식)

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]


  식 내의 문자열을 다른 문자열이나 빈 문자열로 바꾼 후 문자 식을 반환합니다.  
  
> [!NOTE]  
>  REPLACE 함수는 주로 긴 문자열을 사용합니다. 잘림 결과가 적절하게 처리될 수 있지만 경고나 오류를 일으킬 수도 있습니다. 자세한 내용은 [구문&#40;SSIS&#41;](../../integration-services/expressions/syntax-ssis.md)을 참조하세요.  
  
## <a name="syntax"></a>구문  
  
```  
  
REPLACE(character_expression,searchstring,replacementstring)  
```  
  
## <a name="arguments"></a>인수  
 *character_expression*  
 함수가 검색하는 유효한 문자 식입니다.  
  
 *searchstring*  
 함수가 검색하는 유효한 문자 식입니다.  
  
 *replacementstring*  
 대체 식인 유효한 문자 식입니다.  
  
## <a name="result-types"></a>결과 형식  
 DT_WSTR  
  
## <a name="remarks"></a>설명  
 *searchstring* 길이는 0이 아니어야 합니다.  
  
 *replacementstring* 길이는 0이 될 수 있습니다.  
  
 *searchstring* 및 *replacementstring* 인수는 변수와 열을 사용할 수 있습니다.  
  
 REPLACE는 DT_WSTR 데이터 형식에서만 실행됩니다. DT_STR 데이터 형식인 문자열 리터럴 및 데이터 열인*character_expression1, character_expression2* 및 *character_expression3* 인수는 REPLACE 연산이 수행되기 전에 DT_WSTR 데이터 형식으로 암시적으로 캐스팅됩니다. 다른 데이터 형식은 DT_WSTR 데이터 형식으로 명시적으로 캐스팅되어야 합니다. 자세한 내용은 [캐스트&#40;SSIS 식&#41;](../../integration-services/expressions/cast-ssis-expression.md)를 참조하세요.  
  
 인수가 Null이면 REPLACE 결과도 Null입니다.  
  
## <a name="expression-examples"></a>식 예  
 이 예에서는 문자열 리터럴을 사용합니다. 반환 결과는 "All Terrain Bike"입니다.  
  
```  
REPLACE("Mountain Bike", "Mountain","All Terrain")  
```  
  
 이 예에서는 **Product** 열에서 문자열 "Bike"를 제거합니다.  
  
```  
REPLACE(Product, "Bike","")  
```  
  
 이 예에서는 **DaysToManufacture** 열의 값을 바꿉니다. 열에는 정수 데이터 형식이 있고 식에는 DT_WSTR 데이터 형식으로의 **DaysToManufacture** 캐스팅이 포함되어 있습니다.  
  
```  
REPLACE((DT_WSTR,8)DaysToManufacture,"6","5")  
```  
  
## <a name="see-also"></a>참고 항목  
 [SUBSTRING&#40;SSIS 식&#41;](../../integration-services/expressions/substring-ssis-expression.md)   
 [함수&#40;SSIS 식&#41;](../../integration-services/expressions/functions-ssis-expression.md)  
  
  
