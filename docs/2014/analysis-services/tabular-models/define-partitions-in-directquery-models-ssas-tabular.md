---
title: 파티션 및 DirectQuery 모드 (SSAS 테이블 형식) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 5f179ba9-6efb-46ae-90e5-945bbfddb719
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 1fe22de3cc0718647de84345260017a4dd4e477e
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/26/2020
ms.locfileid: "66067304"
---
# <a name="partitions-and-directquery-mode-ssas-tabular"></a>파티션 및 DirectQuery 모드(SSAS 테이블 형식)
  이 섹션에서는 DirectQuery 모델에서 파티션을 사용하는 방법에 대해 설명합니다. 테이블 형식 모델의 파티션에 대한 일반적인 정보는 [파티션&#40;SSAS 테이블 형식&#41;](partitions-ssas-tabular.md)을 참조하세요.  
  
 사용 되는 파티션을 변경 하는 방법 또는 파티션에 대 한 정보를 확인 하는 방법에 대 한 지침은 [DirectQuery 파티션 변경 &#40;SSAS 테이블 형식&#41;](../change-the-directquery-partition-ssas-tabular.md)을 참조 하세요.  
  
## <a name="using-partitions-in-directquery-mode"></a>DirectQuery 모드에서 파티션 사용  
 각 테이블에 대해 DirectQuery 데이터 원본으로 사용할 단일 파티션을 지정해야 합니다.  여러 파티션이 있는 경우에는 DirectQuery 모드를 사용할 수 있도록 모델을 전환하면 기본적으로 테이블에 처음 만들어진 파티션이 DirectQuery 파티션으로 플래그가 지정됩니다. 나중에 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]에서 파티션 관리자를 사용하여 이를 변경할 수 있습니다.  
  
 DirectQuery 모드에서 단일 파티션만 허용되는 이유  
  
 테이블 형식 모델에서는 OLAP 모델에서와 마찬가지로 테이블의 파티션이 SQL 쿼리로 정의됩니다. 파티션 정의를 만드는 개발자는 파티션이 겹치지 않도록 해야 합니다. Analysis Services에서는 레코드가 하나의 파티션에 속하는지 아니면 여러 파티션에 속하는지 확인하지 않습니다.  
  
 캐시된 테이블 형식 모델의 파티션도 동일한 방식으로 동작합니다. 캐시에 액세스하는 동안 메모리 내 모델을 사용하는 경우 각 파티션에 대해 DAX 수식이 계산되고 결과가 결합됩니다. 그러나 테이블 형식 모델에서 DirectQuery 모드를 사용하는 경우에는 여러 파티션을 평가하고 결과를 결합해 SQL 문으로 변환하여 관계형 데이터 저장소에 보낼 수 없습니다. 그렇게 하면 결과가 집계될 때 정확성이 떨어지고 성능이 크게 저하될 수 있습니다.  
  
 따라서 DirectQuery 모드에서 응답하는 쿼리의 경우 서버는 DirectQuery 액세스용 주 파티션으로 표시된 단일 파티션인 *DirectQuery 파티션*을 사용합니다.  이 파티션의 정의에 지정된 SQL 쿼리는 DirectQuery 모드에서 쿼리에 응답하는 데 사용할 수 있는 전체 데이터 집합을 정의합니다.  
  
 파티션을 명시적으로 지정하지 않은 경우 엔진은 단순히 전체 관계형 데이터 원본에 대한 SQL 쿼리를 실행하고 DAX 수식으로 지정된 집합 기반 연산을 수행하고 쿼리 결과를 반환합니다.  
  
 테이블에 파티션이 여러 개 있을 때 파티션 하나를 DirectQuery 파티션으로 선택하면 기본적으로 다른 모든 파티션은 자동으로 메모리 내 전용으로 표시됩니다.  
  
## <a name="partitions-in-cached-models-and-in-directquery-models"></a>캐시된 모델 및 DirectQuery 모델의 파티션  
 DirectQuery 파티션을 구성할 때 파티션에 대한 처리 옵션을 지정해야 합니다.  
  
 DirectQuery에 대한 처리 옵션은 두 가지가 있습니다. 이 속성을 설정하려면 **또는** 에서 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]파티션 관리자 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]를 사용하고 **처리 옵션** 속성을 선택합니다. 다음 표에서는 이 속성 값을 나열하고 각 값을 연결 문자열에서 DirectQueryUsage 속성과 결합할 때의 효과에 대해 설명합니다.  
  
|**DirectQueryUsage** 속성|**처리 옵션** 속성|메모|  
|-----------------------------------|------------------------------------|-----------|  
|DirectQuery|이 파티션 처리 안 함|모델이 DirectQuery만 사용 중인 경우 처리가 필요 없습니다.<br /><br /> 혼합 모델에서 DirectQuery 파티션이 처리되지 않도록 구성할 수 있습니다. 예를 들어 매우 큰 데이터 집합에 대해 작동 중일 때 캐시에 전체 결과를 추가하지는 않으려는 경우 테이블의 다른 모든 파티션에 대한 결과의 합집합을 DirectQuery 파티션에 포함하도록 지정할 수 있습니다. 관계형 원본으로 이동하는 쿼리는 영향을 받지 않으며 캐시된 데이터에 대한 쿼리는 다른 파티션의 데이터를 결합합니다.|  
|InMemory With DirectQuery|파티션을 처리하도록 허용|모델이 혼합 모드를 사용 중인 경우 메모리 내 모델에 대한 쿼리와 DirectQuery 데이터 원본에 대한 쿼리에 대해 동일한 파티션을 사용해야 합니다.|  
  
## <a name="see-also"></a>참고 항목  
 [파티션&#40;SSAS 테이블 형식&#41;](partitions-ssas-tabular.md)  
  
  
