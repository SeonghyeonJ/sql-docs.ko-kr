---
title: DATEDIFF(SSIS 식) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- DATEDIFF statement
- dates [Integration Services], DATEDIFF
ms.assetid: 449b327f-47c7-4709-8bc6-4ee9a35cc330
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: b42115278e6866063639c7ce2fc596749ad2d39f
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/26/2020
ms.locfileid: "62898088"
---
# <a name="datediff-ssis-expression"></a>DATEDIFF(SSIS 식)
  지정한 두 날짜 간에 교차되는 날짜와 시간 경계값을 반환합니다. *datepart* 매개 변수는 비교할 날짜 및 시간 범위를 식별합니다.  
  
## <a name="syntax"></a>구문  
  
```  
  
DATEDIFF(datepart, startdate, endate)  
```  
  
## <a name="arguments"></a>인수  
 *datepart*  
 비교하여 값을 반환할 날짜 부분을 지정하는 매개 변수입니다.  
  
 *startdate*  
 간격의 시작 날짜입니다.  
  
 *endate*  
 간격의 종료 날짜입니다.  
  
## <a name="result-types"></a>결과 형식  
 DT_I4  
  
## <a name="remarks"></a>설명  
 다음 표에서는 식 계산기가 인식하는 날짜 부분 및 약어를 나열합니다.  
  
|날짜 부분|약어|  
|--------------|-------------------|  
|Year|yy, yyyy|  
|Quarter|qq, q|  
|Month|mm, m|  
|Dayofyear|dy, y|  
|일|dd, d|  
|Week|wk, ww|  
|요일|dw, w|  
|Hour|Hh|  
|Minute|mi, n|  
|초|ss, s|  
|Millisecond|Ms|  
  
 인수가 Null이면 DATEDIFF 결과도 Null입니다.  
  
 날짜 리터럴은 다음의 날짜 데이터 형식 중 하나로 명시적 캐스팅되어야 합니다. 자세한 내용은 [Integration Services Data Types](../data-flow/integration-services-data-types.md)을 참조하세요.  
  
 올바른 날짜가 아니거나, 날짜 또는 시간 단위가 문자열이 아니거나, 시작 날짜가 날짜가 아니거나, 종료 날짜가 날짜가 아니면 오류가 발생합니다.  
  
 종료 날짜가 시작 날짜보다 빠르면 음수가 반환됩니다. 시작 날짜와 종료 날짜가 같거나 동일한 간격 내에 있으면 0이 반환됩니다.  
  
## <a name="ssis-expression-examples"></a>SSIS 식 예  
 이 예에서는 두 날짜 리터럴 사이의 일 수를 계산합니다. 날짜 형식이 "mm/dd/yyyy"이면 7이 반환됩니다.  
  
```  
DATEDIFF("dd", (DT_DBTIMESTAMP)"8/1/2003", (DT_DBTIMESTAMP)"8/8/2003")  
```  
  
 이 예에서는 날짜 리터럴과 현재 날짜 사이의 개월 수를 반환합니다.  
  
```  
DATEDIFF("mm", (DT_DBTIMESTAMP)"8/1/2003",GETDATE())  
```  
  
 이 예에서는 **ModifiedDate** 열의 날짜와 **YearEndDate** 변수 사이의 주 수를 반환합니다. **YearEndDate** 에 `date` 데이터 형식이 있는 경우에는 명시적 캐스팅이 필요 하지 않습니다.  
  
```  
DATEDIFF("Week", ModifiedDate,@YearEndDate)  
```  
  
## <a name="see-also"></a>참고 항목  
 [DATEADD&#40;SSIS 식&#41;](dateadd-ssis-expression.md)   
 [DATEPART&#40;SSIS 식&#41;](datepart-ssis-expression.md)   
 [DAY&#40;SSIS 식&#41;](day-ssis-expression.md)   
 [MONTH&#40;SSIS 식&#41;](month-ssis-expression.md)   
 [YEAR&#40;SSIS 식&#41;](year-ssis-expression.md)   
 [함수&#40;SSIS 식&#41;](functions-ssis-expression.md)  
  
  
