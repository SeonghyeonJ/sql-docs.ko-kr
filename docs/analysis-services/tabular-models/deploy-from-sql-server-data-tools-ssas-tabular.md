---
title: Analysis Services 테이블 형식 모델 SQL Server Data Tools에서 배포 | Microsoft Docs
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 09d859cf8b5c372b9588266b9210837012396ea6
ms.sourcegitcommit: 8a64c59c5d84150659a015e54f8937673cab87a0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/08/2018
ms.locfileid: "53072140"
---
# <a name="deploy-from-sql-server-data-tools"></a>SQL Server Data Tools에서 배포
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  SSDT에서 배포 명령을 사용 하 여 테이블 형식 모델 솔루션을 배포 하려면이 항목의 태스크를 사용 합니다.  
  
##  <a name="bkmk_deploy"></a> 배포 옵션 및 배포 서버 속성 구성  
 테이블 형식 모델 솔루션을 배포하기 전에 먼저 배포 옵션 및 배포 서버 속성을 지정해야 합니다. 배포 속성 설정에 대 한 자세한 내용은 참조 하세요. [테이블 형식 모델 솔루션 배포](../../analysis-services/tabular-models/tabular-model-solution-deployment-ssas-tabular.md)합니다.  
  
#### <a name="to-configure-options-and-properties"></a>옵션 및 속성을 구성 하려면  
  
1.  SSDT에서의 **솔루션 탐색기**에서 프로젝트 이름을 마우스 오른쪽 단추로 클릭 하 고 클릭 **속성**합니다.  
  
2.  에  **\<프로젝트 이름 > 속성** 대화 상자에서 **배포 옵션**, 기본 설정과에서 다른 경우 속성 설정을 지정 합니다.  
  
    > [!NOTE]  
    >  캐시된 모드의 모델의 경우 **쿼리 모드** 는 항상 **메모리 내**입니다.  
  
    > [!NOTE]  
    >  DirectQuery 모드에서는 모델에 **가장 설정** 을 지정할 수 없습니다.  
  
3.  **배포 서버**에서 기본 설정과 다른 경우 **서버** (이름), **버전**, **데이터베이스** (이름) 및 **큐브 이름** 속성 설정을 지정한 다음 **확인**을 클릭합니다.  
  
> [!NOTE]  
>  새 프로젝트를 만들 때마다 자동으로 지정된 서버로 배포되도록 기본 배포 서버 속성 설정을 지정할 수도 있습니다. 자세한 내용은 [기본 데이터 모델링 및 배포 속성 구성](../../analysis-services/tabular-models/configure-default-data-modeling-and-deployment-properties-ssas-tabular.md)합니다.  
  
##  <a name="bkmk_deploy_proc"></a> 테이블 형식 모델 배포  
  
#### <a name="to-deploy-a-tabular-model"></a>테이블 형식 모델을 배포 하려면
  
-   SSDT에서에 **빌드** 메뉴에서 클릭 **배포 \<프로젝트 이름 >** 합니다.  
  
     처리 옵션 속성이 처리 안 함으로 설정되지 않았으면 **배포** 대화 상자에 메타데이터 배포 및 모델에 포함된 각 테이블의 처리 상태가 표시됩니다. 배포 프로세스를 완료 한 후 SSMS를 사용 하 여 Analysis Services 인스턴스에 연결 하 고 새 model 데이터베이스 개체가 만들어졌는지 확인 하려면 또는 클라이언트 응용 프로그램이 배포 된 모델에 연결할 reporting를 사용 합니다.  
  
##  <a name="bkmk_deploy_status"></a> 배포 상태  
 **배포** 대화 상자에서는 배포 작업의 진행 상황을 모니터링할 수 있습니다. 배포 작업을 중지할 수도 있습니다.  
  
 **상태**  
 배포 작업의 성공 여부를 나타냅니다.  
  
 **세부 정보**  
 배포된 메타데이터 항목 및 각 메타데이터 항목의 상태를 나열하고 각 문제에 대한 메시지를 제공합니다.  
  
 **배포 중지**  
 배포 작업을 중지하려면 클릭합니다. 이 옵션은 배포 작업에 시간이 너무 많이 걸리거나 오류가 너무 많은 경우에 유용합니다.  
  
## <a name="see-also"></a>참고자료  
 [테이블 형식 모델 솔루션 배포](../../analysis-services/tabular-models/tabular-model-solution-deployment-ssas-tabular.md)   
 [기본 데이터 모델링 및 배포 속성 구성](../../analysis-services/tabular-models/configure-default-data-modeling-and-deployment-properties-ssas-tabular.md)  
  
  
