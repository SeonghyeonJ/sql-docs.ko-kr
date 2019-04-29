---
title: '2단계: 패키지 구성 설정 및 구성 | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 005218ab-8dd5-48e9-a185-6bc60cd43a7a
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: fa75b3a71832eaba4064de5a9dd90e73236e8177
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62891072"
---
# <a name="step-2-enabling-and-configuring-package-configurations"></a>2단계: 패키지 구성 설정 및 구성
  이 작업에서는 프로젝트를 패키지 배포 모델로 변환하고 패키지 구성 마법사를 사용하여 패키지 구성을 설정합니다. 이 마법사를 사용하여 Foreach 루프 컨테이너의 `Directory` 속성에 대한 구성 설정을 포함하는 XML 구성 파일을 생성합니다. 런타임에 업데이트할 수 있는 새 패키지 수준 변수에서 Directory 속성 값을 제공합니다. 또한 테스트하는 동안 사용할 새로운 예제 데이터 폴더를 채웁니다.  
  
### <a name="to-create-a-new-package-level-variable-mapped-to-the-directory-property"></a>Directory 속성에 매핑되는 새 패키지 수준 변수를 만들려면  
  
1.  **디자이너에서** 제어 흐름 [!INCLUDE[ssIS](../includes/ssis-md.md)] 탭의 배경을 클릭합니다. 그러면 패키지에 만들 변수의 범위가 설정됩니다.  
  
2.  [!INCLUDE[ssIS](../includes/ssis-md.md)] 메뉴에서 **변수**를 선택합니다.  
  
3.  **변수** 창에서 변수 추가 아이콘을 클릭합니다.  
  
4.  **이름** 상자에 **varFolderName**을 입력합니다.  
  
    > [!IMPORTANT]  
    >  변수 이름은 대/소문자를 구분합니다.  
  
5.  **범위** 상자에 패키지 이름 Lesson 5가 표시되는지 확인합니다.  
  
6.  **변수의** 데이터 형식 `varFolderName` 상자 값을 **String**으로 설정합니다.  
  
7.  **제어 흐름** 탭으로 돌아가 **Foreach File in Folder** 컨테이너를 두 번 클릭합니다.  
  
8.  **Foreach 루프 편집기**의 **컬렉션** 페이지에서 **Expressions**를 클릭한 다음, 줄임표 단추 **(...)** 를 클릭합니다.  
  
9. 에 **속성 식 편집기**, 클릭 합니다 **속성** 목록에서 선택한 `Directory`.  
  
10. 에 **식을** 상자에서 줄임표 단추를 클릭 **(...)** .  
  
11. **식 작성기**에서 변수 폴더를 확장하고 **User::varFolderName** 변수를 **식** 상자로 끕니다.  
  
12. **확인** 을 클릭하여 **식 작성기**를 종료합니다.  
  
13. **확인** 을 클릭하여 **속성 식 편집기**를 종료합니다.  
  
14. **확인** 을 클릭하여 **For 루프 편집기**를 끝냅니다.  
  
### <a name="to-enable-package-configurations"></a>패키지 구성을 설정하려면  
  
1.  **프로젝트 메뉴**에서 **패키지 배포 모델로 변환**을 클릭합니다.  
  
2.  경고 프롬프트에서 **확인** 을 클릭하고 변환이 완료되면 **패키지 배포 모델로 변환** 대화 상자에서 **확인** 을 클릭합니다.  
  
3.  [!INCLUDE[ssIS](../includes/ssis-md.md)] 디자이너에서 **제어 흐름** 탭의 배경을 클릭합니다.  
  
4.  **SSIS** 메뉴에서 **패키지 구성**을 클릭합니다.  
  
5.  **패키지 구성 도우미** 대화 상자에서 **패키지 구성 설정**을 선택한 다음 **추가**를 클릭합니다.  
  
6.  패키지 구성 마법사 시작 페이지에서 **다음**을 클릭합니다.  
  
7.  **구성 유형 선택** 페이지에서 **구성 유형** 이 **XML 구성 파일**로 설정되었는지 확인합니다.  
  
8.  **구성 유형 선택** 페이지에서 **찾아보기**를 클릭합니다.  
  
9. 기본적으로 **구성 파일 위치 선택** 대화 상자가 프로젝트 폴더에 대해 열립니다.  
  
10. **구성 파일 위치 선택** 대화 상자에서 **파일 이름** 에 **SSISTutorial**을 입력한 다음 **저장**을 클릭합니다.  
  
11.  **구성 유형 선택** 페이지에서 **다음**을 클릭합니다.  
  
12. **내보낼 속성 선택** 페이지의 **개체** 창에서 **변수**, **varFolderName**, **Properties**를 차례로 확장한 다음 **값**을 선택합니다.  
  
13. **내보낼 속성 선택** 페이지에서 **다음**을 클릭합니다.  
  
14. **마법사 완료** 페이지에서 **SSIS Tutorial Directory configuration**등의 구성 이름을 입력합니다. 이 구성 이름은 **패키지 구성 도우미** 대화 상자에 표시됩니다.  
  
15. **마침**을 클릭합니다.  
  
16. **닫기**를 클릭합니다.  
  
17. 마법사에 대 한 구성 설정을 포함 하는 ssistutorial.dtsconfig 구성 파일을 만듭니다는 `value` 설정 하는 변수는 `Directory` 열거자의 속성입니다.  
  
    > [!NOTE]  
    >  일반적으로 구성 파일에는 패키지 속성에 대한 복잡한 정보가 있지만 이 자습서에서는 구성 정보만 있어야 합니다.  
    > <Configuration ConfiguredType="Property"  
    > Path="\Package.Variables[User::varFolderName].Properties[Value]" ValueType="String"\>  
    >  \<ConfiguredValue>\</ConfiguredValue>  
    > \</ 구성 >.  
  
### <a name="to-create-and-populate-a-new-sample-data-folder"></a>새 예제 데이터 폴더를 만들고 채우려면  
  
1.  드라이브의 루트 수준에서 Windows 탐색기에서 (예: c:\\)를 라는 새 폴더를 만듭니다 `New Sample Data`합니다.  
  
2.  컴퓨터에서 예제 파일을 찾아 폴더에서 3개의 파일을 복사합니다.  
  
3.  에 `New Sample Data` 폴더에 복사한 파일을 붙여넣습니다.  
  
## <a name="next-task-in-lesson"></a>단원의 다음 태스크  
 [3단계: Directory 속성 구성 값 수정](lesson-5-3-modifying-the-directory-property-configuration-value.md)  
  
  
