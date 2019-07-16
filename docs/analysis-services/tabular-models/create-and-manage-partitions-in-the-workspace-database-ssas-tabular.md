---
title: Analysis Services 작업 영역 데이터베이스에서 파티션 만들기 및 관리 | Microsoft Docs
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 40e87650a36f717aea1a333c134e7722383f4ec4
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/15/2019
ms.locfileid: "68207723"
---
# <a name="create-and-manage-partitions-in-the-workspace-database"></a>작업 영역 데이터베이스에서 파티션 만들기 및 관리 
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  파티션은 테이블을 논리적 부분으로 나눕니다. 각 파티션은 다른 파티션에 독립적으로 또는 병렬로 처리(새로 고침)할 수 있습니다. 파티션은 확장성 및 대형 데이터베이스의 관리 효율성을 높일 수 있습니다. 기본적으로 각 테이블에는 모든 열을 포함하는 파티션이 하나 있습니다. 이 항목의 태스크에서는 **의** 파티션 관리자 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]  
  
 다른 Analysis Services 인스턴스로 모델을 배포한 후 데이터베이스 관리자는 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]를 사용하여 (배포된) 모델에서 파티션을 만들고 관리할 수 있습니다. 자세한 내용은 [만들기 및 테이블 형식 모델 파티션 관리](../../analysis-services/tabular-models/create-and-manage-tabular-model-partitions-ssas-tabular.md)합니다.  
  
> [!NOTE]  
>  파티션 관리자 대화 상자를 사용하여 모델 작업 영역 데이터베이스에서 파티션을 병합할 수 없습니다. [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]만을 사용하여 배포된 모델에서 파티션을 병합할 수 있습니다.  
  
## <a name="tasks"></a>태스크  
 파티션을 만들고 관리하려면 **파티션 관리자** 대화 상자를 사용해야 합니다. **파티션 관리자** 대화 상자를 확인하려면 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]에서 **테이블** 메뉴를 클릭한 다음 **파티션**을 클릭합니다.  
  
###  <a name="bkmk_create_new"></a> 새 파티션을 만들려면  
  
1.  모델 디자이너에서 파티션을 정의할 테이블을 선택합니다.  
  
2.  **테이블** 메뉴를 클릭한 다음 **파티션**을 클릭합니다.  
  
3.  **파티션 관리자**의 **테이블** 목록 상자에서 분할할 테이블을 확인 또는 선택한 다음 **새로 만들기**를 클릭합니다.  
  
4.  **파티션 이름**에 파티션의 이름을 입력합니다. 기본적으로 기본 파티션의 이름은 새 파티션마다 증분 번호로 지정됩니다.  
  
5.  테이블 미리 보기 모드 또는 쿼리 편집기 모드를 사용하여 생성한 SQL 쿼리를 사용해 파티션에 포함할 행과 열을 선택할 수 있습니다.  
  
     테이블 미리 보기 모드(기본값)를 사용하려면 미리 보기 창의 오른쪽 위에 있는 **테이블 미리 보기** 단추를 클릭합니다. 열 이름 옆에 있는 확인란을 선택하여 파티션에 포함할 열을 선택합니다. 행을 필터링하려면 셀 값을 마우스 오른쪽 단추로 클릭하고 **선택한 셀 값으로 필터링**을 클릭합니다.  
  
     SQL 문을 사용하려면 미리 보기 창의 오른쪽 위에 있는 **쿼리 편집기** 단추를 클릭한 다음 SQL 쿼리 문을 쿼리 창에 입력하거나 붙여넣습니다. 문의 유효성을 검사하려면 **유효성 검사**를 클릭합니다. 쿼리 디자이너를 사용하려면 **디자인**을 클릭합니다.  
  
###  <a name="bkmk_copy"></a> 파티션을 복사하려면  
  
1.  **파티션 관리자**의 **테이블** 목록 상자에서 복사할 파티션을 포함하는 테이블을 확인 또는 선택합니다.  
  
2.  **파티션** 목록에서 복사할 파티션을 선택한 다음 **복사**를 클릭합니다.  
  
3.  **파티션 이름**에 파티션의 새 이름을 입력합니다.  
  
###  <a name="bkmk_delete"></a> 파티션을 삭제하려면  
  
1.  **파티션 관리자**의 **테이블** 목록 상자에서 삭제할 파티션을 포함하는 테이블을 확인 또는 선택합니다.  
  
2.  **파티션** 목록에서 삭제할 파티션을 선택한 다음 **삭제**를 클릭합니다.  
  
## <a name="see-also"></a>참조  
 [파티션](../../analysis-services/tabular-models/partitions-ssas-tabular.md)   
 [작업 영역 데이터베이스에서 파티션 처리](../../analysis-services/tabular-models/process-partitions-in-the-workspace-database-ssas-tabular.md)  
  
  
