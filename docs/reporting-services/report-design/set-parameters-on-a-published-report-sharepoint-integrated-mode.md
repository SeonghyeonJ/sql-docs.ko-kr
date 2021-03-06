---
title: 게시된 보고서에 매개 변수 설정 - SharePoint 통합 모드 | Microsoft Docs
description: 보고서 작성기에서 보고서를 게시한 후 또는 보고서 정의에서 매개 변수를 설정하고 매개 변수가 있는 보고서를 실행하는 방법을 알아봅니다.
ms.date: 03/07/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-design
ms.topic: conceptual
helpviewer_keywords:
- SharePoint integration [Reporting Services], content management
- report parameters [Reporting Services]
ms.assetid: dec5d985-a6c1-4dd8-8a66-a848e89a2e18
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: a04058cc679d7697f2526c85b8b6526e8ea4a8ce
ms.sourcegitcommit: 02b22274da4a103760a376c4ddf26c4829018454
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/11/2020
ms.locfileid: "84681222"
---
# <a name="set-parameters-on-a-published-report---sharepoint-integrated-mode"></a>게시된 보고서에 매개 변수 설정 - SharePoint 통합 모드
  매개 변수가 있는 보고서는 보고서 실행 시 데이터를 필터링하는 데 사용되는 입력 값을 받아들이는 보고서입니다. 매개 변수는 보고서를 만들 때 정의됩니다. 보고서 매개 변수는 보고서 정의에 정의된 방식에 따라 단일 값, 다중 값 또는 동적 값을 받아들일 수 있습니다. 여기서 동적 값은 이전 선택 사항에 따라 변경되는 값입니다. 예를 들어 제품 범주를 선택하면 다음 선택 사항은 해당 범주에 속한 특정 제품이 될 수 있습니다. 매개 변수에는 기본값을 지정할 수 있으며 이 값을 사용하여 자동으로 보고서의 필터링된 버전을 실행하거나 해당 값을 다른 값으로 바꿀 수 있습니다.  
  
 이러한 속성은 보고서 정의에 설정하거나 보고서가 게시된 후 설정할 수 있습니다. 게시된 보고서에서 일부 매개 변수 속성을 수정하여 값과 표시 속성을 변경할 수 있지만 매개 변수 이름이나 데이터 형식은 변경할 수 없습니다. 매개 변수 이름과 데이터 형식은 보고서 작성자가 보고서 정의에서만 변경할 수 있습니다.  
  
 매개 변수가 있는 보고서를 실행하려면 선택할 유효한 값 드롭다운 목록이 보고서에 포함되어 있는 경우에도 입력할 값을 알고 있어야 하는 경우가 많습니다.  
  
 게시된 보고서에 매개 변수 속성을 설정하려면 해당 보고서에 대한 항목 편집 권한이 있어야 합니다. SharePoint 사이트에서 실행하는 보고서의 매개 변수 속성을 일부 또는 모두 수정할 수 있습니다. 반복해서 사용하려는 매개 변수 값 조합을 저장하여 보고서를 개인 설정할 수는 없습니다. 지정한 기본값은 보고서를 여는 모든 사용자에 의해 사용됩니다.  
  
 보고서를 항상 표시하도록 구성된 보고서 뷰어 웹 파트에 보고서가 포함되어 있는 경우에는 보고서 뷰어 웹 파트에서 속성을 설정하십시오. 자세한 내용은 [웹 페이지에 보고서 뷰어 웹 파트 추가&#40;SharePoint 통합 모드의 Reporting Services&#41;](../../reporting-services/report-server-sharepoint/add-the-report-viewer-web-part-to-a-web-page.md)를 참조하세요.  
  
### <a name="to-run-a-parameterized-report"></a>매개 변수가 있는 보고서를 실행하려면  
  
1.  보고서가 포함된 라이브러리를 엽니다.  
  
2.  보고서 이름을 클릭합니다. 매개 변수가 있는 보고서를 미리 알고 있어야 합니다. 보고서에 매개 변수가 있다는 사실이 시각적으로 표시되지는 않습니다.  
  
3.  보고서가 열리면 사용할 매개 변수를 지정합니다. 매개 변수 영역은 보고서 뷰어 웹 파트에 속성이 설정된 방식에 따라 표시 또는 축소되거나 숨겨질 수 있습니다.  
  
    1.  매개 변수 영역이 표시되어 있으면 각 매개 변수의 값을 선택합니다.  
  
    2.  보고서의 위에서 아래까지 이어지고 가운데에 화살표가 있는 가는 색 줄이 있으면 매개 변수 영역이 축소된 것입니다. 화살표를 클릭하여 해당 영역을 확장할 수 있습니다.  
  
    3.  매개 변수 영역이 숨겨져 있으면 값을 지정할 수 없습니다.  
  
4.  매개 변수 영역의 아래쪽에서 **적용** 을 클릭하여 보고서를 실행합니다.  
  
     지정한 값 조합이 원하는 결과를 제공하지 않을 수 있으며 이렇게 필요한 정보를 얻을 수 없는 경우 보고서 작성자가 보고서를 수정해야 할 수 있습니다.  
  
5.  **확인**을 클릭합니다.  
  
### <a name="to-set-parameter-properties"></a>매개 변수 속성을 설정하려면  
  
1.  보고서가 포함된 라이브러리나 폴더를 엽니다.  
  
2.  보고서를 가리키고 아래쪽 화살표를 클릭합니다.  
  
3.  **매개 변수 관리**를 클릭합니다. 보고서에 매개 변수가 포함되어 있으면 각 매개 변수가 페이지에 나열됩니다. 이 목록에는 매개 변수 이름, 데이터 형식, 기본적으로 사용되는 데이터 값 및 보고서를 열 때 이 값이 매개 변수 영역에 나타나는지 여부가 표시됩니다.  
  
4.  목록에서 매개 변수를 클릭하여 해당 설정을 수정합니다.  
  
5.  기본값에 매개 변수의 값을 입력합니다. 값의 유효성은 검사되지 않으므로 보고서에 유효한 값을 제공해야 합니다.  
  
    1.  보고서를 만들 때 정의한 기본값을 사용하려면 **보고서에 지정된 값 식 사용** 을 선택합니다. 보고서 정의에 기본값이 제공되어 있지 않으면 이 옵션을 사용할 수 없습니다.  
  
    2.  보고서 정의 기본값을 대체할 값을 지정하려면 **보고서 기본값 다시 정의** 를 선택합니다. Null 값을 허용하는 보고서 매개 변수에 대해 필요에 따라 **Null** 확인란을 선택하여 해당 매개 변수를 기반으로 필터링되지 않도록 할 수 있습니다.  
  
    3.  보고서가 처리되기 전에 각 사용자가 값을 지정하도록 하려면 **기본값 사용 안 함** 을 선택합니다. 이 옵션을 선택하는 경우 사용자에게 값을 지정하라는 메시지를 나타내는 표시 설정을 지정해야 합니다.  
  
     모든 매개 변수 값에 기본값이 있으면 사용자가 보고서를 열 때 해당 값을 사용하여 자동으로 보고서가 실행됩니다. 그러나 매개 변수 영역이 표시되면 사용자가 기본값을 다시 정의하고 보고서를 다시 실행할 수 있습니다.  
  
6.  표시 옵션을 설정하여 매개 변수를 표시할지 여부를 결정합니다.  
  
    1.  페이지에 매개 변수를 표시하려면 **사용자에게 확인** 을 선택합니다. 사용자가 제공해야 하는 데이터 형식에 대해 간단히 설명하는 프롬프트 텍스트를 지정하여 필드 내에 표시할 수 있습니다.  
  
    2.  기본값을 사용하고 매개 변수 영역에 매개 변수를 표시하지 않으려면 **숨김** 을 선택합니다.  
  
    3.  기본값을 사용하고 매개 변수 영역이나 구독 페이지에 매개 변수를 표시하지 않으려면 **내부** 를 선택합니다.  
  
7.  **적용**을 클릭합니다.  
  
## <a name="see-also"></a>참고 항목  
 [보고서 서버 항목에 대한 SharePoint 사이트 및 목록 사용 권한 참조](../../reporting-services/security/sharepoint-site-and-list-permission-reference-for-report-server-items.md)  
  
  
