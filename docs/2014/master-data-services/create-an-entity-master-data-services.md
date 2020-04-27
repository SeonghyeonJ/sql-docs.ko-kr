---
title: 엔터티 만들기(Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- entities [Master Data Services], creating
- creating entities [Master Data Services]
ms.assetid: d9a6a51e-7b53-4785-a118-3baeb7ca2d48
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: d85fc4c21f200bcdc5a489cfcee6b50bc9f4b98e
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/26/2020
ms.locfileid: "65479908"
---
# <a name="create-an-entity-master-data-services"></a>엔터티 만들기(Master Data Services)
  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]에서 멤버와 해당 특성을 포함할 엔터티를 만듭니다.  
  
## <a name="prerequisites"></a>사전 요구 사항  
 이 절차를 수행하려면  
  
-   **시스템 관리** 기능 영역에 액세스할 수 있는 권한이 있어야 합니다.  
  
-   모델 관리자여야 합니다. 자세한 내용은 [관리자 &#40;MDS(Master Data Services)&#41;](administrators-master-data-services.md)를 참조 하세요.  
  
-   모델이 있어야 합니다. 자세한 내용은 [모델 만들기&#40;Master Data Services&#41;](../../2014/master-data-services/create-a-model-master-data-services.md)를 참조하세요.  
  
### <a name="to-create-an-entity"></a>엔터티를 만들려면  
  
1.  [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]에서 **시스템 관리**를 클릭합니다.  
  
2.  **모델 뷰** 페이지의 메뉴 모음에서 **관리** 를 가리키고 **엔터티**를 클릭합니다.  
  
3.  **엔터티 유지 관리** 페이지의 **모델** 목록에서 모델을 선택합니다.  
  
4.  **엔터티 추가**를 클릭 합니다.  
  
5.  **엔터티 이름** 상자에 엔터티의 이름을 입력 합니다.  
  
6.  준비 테이블 **이름** 상자에 준비 테이블의 이름을 입력 합니다.  
  
    > [!TIP]  
    >  모델 이름을 준비 테이블의 일부로 사용합니다(예: *Modelname_Entityname*). 그러면 데이터베이스에서 테이블을 더 쉽게 찾을 수 있습니다. 준비 테이블에 대 한 자세한 내용은 [데이터 가져오기 &#40;MDS(Master Data Services)&#41;](overview-importing-data-from-tables-master-data-services.md)를 참조 하세요.  
  
7.  선택 사항입니다. **코드 값 자동으로 만들기** 확인란을 선택합니다. 자세한 내용은 [MDS(Master Data Services)&#41;&#40;자동 코드 만들기 ](../../2014/master-data-services/automatic-code-creation-master-data-services.md)를 참조 하세요.  
  
8.  **명시적 계층 및 컬렉션 사용** 목록에서 다음 옵션 중 하나를 선택 합니다.  
  
    -   **No**. 명시적 계층 및 컬렉션에 대해 엔터티를 사용할 필요가 없으면 이 옵션을 선택합니다. 필요할 경우 나중에 이 옵션을 변경할 수 있습니다.  
  
    -   **예**. 명시적 계층 및 컬렉션에 대해 엔터티를 사용하려면 이 옵션을 선택합니다. **명시적 계층 이름** 상자에 이름을 입력 합니다. 필요에 따라 **필수 계층 (모든 리프 멤버 포함)** 을 선택 하 여 명시적 계층을 필수 계층으로 만듭니다.  
  
9. **엔터티 저장**을 클릭합니다.  
  
## <a name="next-steps"></a>다음 단계  
  
-   [텍스트 특성 만들기&#40;Master Data Services&#41;](../../2014/master-data-services/create-a-text-attribute-master-data-services.md)  
  
-   [도메인 기반 특성 만들기&#40;Master Data Services&#41;](../../2014/master-data-services/create-a-domain-based-attribute-master-data-services.md)  
  
-   [파일 특성 만들기&#40;Master Data Services&#41;](../../2014/master-data-services/create-a-file-attribute-master-data-services.md)  
  
## <a name="see-also"></a>참고 항목  
 [엔터티 &#40;MDS(Master Data Services)&#41;](../../2014/master-data-services/entities-master-data-services.md)   
 [명시적 계층 &#40;MDS(Master Data Services)&#41;](../../2014/master-data-services/explicit-hierarchies-master-data-services.md)   
 [엔터티 이름 &#40;MDS(Master Data Services)&#41;변경](edit-an-entity-master-data-services.md)   
 [엔터티 삭제&#40;Master Data Services&#41;](../../2014/master-data-services/delete-an-entity-master-data-services.md)  
  
  
