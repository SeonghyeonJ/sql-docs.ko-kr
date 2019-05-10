---
title: 병합 충돌(Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: 797219ad-5109-4666-94d3-dd1d59440a33
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 993e46a9795aa8528f4e1a1744dbf9dd5b27f89f
ms.sourcegitcommit: 5748d710960a1e3b8bb003d561ff7ceb56202ddb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/09/2019
ms.locfileid: "65488912"
---
# <a name="merge-conflicts-master-data-services"></a>병합 충돌(Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]에서는 다른 사용자가 변경한 데이터를 게시하려고 하면 충돌 오류로 인해 게시에 실패합니다. 이 오류를 해결하려면 병합 충돌을 수행하고 변경 내용을 다시 게시합니다.  
  
## <a name="prerequisites"></a>사전 요구 사항  
 이 절차를 수행하려면  
  
-   **탐색기** 기능 영역에 액세스할 수 있는 권한이 있어야 합니다.  
  
-   업데이트할 엔터티의 리프 모델 개체에 대한 업데이트 이상의 권한이 있어야 합니다.  
  
### <a name="to-merge-conflicts"></a>충돌 내용을 병합하려면  
  
1.  **탐색기** 페이지에서 멤버 특성을 업데이트합니다.  
  
2.  다른 사용자가 동일한 멤버 특성을 변경한 경우 **병합 충돌** 대화 상자가 나타납니다.  
  
3.  **병합 충돌** 대화 상자에서 다음 중 하나를 수행할 수 있습니다.  
  
    -   **최신 버전** 을 선택하고 **적용** 을 클릭하여 보류 중인 변경을 실행 취소하고 서버에서 최신 버전을 다시 로드합니다.  
  
    -   **원본** 을 선택하고 **적용** 을 클릭하여 워크시트의 원래 버전을 적용합니다.  
  
    -   **내 변경 내용** 을 선택하고 **적용** 을 클릭하여 기존 로컬 변경 내용을 유지합니다.  
  
4.  **적용**을 클릭한 후에 추가 변경을 수행하고 데이터를 다시 게시할 수 있습니다. 또는 **취소** 를 클릭하여 업데이트를 취소하고 서버에서 최신 버전을 다시 로드할 수도 있습니다.  
  
## <a name="see-also"></a>관련 항목  
 [멤버&#40;Master Data Services&#41;](../master-data-services/members-master-data-services.md)  
  
  
