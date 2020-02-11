---
title: 비즈니스 규칙 적용(Excel용 MDS 추가 기능) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: cd106345-f561-4966-88d3-a69139b2bd78
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 32819a694769092c255c4b2ed918dd8fde99362e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2020
ms.locfileid: "65482599"
---
# <a name="apply-business-rules-mds-add-in-for-excel"></a>비즈니스 규칙 적용(Excel용 MDS 추가 기능)
  
  [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)]
  [!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)] 에서는 데이터의 유효성을 검사하고 데이터가 유효한지 확인하려는 경우에 비즈니스 규칙을 적용합니다. 유효성 검사를 수정하고 데이터를 다시 게시할 수 있습니다.  
  
> [!NOTE]  
>  데이터 유효성 검사는 데이터를 게시할 때 자동으로 수행됩니다. 자세한 내용은 [유효성 검사 저장 프로시저&#40;Master Data Services&#41;](../validation-stored-procedure-master-data-services.md)를 참조하세요.  
  
## <a name="prerequisites"></a>사전 요구 사항  
 이 절차를 수행하려면  
  
-   
  **탐색기** 기능 영역에 대한 액세스 권한이 있어야 합니다.  
  
-   MDS 관리 데이터가 포함된 활성 워크시트가 있어야 합니다.  
  
### <a name="to-apply-business-rules"></a>비즈니스 규칙을 적용하려면  
  
1.  
  **게시 및 유효성 검사** 그룹에서 **규칙 적용**을 클릭합니다.  
  
    > [!NOTE]  
    >  한 번에 유효성이 검사되는 멤버(행) 수는 [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)]의 설정에 따라 달라집니다. 자세한 내용은 [Business Rule Settings](../system-settings-master-data-services.md#BusinessRules)을 참조하세요.  
  
2.  비즈니스 규칙에 따라 데이터의 유효성을 검사하고 두 개의 상태 열이 표시됩니다. 이러한 열은 자동으로 표시되지 않으며, 열을 표시하려면 **게시 및 검증** 그룹에서 **상태 표시** 를 클릭합니다.  
  
## <a name="see-also"></a>참고 항목  
 [데이터 &#40;Excel용 MDS 추가 기능&#41;게시](overview-importing-data-from-excel-mds-add-in-for-excel.md)  
  
  
