---
title: YEAR(SSIS 식) | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- dates [Integration Services], YEAR
- YEAR function
ms.assetid: 9d88dead-ace8-44b9-b8e2-916c1842e155
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 44abaccaf7b41d4dec249e868a5c365f324eb7e0
ms.sourcegitcommit: fd71d04a9d30a9927cbfff645750ac9d5d5e5ee7
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/16/2019
ms.locfileid: "65724835"
---
# <a name="year-ssis-expression"></a>YEAR(SSIS 식)

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  날짜의 연도 부분을 나타내는 정수를 반환합니다.  
  
## <a name="syntax"></a>구문  
  
```  
  
YEAR(date)  
```  
  
## <a name="arguments"></a>인수  
 *date*  
 임의의 날짜 형식을 갖는 날짜입니다.  
  
## <a name="result-types"></a>결과 형식  
 DT_I4  
  
## <a name="remarks"></a>Remarks  
 인수가 Null이면 YEAR 결과도 Null입니다.  
  
 날짜 리터럴은 다음의 날짜 데이터 형식 중 하나로 명시적 캐스팅되어야 합니다. 자세한 내용은 [Integration Services Data Types](../../integration-services/data-flow/integration-services-data-types.md)을 참조하세요.  
  
> [!NOTE]  
>  날짜 리터럴이 DT_DBTIMESTAMPOFFSET 및 DT_DBTIMESTAMP2 날짜 데이터 형식 중 하나로 명시적 캐스팅되면 식의 유효성 검사가 실패합니다.  
  
 YEAR 함수는 DATEPART("Year", date) 함수보다 간단하지만 동일한 결과를 반환합니다.  
  
## <a name="expression-examples"></a>식 예  
 이 예에서는 날짜 리터럴의 연도를 반환합니다. 날짜 형식이 mm/dd/yyyy이면 "2002"가 반환됩니다.  
  
```  
YEAR((DT_DBTIMESTAMP)"11/23/2002")  
```  
  
 이 예에서는 **ModifiedDate** 열의 연도를 나타내는 정수를 반환합니다.  
  
```  
YEAR(ModifiedDate)  
```  
  
 이 예에서는 현재 날짜의 연도를 나타내는 정수를 반환합니다.  
  
```  
YEAR(GETDATE())  
```  
  
## <a name="see-also"></a>참고 항목  
 [DATEADD&#40;SSIS 식&#41;](../../integration-services/expressions/dateadd-ssis-expression.md)   
 [DATEDIFF&#40;SSIS 식&#41;](../../integration-services/expressions/datediff-ssis-expression.md)   
 [DATEPART&#40;SSIS 식&#41;](../../integration-services/expressions/datepart-ssis-expression.md)   
 [DAY&#40;SSIS 식&#41;](../../integration-services/expressions/day-ssis-expression.md)   
 [MONTH&#40;SSIS 식&#41;](../../integration-services/expressions/month-ssis-expression.md)   
 [함수&#40;SSIS 식&#41;](../../integration-services/expressions/functions-ssis-expression.md)  
  
  
