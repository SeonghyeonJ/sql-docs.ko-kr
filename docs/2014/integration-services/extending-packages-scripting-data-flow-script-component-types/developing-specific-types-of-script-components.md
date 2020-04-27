---
title: 특정 유형의 스크립트 구성 요소 개발 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- Script component [Integration Services], examples
ms.assetid: dfbbe959-6b4e-4b47-b9dd-bcc31929482d
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: e0a811b88537d784c9e1db892003391914d50f5d
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/26/2020
ms.locfileid: "62895183"
---
# <a name="developing-specific-types-of-script-components"></a>특정 유형의 스크립트 구성 요소 개발
  스크립트 구성 요소는 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]에 포함된 원본, 변환 및 대상이 충족시키지 않는 거의 모든 요구 사항을 충족시키기 위해 패키지의 데이터 흐름에서 사용할 수 있는 구성 가능한 도구입니다. 이 섹션에는 스크립트 구성 요소를 구성하는 네 가지 옵션을 보여 주는 스크립트 구성 요소 코드 예제가 들어 있습니다.  
  
-   원본으로 구성  
  
-   동기 출력을 사용하는 변환으로 구성  
  
-   비동기 출력을 사용하는 변환으로 구성  
  
-   대상으로 구성  
  
 스크립트 구성 요소에 대한 추가 예제는 [추가 스크립트 구성 요소 예](../extending-packages-scripting-data-flow-script-component-examples/additional-script-component-examples.md)를 참조하세요.  
  
## <a name="in-this-section"></a>섹션 내용  
 [스크립트 구성 요소를 사용하여 원본 만들기](creating-a-source-with-the-script-component.md)  
 스크립트 구성 요소를 사용하여 데이터 흐름 원본을 만드는 방법을 설명하고 예로 보여 줍니다.  
  
 [스크립트 구성 요소를 사용하여 동기 변환 만들기](creating-a-synchronous-transformation-with-the-script-component.md)  
 스크립트 구성 요소를 사용하여 동기 출력을 사용하는 데이터 흐름 변환을 만드는 방법을 설명하고 예로 보여 줍니다. 이러한 종류의 변환에서는 데이터 행이 구성 요소를 통해 전달될 때 현재 위치에서 해당 행을 수정합니다.  
  
 [스크립트 구성 요소를 사용하여 비동기 변환 만들기](../extending-packages-scripting-data-flow-script-component-types/creating-an-asynchronous-transformation-with-the-script-component.md)  
 스크립트 구성 요소를 사용하여 비동기 출력을 사용하는 데이터 흐름 변환을 만드는 방법을 설명하고 예로 보여 줍니다. 이러한 종류의 변환에서는 모든 데이터 행을 읽은 후에만 계산된 집계와 같은 추가 정보를 구성 요소를 통해 전달되는 데이터에 추가할 수 있습니다.  
  
 [스크립트 구성 요소를 사용하여 대상 만들기](../extending-packages-scripting-data-flow-script-component-types/creating-a-destination-with-the-script-component.md)  
 스크립트 구성 요소를 사용하여 데이터 흐름 대상을 만드는 방법을 설명하고 예로 보여 줍니다.  
  
![Integration Services 아이콘 (작은 아이콘)](../media/dts-16.gif "Integration Services 아이콘(작은 아이콘)")  **은 최신 상태로 유지 Integration Services**<br /> Microsoft의 최신 다운로드, 문서, 예제 및 비디오와 커뮤니티에서 선택된 솔루션을 보려면 MSDN의 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 페이지를 방문하세요.<br /><br /> [MSDN의 Integration Services 페이지를 방문하세요.](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> 이러한 업데이트에 대한 자동 알림을 받으려면 해당 페이지에서 제공하는 RSS 피드를 구독하세요.  
  
## <a name="see-also"></a>참고 항목  
 [스크립팅 솔루션과 사용자 지정 개체 비교](../extending-packages-scripting/comparing-scripting-solutions-and-custom-objects.md)   
 [특정 유형의 데이터 흐름 구성 요소 개발](../extending-packages-custom-objects-data-flow-types/developing-specific-types-of-data-flow-components.md)  
  
  
