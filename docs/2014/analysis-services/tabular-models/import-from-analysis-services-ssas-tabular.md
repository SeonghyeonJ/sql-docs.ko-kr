---
title: Analysis Services에서 가져오기 (SSAS 테이블 형식) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: b9a21b23-3a06-4ef8-bc06-9c79cdc54870
author: minewiskan
ms.author: owend
ms.openlocfilehash: 0c0a07a1822bc01e4ce5048a48b754ae0ea10d2e
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84938864"
---
# <a name="import-from-analysis-services-ssas-tabular"></a>Analysis Services에서 가져오기(SSAS 테이블 형식)
  이 항목에서는 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]의 서버에서 가져오기 프로젝트 템플릿을 사용하여 기존 테이블 형식 모델에서 메타데이터를 가져와서 새로운 테이블 형식 모델 프로젝트를 만드는 방법에 대해 설명합니다.  
  
## <a name="create-a-new-model-by-importing-metadata-from-an-existing-model-in-analysis-services"></a>Analysis Services의 기존 모델에서 메타데이터를 가져와서 새 모델 만들기  
 서버에서 가져오기 프로젝트 템플릿을 사용하여 Analysis Services 서버의 기존 테이블 형식 모델에서 메타데이터를 복사하여 새로운 테이블 형식 모델 프로젝트를 만들 수 있습니다. 메타데이터를 가져온 모델과 동일한 데이터 원본 연결, 테이블, 관계, 측정값, KPI, 역할, 계층, 큐브 뷰 및 파티션을 사용하여 새 프로젝트가 만들어집니다. 하지만 데이터는 기존 모델에서 새 모델 작업 영역으로 복사되지 않습니다. 가져오기 프로세스가 완료되고 새 모델 프로젝트가 만들어지면 모두 처리를 실행하여 데이터 원본에서 새 모델 프로젝트 작업 영역 데이터베이스로 데이터를 로드해야 합니다.  
  
#### <a name="to-create-a-new-model-by-importing-metadata-from-an-existing-model"></a>기존 모델에서 메타데이터를 가져와서 새 모델을 만들려면  
  
1.  [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]의 **파일** 메뉴에서 **새로 만들기**를 클릭한 다음 **프로젝트**를 클릭합니다.  
  
2.  **새 프로젝트** 대화 상자의 **설치된 템플릿**에서 **비즈니스 인텔리전스**를 클릭한 다음 **서버에서 가져오기**를 클릭합니다.  
  
3.  **이름**에 프로젝트의 이름을 입력하고 위치 및 솔루션 이름을 지정한 다음 **확인**을 클릭합니다.  
  
4.  **Analysis Services에서 가져오기** 대화 상자의 **서버 이름**에서 가져올 모델 메타데이터가 포함된 Analysis Services 서버의 이름을 지정합니다.  
  
5.  **데이터베이스 이름**에서 가져올 모델 메타데이터가 포함된 테이블 형식 model 데이터베이스를 선택한 다음 **확인**을 클릭합니다.  
  
## <a name="see-also"></a>참고 항목  
 [프로젝트 속성&#40;SSAS 테이블 형식&#41;](properties-ssas-tabular.md)  
  
  
