---
title: Analysis services에서 파워 피벗에서 가져오기 | Microsoft Docs
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 21abcfbec94808df6560af887ff0598d97fcb068
ms.sourcegitcommit: 8a64c59c5d84150659a015e54f8937673cab87a0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/08/2018
ms.locfileid: "53072380"
---
# <a name="import-from-power-pivot"></a>파워 피벗에서 가져오기 
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  이 문서에서는 메타 데이터와 데이터를 가져와서 새로운 테이블 형식 모델 프로젝트를 만드는 방법에 설명 합니다는 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 에서 가져오기를 사용 하 여 통합 문서 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 프로젝트 템플릿을 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]합니다.  
  
## <a name="create-a-new-tabular-model-from-a-power-pivot-for-excel-file"></a>Power Pivot for Excel 파일에서 새 테이블 형식 모델 만들기  
 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 통합 문서에서 가져와서 새로운 테이블 형식 모델 프로젝트를 만드는 경우 통합 문서의 구조를 정의하는 메타데이터를 사용하여 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]에서 테이블 형식 모델 프로젝트의 구조를 만들고 정의합니다. 테이블, 열, 측정값 및 관계와 같은 개체는 그대로 유지되며 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 통합 문서에 표시되는 것과 같이 테이블 형식 모델 프로젝트에 표시됩니다. .xlsx 통합 문서 파일은 변경되지 않습니다.  
  
> [!NOTE]  
>  테이블 형식 모델은 연결된 테이블을 지원하지 않습니다. 연결된 테이블이 포함된 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 통합 문서에서 가져오는 경우 연결된 테이블 데이터는 복사하여 붙여넣은 데이터로 처리되며 Model.bim 파일에 저장됩니다. 복사하여 붙여넣은 테이블의 속성을 볼 때 **원본 데이터** 속성은 비활성화되고 **테이블** 메뉴의 **테이블 속성** 대화 상자도 비활성화됩니다.  
>   
>  모델에 포함된 데이터에 추가할 수 있는 행은 최대 10,000개로 제한됩니다. 모델을 가져오는 경우 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] "데이터가 잘렸습니다 오류를 표시 합니다. 수정 해야 붙여넣은 테이블 행을 10000 개 이상 포함할 수 없습니다 "는 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] SQL Server에서 테이블과 같은 다른 데이터 원본에 포함 된 데이터를 이동 하 여 모델을 다시 가져오십시오.  
  
 작업 영역 데이터베이스가 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 와 동일한 컴퓨터(로컬)의 Analysis Services 인스턴스에 있는지, 아니면 원격 Analysis Services 인스턴스에 있는지에 따라 특별히 고려해야 할 사항이 있습니다.  
  
 작업 영역 데이터베이스가 Analysis Services의 로컬 인스턴스에 있는 경우 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 통합 문서에서 메타데이터와 데이터를 모두 가져올 수 있습니다. 메타데이터는 통합 문서에서 복사되고 테이블 형식 모델 프로젝트를 만드는 데 사용됩니다. 그런 다음 데이터 통합 문서에서 복사 하 고 (복사/붙여넣은 데이터는 Model.bim 파일에 저장 됩니다) 제외 하 고 프로젝트의 작업 영역 데이터베이스에 저장 됩니다.  
  
 작업 영역 데이터베이스가 원격 Analysis Services 인스턴스에 있는 경우 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] for Excel 통합 문서에서 데이터를 가져올 수 없습니다. 통합 문서 메타데이터를 여전히 가져올 수 있지만 이렇게 하면 스크립트가 원격 Analysis Services 인스턴스에서 실행됩니다. 신뢰할 수 있는 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 통합 문서에서만 메타데이터를 가져와야 합니다. 데이터 원본 연결에 정의된 원본에서 데이터를 가져와야 합니다. [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 통합 문서의 복사하여 붙여넣은 테이블 데이터와 연결된 테이블 데이터를 복사하여 테이블 형식 모델 프로젝트에 붙여넣어야 합니다.  
  
#### <a name="to-create-a-new-tabular-model-project-from-a-power-pivot-for-excel-file"></a>PowerPivot for Excel 파일에서 새 테이블 형식 모델 프로젝트를 만들려면  
  
1.  [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]의 **파일** 메뉴에서 **새로 만들기**를 클릭한 다음 **프로젝트**를 클릭합니다.  
  
2.  **새 프로젝트** 대화 상자의 **설치된 템플릿**에서 **비즈니스 인텔리전스**를 클릭한 다음 **[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]에서 가져오기**를 클릭합니다.  
  
3.  **이름**에 프로젝트의 이름을 입력하고 위치 및 솔루션 이름을 지정한 다음 **확인**을 클릭합니다.  
  
4.  **열기** 대화 상자에서 가져올 모델 메타데이터 및 데이터가 포함된 [!INCLUDE[ssGeminiClient](../../includes/ssgeminiclient-md.md)] 파일을 선택한 다음 **열기**를 클릭합니다.  
  
## <a name="see-also"></a>관련 항목  
 [작업 영역 데이터베이스](../../analysis-services/tabular-models/workspace-database-ssas-tabular.md)   
 [데이터 복사 및 붙여넣기](../../analysis-services/tabular-models/ssas-import-data-copy-and-paste-data.md)  
  
  
