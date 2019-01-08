---
title: SQL Server 2017 Analysis Services의 새로운 기능 | Microsoft Docs
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: ''
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 188406e99f32b42079b66536db42810222eb2a24
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/28/2018
ms.locfileid: "52516744"
---
# <a name="whats-new-in-sql-server-2017-analysis-services"></a>SQL Server 2017 Analysis Services의 새로운 기능
[!INCLUDE[ssas-appliesto-sql2017](../includes/ssas-appliesto-sql2017.md)]

SQL Server 2017 Analysis Services는 SQL Server 2012 이후 가장 중요 한 향상 된 기능 중 일부를 참조 합니다. 그 어느 때 보다 더 강력한 테이블 형식 모델을 통해이 릴리스 (SQL Server 2012 Analysis Services에 처음 도입 된) 테이블 형식 모드의 성공 여부를 토대로 합니다.

다차원 모드 및 SharePoint 모드의 파워 피벗은 대부분의 Analysis Services 배포에 대 한 요소 였습니다. Analysis Services 제품 수명 주기에서 이러한 모드는 완성도 높은입니다. 이 릴리스에서 이러한 모드 중 하나에 대 한 새 기능이 없습니다. 그러나 버그 수정 및 성능 개선 사항이 포함 됩니다.

여기서 설명 하는 기능은 SQL Server 2017 Analysis Services에 포함 됩니다. 활용 하 고, 사용 하기 위해도의 최신 버전을 사용 해야 하지만 [SQL Server Data Tools](../ssdt/download-sql-server-data-tools-ssdt.md) (SSDT) 및 [SQL Server Management Studio](../ssms/download-sql-server-management-studio-ssms.md) (SSMS). SSDT 및 SSMS는 SQL Server의 새로운 기능을 사용 하 여 일반적으로 일치 하는 새로운 기능과 향상 된 기능을 사용 하 여 매월 업데이트 됩니다.  

모든 새 기능에 대해 자세히 알아보려면 중요 한 상태인 것도 중요 되는 항목을 알고 사용 되지 않으며이 릴리스와 향후 버전에서 지원 되지 않습니다. 체크 아웃 해야 [이전 버전과 호환성 (SQL Server 2017 Analysis Services)](analysis-services-backward-compatibility-sql2017.md)합니다.

이 릴리스에서 몇 가지 핵심적인 새 기능에 대해를 살펴보겠습니다.

## <a name="1400-compatibility-level-for-tabular-models"></a>테이블 형식 모델에 대한 1400 호환성 수준
  활용 하기 위해 다양 한 새 기능에 설명 된 다음, 기존 또는 새 테이블 형식 모델 설정 이거나 1400 호환성 수준으로 업그레이드 합니다. 1400 호환성 수준의 모델은 SQL Server 2016 SP1 이전 버전에 배포하거나 하위 호환성 수준으로 다운그레이드할 수 없습니다. 자세한 내용은 참조 하세요 [Analysis Services 테이블 형식 모델에 대 한 호환성 수준을](../analysis-services/tabular-models/compatibility-level-for-tabular-models-in-analysis-services.md)합니다.
  
SSDT에서 새 테이블 형식 모델 프로젝트를 만들 때 새 1400 호환성 수준을 선택할 수 있습니다. 

![AS_NewTabular1400Project](../analysis-services/media/as-newtabular1400project.png)


솔루션 탐색기에서 SSDT에서 기존 테이블 형식 모델을 업그레이드 하려면 마우스 오른쪽 단추로 클릭 **Model.bim**, 한 다음 **속성**설정 합니다 **호환성 수준** 속성 **SQL Server 2017 (1400)** 합니다. 

![AS_Model_Properties](../analysis-services/media/as-model-properties.png)

유의 해야 하면 기존 모델을 1400를로 업그레이드 되 면 다운 그레이드할 수 없습니다. 1200 모델 데이터베이스의 백업을 유지 해야 합니다.

## <a name="modern-get-data-experience"></a>최신 데이터 가져오기 환경
SQL Server Data Tools (SSDT)에서는 최신을 테이블 형식 모델에 데이터 원본에서 데이터를 가져오는 방법에 있어서 **데이터 가져오기** 1400 호환성 수준의 모델에 대 한 환경입니다. 이 새로운 기능은 Power BI Desktop 및 Microsoft Excel 2016의 유사한 기능을 기반으로 합니다. 최신 데이터 가져오기 환경 데이터 가져오기 쿼리 작성기 및 M 식을 사용 하 여 거 대 한 데이터 변환 및 데이터 매시업 기능을 제공 합니다.

