---
title: 변경 집합 만들기(Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: cfad6f1c-9125-4896-b5f5-a4b9f9593cc4
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 97cc3f748f5d5b94a65eddcbcb54b9d407c7bed6
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/15/2019
ms.locfileid: "65484231"
---
# <a name="create-a-changeset-master-data-services"></a>변경 집합 만들기(Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  변경 집합은 마스터 데이터에 대해 보류 중인 변경 내용의 컬렉션입니다. 엔터티 변경 시 승인이 필요한 경우 보류 중인 변경 내용을 변경 집합에 저장한 다음 관리자의 승인을 받기 위해 제출해야 합니다.  
  
## <a name="prerequisites"></a>사전 요구 사항  
  
-   탐색기 기능 영역에 액세스할 수 있는 권한이 있어야 합니다. 자세한 내용은 [기능 영역 권한&#40;Master Data Services&#41;](../master-data-services/functional-area-permissions-master-data-services.md)을 참조하세요.  
  
-   엔터티 또는 엔터티의 특성 중 하나에 대한 읽기 이상의 권한이 있어야 합니다.  
  
## <a name="to-create-a-local-changeset"></a>로컬 변경 집합을 만들려면  
  
1.  [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] 홈 페이지에서 모델 및 버전을 선택하고 **탐색기**를 클릭합니다.  
  
2.  **엔터티** 메뉴에서 엔터티를 클릭합니다.  
  
3.  오른쪽 창에서 **변경 집합** 을 선택하고 **만들기**를 클릭합니다.  
  
4.  변경 집합의 이름을 입력한 다음 **저장**을 클릭합니다.  
  
     변경 집합의 이름은 모델 내에서 고유해야 합니다.  
  
## <a name="to-create-a-changeset-for-approval"></a>승인을 위해 변경 집합을 만들려면  
  
1.  [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] 홈 페이지에서 모델 및 버전을 선택하고 **탐색기**를 클릭합니다.  
  
2.  **엔터티** 메뉴에서 엔터티를 클릭합니다.  
  
3.  엔터티를 변경하고**확인**을 클릭합니다.  
  
4.  **변경 집합 선택** 대화 상자가 표시됩니다.  
  
5.  **새로 만들기**를 클릭하고 변경 집합의 이름을 입력한 다음 **저장**을 클릭합니다. 변경 집합 이름은 모델 내에서 고유해야 합니다.  
  
6.  기존 변경 집합을 사용하려면 **기존** 을 클릭하고 목록에서 변경 집합을 선택합니다. 열림 또는 거부됨 상태의 변경 집합만 사용할 수 있습니다.  
  
## <a name="next-steps"></a>다음 단계  
 [변경 집합 적용 및 업데이트&#40;Master Data Services&#41;](../master-data-services/apply-and-update-a-changeset-master-data-services.md)  
  
## <a name="see-also"></a>관련 항목  
 [변경 집합 커밋 또는 제출&#40;Master Data Services&#41;](../master-data-services/commit-or-submit-a-changeset-master-data-services.md)   
 [변경 집합 승인 또는 거부&#40;Master Data Services&#41;](../master-data-services/approve-or-reject-a-changeset-master-data-services.md)  
  
  
