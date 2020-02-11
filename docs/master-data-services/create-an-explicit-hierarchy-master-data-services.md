---
title: 명시적 계층 만들기
ms.custom: ''
ms.date: 04/01/2016
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- creating explicit hierarchies [Master Data Services]
- explicit hierarchies, creating
ms.assetid: ba768393-6990-4eda-8cb0-d58cb3cfc2e2
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 6b366c29412a3a698e793d3153784a8d1450bc81
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2020
ms.locfileid: "73729514"
---
# <a name="create-an-explicit-hierarchy-master-data-services"></a>명시적 계층 만들기(Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  
  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]에서 멤버가 임의의 수준에 존재할 수 있는 비정형 계층이 필요할 때 명시적 계층을 만듭니다. 명시적 계층에는 단일 엔터티의 멤버가 포함됩니다.  
  
 명시적 계층을 만든 후에는 **탐색기** 기능 영역에서 해당 계층에 멤버를 추가할 수 있습니다.  
  
## <a name="prerequisites"></a>사전 요구 사항  
 이 절차를 수행하려면  
  
-   
  **시스템 관리** 기능 영역에 액세스할 수 있는 권한이 있어야 합니다.  
  
-   모델 관리자여야 합니다. 자세한 내용은 [관리자&#40;Master Data Services&#41;](../master-data-services/administrators-master-data-services.md)에 액세스하지 않고 그룹에서 사용자를 추가하고 제거할 수 있습니다.  
  
-   명시적 계층 및 컬렉션에 엔터티가 사용되어야 합니다.  
  
### <a name="to-create-an-explicit-hierarchy"></a>명시적 계층을 만들려면  
  
1.  
  [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]에서 **시스템 관리**를 클릭합니다.  
  
2.  
  **모델 관리** 페이지의 표에서 모델을 선택하고 **엔터티**를 클릭합니다.  
  
3.  
  **엔터티 관리** 페이지의 표에서 명시적 계층을 만들려는 엔터티의 행을 선택합니다.  
  
4.  **명시적 계층**을 클릭 합니다.  
  
5.  
  **명시적 계층 관리** 페이지에서 **추가**를 클릭합니다.  
  
6.  
  **이름** 상자에 계층의 이름을 입력합니다.  
  
7.  또는 **필수 계층** 확인란의 선택을 취소하여 계층을 필수가 아닌 계층으로 만듭니다. 계층 형식에 대한 자세한 내용은 [명시적 계층&#40;Master Data Services&#41;](../master-data-services/explicit-hierarchies-master-data-services.md)를 참조하세요.  
  
8.  **저장**을 클릭합니다.  
  
## <a name="grid-columns"></a>표 형태의 열  
 생성되는 각 명시적 계층에 대해 열이 7개 포함된 행이 표에 추가됩니다. 아래에서는 이러한 열에 대해 설명합니다.  
  
|속성|Description|  
|----------|-----------------|  
|상태|엔터티 상태입니다. 
  **저장** 을 클릭하면 엔터티가 업데이트되고 있음을 나타내는 다음 이미지가 표시됩니다.<br /><br /> ![상태 업데이트 아이콘](../master-data-services/media/mds-statusicon-updating.png "상태 업데이트 아이콘")<br /><br /> 엔터티를 만들거나 편집할 때 오류가 발생하면 다음 이미지가 표시됩니다.<br /><br /> ![오류 상태 아이콘](../master-data-services/media/mds-statusicon-error.png "오류 상태 아이콘")<br /><br /> 엔터티가 정상 상태이면 다음 이미지가 표시됩니다.<br /><br /> ![정상 상태 아이콘](../master-data-services/media/mds-statusicon-ok.png "정상 상태 아이콘")|  
|속성|명시적 계층의 이름입니다.|  
|필수입니다.|명시적 계층이 필수 항목인지 여부를 지정합니다.|  
|만든 사람|명시적 계층을 만든 사용자의 사용자 이름입니다.|  
|만든 날짜|명시적 계층을 만든 날짜와 시간입니다.|  
|업데이트한 사람|명시적 계층을 마지막으로 업데이트한 사용자의 사용자 이름입니다.|  
|Updated On|명시적 계층을 마지막으로 업데이트한 날짜와 시간입니다.|  
  
## <a name="next-steps"></a>다음 단계  
  
-   [MDS(Master Data Services) &#40;통합 멤버를 만듭니다&#41;](../master-data-services/create-a-consolidated-member-master-data-services.md)  
  
  
  
## <a name="see-also"></a>참고 항목  
 [명시적 계층 &#40;MDS(Master Data Services)&#41;](../master-data-services/explicit-hierarchies-master-data-services.md)   
 [명시적 캡이 포함 된 파생 계층 &#40;MDS(Master Data Services)&#41;](../master-data-services/derived-hierarchies-with-explicit-caps-master-data-services.md)   
 [명시적 계층 이름 &#40;MDS(Master Data Services)&#41;변경](../master-data-services/change-an-explicit-hierarchy-name-master-data-services.md)  
  
  

