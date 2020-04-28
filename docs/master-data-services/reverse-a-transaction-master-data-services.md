---
title: 트랜잭션 되돌리기
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- transactions [Master Data Services], reversing
ms.assetid: 6f7c3f07-0f64-4283-8c9c-93facd00a046
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 870341b6ae6a3ffbda345aa7a0abc4a2fe253ac5
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/27/2020
ms.locfileid: "73728935"
---
# <a name="reverse-a-transaction-master-data-services"></a>트랜잭션 되돌리기(Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]에서 동작을 취소해야 할 경우 관리자가 트랜잭션을 되돌릴 수 있습니다. 트랜잭션의 예로 특성 값 변경, 계층 이동 또는 멤버 삭제가 있습니다. 이 항목은 트랜잭션 로그 유형이 "특성"인 엔터티의 트랜잭션에만 적용됩니다. 트랜잭션 로그 유형이 "멤버"인 엔터티의 트랜잭션 기록을 보려면 엔터티 탐색기 페이지로 이동하세요.  
  
## <a name="prerequisites"></a>전제 조건  
  
-   **버전 관리** 기능 영역에 액세스할 수 있는 권한이 있어야 합니다.  
  
-   모델 관리자여야 합니다. 자세한 내용은 [관리자 &#40;MDS(Master Data Services)&#41;](../master-data-services/administrators-master-data-services.md)를 참조 하세요.  
  
### <a name="to-reverse-a-transaction"></a>트랜잭션을 되돌리려면  
  
1.  [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] 홈 페이지에서 **버전 관리**를 클릭합니다.  
  
2.  메뉴 모음에서 **트랜잭션**을 클릭합니다.  
  
3.  **트랜잭션** 페이지의 **모델** 목록에서 모델을 선택합니다.  
  
4.  **버전** 목록에서 버전을 선택합니다.  
  
5.  트랜잭션의 표에서 되돌릴 행을 클릭합니다.  
  
6.  **트랜잭션 되돌리기**를 클릭합니다.  
  
7.  확인 대화 상자에서 **확인**을 클릭합니다. 되돌린 트랜잭션을 기록하기 위해 또 다른 트랜잭션이 표에 추가됩니다.  
  
## <a name="see-also"></a>참고 항목  
 [트랜잭션 &#40;MDS(Master Data Services)&#41;](../master-data-services/transactions-master-data-services.md)   
 [멤버 또는 컬렉션 다시 활성화&#40;Master Data Services&#41;](../master-data-services/reactivate-a-member-or-collection-master-data-services.md)  
 [멤버 수정 기록 롤백](../master-data-services/rollback-member-revision-history-master-data-services.md)
  
  