최신 데이터 가져오기 환경 다양 한 데이터 원본에 대 한 지원을 제공합니다. 업데이트는 앞으로 더에 대 한 지원이 포함 됩니다.

![AS_Get_Data_in_SSDT](../analysis-services/media/as-get-data-in-ssdt.png)

 강력 하 고 직관적인 사용자 인터페이스를 데이터 및 데이터 변환/매시업 기능 그 어느 때 보다 쉽게 선택 하는 합니다.

![고급 매시업](../analysis-services/media/as-get-data-advanced.png)


최신 데이터 가져오기 환경 및 M 매시업 기능 1400 1200 호환성 수준의 기존 테이블 형식 모델 upraded에 적용 되지 않습니다. 새 환경 1400 호환성 수준에서 생성 하는 새 모델에만 적용 됩니다.

## <a name="encoding-hints"></a>인코딩 힌트
이 릴리스는 인코딩 힌트를 대규모 메모리 내 테이블 형식 모델의 처리 (데이터 새로 고침)를 최적화 하는 데 사용 하는 고급 기능을 소개 합니다. 인코딩을 더 잘 이해 하려면 참조 [성능 튜닝의 테이블 형식 모델 SQL Server 2012 Analysis Services에서](https://msdn.microsoft.com/library/dn393915.aspx) 인코딩 더 잘 이해 하는 백서입니다.

* 값 인코딩을 일반적으로 집계의 경우에 사용 되는 열에 대 한 향상 된 쿼리 성능을 제공 합니다.

* 해시 인코딩을 group by 열 (대개 차원 테이블 값) 및 외래 키에 대 한는 것이 좋습니다. 문자열 열은 항상 인코딩된 해시입니다.

숫자 열 인코딩 이러한 메서드 중 하나를 사용할 수 있습니다. 값 또는 해시 인코딩을 적용할지 여부를 확인 하려면 각 숫자 열에 대 한 샘플 값 이동 Analysis Services 테이블을 처리 하거나 테이블 (파티션 없이 또는) 비어 있는 경우 시작 또는 전체 테이블 처리 작업을 수행 중인 경우 . 기본적으로 값 인코딩을 선택 됩니다 때 열의 고유 값의 샘플을 충분히-그렇지 않은 경우 더 나은 압축을 제공 일반적으로 해시 인코딩을. Analysis services가 인코딩 프로세스를 다시 시작 후 열은 부분적으로 처리 하 여 데이터 분포에 대 한 추가 정보에 따라 인코딩 방법을 변경할 수 그러나이 처리 시간이 늘어나고 비효율적입니다. 성능 튜닝 백서는 재 인코딩이 자세히 설명 하 고 SQL Server Profiler를 사용 하 여 검색 하는 방법에 설명 합니다.

인코딩 힌트 모델에서 데이터 프로 파일링 및/또는 대 한 응답으로 다시 추적 이벤트를 인코딩 사전 지식이 지정 된 인코딩 방법에 대 한 기본 설정을 지정할 수 있습니다. 있으므로 해시 인코딩된 열에 대 한 집계 값 인코딩된 열을 통해 값 인코딩을 지정할 수 있습니다 이러한 열에 대 한 힌트로 보다 느립니다. 기본 설정이 적용 되는 보장 되지 않습니다. 이 설정 하는 대신 힌트입니다. 인코딩 힌트를 지정 하려면 열에 EncodingHint 속성을 설정 합니다. 가능한 값은 "Default", "Value" 및 "해시"입니다. Model.bim 파일에서 JSON 기반 메타 데이터의 다음 코드 조각은 Sales Amount 열에 대 한 인코딩 값을 지정 합니다.

```
{
    "name": "Sales Amount",
    "dataType": "decimal",
    "sourceColumn": "SalesAmount",
    "formatString": "\\$#,0.00;(\\$#,0.00);\\$#,0.00",
    "sourceProviderType": "Currency",
    "encodingHint": "Value"
}
```

## <a name="ragged-hierarchies"></a>비정형 계층 구조
테이블 형식 모델에서 부모-자식 계층 구조를 모델링할 수 있습니다. 수준 수가 서로 다른 계층 구조를 종종 비정형 계층 구조라고 합니다. 기본적으로, 비정형 계층 구조에서는 최하위 자식 아래 수준을 위한 공백이 표시됩니다. 조직 차트에서 비정형 계층 구조의 예는 다음과 같습니다.

![AS_Ragged_Hierarchy](../analysis-services/media/as-ragged-hierarchy.png)

이 릴리스에서는 **멤버 숨기기** 속성이 도입되었습니다. 계층 구조에 대한 **멤버 숨기기** 속성을 **빈 멤버 숨기기**로 설정할 수 있습니다.

![AS_Hide_Blank_Members](../analysis-services/media/as-hide-blank-members.png)

 >[!NOTE]
 > 모델의 빈 멤버는 빈 문자열 아니라 DAX 빈 값으로 표시됩니다.

**빈 멤버 숨기기**로 설정하고 모델을 배포한 경우 읽기 쉬운 계층 구조 버전이 Excel 등의 보고 클라이언트에 표시됩니다.

![AS_Non_Ragged_Hierarchy](../analysis-services/media/as-non-ragged-hierarchy.png)


## <a name="detail-rows"></a>정보 행
이제 측정값에 영향을 주는 사용자 지정 행 집합을 정의할 수 있습니다. 정보 행은 다차원 모델의 기본 드릴스루 작업과 비슷합니다. 따라서 최종 사용자가 집계된 수준보다 자세히 정보를 볼 수 있습니다. 

다음 피벗 테이블은 Adventure Works 샘플 테이블 형식 모델의 연도별 인터넷 총 매출액을 보여 줍니다. 측정값에서 집계된 값이 포함된 셀을 마우스 오른쪽 단추로 클릭한 다음 **자세한 정보 표시** 를 클릭하면 정보 행을 볼 수 있습니다.

![AS_Show_Details](../analysis-services/media/as-show-details.png)

기본적으로 Internet Sales 테이블의 관련 데이터가 표시됩니다. 고객 이름 및 주문 정보와 같은 유용한 정보를 표시하는 데 필요한 열이 테이블에 없을 수 있기 때문에 이 제한된 동작은 사용자에게 의미가 없는 경우가 많습니다. 정보 행을 사용하여 측정값의 **정보 행 식** 속성을 지정할 수 있습니다.

#### <a name="detail-rows-expression-property-for-measures"></a>측정값의 정보 행 식 속성
측정값의 **정보 행 식** 속성을 통해 모델 작성자는 최종 사용자에게 반환되는 열과 행을 사용자 지정할 수 있습니다.

![AS_Detail_Rows_Expression_Property](../analysis-services/media/as-detail-rows-expression-property.png)

합니다 [SELECTCOLUMNS](https://msdn.microsoft.com/library/mt761759.aspx) DAX 함수는 세부 정보 행 식에서 널리 사용 됩니다. 다음 예제에서는 샘플 Adventure Works 테이블 형식 모델의 Internet Sales 테이블 행에 대해 반환할 열을 정의합니다.

```
SELECTCOLUMNS(
    'Internet Sales',
    "Customer First Name", RELATED( Customer[Last Name]),
    "Customer Last Name", RELATED( Customer[First Name]),
    "Order Date", 'Internet Sales'[Order Date],
    "Internet Total Sales", [Internet Total Sales]
)
```

속성을 정의하고 모델을 배포한 후 사용자가 **자세한 정보 표시**를 선택하면 사용자 지정 행 집합이 반환됩니다. 선택한 셀의 필터 컨텍스트가 자동으로 적용됩니다. 이 예제에서는 2010 값에 대한 행만 표시됩니다.

![AS_Detail_Rows](../analysis-services/media/as-detail-rows.png)

#### <a name="default-detail-rows-expression-property-for-tables"></a>테이블의 기본 정보 행 식 속성
측정값 외에 테이블에는 정보 행 식을 정의하는 속성도 있습니다. **기본 정보 행 식** 속성은 테이블 내 모든 측정값의 기본값으로 사용됩니다. 해당 식이 정의 되지 않은 측정값 테이블에서 식을 상속 및 행 테이블에 대해 정의 된 집합을 표시 합니다. 이렇게 하면 식의 재사용 하 고 나중에 자동으로 테이블에 추가 된 새 측정값이 식을 상속 합니다.

![AS_Default_Detail_Rows_Expression](../analysis-services/media/as-default-detail-rows-expression.png)
 
#### <a name="detailrows-dax-function"></a>DETAILROWS DAX 함수
이 릴리스에는 정보 행 식에서 정의된 행 집합을 반환하는 새 `DETAILROWS` DAX 함수가 포함되어 있습니다. 테이블 형식 모델에서 정의된 정보 행 식과도 호환되는 MDX의 `DRILLTHROUGH` 문과 유사하게 작동합니다.

다음 DAX 쿼리는 측정값 또는 해당 테이블에 대해 정보 행 식에서 정의된 행 집합을 반환합니다. 식이 정의되지 않은 경우 측정값을 포함하는 테이블인 Internet Sales 테이블에 대한 데이터가 반환됩니다.

```
EVALUATE DETAILROWS([Internet Total Sales])
```

## <a name="object-level-security"></a>개체 수준 보안
이 릴리스에 도입 되었습니다 [개체 수준 보안](../analysis-services/tabular-models/object-level-security.md) 테이블 및 열에 대 한 합니다. 테이블 및 열 데이터에 액세스를 제한 하는 것 외에도 중요 한 테이블 및 열 이름은 보호할 수 있습니다. 이렇게 하면 악의적인 사용자가 해당 테이블이 있는지 검색할 수 없습니다.

JSON 기반 메타 데이터, TMSL Tabular Model Scripting Language (), 또는 개체 모델 TOM (테이블 형식)를 사용 하 여 개체 수준 보안을 설정 해야 합니다. 

예를 들어 다음 코드는 **TablePermission** 클래스의 **MetadataPermission** 속성을 **None**으로 설정하여 샘플 Adventure Works 테이블 형식 모델의 Product 테이블을 보호하는 데 도움이 됩니다.

```
//Find the Users role in Adventure Works and secure the Product table
ModelRole role = db.Model.Roles.Find("Users");
Table productTable = db.Model.Tables.Find("Product");
if (role != null && productTable != null)
{
    TablePermission tablePermission;
    if (role.TablePermissions.Contains(productTable.Name))
    {
        tablePermission = role.TablePermissions[productTable.Name];
    }
    else
    {
        tablePermission = new TablePermission();
        role.TablePermissions.Add(tablePermission);
        tablePermission.Table = productTable;
    }
    tablePermission.MetadataPermission = MetadataPermission.None;
}
db.Update(UpdateOptions.ExpandFull);
```

## <a name="dynamic-management-views-dmvs"></a>동적 관리 뷰(DMV)
[Dmv](../analysis-services/instances/use-dynamic-management-views-dmvs-to-monitor-analysis-services.md) 로컬 서버 작업 및 서버 상태에 대 한 정보를 반환 하는 SQL Server Profiler에서 쿼리 됩니다.
이 릴리스에 향상 된 기능이 [동적 관리 뷰](https://docs.microsoft.com/sql/analysis-services/instances/use-dynamic-management-views-dmvs-to-monitor-analysis-services) (DMV) 1200 및 1400 호환성 수준의 테이블 형식 모델에 대 한 합니다.

[DISCOVER_CALC_DEPENDENCY](https://docs.microsoft.com/bi-reference/schema-rowsets/xml/discover-calc-dependency-rowset) 이제 테이블 형식 1200 및 1400 모델에서 작동 합니다. 테이블 형식 1400 모델 M 파티션, M 식 및 구조화 된 데이터 원본 간의 종속성을 보여 줍니다. 자세한 내용은 참조는 [Analysis Services 블로그](https://blogs.msdn.microsoft.com/analysisservices/2017/07/17/whats-new-in-sql-server-2017-rc1-for-analysis-services/)합니다.

[MDSCHEMA_MEASUREGROUP_DIMENSIONS](https://docs.microsoft.com/bi-reference/schema-rowsets/ole-db-olap/mdschema-measuregroup-dimensions-rowset) 향상 측정값 차원에 표시할 다양 한 클라이언트 도구에서 사용 되는이 DMV에 대 한 포함 됩니다. 예를 들어 Excel 피벗 테이블에서 탐색 기능 간 드릴 선택한 측정값을 관련 된 차원에 사용자를 수 있습니다. 이 릴리스에서 잘못 된 값이 표시 된 이전에 카디널리티 열을 수정 합니다.

## <a name="dax-enhancements"></a>향상된 DAX 기능
이 릴리스에서 새 DAX 함수 및 기능에 대 한 지원. 를 활용 하려면 최신 버전의 SSDT 사용 해야 합니다. 자세한 내용은 참조 하세요 [새 DAX 함수](https://msdn.microsoft.com/library/mt704075.aspx)합니다.

새 DAX 기능의 가장 중요 한 부분 중 하나는 새 [IN 연산자 / CONTAINSROW 함수](https://msdn.microsoft.com/library/mt842621.aspx) DAX 식입니다. 이것은 [`TSQL IN`](https://msdn.microsoft.com/library/ms177682.aspx) 절에서 여러 값을 지정하는 데 자주 사용되는 `WHERE` 연산자와 유사합니다.

이전에는 다음 측정값 식과 같이 논리적 `OR` 연산자를 사용하여 다중 값 필터를 지정하는 것이 일반적이었습니다.

```
Filtered Sales:=CALCULATE (
        [Internet Total Sales],
                 'Product'[Color] = "Red"
            || 'Product'[Color] = "Blue"
            || 'Product'[Color] = "Black"
    )
```

`IN` 연산자를 사용하면 이 작업이 간소화됩니다.
```
Filtered Sales:=CALCULATE (
        [Internet Total Sales], 'Product'[Color] IN { "Red", "Blue", "Black" }
    )
```

이 경우 `IN` 연산자는 지정된 색마다 하나씩, 3개의 행이 포함된 단일 열 테이블을 참조합니다. 테이블 생성자 구문은 중괄호를 사용합니다.

`IN` 연산자는 `CONTAINSROW` 함수와 기능적으로 동일합니다.
```
Filtered Sales:=CALCULATE (
        [Internet Total Sales], CONTAINSROW({ "Red", "Blue", "Black" }, 'Product'[Color])
    )
```

`IN` 연산자를 테이블 생성자와 함께 효과적으로 사용할 수도 있습니다. 예를 들어 다음 측정값은 제품 색 및 범주를 결합하여 필터링합니다.
```
Filtered Sales:=CALCULATE (
        [Internet Total Sales],
        FILTER( ALL('Product'),
              ( 'Product'[Color] = "Red"   && Product[Product Category Name] = "Accessories" )
         || ( 'Product'[Color] = "Blue"  && Product[Product Category Name] = "Bikes" )
         || ( 'Product'[Color] = "Black" && Product[Product Category Name] = "Clothing" )
        )
    )
```

새 `IN` 연산자를 사용하면 위의 측정값 식은 이제 아래 식과 동일합니다.
```
Filtered Sales:=CALCULATE (
        [Internet Total Sales],
        FILTER( ALL('Product'),
            ('Product'[Color], Product[Product Category Name]) IN
            { ( "Red", "Accessories" ), ( "Blue", "Bikes" ), ( "Black", "Clothing" ) }
        )
    )
```

## <a name="additional-improvements"></a>추가 개선 사항
모든 새 기능 외에도 Analysis Services, SSDT 및 SSMS도 다음과 같은 개선 사항이 포함:

* 계층 구조 및 열 다시 사용할 수 있도록 Power BI 필드 목록에 더 유용한 위치에 표시 합니다.
* 날짜 필드를 기반으로 하는 날짜 차원에 대 한 관계를 쉽게 만드는 날짜 관계입니다.
* Analysis Services에 대 한 기본 설치 옵션은 이제 테이블 형식 모드에 대 한 합니다.
* 새 데이터 가져오기 (Power Query) 데이터 원본.
* SSDT용 DAX 편집기
* M 쿼리에 대 한 기존 DirectQuery 데이터 원본 지원합니다.
* SSMS 등 향상 된 보기, 편집 및 스크립팅 구조화 된 데이터 원본에 대 한 지원.



## <a name="see-also"></a>참고자료
[SQL Server 2017 릴리스 정보](../sql-server/sql-server-2017-release-notes.md)   
[SQL Server 2017의 새로운 기능](../sql-server/what-s-new-in-sql-server-2017.md)
