---
title: 승인 필요
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: b475a53d-269d-49f3-bb42-965c555f80be
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 448a8174acef464fa1badb5a25d019891dd53bc6
ms.sourcegitcommit: 6be9a0ff0717f412ece7f8ede07ef01f66ea2061
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85812065"
---
# <a name="approval-required-master-data-services"></a>승인 필요(Master Data Services)

[!INCLUDE [SQL Server - Windows only ASDBMI  ](../includes/applies-to-version/sql-windows-only-asdbmi.md)]

  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]에서 관리자는 엔터티를 승인 필요 항목으로 설정할 수 있습니다. 이 엔터티를 변경할 때마다 엔터티 관리자 중 한 명이 변경 내용을 검토하고 승인해야 합니다.  
  
> [!NOTE]  
>  리프 멤버를 변경하는 경우 승인이 필요합니다. 사용되지 않는 명시적 계층 및 컬렉션을 변경하는 경우에는 승인이 무시됩니다.  
>   
>  준비 테이블 프로세스에서 수행하는 변경에서도 승인이 무시됩니다.  
>   
>  비즈니스 규칙을 통한 변경 역시 승인이 무시됩니다.  
  
## <a name="prerequisites"></a>전제 조건  
 이 절차를 수행하려면  
  
-   시스템 관리 기능 영역에 액세스할 수 있는 권한이 있어야 합니다.  
  
-   모델 관리자여야 합니다. 자세한 내용은 [관리자&#40;Master Data Services&#41;](../master-data-services/administrators-master-data-services.md)를 참조하세요.  
  
-   엔터티가 있어야 합니다. 자세한 내용은 [엔터티 만들기&#40;Master Data Services&#41;](../master-data-services/create-an-entity-master-data-services.md)를 참조하세요.  
  
## <a name="to-enable-approval-required-for-an-entity"></a>엔터티에 대해 승인 필요 기능을 사용하도록 설정하려면  
  
1.  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]에서 **시스템 관리**를 클릭합니다.  
  
2.  **모델 관리** 페이지의 표에서 모델을 선택하고 **엔터티**를 클릭합니다.  
  
3.  **엔터티 관리** 페이지의 표에서  **승인 필요** 를 사용하도록 설정할 엔터티의 행을 선택합니다.  
  
4.  **편집**을 클릭하고 **승인 필요**를 선택한 후에 **저장**을 클릭합니다.  
  
## <a name="see-also"></a>참고 항목  
 [변경 집합&#40;Master Data Services&#41;](../master-data-services/changesets-master-data-services.md)  
  
  
