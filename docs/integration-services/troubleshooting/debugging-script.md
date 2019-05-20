---
title: 스크립트 디버깅 | Microsoft Docs
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Script task [Integration Services], debugging
- debugging [Integration Services], scripts
- scripts [Integration Services], debugging
ms.assetid: fddf57d8-8607-4f88-85a0-1b683087b491
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: b0b038e81c70e3368e9f66c6dfefc925e282b27d
ms.sourcegitcommit: fd71d04a9d30a9927cbfff645750ac9d5d5e5ee7
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/16/2019
ms.locfileid: "65713744"
---
# <a name="debugging-script"></a>스크립트 디버깅

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  VSTA( [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Tools for Applications)에서 스크립트 태스크 및 스크립트 구성 요소에 사용할 스크립트를 작성할 수 있습니다.  
  
 VSTA에서 중단점을 설정하고 스크립팅합니다. VSTA에서 중단점을 관리할 수 있지만 **디자이너에서 제공하는** 중단점 설정 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 대화 상자를 사용하여 중단점을 관리할 수도 있습니다. 자세한 내용은 [Debugging Control Flow](../../integration-services/troubleshooting/debugging-control-flow.md)을 참조하세요.  
  
 **중단점 설정** 대화 상자에는 스크립트 중단점이 포함됩니다. 이러한 중단점은 중단점 목록의 아래에 표시되며, 중단점이 나타나는 함수의 이름과 줄 번호를 표시합니다. **중단점 설정** 대화 상자에서 스크립트 중단점을 삭제할 수 있습니다.  
  
 런타임 시 스크립트의 코드 줄에 설정된 중단점은 패키지 또는 패키지의 태스크 및 컨테이너에 설정된 중단점과 통합됩니다. 디버거는 스크립트의 특정 중단점에서부터 패키지, 태스크 및 컨테이너의 중단점까지 또는 그 반대로 실행할 수 있습니다. 예를 들어 패키지에서 **OnPreExecute** 및 **OnPostExecute** 이벤트를 받을 때 발생하는 중단 조건으로 설정된 중단점이 패키지에 포함되고, 스크립트의 줄에 중단점이 있는 스크립트 태스크가 있을 수 있습니다. 이 경우 패키지는 **OnPreExecute** 이벤트와 연결된 중단 조건에 따라 실행을 일시 중지하고, 스크립트의 중단점까지 실행한 다음 마지막으로, **OnPostExecute** 이벤트와 연결된 중단 조건까지 실행할 수 있습니다.  
  
 스크립트 태스크 및 스크립트 구성 요소를 디버깅하는 방법은 [Coding and Debugging the Script Task](../../integration-services/extending-packages-scripting/task/coding-and-debugging-the-script-task.md) 및 [Coding and Debugging the Script Component](../../integration-services/extending-packages-scripting/data-flow-script-component/coding-and-debugging-the-script-component.md)을 참조하십시오.  
  
### <a name="to-set-a-breakpoint-in-visual-studio-for-applications"></a>Visual Studio for Applications에서 중단점을 설정하려면  
  
-   [스크립트 태스크 및 스크립트 구성 요소에서 중단점을 설정하여 스크립트 디버깅](../../integration-services/extending-packages-scripting/debug-a-script-by-setting-breakpoints-in-a-script-task-and-script-component.md)  
  
## <a name="see-also"></a>참고 항목  
 [패키지 배포 문제 해결 도구](../../integration-services/troubleshooting/troubleshooting-tools-for-package-development.md)  
  
  
