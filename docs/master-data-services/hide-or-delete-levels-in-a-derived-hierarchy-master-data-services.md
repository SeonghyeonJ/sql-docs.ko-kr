---
description: 파생 계층의 수준 숨기기 또는 삭제(Master Data Services)
title: 파생 계층의 수준 숨기기 또는 삭제
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- derived hierarchies, hiding levels
- derived hierarchies, deleting levels
ms.assetid: e00582b9-9415-4b66-b4a7-9f590d83875f
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 21d638e7a4600dfc818d1213c9cd72db588aaded
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88471949"
---
# <a name="hide-or-delete-levels-in-a-derived-hierarchy-master-data-services"></a>파생 계층의 수준 숨기기 또는 삭제(Master Data Services)

[!INCLUDE [SQL Server - Windows only ASDBMI  ](../includes/applies-to-version/sql-windows-only-asdbmi.md)]

  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]에서는 그룹화용으로 수준이 필요하지만 해당 수준을 표시할 필요는 없는 경우 파생 계층의 수준을 숨길 수 있습니다. 그룹화에 수준을 사용하지 않으려면 수준을 삭제합니다.  
  
## <a name="prerequisites"></a>사전 요구 사항  
 이 절차를 수행하려면  
  
-   **시스템 관리** 기능 영역에 액세스할 수 있는 권한이 있어야 합니다.  
  
-   모델 관리자여야 합니다. 자세한 내용은 [관리자 &#40;MDS(Master Data Services)&#41;](../master-data-services/administrators-master-data-services.md)를 참조 하세요.  
  
### <a name="to-hide-or-delete-levels-in-a-derived-hierarchy"></a>파생 계층의 수준을 숨기거나 삭제하려면  
  
1.  [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]에서 **시스템 관리**를 클릭합니다.  
  
2.  메뉴 모음에서 **관리** 를 가리키고 **파생 계층**을 클릭합니다.  
  
3.  **파생 계층 유지 관리** 페이지의 **모델** 목록에서 모델을 선택합니다.  
  
4.  편집하려는 파생 계층의 행을 선택합니다.  
  
5.  **편집**을 클릭합니다.  
  
6.  **현재 수준** 창에서 다음을 수행합니다.  
  
    -   수준을 숨기려면 맨 위 또는 맨 아래 수준 외의 수준을 클릭합니다. **표시** 목록에서 **아니요**를 선택하고 **선택한 계층 항목 저장**을 클릭합니다.  
  
    -   최상위 수준을 삭제하려면 **선택한 계층 항목 삭제**를 클릭합니다. 확인 대화 상자에서 **확인**을 클릭합니다. 최상위 수준만 삭제할 수 있습니다.  
  
## <a name="see-also"></a>참고 항목  
    
 [파생 계층&#40;Master Data Services&#41;](../master-data-services/derived-hierarchies-master-data-services.md)  
  
  
