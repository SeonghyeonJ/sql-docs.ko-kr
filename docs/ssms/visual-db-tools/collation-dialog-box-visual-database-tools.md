---
title: 데이터 정렬 대화 상자
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- vdt.dlgbox.definecolumncollation
- vdtsql.chm:65561
ms.assetid: e4020f79-7abf-4839-b9b2-984ef7049817
author: markingmyname
ms.author: maghan
ms.manager: jroth
ms.reviewer: ''
ms.openlocfilehash: 1c926bd77ab1fd2abf048c15d93b8935b2ed679d
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/31/2020
ms.locfileid: "75255481"
---
# <a name="collation-dialog-box-visual-database-tools"></a>데이터 정렬 대화 상자(Visual Database Tools)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
이 대화 상자를 사용하면 열의 데이터 정렬 순서를 지정할 수 있습니다. 열의 데이터 정렬 순서는 열의 값을 다른 열이나 상수 값과 비교하는 모든 작업에 사용됩니다. 이 순서는 SUBSTRING 및 CHARINDEX 등과 같은 일부 문자열 함수의 동작에도 영향을 줍니다. 열의 데이터 정렬 순서 설정이 미치는 영향에 대한 전체 목록은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 설명서를 참조하십시오.  
  
이 대화 상자는 다음과 같은 경우에 나타납니다.  
  
-   **열 속성** 탭의 **데이터 정렬** 필드에 잘못된 데이터 정렬 이름을 입력한 경우  
  
-   **열 속성** 탭의 **데이터 정렬** 필드를 클릭한 다음, 필드의 오른쪽에 있는 줄임표 단추( **...** )를 클릭한 경우  
  
## <a name="options"></a>옵션  
**SQL 데이터 정렬**  
드롭다운 목록의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에 정의되어 있는 데이터 정렬 순서 중에서 하나를 선택합니다.  
  
**Windows 데이터 정렬**  
드롭다운 목록의 Windows에 정의되어 있는 데이터 정렬 순서 중에서 하나를 선택합니다.  
  
**이진 정렬**  
문자 값의 이진 코드를 사용하여 비교하려는 경우에 선택합니다. 이 옵션을 선택하면 특정 영문자 비교 옵션을 사용할 수 없게 됩니다. 예를 들어, 대문자와 소문자는 이진 인코딩이 서로 다르므로 대/소문자를 구분하지 않고 비교하는 옵션을 사용할 수 없습니다. **Windows 데이터 정렬**을 선택한 경우에만 적용됩니다.  
  
**사전 정렬**  
영문자 비교 옵션을 사용합니다. **Windows 데이터 정렬**을 선택한 경우에만 적용됩니다. 영문자 비교 옵션은 다음과 같습니다.  
  
-   **대/소문자 구분** 대문자와 소문자를 동일하지 않은 것으로 간주하여 비교하려는 경우에 선택합니다.  
  
-   **악센트 구분** 악센트 부호가 있는 문자와 없는 문자를 동일하지 않은 것으로 간주하여 비교하려는 경우에 선택합니다. 이 옵션을 선택하면 악센트 부호가 서로 다른 방식으로 추가된 문자도 동일하지 않은 것으로 간주됩니다.  
  
-   **일본어 가나 구분** 일본어 가타카나 음절과 히라가나 음절이 동일하지 않은 것으로 간주하여 비교하려는 경우에 선택합니다.  
  
-   **전자/반자 구분** 반자 및 전자 문자가 동일하지 않은 것으로 간주하여 비교하려는 경우에 선택합니다.  
  
**기본값 복원 단추**  
데이터베이스의 기본 데이터 정렬 순서를 열에 적용합니다.  
  
## <a name="see-also"></a>참고 항목  
[집계 쿼리에서 열 작업&#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/work-with-columns-in-aggregate-queries-visual-database-tools.md)  
  
