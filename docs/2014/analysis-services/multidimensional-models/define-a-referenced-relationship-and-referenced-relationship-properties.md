---
title: 참조 관계를 정의 및 참조 관계 속성 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
helpviewer_keywords:
- referenced dimension relationship
- relationships [Analysis Services], referenced dimensions
ms.assetid: 5bb44b41-635b-4398-8fe9-0bfbb142553e
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 0b173aa62dfe5656bfc784c766791c294453596c
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48133243"
---
# <a name="define-a-referenced-relationship-and-referenced-relationship-properties"></a>참조 관계 및 참조 관계 속성 정의
  참조 차원 관계는 큐브 디자이너의 **차원 용도** 탭에서 다음을 지정하여 정의됩니다.  
  
-   조인할 중간 차원. 일반 차원이나 다른 참조 차원이 될 수 있습니다.  
  
-   측정값 그룹에 대해 차원을 집계에 사용할 수 있는 최하위 수준을 정의하는 참조 차원 특성입니다.  
  
-   참조 차원 특성에 해당되는 중간 차원의 (외래 키) 특성  
  
 일반적으로 참조 차원을 팩트 테이블에 연결하는 열(참조 차원에서 키 특성에 해당) 또한 중간 차원에서 특성으로 정의해야 합니다. 참조 차원 체인을 만들 때는 먼저 체인의 첫 번째 차원과 측정값 그룹 간의 일반 관계를 만듭니다. 그런 다음 각각의 추가 참조된 관계를 순서대로 만듭니다. 참조된 관계는 측정값 그룹에 대한 기존 관계가 있는 차원에 대해서만 가능합니다.  
  
 참조 차원 관계를 만들 때는 기본적으로 차원 특성 링크가 구체화됩니다. 차원의 MOLAP 구조에서 차원 특성 링크를 구체화하면 처리하는 동안 팩트 테이블과 각 행의 참조 차원 간 링크 값이 구체화되거나 저장됩니다. 이렇게 해도 처리 성능과 스토리지 요구 사항에는 거의 영향을 주지 않지만 쿼리 성능은 향상됩니다.  
  
 참조 차원에서 세분성은 참조 차원과 주 차원 테이블에 해당되는 측정값 그룹 간의 관계를 정의하는 특성을 식별하여 지정됩니다. 여러 참조 차원이 함께 연결될 때는 참조가 가장 바깥쪽 차원에서 측정값 그룹까지의 관계를 정의합니다.  
  
  
