---
title: 원시 파일 대상 편집기 (연결 관리자 페이지) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.rawfiledestinationconnectionmanager.f1
ms.assetid: a0ec9643-3b44-4467-b855-f45ae4794f7f
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 2677d0dd1f4697177171ba0edd4641ec02110310
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/26/2020
ms.locfileid: "66056573"
---
# <a name="raw-file-destination-editor-connection-manager-page"></a>원시 파일 대상 편집기(연결 관리자 페이지)
  원시 파일 대상 편집기를 사용하여 원시 데이터를 파일에 기록하도록 원시 파일 대상을 구성합니다.  
  
 **수행 작업**  
  
-   [원시 파일 대상 편집기 열기](#open)  
  
-   [연결 관리자 탭에서 옵션 설정](#connection)  
  
-   [열 탭에서 옵션 설정](#mapping)  
  
##  <a name="open-the-raw-file-destination-editor"></a><a name="open"></a>원시 파일 대상 편집기 열기  
  
1.  [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 에서 원시 파일 대상을 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]패키지에 추가합니다.  
  
2.  구성 요소를 마우스 오른쪽 단추로 클릭한 다음 **편집**을 클릭합니다.  
  
##  <a name="set-options-on-the-connection-manager-tab"></a><a name="connection"></a> 연결 관리자 탭에서 옵션 설정  
 **액세스 모드**  
 파일 이름 지정 방법을 선택합니다. **파일 이름** 을 선택하여 파일 이름 및 경로를 직접 입력하고 **변수를 사용한 파일 이름** 을 선택하여 파일 이름이 포함된 변수를 지정합니다.  
  
 **파일 이름** 또는 **변수 이름**  
 원시 파일의 이름과 경로를 입력하거나 파일 이름이 포함된 변수를 선택합니다.  
  
 **쓰기 옵션**  
 파일을 만들고 파일에 쓰는 데 사용할 메서드를 선택합니다.  
  
 **초기 원시 파일 생성**  
 패키지를 실행할 필요 없이 열만 포함된 빈 원시 파일(메타데이터 전용 파일)을 생성하려면 단추를 클릭합니다. 파일에는 **원시 파일 대상 편집기** 의 **열**페이지에서 선택한 열이 포함됩니다. 원시 파일 원본이 이 메타데이터 전용 파일을 가리키도록 설정할 수 있습니다.  
  
 **초기 원시 파일 생성**을 누르면 메시지 상자가 표시됩니다. **확인** 을 클릭하여 파일 만들기를 계속합니다. **열** 페이지의 서로 다른 열 목록을 선택하려면 **취소** 를 클릭합니다.  
  
##  <a name="set-options-on-the-columns-tab"></a><a name="mapping"></a>열 탭에서 옵션 설정  
 **사용 가능한 입력 열**  
 원시 파일에 쓸 하나 이상의 입력 열을 선택합니다.  
  
 **입력 열**  
 입력 열은 **사용 가능한 입력 열**에서 선택할 경우 이 테이블에 자동으로 추가되거나 이 테이블에서 입력 열을 직접 선택할 수 있습니다.  
  
 **출력 별칭**  
 출력 열에 사용할 대체 이름을 지정합니다.  
  
## <a name="see-also"></a>참고 항목  
 [Raw File Destination](data-flow/raw-file-destination.md)  
  
  
