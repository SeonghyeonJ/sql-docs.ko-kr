---
title: Analysis Services 테이블 형식 모델의 계산된 테이블 만들기 | Microsoft Docs
ms.date: 12/19/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 199096efcdf9212e19e1055f1276079eddfb1a75
ms.sourcegitcommit: c51f7f2f5d622a1e7c6a8e2270bd25faba0165e7
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/19/2018
ms.locfileid: "53626262"
---
# <a name="create-a-calculated-table"></a>계산된 테이블 만들기 
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  *계산 테이블* 은 DAX 쿼리 또는 식을 기반으로 계산된 개체이며 같은 모델에 포함된 다른 테이블의 전체 또는 일부에서 파생됩니다.  
  
 계산 테이블이 해결할 수 있는 일반적인 디자인 문제는 클라이언트 애플리케이션의 쿼리 구조로 노출할 수 있도록 특정 컨텍스트에서 롤플레잉 차원을 겉으로 드러내는 것입니다.  롤플레잉 차원은 여러 컨텍스트에 표면화되는 테이블입니다. 전형적인 예에는 외래 키 관계에 따라서 OrderDate, ShipDate, 또는 DueDate으로 표시되는 날짜 테이블이 있습니다. ShipDate의 계산 테이블을 명시적으로 만들면, 쿼리에 사용할 수 있는 다른 테이블처럼 완벽하게 작동되는 독립 실행형 테이블을 갖게 됩니다. 다른 사용 하 여 필터링 된 행 집합, 하위 집합 또는 상위 집합 기존의 다른 테이블의 열을 구성 하는 포함 되어 있습니다. 이렇게 하면 특정 시나리오를 지원하기 위해 테이블의 변형을 생성하더라도 원래 테이블을 그대로 유지할 수 있습니다.  
  
 계산 테이블을 최대한 활용하려면 적어도 몇 가지 DAX를 알아야 합니다. 테이블에 대 한 식을 사용 하 여 작업할 때 계산된 된 테이블에 있는 식이 DAX 식인 daxsource 단일 파티션에 인지 알고 있어야 하는 데 도움이 됩니다.  
식에 의해 반환되는 각 열에는 하나의 CalculatedTableColumn이 있으며, SourceColumn은 반환된 열의 이름입니다(비 계산 테이블의 DataColumns과 유사). 

계산된 된 테이블을 만들려면 적어도 하나 이상의 테이블이 이미 있어야 합니다. 독립 실행형 계산된 테이블 개체로 계산된 된 테이블을 만드는 경우 (csv, xls, xml) 파일 데이터 원본에서 가져와서 먼저 테이블을 만들 수 있습니다. 가져온 파일은 단일 열과 단일 값을 가질 수 있습니다. 그런 다음 해당 테이블을 숨길 수 있습니다. 
  
## <a name="how-to-create-a-calculated-table"></a>계산 테이블을 만드는 방법  
  
1.  먼저, 테이블 형식 모델의 호환성 수준이 1200 이상인 확인 합니다. SSDT의 모델에서 **호환성 수준** 속성을 확인할 수 있습니다.  
  
2.  데이터 뷰로 전환합니다. 다이어그램 뷰에서는 계산 테이블을 만들 수 없습니다.  
  
3.  **테이블** > **새 계산 테이블**을 선택합니다.  
  
4.  DAX 식을 입력하거나 붙여넣습니다(아래 참조).  
  
5.  테이블 이름을 지정합니다.  
  
6.  모델의 다른 테이블과 관계를 만듭니다. 참조 [는 두 테이블 간에 관계 만들기](../../analysis-services/tabular-models/create-a-relationship-between-two-tables-ssas-tabular.md) 이 단계를 사용 하 여 도움이 필요한 경우.  
  
7.  모델의 계산 또는 식에 포함된 테이블을 참조하거나 임시 데이터 탐색을 위해 **Excel에서 분석** 을 사용합니다.  
  
### <a name="replicate-a-role-playing-dimension"></a>롤플레잉 차원 복제  
 수식 입력줄에 다른 테이블의 사본을 가져오도록 하는 DAX 수식을 입력합니다. 계산 테이블이 채워진 후에 설명하는 이름을 지정한 다음 특정 역할에 대한 외래 키를 사용하는 관계를 설정합니다. 예를 들어, Adventure Works 데이터베이스에서 Due Date의 계산 테이블을 만들고 DueDateKey를 팩트 테이블에 대한 관계의 기반으로 사용할 수 있습니다.  
  
```  
=DimDate  
```  
  
### <a name="summarized-or-filtered-dataset"></a>요약 또는 필터링된 데이터 세트  
 수식 입력 줄에 원하는 행을 포함하도록 데이터 세트를 조작하거나, 필터링하거나 요약하는 DAX 식을 입력합니다. 이 예는 판매, 색상, 화폐별 그룹이 형성됩니다.  
  
```  
=SUMMARIZECOLUMNS(DimProduct[Color]  
, DimCurrency[CurrencyName]   
, "Sales" , SUM(FactInternetSales[SalesAmount])  
)  
```  
  
### <a name="superset-using-columns-from-multiple-tables"></a>여러 테이블의 열을 사용한 상위 집합  
 수식 입력줄에 여러 테이블의 열을 결합하는 DAX 식을 입력합니다. 이 경우, 쿼리는 각 화폐에 대한 제품 범주 목록을 출력합니다.  
  
```  
=CROSSJOIN(DimProductCategory, DimCurrency)  
```  
  
## <a name="see-also"></a>참고 항목  
 [호환성 수준](../../analysis-services/tabular-models/compatibility-level-for-tabular-models-in-analysis-services.md)   
 [Analysis Services의 DAX&#40;Data Analysis Expressions&#41;](http://msdn.microsoft.com/library/abb336c9-3346-4cab-b91b-90f93f4575e5)   
 [테이블 형식 모델의 DAX 이해](../../analysis-services/tabular-models/understanding-dax-in-tabular-models-ssas-tabular.md)  
  
  
