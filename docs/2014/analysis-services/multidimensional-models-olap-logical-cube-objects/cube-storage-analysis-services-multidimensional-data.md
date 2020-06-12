---
title: 큐브 저장소 (Analysis Services 다차원 데이터) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- measure groups [Analysis Services], cubes
- cubes [Analysis Services], storage
- linked measure groups [Analysis Services]
- storing data [Analysis Services], cubes
- partitions [Analysis Services], cubes
- storage [Analysis Services], cubes
ms.assetid: 1b1ad360-9a9b-4996-bee9-84238a2bb4ac
author: minewiskan
ms.author: owend
ms.openlocfilehash: eef1dd188b0038c637dc15750a6538c929359299
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84545295"
---
# <a name="cube-storage-analysis-services---multidimensional-data"></a>큐브 스토리지(Analysis Services - 다차원 데이터)
  스토리지에는 큐브 메타데이터만 포함되거나, 측정값 그룹과 관련된 차원으로 정의한 집계 및 팩트 테이블의 모든 원본 데이터가 포함될 수 있습니다. 저장되는 데이터 양은 선택한 스토리지 모드와 집계 수에 따라 달라집니다. 저장되는 데이터 양은 쿼리 성능에 직접적인 영향을 줍니다. [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 에서는 큐브 데이터 및 집계 저장소에 필요한 공간을 최소화 하기 위해 여러 가지 기술을 사용 합니다.  
  
-   스토리지 옵션을 사용하여 큐브 데이터에 가장 적합한 스토리지 모드 및 위치를 선택할 수 있습니다.  
  
-   고급 알고리즘으로 속도 저하 없이 스토리지를 최소화하기 위한 효율적인 요약 집계를 디자인합니다.  
  
-   빈 셀에는 스토리지를 할당하지 않습니다.  
  
 스토리지는 파티션 단위로 정의되며 큐브의 각 측정값 그룹에 대해 하나 이상의 파티션이 존재합니다. 자세한 내용은 [파티션 &#40;Analysis Services-다차원 데이터&#41;](partitions-analysis-services-multidimensional-data.md), [파티션 저장소 모드 및 처리](partitions-partition-storage-modes-and-processing.md), 측정값 [및 측정값 그룹](../multidimensional-models/measures-and-measure-groups.md), [다차원 모델에서 측정값 및 측정값 그룹 만들기](../multidimensional-models/create-measures-and-measure-groups-in-multidimensional-models.md)를 참조 하세요.  
  
## <a name="partition-storage"></a>파티션 스토리지  
 측정값 그룹의 스토리지를 여러 파티션으로 나눌 수 있습니다. 파티션을 사용하면 측정값 그룹을 단일 서버나 여러 서버에서 불연속 세그먼트로 배포하고 스토리지 및 쿼리 성능을 최적화할 수 있습니다. 측정값 그룹의 각 파티션은 서로 다른 데이터 원본을 기반으로 할 수 있으며 개별적인 스토리지 설정에 따라 저장될 수 있습니다.  
  
 파티션을 만들 때 이에 대한 데이터 원본을 지정합니다. 기존 파티션의 데이터 원본을 변경할 수도 있습니다. 측정값 그룹을 수직 또는 수평 분할할 수 있습니다. 수직 분할된 측정값 그룹의 각 파티션은 단일 원본 테이블의 필터링된 뷰를 기반으로 합니다. 예를 들어 측정값 그룹이 여러 해에 걸친 데이터를 포함하는 단일 테이블을 기반으로 하는 경우 각 연도의 데이터에 대해 별도의 파티션을 만들 수 있습니다. 이와 반대로 수평 분할된 측정값 그룹의 각 파티션은 별도의 테이블을 기반으로 합니다. 데이터 원본이 개별 테이블에 각 연도의 데이터를 저장하는 경우에는 수평 분할을 사용합니다.  
  
 파티션이 생성되는 측정값 그룹과 동일한 스토리지 설정으로 파티션이 처음 생성됩니다. 세부 데이터와 집계 데이터는 스토리지 설정에 따라 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]인스턴스에 다차원 형식으로 저장되거나, 원본 서버에 관계형 형식으로 저장되거나, 두 가지 방법을 모두 사용하여 저장됩니다. [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]에 저장되는 다차원 데이터에 대한 원본 데이터 변경 내용을 자동으로 처리하기 위해 자동 관리 캐싱을 사용할지 여부도 스토리지 설정에 따라 결정됩니다.  
  
 큐브의 파티션은 사용자에게 표시되지 않습니다. 그러나 다른 파티션에 대한 스토리지 설정 선택 사항은 데이터의 즉시성, 사용되는 디스크 공간의 양 및 쿼리 성능에 영향을 미칠 수 있습니다. 파티션을 여러 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]인스턴스에 저장하여 큐브 스토리지에 대한 클러스터형 액세스를 제공할 수 있으며 작업을 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 서버 전체에 걸쳐 분산시킬 수 있습니다. 자세한 내용은 [파티션 저장소 모드 및 처리](partitions-partition-storage-modes-and-processing.md), [원격 파티션](partitions-remote-partitions.md)및 [파티션 &#40;Analysis Services 다차원 데이터&#41;](partitions-analysis-services-multidimensional-data.md)을 참조 하세요.  
  
## <a name="linked-measure-groups"></a>연결된 측정값 그룹  
 서로 다른 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]인스턴스에 큐브 복사본을 여러 개 저장하려면 상당한 디스크 공간이 필요할 수 있지만 측정값 그룹의 복사본을 연결된 측정값 그룹으로 바꿔 필요한 공간을 상당히 줄일 수 있습니다. 연결된 측정값 그룹은 동일하거나 서로 다른 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 인스턴스의 또 다른 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]데이터베이스에 있는 큐브의 측정값 그룹을 기반으로 합니다. 연결된 측정값 그룹은 같은 원본 큐브의 연결된 차원에서도 사용할 수 있습니다. 연결된 차원과 측정값 그룹은 원본 큐브의 집계를 사용하며 자체의 데이터 스토리지가 필요하지 않습니다. 따라서 한 데이터베이스에서는 원본 측정값 그룹 및 차원을 유지 관리하고 다른 데이터베이스에서는 큐브에 연결된 큐브 및 차원을 만들어 스토리지로 사용될 수 있는 디스크 공간을 절약할 수 있습니다. 자세한 내용은 [Linked Measure Groups](../multidimensional-models/linked-measure-groups.md)을 참조하세요.  
  
## <a name="see-also"></a>참고 항목  
 [Aggregations and Aggregation Designs](aggregations-and-aggregation-designs.md)  
  
  
