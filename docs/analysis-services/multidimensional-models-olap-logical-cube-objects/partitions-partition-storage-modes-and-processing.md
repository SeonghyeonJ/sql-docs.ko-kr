---
title: 파티션 저장소 모드 및 처리 | Microsoft Docs
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: olap
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 57c73e3ae9661058277a377b7d17b6a4af393ba0
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62640455"
---
# <a name="partitions---partition-storage-modes-and-processing"></a>파티션 - 파티션 스토리지 모드 및 처리
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  파티션의 저장소 모드는 파티션과 해당 부모 측정값 그룹 및 큐브의 쿼리 및 처리 성능, 저장소 요구 사항, 저장소 위치 등에 영향을 줍니다. 선택한 저장소 모드는 처리 선택 사항에도 영향을 줍니다.  
  
 파티션에는 다음 3가지 기본 저장소 모드 중 하나를 사용할 수 있습니다.  
  
-   MOLAP(다차원 OLAP)  
  
-   ROLAP(관계형 OLAP)  
  
-   HOLAP(하이브리드 OLAP)  
  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 모든 세 가지 기본 저장소 모드를 지원합니다. 또한 자동 관리 캐싱을 지원하므로 ROLAP과 MOLAP 저장소의 특성을 적절히 조합하여 데이터를 즉시 검색하고 쿼리 성능을 향상시킬 수 있습니다. 자세한 내용은 [자동 관리 캐싱&#40;파티션&#41;](../../analysis-services/multidimensional-models-olap-logical-cube-objects/partitions-proactive-caching.md)을 참조하세요.  
  
## <a name="molap"></a>MOLAP  
 MOLAP 저장소 모드에서는 파티션을 처리할 때 파티션 집계와 해당 원본 데이터의 복사본이 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]에 다차원 구조로 저장됩니다. 이 MOLAP 구조는 최적의 쿼리 성능을 얻을 수 있도록 최적화된 구조입니다. 저장소 위치는 파티션이 정의된 컴퓨터나 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]를 실행 중인 다른 컴퓨터일 수 있습니다. 원본 데이터 복사본이 다차원 구조에 있으므로 파티션의 원본 데이터에 액세스하지 않고 쿼리를 해결할 수 있습니다. 집계를 사용하면 쿼리 응답 시간이 훨씬 줄어들 수 있습니다. 파티션의 MOLAP 구조에 있는 데이터는 파티션에서 가장 최근에 처리 중인 데이터입니다.  
  
 원본 데이터가 변경되면 해당 변경 내용을 통합할 수 있도록 MOLAP 저장소의 개체가 정기적으로 처리되어야 하며 사용자가 사용할 수 있도록 해야 합니다. 처리 시 MOLAP 구조의 데이터가 전체 또는 증분 업데이트됩니다. 앞의 처리와 다음 처리 간에 생기는 간격으로 인해 대기 시간이 발생하게 되는데 이 시간 동안에는 OLAP 개체가 원본 데이터와 일치하지 않을 수 있습니다. 파티션이나 큐브를 오프라인 상태로 만들지 않고도 MOLAP 저장소의 개체를 증분 또는 전체 업데이트할 수 있습니다. 그러나 OLAP 개체에 대한 특정 구조 변경 내용을 처리하기 위해 큐브를 오프라인 상태로 만들어야 하는 경우도 있습니다. 준비 서버(staging server)에서 큐브를 업데이트 및 처리하고 데이터베이스 동기화를 통해 처리된 개체를 프로덕션 서버로 복사하면 MOLAP 저장소 업데이트에 필요한 작동 중단 시간을 최소화할 수 있습니다. 또한 자동 관리 캐싱을 사용하여 대기 시간을 최소화하고 가용성을 최대화하는 동시에 MOLAP 저장소가 제공하는 성능상의 장점을 최대한으로 활용할 수 있습니다. 자세한 내용은 [자동 관리 캐싱 &#40;파티션&#41;](../../analysis-services/multidimensional-models-olap-logical-cube-objects/partitions-proactive-caching.md)를 [Analysis Services 데이터베이스 동기화](../../analysis-services/multidimensional-models/synchronize-analysis-services-databases.md), 및 [다차원 모델 처리 &#40; Analysis Services&#41;](../../analysis-services/multidimensional-models/processing-a-multidimensional-model-analysis-services.md)합니다.  
  
## <a name="rolap"></a>ROLAP  
 ROLAP 저장소 모드에서는 파티션의 집계가 파티션의 데이터 원본에 지정된 관계형 데이터베이스의 인덱싱된 뷰에 저장됩니다. MOLAP 저장소 모드와는 달리 ROLAP에서는 원본 데이터의 복사본이 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 데이터 폴더에 저장되지 않습니다. 대신 쿼리 캐시에서 결과를 얻을 수 없는 경우 쿼리에 응답하기 위해 데이터 원본의 인덱싱된 뷰가 액세스됩니다. ROLAP 저장소 모드를 사용하는 경우 일반적으로 쿼리 응답 시간은 MOLAP 또는 HOLAP 저장소 모드를 사용하는 경우에서보다 느립니다. ROLAP을 사용하면 처리 시간도 대체로 느립니다. 그러나 ROLAP을 사용하면 사용자가 실시간으로 데이터를 볼 수 있으며 기록 데이터와 같이 자주 쿼리되지 않는 대량의 데이터 집합 작업을 수행하는 경우 저장소 공간을 절약할 수 있습니다.  
  
> [!NOTE]  
>  ROLAP을 사용하는 경우 조인이 GROUP BY 절과 결합되어 있으면 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]에서 알 수 없는 멤버와 관련된 부정확한 정보를 반환할 수 있습니다. [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]에서는 이와 같은 알 수 없는 멤버 값을 반환하는 대신 관계 무결성 오류를 제거합니다.  
  
 파티션에 ROLAP 저장소 모드를 사용하고 해당 원본 데이터가 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]에 저장되어 있는 경우 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]에서는 파티션의 집계를 포함할 인덱싱된 뷰를 만듭니다. [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]에서 인덱싱된 뷰를 만들 수 없으면 집계 테이블을 생성하지 않습니다. [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]에서 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]에 인덱싱된 뷰를 만들기 위해 필요한 세션 요구 사항을 처리하지만 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]에서 집계에 대해 인덱싱된 뷰를 만들려면 ROLAP 파티션과 해당 스키마의 테이블이 다음 조건을 만족해야 합니다.  
  
