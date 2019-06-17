---
title: 데이터 마이닝 솔루션 배포 | Microsoft Docs
ms.date: 05/01/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: data-mining
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: b42d01b097483d9088bd76257cd30ac37158f889
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62467409"
---
# <a name="deployment-of-data-mining-solutions"></a>데이터 마이닝 솔루션 배포
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  데이터 마이닝 프로세스의 마지막 단계는 모델을 프로덕션 환경에 배포하는 것입니다. 배포 작업을 수행해야 사용자가 모델을 사용하여 다음과 같은 태스크를 수행할 수 있습니다.  
  
-   모델을 사용하여 예측을 만들고 비즈니스 의사 결정을 내릴 수 있습니다. 쿼리를 만드는 데 사용할 수 있는 도구에 대한 자세한 내용은 [데이터 마이닝 쿼리 도구](../../analysis-services/data-mining/data-mining-query-tools.md)를 참조하세요.  
  
-   데이터 마이닝 기능을 직접 애플리케이션에 포함할 수 있습니다. 마이닝 구조 및 마이닝 모델을 생성, 변경, 처리 및 삭제하기 위해 애플리케이션에서 사용할 수 있는 개체 집합이 포함된 어셈블리 또는 AMO(Analysis Management Objects)를 포함할 수 있습니다.  
  
-   사용자가 예측을 요청하고, 추세를 보고, 모델을 비교하는 데 사용할 수 있는 보고서를 만들 수 있습니다.  
  
 이 섹션에서는 배포 옵션에 대해 자세히 설명합니다.  
  
 [데이터 마이닝 솔루션 배포 요구 사항](#bkmk_Reqs)  
  
 [관계형 솔루션 배포](#bkmk_RelationalSltn)  
  
 [다차원 솔루션 배포](#bkmk_MDSltn)  
  
 [관련 리소스](#bkmk_Resources)  
  
## <a name="in-this-section"></a>섹션 내용  
 [이전 버전의 SQL Server 데이터 마이닝 솔루션 배포](../../analysis-services/data-mining/deploy-a-data-mining-solution-to-previous-versions-of-sql-server.md)  
  
 [데이터 마이닝 개체 내보내기 및 가져오기](../../analysis-services/data-mining/export-and-import-data-mining-objects.md)  
  
##  <a name="bkmk_Reqs"></a> 데이터 마이닝 솔루션 배포 요구 사항  
 솔루션을 배포하는 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 인스턴스는 다차원 개체 및 데이터 마이닝 개체를 지원하는 모드에서 실행되고 있어야 합니다. 즉 데이터 마이닝 개체를 테이블 형식 모델 또는 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 데이터를 호스팅하는 인스턴스에 배포할 수는 없습니다.  
  
 따라서 Visual Studio에서 데이터 마이닝 솔루션을 만드는 경우 반드시 **Analysis Services 다차원 및 데이터 마이닝 프로젝트**템플릿을 사용하십시오.  
  
 솔루션을 배포하면 지정된 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 인스턴스에서 솔루션 파일과 같은 이름의 데이터베이스에 데이터 마이닝에 사용되는 개체가 만들어집니다.  
  
###  <a name="bkmk_RelationalSltn"></a> 관계형 솔루션 배포  
 관계형 데이터 마이닝 솔루션을 배포하면 필요한 데이터 마이닝 개체가 새 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 데이터베이스에 만들어지고 해당 개체가 기본적으로 처리됩니다. 구성 속성인 **처리 옵션**을 사용하여 처리 옵션을 변경할 수 있습니다. 자세한 내용은 [Analysis Services 프로젝트 속성 구성&#40;SSDT&#41;](../../analysis-services/multidimensional-models/configure-analysis-services-project-properties-ssdt.md)을 참조하세요.  
  
 기본적으로 매번 증분 변경 내용만 배포됩니다. 즉 마이닝 모델을 수정하는 경우 프로젝트를 다시 배포하면 해당 마이닝 모델만 업데이트됩니다. 하지만 여러 클라이언트가 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 데이터베이스를 편집하고 있으면 이 경우 오류가 발생할 수 있습니다. 솔루션을 배포할 때 전체 데이터베이스를 새로 고치도록 기본 배포 모드를 변경하려면 **배포 모드** 속성을 변경합니다.  
  
 관계형 데이터 마이닝 솔루션에서 배포해야 하는 개체는 데이터 원본 정의, 사용된 모든 데이터 원본 뷰, 마이닝 구조 및 모든 종속 마이닝 모델 뿐입니다.  
  
###  <a name="bkmk_MDSltn"></a> 다차원 솔루션 배포  
 다차원 데이터 마이닝 솔루션을 배포하면 원본 큐브와 동일한 데이터베이스 내부에 데이터 마이닝 개체가 만들어집니다.  
  
 마이닝 구조 또는 마이닝 모델을 처리할 때 원본 큐브도 처리해야 합니다. 따라서 OLAP 마이닝 모델을 사용하는 솔루션을 배포하는 데 걸리는 시간이 관계형 데이터 마이닝 솔루션의 경우보다 더 길 수 있습니다.  
  
 대개 데이터 마이닝 개체는 큐브에 사용되는 것과 동일한 데이터 원본 및 데이터 원본 뷰를 사용합니다. 하지만 데이터 마이닝에 사용하도록 특별히 만든 데이터 원본 및 데이터 원본 뷰를 추가할 수 있습니다. 예를 들어 대개 큐브는 잠재 클라이언트에 대한 데이터 또는 다차원 개체에 사용되지 않은 외부 데이터를 포함하지 않습니다.  
  
##  <a name="bkmk_Resources"></a> 관련 리소스  
 [데이터 마이닝 개체 이동](../../analysis-services/data-mining/moving-data-mining-objects.md)  
  
 모델이 관계형 데이터만 기반으로 하는 경우 모델을 이동하는 가장 손쉬운 방법은 DMX를 사용하여 개체를 내보내고 가져오는 것입니다.  
  
 [Analysis Services 데이터베이스 이동](../../analysis-services/multidimensional-models/move-an-analysis-services-database.md)  
  
 모델이 큐브를 데이터 원본으로 사용하는 경우 모델과 해당 지원 큐브 데이터를 이동하는 방법을 보려면 다음 항목을 참조하십시오.  
  
 [Analysis Services 프로젝트 배포&#40;SSDT&#41;](../../analysis-services/multidimensional-models/deploy-analysis-services-projects-ssdt.md)  
  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 프로젝트의 배포에 대한 일반적인 정보를 제공하고 프로젝트를 구성할 때 설정할 수 있는 속성에 대해 설명합니다.  
  
## <a name="see-also"></a>관련 항목:  
 [다차원 모델 처리&#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/processing-a-multidimensional-model-analysis-services.md)   
 [데이터 마이닝 쿼리 도구](../../analysis-services/data-mining/data-mining-query-tools.md)   
 [처리 요구 사항 및 고려 사항 & #40; 데이터 마이닝 & #41;](../../analysis-services/data-mining/processing-requirements-and-considerations-data-mining.md)  
  
  
