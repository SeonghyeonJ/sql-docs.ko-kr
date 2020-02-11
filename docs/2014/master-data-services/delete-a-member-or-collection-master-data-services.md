---
title: 멤버 또는 컬렉션 삭제(Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- collections [Master Data Services], deleting
- leaf members [Master Data Services], deleting
- deleting members [Master Data Services]
- members [Master Data Services], deleting
- consolidated members [Master Data Services], deleting
ms.assetid: 519130a7-4226-4d71-9124-d2ee0ce7e5bd
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: f3164bca23e709fd434c6ba7850ec21179a076ef
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2020
ms.locfileid: "65479711"
---
# <a name="delete-a-member-or-collection-master-data-services"></a>멤버 또는 컬렉션 삭제(Master Data Services)
  
  [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]에서는 멤버나 컬렉션이 더 이상 필요하지 않으면 삭제할 수 있습니다. 멤버를 대량으로 삭제하려면 준비 프로세스를 대신 사용합니다. 자세한 내용은 [준비 프로세스를 사용 하 여 멤버 비활성화 또는 삭제 &#40;MDS(Master Data Services)&#41;](add-update-and-delete-data-master-data-services.md)를 참조 하세요.  
  
> [!NOTE]  
>  다른 멤버의 도메인 기반 특성 값으로 사용되는 멤버는 삭제할 수 없습니다.  
  
## <a name="prerequisites"></a>사전 요구 사항  
 이 절차를 수행하려면  
  
-   
  **탐색기** 기능 영역에 액세스할 수 있는 권한이 있어야 합니다.  
  
-   멤버의 경우 멤버를 삭제할 리프 모델 개체에 대 한 **업데이트** 이상의 권한이 있어야 합니다.  
  
-   컬렉션의 경우 컬렉션을 삭제할 리프 컬렉션 모델 개체에 대한 **업데이트** 이상의 권한이 있어야 합니다.  
  
### <a name="to-delete-a-member-or-collection"></a>멤버 또는 컬렉션을 삭제하려면  
  
1.  
  [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] 홈 페이지의 **모델** 목록에서 모델을 선택합니다.  
  
2.  
  **버전** 목록에서 버전을 선택합니다.  
  
3.  
  **탐색기**를 클릭합니다.  
  
4.  삭제하려면  
  
    -   리프 멤버를 삭제하려면 메뉴 모음에서 **엔터티** 를 가리키고 멤버가 포함된 엔터티의 이름을 클릭합니다.  
  
    -   통합 멤버를 삭제하려면 메뉴 모음에서 **계층** 을 가리키고 멤버가 포함된 계층의 이름을 클릭합니다. 그런 다음 멤버를 포함하고 있는 계층에서 노드를 클릭합니다.  
  
    -   컬렉션을 삭제하려면 메뉴 모음에서 **컬렉션** 을 가리키고 컬렉션이 포함된 엔터티의 이름을 클릭합니다.  
  
5.  표에서 삭제할 멤버 또는 컬렉션의 행을 선택합니다.  
  
6.  
  **멤버 삭제**또는 **삭제**또는 **컬렉션 삭제**를 클릭합니다.  
  
7.  확인 대화 상자에서 **확인**을 클릭합니다.  
  
## <a name="see-also"></a>참고 항목  
 [MDS(Master Data Services) &#40;멤버 또는 컬렉션을 다시 활성화&#41;](../../2014/master-data-services/reactivate-a-member-or-collection-master-data-services.md)   
 [멤버가 MDS(Master Data Services)를 &#40;&#41;](../../2014/master-data-services/members-master-data-services.md)   
 [컬렉션 &#40;MDS(Master Data Services)&#41;](../../2014/master-data-services/collections-master-data-services.md)  
  
  
