---
title: '5단계: 플랫 파일 원본 추가 및 구성 | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 5c95ce51-e0fe-4fc5-95eb-2945929f2b13
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 32b95a5d156ae52394b7128b024c86b9a7e308b1
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/26/2020
ms.locfileid: "62891541"
---
# <a name="step-5-adding-and-configuring-the-flat-file-source"></a>5단계: 플랫 파일 원본 추가 및 구성
  이 태스크에서는 플랫 파일 원본을 패키지에 추가하고 구성하는 방법에 대해 설명합니다. 플랫 파일 원본은 플랫 파일 연결 관리자에서 정의된 메타데이터를 사용하여 변환 프로세스를 통해 플랫 파일에서 추출할 데이터 구조와 형식을 지정하는 데이터 흐름 구성 요소입니다. 플랫 파일 원본은 플랫 파일 연결 관리자에서 제공된 파일 형식 정의를 사용하여 단일 플랫 파일에서 데이터를 추출하도록 구성할 수 있습니다.  
  
 이 자습서에서는 이전에 만든 `Sample Flat File Source Data` 연결 관리자를 사용 하도록 플랫 파일 원본을 구성 합니다.  
  
### <a name="to-add-a-flat-file-source-component"></a>플랫 파일 원본 구성 요소를 추가하려면  
  
1.  데이터 흐름 태스크를 두 번 클릭 `Extract Sample Currency Data` 하거나 데이터 흐름 **탭**을 클릭 하 여 **데이터 흐름** 디자이너를 엽니다.  
  
2.  **SSIS 도구 상자**에서 **기타 원본**을 확장한 다음 **플랫 파일 원본** 을 **데이터 흐름** 탭의 디자인 화면으로 끌어다 놓습니다.  
  
3.  **데이터 흐름** 디자인 화면에서 새로 추가한 **플랫 파일 원본을**마우스 오른쪽 단추로 클릭 하 고 이름 **바꾸기**를 클릭 한 다음 이름을로 `Extract Sample Currency Data`변경 합니다.  
  
4.  플랫 파일 원본을 두 번 클릭하여 플랫 파일 원본 편집기 대화 상자를 엽니다.  
  
5.  **플랫 파일 연결 관리자** 상자에서를 선택 `Sample Flat File Source Data`합니다.  
  
6.  **열** 을 클릭하고 열 이름이 올바른지 확인합니다.  
  
7.  **확인**을 클릭합니다.  
  
8.  플랫 파일 원본을 마우스 오른쪽 단추로 클릭한 다음 **속성**을 클릭합니다.  
  
9. 속성 창에서 `LocaleID` 속성이 **영어 (미국)** 로 설정 되어 있는지 확인 합니다.  
  
## <a name="next-task-in-lesson"></a>단원의 다음 태스크  
 [6단계: 조회 변환 추가 및 구성](lesson-1-6-adding-and-configuring-the-lookup-transformations.md)  
  
## <a name="see-also"></a>참고 항목  
 [플랫 파일 원본](data-flow/flat-file-source.md)   
 [플랫 파일 연결 관리자 편집기&#40;일반 페이지&#41;](general-page-of-integration-services-designers-options.md)  
  
  
