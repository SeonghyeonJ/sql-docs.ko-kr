---
title: 모델 관리자 만들기(Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- administrators [Master Data Services], creating
ms.assetid: dae17afc-3b39-490e-b51f-2d8da26d429e
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: bccf908359fa0cb75a8ae0bcfe7a601ccbfd6618
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2020
ms.locfileid: "65483401"
---
# <a name="create-a-model-administrator-master-data-services"></a>모델 관리자 만들기(Master Data Services)
  에서 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]그룹이 나 사용자에 게 하나 이상의 모델에 있는 모든 개체에 대 한 **업데이트** 권한을 부여 하려면 모델 관리자를 만듭니다.  
  
> [!TIP]  
>  관리를 단순화하기 위해 Windows 또는 로컬 그룹을 만들고 이를 모델 관리자로 구성합니다. 그러면 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]에 액세스하지 않고 그룹에서 사용자를 추가하고 제거할 수 있습니다.  
  
## <a name="prerequisites"></a>사전 요구 사항  
 이 절차를 수행하려면  
  
-   
  **사용자 및 그룹 권한** 기능 영역에 액세스할 수 있는 권한이 있어야 합니다.  
  
-   모델 관리자여야 합니다. 자세한 내용은 [관리자&#40;Master Data Services&#41;](administrators-master-data-services.md)에 액세스하지 않고 그룹에서 사용자를 추가하고 제거할 수 있습니다.  
  
### <a name="to-create-a-model-administrator"></a>모델 관리자를 만들려면  
  
1.  
  [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]에서 **사용자 및 그룹 권한**을 클릭합니다.  
  
2.  
  **사용자** 또는 **그룹** 페이지에서 편집하려는 사용자나 그룹의 행을 선택합니다.  
  
3.  
  **선택한 사용자 편집**을 클릭합니다.  
  
4.  
  **모델** 탭을 클릭합니다.  
  
5.  또는 **모델** 목록에서 모델을 선택합니다.  
  
6.  
  **편집**을 클릭합니다.  
  
7.  사용 권한을 부여할 모델을 클릭합니다.  
  
8.  메뉴에서 **업데이트**를 선택 합니다.  
  
9. 그룹 또는 사용자를 관리자로 만들 각 모델에 대해 7단계와 8단계를 수행합니다.  
  
10. **저장**을 클릭합니다.  
  
## <a name="remarks"></a>설명  
 모델 개체 또는 계층 멤버에 다른 사용 권한을 할당하지 마십시오. 이렇게 하면 사용자가 더 이상 관리자가 아니므로 **탐색기**외의 모든 기능 영역에서 모델을 볼 수 없습니다.  
  
 한 가지 예외가 있습니다. 사용자가 **계층 멤버** 탭의 계층 **루트** 에 할당 된 **업데이트** 권한이 있는 경우 사용자는 여전히 모델 관리자로 간주 됩니다.  
  
## <a name="see-also"></a>참고 항목  
 [관리자는 MDS(Master Data Services) &#40;&#41;](administrators-master-data-services.md)   
 [모델 개체 사용 권한 할당 &#40;MDS(Master Data Services)&#41;](../../2014/master-data-services/assign-model-object-permissions-master-data-services.md)   
 [계층 멤버 권한 할당 &#40;MDS(Master Data Services)&#41;](../../2014/master-data-services/assign-hierarchy-member-permissions-master-data-services.md)   
 [모델 개체 사용 권한 &#40;MDS(Master Data Services)&#41;](../../2014/master-data-services/model-object-permissions-master-data-services.md)   
 [계층 멤버 권한 &#40;MDS(Master Data Services)&#41;](../../2014/master-data-services/hierarchy-member-permissions-master-data-services.md)  
  
  
