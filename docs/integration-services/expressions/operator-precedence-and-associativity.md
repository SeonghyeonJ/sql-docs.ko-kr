---
title: 연산자 우선 순위 및 계산 방향 | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- associativity [Integration Services]
- precedence [Integration Services]
ms.assetid: 5094164f-dabc-45b5-b611-384feb2b3fe3
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 801f0358ce5dd6b68e42aff37e7135ec813b3bc0
ms.sourcegitcommit: c8e1553ff3fdf295e8dc6ce30d1c454d6fde8088
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/22/2020
ms.locfileid: "86901297"
---
# <a name="operator-precedence-and-associativity"></a>연산자 우선 순위 및 계산 방향

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]


  식 계산기가 지원하는 연산자 집합의 각 연산자에는 우선 순위 계층에서 지정된 우선 순위와 계산 방향이 있습니다. 연산자의 계산 방향은 연산자의 연결성을 나타냅니다. 우선 순위가 높은 연산자가 우선 순위가 낮은 연산자보다 먼저 계산됩니다. 복잡한 식에 여러 개의 연산자가 있을 경우 연산자 우선 순위가 연산 수행 순서를 결정합니다. 실행 순서는 결과 값에 중대한 영향을 줄 수 있습니다. 일부 연산자는 우선 순위가 같습니다. 우선 순위가 같은 여러 개의 연산자가 식에 포함되어 있으면 연산자는 왼쪽에서 오른쪽으로 또는 오른쪽에서 왼쪽으로 계산됩니다.  
  
 다음 표에서는 연산자의 우선 순위를 높은 순서부터 낮은 순서로 보여 줍니다. 동일한 수준의 연산자는 우선 순위가 같습니다.  
  
|연산자 기호|연산 유형|계산 방향|  
|---------------------|-----------------------|-------------------|  
|( )|식|왼쪽에서 오른쪽|  
|-, !, ~|단항 연산자|오른쪽에서 왼쪽|  
|casts|단항 연산자|오른쪽에서 왼쪽|  
|*, / ,%|곱셈|왼쪽에서 오른쪽|  
|+, -|가산적|왼쪽에서 오른쪽|  
|\<, >, \<=, >=|관계형|왼쪽에서 오른쪽|  
|==, !=|등호|왼쪽에서 오른쪽|  
|&|비트 AND|왼쪽에서 오른쪽|  
|^|배타적 비트 OR|왼쪽에서 오른쪽|  
|&#124;|포괄적 비트 OR|왼쪽에서 오른쪽|  
|&&|논리적 AND|왼쪽에서 오른쪽|  
|&#124;&#124;|논리적 OR|왼쪽에서 오른쪽|  
|? :|조건 식|오른쪽에서 왼쪽|  
  
## <a name="see-also"></a>참고 항목  
 [연산자&#40;SSIS 식&#41;](../../integration-services/expressions/operators-ssis-expression.md)  
  
  
