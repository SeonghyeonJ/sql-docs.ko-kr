---
title: 집계 디자인 (XMLA) | Microsoft Docs
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: b9f681b3c99bd0e8351a844f28b16be6249de199
ms.sourcegitcommit: 7fe14c61083684dc576d88377e32e2fc315b7107
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/26/2018
ms.locfileid: "50147188"
---
# <a name="designing-aggregations-xmla"></a>집계 디자인(XMLA)
  집계 디자인은 특정 측정값 그룹의 파티션과 연결되어 해당 파티션에서 집계를 저장할 때 동일한 구조를 사용하도록 합니다. 사용 하 여 나중에 병합할 수 있는 파티션을 쉽게 정의할 수 있습니다 파티션에 동일한 저장 구조를 사용 합니다 [MergePartitions](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/mergepartitions-element-xmla) 명령입니다. 집계 디자인에 대 한 자세한 내용은 참조 하세요. [집계 및 집계 디자인](../../analysis-services/multidimensional-models-olap-logical-cube-objects/aggregations-and-aggregation-designs.md)합니다.  
  
 집계 디자인의 집계를 정의 하려면 사용할 수 있습니다 합니다 [DesignAggregations](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/designaggregations-element-xmla) XMLA (XML for Analysis) 명령을 합니다. 합니다 **DesignAggregations** 명령에 대 한 참조 및 해당 참조에 따라 디자인 프로세스를 제어 하는 방법으로 사용할 집계 디자인과 식별 하는 속성이 있습니다. 사용 하는 **DesignAggregations** 명령과 해당 속성을 반복적으로 또는 일괄 처리로 집계를 디자인 하 고 다음 디자인 프로세스를 평가할 결과 디자인 통계를 볼 수 있습니다.  
  
## <a name="specifying-an-aggregation-design"></a>집계 디자인 지정  
 합니다 [개체](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/object-element-xmla) 의 속성을 **DesignAggregations** 기존 집계 디자인에 대 한 개체 참조가 포함 되어야 합니다. 개체 참조는 데이터베이스 식별자, 큐브 식별자, 측정값 그룹 식별자 및 집계 디자인 식별자를 포함합니다. 집계 디자인이 아직 없으면 오류가 발생합니다.  
  
## <a name="controlling-the-design-process"></a>디자인 프로세스 제어  
 다음 속성을 사용할 수는 **DesignAggregations** 집계 디자인의 집계를 정의 하는 알고리즘을 제어 하는 명령:  
  
-   [단계](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/steps-element-xmla) 반복 횟수를 결정 하는 속성을 **DesignAggregations** 클라이언트 응용 프로그램에 제어를 반환 하기 전에 명령을 걸립니다.  
  
-   [시간](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/time-element-xmla) 얼마나 많은 시간 (밀리초)을 결정 하는 속성을 **DesignAggregations** 클라이언트 응용 프로그램에 제어를 반환 하기 전에 명령을 걸립니다.  
  
-   [최적화](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/optimization-element-xmla) 속성의 예상된 성능 향상률을 결정 합니다 **DesignAggregations** 달성 하려는 명령입니다. 집계를 반복적으로 디자인할 경우 첫 번째 명령에서만 이 속성을 보내면 됩니다.  
  
-   합니다 [저장소](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/storage-element-xmla) 속성에 사용 된 바이트의 디스크 저장소의 예상된 크기를 결정 합니다 **DesignAggregations** 명령입니다. 집계를 반복적으로 디자인할 경우 첫 번째 명령에서만 이 속성을 보내면 됩니다.  
  
-   [구체화](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/materialize-element-xmla) 속성에 따라 결정 하는지 여부를 **DesignAggregations** 명령이 디자인 프로세스 중에 정의 된 집계를 만들어야 합니다. 집계를 반복적으로 디자인할 경우 디자인된 집계를 저장할 준비가 될 때까지 이 속성을 false로 설정해야 합니다. 이 속성을 true로 설정하면 현재 디자인 프로세스가 종료되고 정의된 집계가 지정된 집계 디자인에 추가됩니다.  
  