-   파티션을 사용 하는 측정값을 포함할 수 없습니다는 **Min** 또는 **Max** 집계 함수입니다.  
  
-   ROLAP 파티션 스키마의 각 테이블은 한 번씩만 사용되어야 합니다. 예를 들어 스키마에 [dbo].[address] AS "Customer Address"와 [dbo].[address] AS "SalesRep Address"가 함께 포함될 수 없습니다.  
  
-   각 테이블은 뷰가 아니라 테이블이어야 합니다.  
  
-   파티션 스키마의 모든 테이블 이름은 소유자 이름으로 정규화(예: [dbo].[customer])되어야 합니다.  
  
-   파티션 스키마의 모든 테이블에서 소유자가 동일해야 합니다. 예를 들어 [tk].[customer], [john].[store] 및 [dave].[sales_fact_2004]를 참조하는 FROM 절이 있을 수 없습니다.  
  
-   파티션 측정값의 원본 열에는 Null이 허용되지 않습니다.  
  
-   뷰에서 사용하는 모든 테이블은 다음 옵션을 ON으로 설정하여 생성된 것이어야 합니다.  
  
    -   ANSI_NULLS  
  
    -   QUOTED_IDENTIFIER  
  
-   [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]에서 인덱스 키의 전체 크기는 900바이트를 초과할 수 없습니다. [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 에서는 CREATE INDEX 문 처리 시 고정된 길이 키 열에 따라 이러한 조건을 적용 합니다. 그러나 인덱스 키에 가변 길이 열이 없으면, [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 기본 테이블에 대 한 모든 업데이트에 대 한이 조건에도 적용 됩니다. 여러 집계에는 서로 다른 뷰 정의를 사용하므로, 인덱싱된 뷰를 사용하는 ROLAP 처리는 집계 디자인에 따라 성공할 수도 있고 실패할 수도 있습니다.  
  
-   인덱싱된 뷰를 만드는 세션에서는 ARITHABORT, CONCAT_NULL_YIELDS_NULL, QUOTED_IDENTIFIER, ANSI_NULLS, ANSI_PADDING, ANSI_WARNING 등의 옵션이 ON이어야 합니다. 이 설정은 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]에서 지정할 수 있습니다.  
  
-   인덱싱된 뷰를 만드는 세션에서는 NUMERIC_ROUNDABORT 옵션이 OFF이어야 합니다. 이 설정은 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]에서 지정할 수 있습니다.  
  
## <a name="holap"></a>HOLAP  
 HOLAP 저장소 모드는 MOLAP과 ROLAP의 특성을 모두 포함합니다. MOLAP과 마찬가지로 holap 집계가 파티션의 다차원 구조에 저장 되는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 인스턴스. HOLAP 모드에서는 원본 데이터 복사본이 저장되지 않습니다. 파티션의 집계에 포함된 요약 데이터에만 액세스하는 쿼리의 경우 HOLAP이 MOLAP과 동일합니다. 원본 데이터에 액세스 하는 쿼리-원자성 큐브 셀으로 드릴 다운 하려는 경우에 없는 집계 데이터 반드시 관계형 데이터베이스에서 데이터를 검색 하 고 원본 데이터가 MOLAP structur 저장 된 경우 처럼 빠른 됩니다 예를 들어, e입니다. HOLAP 저장소 모드에서는 일반적으로 캐시 또는 집계에서 쿼리를 해결할 수 있는지 또는 원본 데이터 자체에서 해결할 수 있는지에 따라 쿼리 시간에 큰 차이가 있습니다.  
  
 HOLAP으로 저장된 파티션은 원본 데이터를 포함하지 않으므로 동일한 MOLAP 파티션보다 크기가 작으며 요약 데이터를 사용하는 쿼리에 대해 ROLAP 파티션보다 응답 속도가 빠릅니다. HOLAP 저장소 모드는 일반적으로 방대한 원본 데이터를 기반으로 하는 요약에 대해 신속한 쿼리 응답이 필요한 큐브의 파티션에 적합합니다. 그러나 중앙값 계산과 같이 리프 수준 데이터에 액세스해야 하는 쿼리를 생성하는 경우에는 대개 MOLAP을 사용하는 것이 더 낫습니다.  
  
## <a name="see-also"></a>관련 항목  
 [자동 관리 캐싱 &#40;파티션&#41;](../../analysis-services/multidimensional-models-olap-logical-cube-objects/partitions-proactive-caching.md)   
 [Analysis Services 데이터베이스 동기화](../../analysis-services/multidimensional-models/synchronize-analysis-services-databases.md)   
 [파티션 & #40; Analysis Services-다차원 데이터 & #41;](../../analysis-services/multidimensional-models-olap-logical-cube-objects/partitions-analysis-services-multidimensional-data.md)  
  
  
