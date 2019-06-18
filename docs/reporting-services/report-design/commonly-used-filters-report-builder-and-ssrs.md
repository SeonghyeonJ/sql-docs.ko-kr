---
title: 일반적으로 사용되는 필터(보고서 작성기 및 SSRS) | Microsoft Docs
ms.date: 03/07/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-design
ms.topic: conceptual
helpviewer_keywords:
- multivalued parameters [Reporting Services]
- single-valued parameters [Reporting Services]
- parameters [Reporting Services], multivalued
- valid values [Reporting Services]
ms.assetid: cb70d0cd-707b-4de5-b39f-e4eb57d316aa
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 0757982d8e1e758a771d7ccdf880c88576f980f7
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 06/15/2019
ms.locfileid: "65581585"
---
# <a name="commonly-used-filters-report-builder-and-ssrs"></a>일반적으로 사용되는 필터(보고서 작성기 및 SSRS)
  필터를 만들려면 하나 이상의 필터 수식을 지정해야 합니다. 필터 수식에는 식, 데이터 형식, 연산자 및 값이 포함됩니다. 이 항목에서는 일반적으로 사용되는 필터의 예를 제공합니다.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="filter-examples"></a>필터 예  
 다음 표에서는 다양한 데이터 형식 및 연산자를 사용하는 필터 수식의 예를 보여 줍니다. 비교 범위는 필터가 정의된 보고서 항목에 따라 결정됩니다. 예를 들어 데이터 세트에 대해 정의된 필터의 경우 **TOP % 10**은 데이터 세트의 상위 10% 값이며 그룹에 대해 정의된 필터의 경우 **TOP % 10**은 그룹의 상위 10% 값입니다.  
  
|간단한 식|데이터 형식|연산자|값|설명|  
|-----------------------|---------------|--------------|-----------|-----------------|  
|`[SUM(Quantity)]`|**Integer**|**>**|`7`|7보다 큰 데이터 값을 포함합니다.|  
|`[SUM(Quantity)]`|**Integer**|**TOP N**|`10`|상위 10개 데이터 값을 포함합니다.|  
|`[SUM(Quantity)]`|**Integer**|**TOP %**|`20`|데이터 값의 상위 20%를 포함합니다.|  
|`[Sales]`|**텍스트**|**>**|`=CDec(100)`|$100보다 큰 System.Decimal 형식(SQL "money" 데이터 형식)의 모든 값을 포함합니다.|  
|`[OrderDate]`|**DateTime**|**>**|`2088-01-01`|2008년 1월 1일부터 현재 날짜까지의 모든 날짜를 포함합니다.|  
|`[OrderDate]`|**DateTime**|**BETWEEN**|`2008-01-01`<br /><br /> `2008-02-01`|2008년 1월 1일부터 2008년 2월 1일까지의 날짜를 포함합니다.|  
|`[Territory]`|**텍스트**|**LIKE**|`*east`|"east"로 끝나는 모든 지역 이름입니다.|  
|`[Territory]`|**텍스트**|**LIKE**|`%o%th*`|이름의 시작 부분에 North와 South를 포함하는 모든 지역 이름입니다.|  
|`=LEFT(Fields!Subcat.Value,1)`|**텍스트**|**IN**|`B, C, T`|B, C 또는 T 문자로 시작하는 모든 하위 범주 값입니다.|  
  
## <a name="examples-with-report-parameters"></a>보고서 매개 변수가 있는 예  
 다음 표에서는 단일 값 또는 다중값 매개 변수 참조를 포함하는 필터 식의 예를 제공합니다.  
  
|매개 변수 유형|(필터) 식|연산자|값|데이터 형식|  
|--------------------|---------------------------|--------------|-----------|---------------|  
|단일 값|`[EmployeeID]`|=|`[@EmployeeID]`|정수|  
|다중값|`[EmployeeID]`|IN|`[@EmployeeID]`|정수|  
  
## <a name="see-also"></a>참고 항목  
 [보고서 매개 변수&#40;보고서 작성기 및 보고서 디자이너&#41;](../../reporting-services/report-design/report-parameters-report-builder-and-report-designer.md)   
 [데이터 세트 필터, 데이터 영역 필터 및 그룹 필터 추가&#40;보고서 작성기 및 SSRS&#41;](../../reporting-services/report-design/add-dataset-filters-data-region-filters-and-group-filters.md)   
 [보고서에 사용되는 식&#40;보고서 작성기 및 SSRS&#41;](../../reporting-services/report-design/expression-uses-in-reports-report-builder-and-ssrs.md)   
 [식 예&#40;보고서 작성기 및 SSRS&#41;](../../reporting-services/report-design/expression-examples-report-builder-and-ssrs.md)   
 [식의 데이터 형식&#40;보고서 작성기 및 SSRS&#41;](../../reporting-services/report-design/data-types-in-expressions-report-builder-and-ssrs.md)  
  
  
