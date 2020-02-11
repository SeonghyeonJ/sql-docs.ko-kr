---
title: 새 관계형 마이닝 구조 만들기 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining structures [Analysis Services], relational
- mining structures [Analysis Services], creating
- relational mining models [Analysis Services]
ms.assetid: 55bac3bd-700e-4f91-bcc6-f3cd8c026da1
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: b4ec4bc871723b829d9ce9ec805d4b52b1c649e8
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66085385"
---
# <a name="create-a-new-relational-mining-structure"></a>새 관계형 마이닝 구조 만들기
  데이터 마이닝 마법사를 사용 하 여 관계형 데이터베이스 또는 기타 원본의 데이터를 사용 하 여 새 마이닝 구조를 만든 다음 구조와 모든 관련 모델을 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 데이터베이스에 저장할 수 있습니다.  
  
### <a name="to-create-a-relational-mining-structure"></a>관계형 마이닝 구조를 만들려면  
  
1.  솔루션 탐색기에서 **프로젝트의** 마이닝 구조 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 폴더를 마우스 오른쪽 단추로 클릭하고 **새 마이닝 구조**를 클릭합니다.  
  
     데이터 마이닝 마법사가 열립니다.  
  
2.  
  **데이터 마이닝 마법사 시작** 페이지에서 **다음**을 클릭합니다.  
  
3.  
  **정의 방법 선택** 페이지에서 **기존 관계형 데이터베이스 또는 데이터 웨어하우스 사용**을 선택하고 **다음**을 클릭합니다.  
  
4.  
  **데이터 마이닝 기술 선택** 페이지에서 사용할 데이터 마이닝 알고리즘을 선택하고 **다음**을 클릭합니다.  
  
     데이터 마이닝 알고리즘에 대한 자세한 내용은 [데이터 마이닝 알고리즘&#40;Analysis Services - 데이터 마이닝&#41;](data-mining-algorithms-analysis-services-data-mining.md)을 참조하세요.  
  
5.  
  **데이터 원본 뷰 선택** 페이지의 **사용 가능한 데이터 원본 뷰**에서 사용할 데이터 원본 뷰를 클릭하고 **다음**을 클릭합니다.  
  
     데이터 원본 뷰 만들기에 대한 자세한 내용은 [다차원 모델의 데이터 원본 뷰](../multidimensional-models/data-source-views-in-multidimensional-models.md)를 참조하세요.  
  
6.  
  **테이블 유형 지정** 페이지의 **입력 테이블**에서 사례 테이블과 중첩 테이블을 선택합니다.  
  
7.  
  **학습 데이터 지정** 페이지의 **마이닝 모델 구조**에서 키 열, 입력 열 및 예측 가능한 열을 선택합니다.  
  
     예측 가능한 열을 선택한 후 **제안** 단추를 클릭하여 **관련 열 제안** 대화 상자를 열 수 있습니다. 선택한 열이 마이닝 구조에 포함되도록 이 대화 상자에서 **확인** 을 클릭하여 제안된 열을 적용하거나 **입력** 열의 선택 내용을 변경한 후 **확인**을 클릭할 수 있습니다. 제안 사항을 무시하려면 **취소**를 클릭합니다.  
  
8.  **다음**을 클릭합니다.  
  
9. 
  **열 내용 및 데이터 형식 지정** 페이지의 **마이닝 모델 구조**에서 각 열의 내용 유형과 데이터 형식을 조정할 수 있습니다.  
  
    > [!NOTE]  
    >  
  **검색** 을 클릭하여 열에 포함된 데이터가 연속 데이터인지 비연속 데이터인지 자동으로 검색할 수 있습니다. 이 단추를 클릭하면 **내용 유형** 열과 **데이터 형식** 열에서 열 내용 유형과 열 데이터 형식이 업데이트됩니다. 콘텐츠 형식 및 데이터 형식에 대한 자세한 내용은 [콘텐츠 형식&#40;데이터 마이닝&#41;](content-types-data-mining.md) 및 [데이터 형식&#40;데이터 마이닝&#41;](data-types-data-mining.md)을 참조하세요.  
  
10. **다음**을 클릭합니다.  
  
11. 
  **마법사 완료** 페이지에서 마이닝 구조의 이름과 생성될 관련 초기 마이닝 모델을 지정하고 **마침**을 클릭합니다.  
  
## <a name="see-also"></a>참고 항목  
 [마이닝 구조 태스크 및 방법](mining-structure-tasks-and-how-tos.md)  
  
  
