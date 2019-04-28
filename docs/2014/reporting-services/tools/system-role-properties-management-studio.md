---
title: 시스템 역할 속성(Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.swb.reportserver.systemroleproperties.f1
ms.assetid: 0210fc2a-74fb-41dd-8e39-4830047ec417
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 84c201e4370adafbd944ba803326d5b97e11e42a
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62634515"
---
# <a name="system-role-properties-management-studio"></a>시스템 역할 속성(Management Studio)
  시스템 역할 페이지를 사용하여 보고서 서버에 현재 정의되어 있는 시스템 역할 정의를 볼 수 있습니다. 시스템 역할 정의에는 개별 항목이 아닌 전체 사이트에 대해 수행되는 태스크의 명명된 모음이 포함됩니다. 역할 정의는 사용자나 그룹에 할당되어 역할 할당을 만듭니다. 역할 정의의 태스크는 사용자나 그룹이 수행할 수 있는 태스크를 지정합니다.  
  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 두 개의 미리 정의 된 시스템 역할 정의 있습니다. **시스템 관리자** 하 고 **시스템 사용자**합니다. 태스크 목록을 변경하여 이러한 역할 정의를 수정하거나 다른 태스크 조합을 지원하는 새 시스템 역할을 만들 수 있습니다. 역할 정의를 편집하면 역할 정의를 포함하는 모든 역할 할당에 영향을 줍니다.  
  
> [!NOTE]  
>  시스템 역할 할당은 기본 모드로 실행되는 보고서 서버에만 사용됩니다. 보고서 서버가 SharePoint 통합 모드로 구성된 경우 이 페이지를 사용할 수 없습니다.  
  
## <a name="options"></a>변수  
 **이름**  
 시스템 역할 정의 이름을 지정합니다.  
  
 **설명**  
 시스템 역할 정의에 대한 설명을 보여 줍니다.  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]에서 이 설명은 이 페이지에만 표시됩니다. 보고서 관리자를 통해 이 항목을 보는 사용자는 폴더 계층을 검색할 때 이 설명을 볼 수 있습니다.  
  
 **태스크**  
 이 역할 정의에 대해 선택할 수 있는 시스템 수준 태스크를 모두 나열합니다. 미리 정의된 태스크 목록에서 항목을 추가 또는 제거하여 사용자가 이 역할을 통해 지정된 항목에 액세스하는 방법을 정의할 수 있습니다. 새 태스크를 만들거나 기존 작업을 수정할 수 없습니다.  
  
 **설명**  
 각 태스크에 대한 정보를 제공합니다. 태스크 설명은 수정할 수 없습니다.  
  
## <a name="see-also"></a>관련 항목  
 [Management Studio의 보고서 서버 F1 도움말](report-server-in-management-studio-f1-help.md)   
 [시스템 수준 태스크](../security/tasks-and-permissions-system-level-tasks.md)   
 [태스크 및 권한](../security/tasks-and-permissions.md)   
 [미리 정의된 역할](../security/role-definitions-predefined-roles.md)  
  
  
