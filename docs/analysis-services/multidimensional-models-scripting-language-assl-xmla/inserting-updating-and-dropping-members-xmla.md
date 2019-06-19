---
title: 삽입, 업데이트 및 삭제 (XMLA) 멤버 | Microsoft Docs
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 3a409e21e925b3912aee5ec751747f61bce05276
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63138585"
---
# <a name="inserting-updating-and-dropping-members-xmla"></a>멤버 삽입, 업데이트 및 삭제(XMLA)
  사용할 수는 [삽입](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/insert-element-xmla)를 [업데이트](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/update-element-xmla), 및 [Drop](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/drop-element-xmla) 명령은 xml에서 for Analysis (XMLA) 삽입, 업데이트 또는 쓰기 가능 차원에서 멤버를 삭제 합니다. 쓰기 가능 차원에 대 한 자세한 내용은 참조 하세요. [쓰기 가능한 차원](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/write-enabled-dimensions.md)합니다.  
  
## <a name="inserting-new-members"></a>새 멤버 삽입  
 합니다 **삽입** 명령에서는 쓰기 가능 차원에서 지정 된 특성에 새 멤버를 삽입 합니다.  
  
 생성 하기 전에 합니다 **삽입** 명령을 삽입할 새 멤버를 위한 다음 정보가 있어야 합니다.  
  
-   새 멤버를 삽입할 차원.  
  
-   새 멤버를 삽입할 차원 특성.  
  
-   이름의 적용할 수 있는 번역을 포함한 새 멤버의 이름.  
  
-   새 멤버의 키. 특성이 복합 키를 사용하는 경우 이 키에는 값이 여러 개 필요할 수 있습니다.  
  
-   차원 내에서 다른 특성으로 구현되지 않은 적용 가능한 모든 특성 속성의 값. 이러한 특성 속성에는 단항 연산, 번역, 사용자 지정 롤업, 사용자 지정 롤업 속성 및 건너뛴 수준이 있습니다.  
  
 합니다 **삽입** 명령은 두 개의 속성만 사용 합니다.  
  
-   합니다 [개체](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/object-element-xmla) 멤버를 삽입할에 차원에 대 한 개체 참조를 포함 하는 속성입니다. 개체 참조는 차원에 대한 데이터베이스 식별자, 큐브 식별자 및 차원 식별자를 포함합니다.  
  
-   합니다 [특성](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/attributes-element-xmla) 속성을 하나 이상 포함 [특성](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/attribute-element-xmla) 멤버를 삽입할에 특성을 식별 하는 요소입니다. 각 **특성** 요소 이름, 값, 번역, 단항 연산자, 사용자 지정 롤업, 사용자 지정 롤업 속성을 제공 및 건너뛴 수준이 식별된 된 특성에 추가할 단일 멤버는 특성을 식별 합니다.  
  
    > [!NOTE]  
    >  에 대 한 모든 속성을 **특성** 요소가 포함 되어야 합니다. 그렇지 않으면 오류가 발생할 수 있습니다.  
  
## <a name="updating-existing-members"></a>기존 멤버 업데이트  
 합니다 **업데이트** 명령에서는 쓰기 가능 차원에서 다른 특성의 다른 멤버와 관계를 기반으로 지정 된 특성의 기존 멤버를 업데이트 합니다. 합니다 **업데이트** 명령은 이동할 수 계층의 다른 수준으로 멤버를 차원에 포함 되어 있으며 부모 특성에 의해 정의 된 부모-자식 계층 구조를 사용할 수 있습니다.  
  
 생성 하기 전에 합니다 **업데이트** 명령을 업데이트할 멤버를 위한 다음 정보가 있어야 합니다.  
  
-   기존 멤버를 업데이트할 차원.  
  
-   기존 멤버를 업데이트할 차원 특성.  
  
-   기존 멤버의 키. 특성이 복합 키를 사용하는 경우 이 키에는 값이 여러 개 필요할 수 있습니다.  
  
-   차원 내에서 다른 특성으로 구현되지 않은 적용 가능한 모든 특성 속성의 값. 이러한 특성 속성에는 단항 연산, 번역, 사용자 지정 롤업, 사용자 지정 롤업 속성 및 건너뛴 수준이 있습니다.  
  
 합니다 **업데이트** 명령은 세 개의 필수 속성만 사용 합니다.  
  
-   합니다 **개체** 업데이트할 멤버는 차원에 대 한 개체 참조를 포함 하는 속성입니다. 개체 참조는 차원에 대한 데이터베이스 식별자, 큐브 식별자 및 차원 식별자를 포함합니다.  
  
-   합니다 **특성** 속성을 하나 이상 포함 **특성** 멤버를 업데이트할에 특성을 식별 하는 요소입니다. 합니다 **특성** 요소 이름, 값, 번역, 단항 연산자, 사용자 지정 롤업, 사용자 지정 롤업 속성을 제공 및 건너뛴 수준이 식별된 된 특성에 대 한 업데이트 된 단일 멤버는 특성을 식별 합니다.  
  
    > [!NOTE]  
    >  에 대 한 모든 속성을 **특성** 요소가 포함 되어야 합니다. 그렇지 않으면 오류가 발생할 수 있습니다.  
  
