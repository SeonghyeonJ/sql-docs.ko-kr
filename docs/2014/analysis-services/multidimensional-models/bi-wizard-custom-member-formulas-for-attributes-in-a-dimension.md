---
title: 차원의 특성에 대 한 사용자 지정 멤버 수식 설정 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Business Intelligence enhancements [Analysis Services], custom member formulas
- member formulas [Analysis Services]
- dimensions [Analysis Services], Business Intelligence enhancements
- custom member formulas [Analysis Services]
- CustomRollupColumn property
ms.assetid: c4467b08-ce59-4de7-a2d9-c22e246bdd52
author: minewiskan
ms.author: owend
ms.openlocfilehash: 112f8944bd20b2b6a464b0d84fb8ac1a0e89d976
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84544575"
---
# <a name="set-custom-member-formulas-for-attributes-in-a-dimension"></a>차원에 특성의 사용자 지정 멤버 수식 설정
  큐브나 차원에 사용자 지정 멤버 수식 기능을 추가하여 차원 멤버와 연결된 기본 집계를 MDX(Multidimensional Expression) 식의 결과로 바꿀 수 있습니다. 이 기능은 차원에서 지정한 특성에 대한 `CustomRollupColumn` 속성을 설정합니다.  
  
> [!NOTE]  
>  사용자 지정 멤버 수식은 기존 데이터 원본을 기반으로 하는 차원에만 사용할 수 있습니다. 데이터 원본을 사용하지 않고 만든 차원의 경우에는 사용자 지정 멤버 수식을 추가하기 전에 스키마 생성 마법사를 실행하여 데이터 원본 뷰를 만들어야 합니다.  
  
 사용자 지정 멤버 수식을 추가하려면 비즈니스 인텔리전스 마법사의 **기능 선택** 페이지에서 **사용자 지정 멤버 수식 만들기** 옵션을 선택합니다. 그런 다음 마법사의 안내를 따라 사용자 지정 멤버 수식을 적용할 차원을 선택하고 사용자 지정 멤버 수식을 사용하도록 설정합니다.  
  
## <a name="selecting-a-dimension"></a>차원 선택  
 마법사의 첫 번째 **사용자 지정 멤버 수식 만들기** 페이지에서 사용자 지정 멤버 수식을 적용할 차원을 지정합니다. 선택한 차원에 사용자 지정 멤버 수식 기능을 추가하면 차원이 변경됩니다. 이러한 변경 내용은 선택된 차원을 포함하는 모든 큐브에 상속됩니다.  
  
## <a name="enabling-a-custom-member-formula"></a>사용자 지정 멤버 수식 사용 설정  
 두 번째 **사용자 지정 멤버 수식 만들기** 페이지에서 사용자 지정 멤버 수식이 포함된 원본 열을 차원에 있는 하나 이상의 특성과 연결합니다. **특성** 열에서 사용자 지정 멤버 수식 열과 연결할 특성 옆에 있는 확인란을 선택합니다. 특성을 선택할 때마다 **열 선택** 대화 상자가 표시됩니다. 이 대화 상자에서 수식이 포함된 차원 테이블의 열을 클릭합니다. **열 선택** 대화 상자를 닫은 후에 선택 사항을 변경하려면 변경할 **원본 열** 셀을 클릭한 다음 줄임표(**...**)를 클릭하여 **열 선택** 대화 상자를 다시 엽니다.  
  
## <a name="see-also"></a>참고 항목  
 [비즈니스 인텔리전스 마법사를 사용하여 차원 향상](../use-the-business-intelligence-wizard-to-enhance-dimensions.md)  
  
  
