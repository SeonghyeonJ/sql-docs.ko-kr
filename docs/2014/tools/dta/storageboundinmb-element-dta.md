---
title: StorageBoundInMB 요소 (DTA) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- StorageBoundInMB element
ms.assetid: a8374910-bf68-4edb-b464-53a3a705e7f4
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 33dbfad3c3774abe3de74d4dbf1d67575630b21e
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63460108"
---
# <a name="storageboundinmb-element-dta"></a>StorageBoundInMB 요소(DTA)
  데이터베이스 엔진 튜닝 관리자 튜닝 권장 구성(인덱스 및 분할 집합)에 사용될 수 있는 최대 공간(MB)을 지정합니다.  
  
## <a name="syntax"></a>구문  
  
```  
  
<DTAInput>  
...code removed...  
    <TuningOptions>  
      <StorageBoundInMB>...</ StorageBoundInMB >  
```  
  
## <a name="element-characteristics"></a>요소 특징  
  
|특징|Description|  
|--------------------|-----------------|  
|**데이터 형식 및 길이**|`unsignedInt`, 길이 제한 없음|  
|**기본값**|없음|  
|**발생 빈도**|(선택 사항) `TuningOptions` 요소에 한 번만 사용할 수 있습니다.|  
  
## <a name="element-relationships"></a>요소 관계  
  
|관계|요소|  
|------------------|--------------|  
|**부모 요소**|[TuningOptions 요소&#40;DTA&#41;](tuningoptions-element-dta.md)|  
|**자식 요소**|없음|  
  
## <a name="remarks"></a>Remarks  
 여러 개의 데이터베이스를 튜닝할 경우 모든 데이터베이스에 대한 권장 구성은 공간 계산을 고려하여 처리됩니다. 기본적으로 데이터베이스 엔진 튜닝 관리자는 다음 스토리지 크기보다 작은 공간을 가정합니다.  
  
-   현재 원시 데이터 크기의 3배이며 테이블에 있는 힙과 클러스터형 인덱스의 전체 크기를 포함합니다.  
  
-   연결된 모든 디스크 드라이브의 여유 공간과 원시 데이터 크기를 더한 것입니다.  
  
 기본 스토리지 크기는 비클러스터형 인덱스 및 인덱싱된 뷰를 포함하지 않습니다.  
  
 `StorageBoundInMB` 요소에 지정된 값이 실제 디스크 공간을 초과할 경우 데이터베이스 엔진 튜닝 관리자는 오류를 반환하지만 튜닝 작업은 계속합니다. 튜닝이 완료된 후 권장 구성을 구현하려는 경우에는 디스크 공간을 추가할 수 있습니다.  
  
## <a name="example"></a>예제  
  
## <a name="description"></a>Description  
 다음 코드 예에서는 튜닝 권장 구성에서 사용할 수 있는 최대 디스크 공간으로 1500MB를 설정하는 방법을 보여 줍니다.  
  
## <a name="code"></a>코드  
  
```  
<DTAInput>  
  <Server>...</Server>  
  <Workload>...</Workload>  
  <TuningOptions>  
    <StorageBoundInMB>1500</StorageBoundInMB>  
...code removed here...  
</DTAInput>  
```  
  
## <a name="see-also"></a>관련 항목  
 [XML 입력 파일 참조&#40;데이터베이스 엔진 튜닝 관리자&#41;](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