-   합니다 [여기서](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/where-element-xmla) 하나 이상 포함 된 속성을 **특성** 멤버를 업데이트할에 특성을 제한 하는 요소입니다. 합니다 **여기서** 속성이 제한 하는 것이 중요는 **업데이트** 명령을 멤버의 특정 인스턴스로. 경우는 **여기서** 속성이 지정 되지 않은, 지정된 된 멤버의 모든 인스턴스가 업데이트 됩니다. 예를 들어, 세 명의 고객에 대한 도시 이름을 Redmond에서 Bellevue로 변경하려고 합니다. 제공 된 도시 이름을 변경 해야 합니다는 **여기서** 는 City 특성의 멤버를 변경 해야 하는 것에 대 한 고객의 세 멤버를 식별 하는 속성 특성입니다. 이 제공 하지 않는 경우 **여기서** 속성인 도시 이름이 현재 redmond로 되어 모든 고객은 도시 이름이 bellevue로 변경 후의 **업데이트** 명령 실행 합니다.  
  
    > [!NOTE]  
    >  새 멤버를 제외 하 고는 **업데이트** 명령에 포함 되지 않은 특성의 특성 키 값만 업데이트할 수는 **여기서** 절. 예를 들어, 고객을 업데이트하는 경우 도시 이름을 업데이트할 수 없습니다. 이렇게 하지 않으면 모든 고객의 도시 이름이 변경됩니다.  
  
### <a name="updating-members-in-parent-attributes"></a>부모 특성의 멤버 업데이트  
 부모 특성을 지원 하 여 **업데이트** 명령에 선택적 [MoveWithDescendants](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/movewithdescendants-element-xmla)위해 속성입니다. 설정 된 **MoveWithDescendants** 속성을 true로 부모 멤버의 하위 항목도 수 이동 부모 멤버와 해당 부모 멤버의 식별자가 변경 하는 경우를 나타냅니다. 이 값을 false로 설정한 경우 부모 멤버를 이동하면 해당 부모 멤버의 직계 하위 항목이 부모 멤버의 이전 수준으로 승격됩니다.  
  
 부모 특성의 멤버를 업데이트할 때 합니다 **업데이트** 명령은 다른 특성의 멤버를 업데이트할 수 없습니다.  
  
## <a name="dropping-existing-members"></a>기존 멤버 삭제  
 생성 하기 전에 합니다 **Drop** 명령을 삭제할 멤버를 위한 다음 정보가 있어야 합니다.  
  
-   기존 멤버를 삭제할 차원.  
  
-   기존 멤버를 삭제할 차원 특성.  
  
-   삭제할 기존 멤버의 키. 특성이 복합 키를 사용하는 경우 이 키에는 값이 여러 개 필요할 수 있습니다.  
  
 합니다 **Drop** 명령은 두 개의 필수 속성만 사용 합니다.  
  
-   합니다 **개체** 삭제할 멤버는 차원에 대 한 개체 참조를 포함 하는 속성입니다. 개체 참조는 차원에 대한 데이터베이스 식별자, 큐브 식별자 및 차원 식별자를 포함합니다.  
  
-   합니다 **여기서** 하나 이상 포함 된 속성을 **특성** 삭제할 멤버는 특성 제한 하는 요소입니다. 합니다 **여기서** 속성이 제한 하는 것이 중요를 **Drop** 명령을 멤버의 특정 인스턴스로. 경우는 **여기서** 명령을 지정 하지 않으면 지정된 된 멤버의 모든 인스턴스가 삭제 됩니다. 예를 들어, Redmond의 고객 세 명을 삭제하려고 합니다. 이러한 고객을 삭제 하려면 제공 해야 합니다는 **여기서** 속성이 식별 하는 제거할 Customer 특성의 세 멤버와 세 고객을 제거할 City 특성 올의 Redmond 멤버입니다. 경우는 **여기서** 속성에 City 특성의 Redmond 멤버만 지정, Redmond에 연결 된 모든 고객 삭제 됩니다 합니다 **삭제** 명령입니다. 경우는 **위치** 속성 Customer 특성의 세 멤버만 지정, 세 고객을 통해 완전히 삭제 되는 합니다 **삭제** 명령입니다.  
  
    > [!NOTE]  
    >  **특성** 에 포함 된 요소를 **Drop** 만 포함 되어야 합니다는 **AttributeName** 및 **키** 속성입니다. 그렇지 않으면 오류가 발생할 수 있습니다.  
  
### <a name="dropping-members-in-parent-attributes"></a>부모 특성의 멤버 삭제  
 설정 된 [DeleteWithDescendants](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/deletewithdescendants-element-xmla) 속성은 부모 멤버를 사용 하 여도 부모 멤버의 하위 항목을 삭제 해야 함을 나타냅니다. 이 값을 false로 설정한 경우에는 부모 멤버의 직계 하위 항목이 부모 멤버의 이전 수준으로 승격됩니다.  
  
> [!IMPORTANT]  
>  부모 멤버와 해당 하위 항목을 모두 삭제하려면 부모 멤버에 대한 삭제 권한만 있으면 됩니다. 하위 항목에 대한 삭제 권한은 필요하지 않습니다.  
  
## <a name="see-also"></a>관련 항목  
 [Drop 요소 &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/drop-element-xmla)   
 [요소를 삽입 &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/insert-element-xmla)   
 [Update 요소 &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/update-element-xmla)   
 [개체 정의 및 식별 &#40;XMLA&#41;](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/defining-and-identifying-objects-xmla.md)   
 [Analysis Services에서 XMLA를 사용하여 개발](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/developing-with-xmla-in-analysis-services.md)  
  
  