## <a name="specifying-queries"></a>쿼리 지정  
 DesignAggregations 명령은 하나 이상 포함 하 여 사용 빈도 기반 최적화 명령을 지원 **쿼리** 요소에는 [쿼리](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/queries-element-xmla) 속성입니다. **쿼리에** 속성에는 하나 이상 포함 될 수 있습니다 [쿼리](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/query-element-xmla) 요소입니다. 경우는 **쿼리** 속성을 포함 하지 **쿼리** 요소에 지정 된 집계 디자인을 **개체** 포함 하는 기본 구조를 사용 하는 요소는 일반적인 집계 집합입니다. 이 일반적인 집계 집합에 지정 된 조건에 맞게 설계 되었습니다 합니다 **최적화** 및 **저장소** 의 속성을 **DesignAggregations** 명령입니다.  
  
 각 **Query** 요소는 가장 자주 사용하는 쿼리를 대상으로 하는 집계를 정의하기 위해 디자인 프로세스에서 사용하는 목표 쿼리를 나타냅니다. 사용자 고유의 목표 쿼리를 지정하거나 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 인스턴스에 의해 쿼리 로그에 저장된 정보를 사용하여 가장 자주 사용하는 쿼리에 대한 정보를 검색할 수 있습니다. 빈도 기반 최적화 마법사를 사용 하는 쿼리 로그를 사용 하 여 보낼 때 시간, 사용 또는 지정 된 사용자를 기반으로 목표 쿼리를 검색 하는 **DesignAggregations** 명령입니다. 자세한 내용은 [사용량-Based Optimization Wizard F1 Help](http://msdn.microsoft.com/library/e5f5a938-ae7c-4f4e-9416-a7f94ac82763)합니다.  
  
 반복적으로 집계를 디자인하는 경우 첫 번째 **DesignAggregations** 명령에서만 목표 쿼리를 전달하면 됩니다. 이는 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 인스턴스가 이러한 목표 쿼리를 저장하여 후속 **DesignAggregations** 명령 중에 사용하기 때문입니다. 반복 프로세스의 첫 번째 **DesignAggregations** 명령에서 목표 쿼리를 전달하면 **DesignAggregations** 속성에 목표 쿼리를 포함하는 모든 후속 **Queries** 명령은 오류를 생성합니다.  
  
 **Query** 요소에는 다음 인수를 포함하는 쉼표로 구분된 값이 포함됩니다.  
  
 *Frequency*,*Dataset*[,*Dataset*...]  
  
 *빈도*  
 쿼리가 이전에 실행된 횟수에 해당하는 가중 요인입니다. **Query** 요소가 새 쿼리를 나타내는 경우 *Frequency* 값은 쿼리를 평가하기 위해 디자인 프로세스에 사용되는 가중 요인을 나타냅니다. 빈도 값이 증가하면서 디자인 프로세스 중 쿼리에 적용되는 가중치도 증가합니다.  
  
 *데이터 집합*  
 쿼리에 포함될 차원 특성을 지정하는 숫자 문자열입니다. 이 문자열에는 차원의 특성 수와 같은 문자 수가 있어야 합니다. 영(0)은 지정된 서수 위치의 특성이 지정된 차원의 쿼리에 포함되지 않음을 나타내고 일(1)은 지정된 서수 위치의 특성이 지정된 차원의 쿼리에 포함됨을 나타냅니다.  
  
 예를 들어 문자열 "011"은 세 개의 특성이 있는 차원을 사용하는 쿼리를 참조하며 여기서 두 번째 및 세 번째 특성이 쿼리에 포함됩니다.  
  
> [!NOTE]  
>  일부 특성은 데이터 세트에서 고려되지 않습니다. 제외 되는 특성에 대 한 자세한 내용은 참조 하세요. [Query 요소 &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/query-element-xmla)합니다.  
  
 집계 디자인을 포함하는 측정값 그룹의 각 차원은 *Query* 요소의 **Dataset** 값으로 나타납니다. *Dataset* 값의 순서는 측정값 그룹에 포함된 차원의 순서와 일치해야 합니다.  
  
## <a name="designing-aggregations-using-iterative-or-batch-processes"></a>반복 또는 일괄 처리를 사용하여 집계 디자인  
 사용할 수는 **DesignAggregations** 반복 처리 나 디자인 프로세스에 필요한 상호 작용에 따라 일괄 처리 프로세스의 일부로 명령입니다.  
  
### <a name="designing-aggregations-using-an-iterative-process"></a>반복 처리를 사용하여 집계 디자인  
 집계를 반복적으로 디자인 하려면 여러 보냅니다 **DesignAggregations** 명령이 디자인 프로세스를 세부적으로 제어할 수 있도록 합니다. 집계 디자인 마법사에서는 이와 동일한 방법을 사용하여 디자인 프로세스를 세부적으로 제어할 수 있습니다. 자세한 내용은 [집계 디자인 마법사 F1 도움말](http://msdn.microsoft.com/library/39e23cf1-6405-4fb6-bc14-ba103314362d)합니다.  
  
> [!NOTE]  
>  집계를 반복적으로 디자인하려면 명시적 세션이 필요합니다. 명시적 세션에 대 한 자세한 내용은 참조 하십시오 [관리 연결 및 세션 &#40;XMLA&#41;](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/managing-connections-and-sessions-xmla.md)합니다.  
  
 반복적인 프로세스를 시작 하려면 먼저 보냅니다를 **DesignAggregations** 다음 정보를 포함 하는 명령:  
  
-   합니다 **저장소** 하 고 **최적화** 디자인 프로세스 전체를 대상 속성 값입니다.  
  
-   합니다 **단계** 하 고 **시간** 디자인 프로세스의 첫 번째 단계는 제한 된 속성 값입니다.  
  
-   빈도 기반 최적화 하려는 경우는 **쿼리** 디자인 프로세스 전체를 대상 목표를 포함 하는 속성을 쿼리 합니다.  
  
-   합니다 **구체화** 속성이 false로 설정 합니다. 이 속성을 false로 설정하면 디자인 프로세스에서는 명령이 완료되었을 때 정의된 집계를 집계 디자인에 저장하지 않습니다.  
  
 때 첫 번째 **DesignAggregations** 명령이 완료 되 면 명령 디자인 통계가 들어 있는 행 집합을 반환 합니다. 이러한 디자인 통계를 평가하여 디자인 프로세스를 계속할지 여부나 디자인 프로세스가 완료되었는지 여부를 결정할 수 있습니다. 프로세스를 계속 한 다음 보낼 다른 **DesignAggregations** 명령을 포함 하는 **단계** 및 **시간** 값 있는 디자인의이 단계는 다음과 같이 처리 됩니다. 제한 됩니다. 결과 통계를 평가한 다음 디자인 프로세스를 계속할지 여부를 결정합니다. 전송 하는이 반복적 처리 **DesignAggregations** 명령 결과 평가 및 목표에 도달 하 고는 적절 한 집계 집합이 정의 될 때까지 계속 됩니다.  
  
 원하는 집계 집합에 도달한 후 하나의 최종 보내는 **DesignAggregations** 명령입니다. 이 최종 **DesignAggregations** 해야 해당 **단계** 속성이 1로 설정 및 해당 **구체화** 속성이 true로 설정 합니다. 이러한 설정을 사용 하면이 최종 **DesignAggregations** 명령이 디자인 프로세스를 완료 하 고 정의 된 집계를 집계 디자인에 저장 합니다.  
  
### <a name="designing-aggregations-using-a-batch-process"></a>일괄 처리를 사용하여 집계 디자인  
 단일을 전송 하 여 일괄 처리에서는 집계를 디자인할 수도 있습니다 **DesignAggregations** 명령을 포함 하는 **단계**를 **시간**, **저장소** , 및 **최적화** 는 디자인 프로세스 전체를 대상으로 이며 제한 된 속성 값입니다. 사용 빈도 기반 최적화를 하려는 경우 디자인 프로세스를 대상으로 하는 목표 쿼리를 포함 해야에 **쿼리** 속성입니다. 되었는지도 확인 합니다 **구체화** 속성은 true로 설정 하는 명령이 완료 되었을 때 디자인 프로세스 집계 디자인에 정의 된 집계를 저장 합니다.  
  
 암시적 세션이나 명시적 세션에서 일괄 처리를 사용하여 집계를 디자인할 수 있습니다. 암시적 세션과 명시적 세션에 대 한 자세한 내용은 참조 하세요. [관리 연결 및 세션 &#40;XMLA&#41;](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/managing-connections-and-sessions-xmla.md)합니다.  
  
## <a name="returning-design-statistics"></a>디자인 통계 반환  
 경우는 **DesignAggregations** 명령은 클라이언트 응용 프로그램에 제어를 반환 합니다., 명령은 명령에 대 한 디자인 통계를 나타내는 단일 행을 포함 하는 행 집합을 반환 합니다. 행 집합에는 다음 표에 나열된 열이 들어 있습니다.  
  
|Column|데이터 형식|Description|  
|------------|---------------|-----------------|  
|단계|정수|클라이언트 응용 프로그램에 제어를 반환하기 전에 해당 명령에서 수행하는 단계 수입니다.|  
|Time|정수(Long)|클라이언트 응용 프로그램에 제어를 반환하기 전에 해당 명령에서 소요되는 시간(밀리초)입니다.|  
|Optimization|Double|클라이언트 응용 프로그램에 제어를 반환하기 전에 해당 명령에 의해 달성되는 예상 성능 향상률입니다.|  
|저장소|정수(Long)|클라이언트 응용 프로그램에 제어를 반환하기 전에 해당 명령에서 사용하는 예상 바이트 수입니다.|  
|Aggregations|정수(Long)|클라이언트 응용 프로그램에 제어를 반환하기 전에 해당 명령에 의해 정의되는 집계 수입니다.|  
|LastStep|Boolean|행 집합의 데이터가 디자인 프로세스의 마지막 단계를 나타내는지 여부를 나타냅니다. 경우는 **구체화** 명령의 속성으로 설정한 true 이면이 열의 값 집합은 true로 합니다.|  
  
 각 반환 된 행에 있는 디자인 통계를 사용할 수 있습니다 **DesignAggregations** 반복 모두에 명령 및 일괄 처리 합니다. 반복 디자인에서는 디자인 통계를 사용하여 진행률을 확인하고 표시할 수 있습니다. 일괄 처리로 집계를 디자인할 때는 디자인 통계를 사용하여 해당 명령으로 만들어진 집계 수를 확인할 수 있습니다.  
  
## <a name="see-also"></a>관련 항목  
 [Analysis Services에서 XMLA를 사용하여 개발](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/developing-with-xmla-in-analysis-services.md)  
  
  
