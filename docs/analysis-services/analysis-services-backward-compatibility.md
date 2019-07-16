---
title: SQL Server 2016 Analysis Services 이전 버전과 호환성 | Microsoft Docs
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: ''
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 5ab4f304d865992a3269b4ee83c9e25f61069e8c
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/15/2019
ms.locfileid: "68210264"
---
# <a name="analysis-services-backward-compatibility-sql-server-2016"></a>Analysis Services 이전 버전과 호환성 (SQL Server 2016)
[!INCLUDE[ssas-appliesto-sql2016](../includes/ssas-appliesto-sql2016.md)]

기능 가용성 및 현재 버전 및 이전 버전 간의 동작 변경 내용을 설명합니다.

## <a name="deprecated-features"></a>사용되지 않는 기능
A *사용 되지 않는 기능* 향후 릴리스에서 제품에서 중단 될 예정 이지만 여전히 지원 되 고 이전 버전과 호환성을 유지 하기 위해 현재 릴리스에서 포함 합니다. 신규 및 기존 프로젝트에서 사용 되지 않는 기능을 사용 하 여 향후 릴리스와도 호환을 유지 관리를 중단 하는 것이 좋습니다.
  
다음 기능은이 릴리스에서 사용 되지 않습니다.
  
|||  
|-|-|  
|**모드/범주**|**기능**|  
|다차원|원격 파티션|  
|다차원|원격으로 연결된 측정값 그룹|  
|다차원|차원 쓰기(writeback)|  
|다차원|연결된 차원|   
|다차원|자동 관리 캐싱을 위한 SQL Server 테이블 알림.  <br />자동 관리 캐싱을 위한 폴링을 대신 사용할 수 있습니다. <br />[자동 관리 캐싱&#40;차원&#41;](../analysis-services/multidimensional-models-olap-logical-dimension-objects/proactive-caching-dimensions.md) 및 [자동 관리 캐싱&#40;파티션&#41;](../analysis-services/multidimensional-models-olap-logical-cube-objects/partitions-proactive-caching.md)을 참조하세요.|  
|다차원|세션 큐브. 대체 기능은 없습니다.|  
|다차원|로컬 큐브. 대체 기능은 없습니다.|  
|테이블 형식|테이블 형식 모델 1100 및 1103 호환성 수준은 향후 릴리스에서 지원되지 않을 예정입니다. 대체 모델 호환성 수준 1200 이상 설정, 테이블 형식 메타 데이터를 모델 정의 변환 하는 것입니다. [Analysis services에서 테이블 형식 모델에 대한 호환성 수준](../analysis-services/tabular-models/compatibility-level-for-tabular-models-in-analysis-services.md)을 참조하세요.|  
|Tools|추적 캡처용 SQL Server Profiler<br /><br /> SQL Server Management Studio에 포함된 확장 이벤트 프로파일러를 대신 사용할 수 있습니다.  <br /> [Monitor Analysis Services with SQL Server Extended Events](../analysis-services/instances/monitor-analysis-services-with-sql-server-extended-events.md)을 참조하세요.|  
|Tools|추적 재생용 Server Profiler <br />대체 기능 대체 기능은 없습니다.|  
|추적 관리 개체 및 추적 API|Analysis Services 추적 및 재생 개체용 API를 포함하는 Microsoft.AnalysisServices.Trace 개체. 다음과 같은 여러 부분을 대신 사용할 수 있습니다.<br /><br /> 추적 구성: Microsoft.SqlServer.Management.XEvent<br />추적 읽기: Microsoft.SqlServer.XEvent.Linq<br />추적 재생: 없음|  
  
> [!NOTE]  
>  이전에 사용이 중단된 기능에 대한 [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] 의 공지 사항은 계속 적용됩니다. 이러한 기능을 지원하는 코드는 아직 제품에서 삭제되지 않았으므로 이러한 기능 중 대부분은 이 릴리스에도 계속 포함되어 있습니다. 이전에 사용 되지 않는 기능 하는 동안 수는 여전히 것이 사용 되지 않으며 실제로 수에 액세스할 수에서 제거할 제품 언제 든 지 합니다.  

## <a name="discontinued-features"></a>지원 되지 않는 기능
A *기능을 지원 되지 않는* 이전 릴리스에서 사용 되지 않았습니다. 계속 현재 릴리스에서 포함 될 수 있지만 더 이상 지원 되지. 지원 되지 않는 기능을 제거할 수 있습니다 완전히 이후에서 릴리스 또는 업데이트 합니다.

다음 이전 릴리스에서 사용 되지 않는 기능과이 릴리스에서 더 이상 지원 되지.

|||  
|-|-|  
|**기능**|**대체 기능 또는 해결 방법**|  
|[CalculationPassValue&#40;MDX&#41;](../mdx/calculationpassvalue-mdx.md)|없음 이 기능은 SQL Server 2005부터 사용되지 않습니다.|  
|[CalculationCurrentPass&#40;MDX&#41;](../mdx/calculationcurrentpass-mdx.md)|없음 이 기능은 SQL Server 2005부터 사용되지 않습니다.|  
|NON_EMPTY_BEHAVIOR 쿼리 최적화 프로그램 힌트|없음 이 기능은 SQL Server 2008부터 사용되지 않습니다.|  
|COM 어셈블리|없음 이 기능은 SQL Server 2008부터 사용되지 않습니다.|  
|CELL_EVALUATION_LIST 기본 셀 속성|없음 이 기능은 SQL Server 2005부터 사용되지 않습니다.|  
  
> [!NOTE]  
>  이전에 사용이 중단된 기능에 대한 [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] 의 공지 사항은 계속 적용됩니다. 이러한 기능을 지원하는 코드는 아직 제품에서 삭제되지 않았으므로 이러한 기능 중 대부분은 이 릴리스에도 계속 포함되어 있습니다. 이전에 사용 되지 않는 기능 하는 동안 수는 여전히 것이 사용 되지 않으며 실제로 수에 액세스할 수에서 제거할 제품 언제 든 지 합니다.  

## <a name="breaking-changes"></a>주요 변경 내용
*새로운 변경* 이 적용되면 모델이나 서버를 업그레이드한 후에 데이터 모델, 응용 프로그램 코드 또는 스크립트가 더 이상 작동하지 않습니다.
  
### <a name="net-40-version-upgrade"></a>.NET 4.0 버전 업그레이드  
 Analysis Services Management Objects (AMO), ADOMD.NET 및 TOM 테이블 형식 개체 모델 () 클라이언트 라이브러리는 이제.NET 4.0 런타임을 대상입니다. .NET 3.5를 대상으로 하는 애플리케이션의 경우 새로운 변경 사항이 될 수 있습니다. 이러한 어셈블리의 최신 버전을 사용하는 애플리케이션은 이제 .NET 4.0 이상을 대상으로 해야 합니다.  
  
### <a name="amo-version-upgrade"></a>AMO 버전 업그레이드  
 이 릴리스는 버전 업그레이드 [Analysis Services Management Objects &#40;AMO&#41; ](https://msdn.microsoft.com/library/mt436122.aspx) 이며 특정 상황에서 크게 변경 되었습니다.  AMO로 호출되는 기존 코드와 스크립트는 이전 버전에서 업그레이드하기 전과 동일하게 실행됩니다. 그러나 해야 할 경우 *recompile* 응용 프로그램 하며 SQL Server 2016 Analysis Services 인스턴스를 대상에 코드나 스크립트가 작동 하도록 다음 네임 스페이스를 추가 해야 합니다.  
  
```  
  
using Microsoft.AnalysisServices;  
using Microsoft.AnalysisServices.Core;  
  
```  
  
 코드에서 Microsoft.AnalysisServices 어셈블리를 참조할 때마다 [Microsoft.AnalysisServices.Core](https://msdn.microsoft.com/library/microsoft.analysisservices.core.aspx) 네임스페이스가 필요합니다. 이전에는 **Microsoft.AnalysisServices** 네임스페이스에만 포함되었던 개체가 테이블 형식 시나리오와 다차원 시나리오에서 같은 방식으로 사용되는 경우 이번 릴리스에서는 Core 네임스페이스로 이동됩니다.  예를 들어 서버 관련 API는 Core 네임스페이스로 이동됩니다.  
  
 이처럼 이제는 네임스페이스가 여러 개 사용되지만 모든 네임스페이스는 같은 어셈블리(Microsoft.AnalysisServices.dll)에 포함됩니다.  
  
### <a name="xevent-discover-changes"></a>XEvent DISCOVER 변경 사항  
 XEvent DISCOVER SQL Server 2016 Analysis Services에 대 한 SSMS에서 스트리밍을 더 잘 지원할 `DISCOVER_XEVENT_TRACE_DEFINITION` 다음과 같은 XEvent 추적으로 대체 됩니다.  
  
-   DISCOVER_XEVENT_PACKAGES  
  
-   DISCOVER_XEVENT_OBJECT  
  
-   DISCOVER_XEVENT_OBJECT_COLUMNS  
  
-   DISCOVER_XEVENT_SESSION_TARGETS  

## <a name="behavior-changes"></a>동작 변경 내용
*동작 변경 내용* 은 이전 버전의 SQL Server와 비교해서 현재 버전에서 기능이 작동하고 상호 작용하는 방법에 영향을 줍니다.
  
기본값에 대한 수정, 업그레이드 또는 복원 기능을 완료하는 데 필요한 수동 구성 또는 기존 기능의 새로운 구현 작업 시제품에서 동작을 변경할 수 있습니다.
  
이 릴리스에서 변경되고 업그레이드 후 기존 모델 또는 코드를 중단하지 않는 기능 동작이 여기에 나열됩니다.
  
### <a name="analysis-services-in-sharepoint-mode"></a>SharePoint 모드의 Analysis Services
 사후 설치 태스크로 더 이상 파워 피벗 구성 마법사를 실행할 필요가 없습니다. 현재 SQL Server 2016 Analysis Services에서 모델을 로드 하는 SharePoint의 모든 지원 되는 버전에 대 한 마찬가지입니다.
  
### <a name="directquery-mode-for-tabular-models"></a>테이블 형식 모델의 DirectQuery 모드
 *DirectQuery* 는 테이블 형식 모델의 데이터 액세스 모드입니다. 여기서 쿼리 실행은 백 엔드 관계형 데이터베이스에서 수행되며 결과 집합을 실시간으로 검색합니다. 메모리에 맞출 수 없는 매우 큰 데이터 세트나 데이터가 불안정한 경우, 테이블 형식 모델에 대한 쿼리에서 반환된 최근 데이터를 원하는 경우 주로 사용됩니다.
  
 DirectQuery는 지난 몇 번의 릴리스에서 데이터 액세스 모드로 존재해왔습니다. SQL Server 2016 Analysis Services의 구현이 약간 수정 되었으며, 1200 이상 호환성 수준의 테이블 형식 모델을 가정 합니다. DirectQuery는 이전보다 제한이 적습니다. 또한 데이터베이스 속성도 다릅니다.
  
 기존 테이블 형식 모델에서 DirectQuery를 사용하는 경우 현재 호환성 수준 1100 또는 1103에서 모델을 유지하고 해당 수준에 대해 구현된 것으로 DirectQuery를 계속 사용할 수 있습니다. 또는 DirectQuery에 대 한 향상 된 기능을 활용 하려면 1200 이상으로 업그레이드할 수 있습니다.
  
 이전 호환성 수준의 설정은 최신 1200 이상 호환성 수준에서 정확한 해당 항목이 없기 때문에 DirectQuery 모델의 전체 업그레이드 없음 있습니다. DirectQuery 모드에서 실행 되는 기존 테이블 형식 모델에 있는 경우 있습니다 해야 SQL Server Data Tools에서 모델을 열고 DirectQuery를 해제, 설정 된 **호환성 수준** 속성을 1200 이상 및 DirectQuery 후 다시 구성 속성입니다. 참조 [DirectQuery 모드](../analysis-services/tabular-models/directquery-mode-ssas-tabular.md) 세부 정보에 대 한 합니다.


## <a name="see-also"></a>참고자료
[Analysis Services 이전 버전과 호환성 (SQL Server 2017)](analysis-services-backward-compatibility-sql2017.md)
