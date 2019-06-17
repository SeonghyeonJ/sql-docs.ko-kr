---
title: 데이터 마이닝 저장 프로시저 (Analysis Services-데이터 마이닝) | Microsoft Docs
ms.date: 05/01/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: data-mining
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 2984927575e6dcd3c8d6c530a94061b1dc0b6c17
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/15/2019
ms.locfileid: "65449935"
---
# <a name="data-mining-stored-procedures-analysis-services---data-mining"></a>데이터 마이닝 저장 프로시저(Analysis Services - 데이터 마이닝)
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]부터 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 에서는 관리되는 모든 언어로 작성된 저장 프로시저가 지원됩니다. 지원되는 관리 언어에는 [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] .NET, C# 및 Managed C++가 포함됩니다. [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]에서는 저장 프로시저를 **CALL** 문을 사용하여 직접 호출하거나 DMX(Data Mining Extensions) 쿼리의 일부로 호출할 수 있습니다.  
  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 저장 프로시저 호출에 대한 자세한 내용은 [저장 프로시저 호출](../../analysis-services/multidimensional-models-extending-olap-stored-procedures/calling-stored-procedures.md)을 참조하세요.  
  
 프로그래밍 기능에 대 한 일반적인 정보를 참조 하세요 [데이터 마이닝 프로그래밍](../../analysis-services/data-mining/data-mining-programming.md)합니다.  
  
 데이터 마이닝 개체 프로그래밍 방법은 MSDN 라이브러리에서 "[SQL Server 데이터 마이닝 프로그래밍 기능(SQL Server Data Mining Programmability)](http://go.microsoft.com/fwlink/?LinkId=93735)" 문서를 참조하십시오.  
  
> [!NOTE]  
>  마이닝 모델을 쿼리할 경우 특히 새 데이터 마이닝 솔루션을 테스트할 경우에는 데이터 마이닝 엔진에 내부적으로 사용되는 시스템 저장 프로시저를 호출하는 것이 편리할 수 있습니다. [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 를 사용하여 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 서버에서 추적을 만든 다음 데이터 마이닝 모델을 작성하고 찾아보고 쿼리하여 이러한 시스템 저장 프로시저의 이름을 볼 수 있습니다. 그러나 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 에서는 버전 간에 시스템 저장 프로시저의 호환성을 보장하지 않으므로 프로덕션 시스템에서는 시스템 저장 프로시저를 호출하지 않도록 해야 합니다. 대신 호환성을 위해 DMX 또는 XML/A를 사용하여 쿼리를 직접 작성하는 것이 좋습니다.  
  
## <a name="in-this-section"></a>섹션 내용  
  
-   [SystemGetCrossValidationResults&#40;Analysis Services - 데이터 마이닝&#41;](../../analysis-services/data-mining/systemgetcrossvalidationresults-analysis-services-data-mining.md)  
  
-   [SystemGetClusterCrossValidationResults&#40;Analysis Services - 데이터 마이닝&#41;](../../analysis-services/data-mining/systemgetclustercrossvalidationresults-analysis-services-data-mining.md)  
  
-   [SystemGetAccuracyResults&#40;Analysis Services - 데이터 마이닝&#41;](../../analysis-services/data-mining/systemgetaccuracyresults-analysis-services-data-mining.md)  
  
-   [SystemGetClusterAccuracyResults&#40;Analysis Services - 데이터 마이닝&#41;](../../analysis-services/data-mining/systemgetclusteraccuracyresults-analysis-services-data-mining.md)  
  
## <a name="see-also"></a>관련 항목  
 [교차 유효성 검사&#40;Analysis Services - 데이터 마이닝&#41;](../../analysis-services/data-mining/cross-validation-analysis-services-data-mining.md)   
 [교차 유효성 검사 탭&#40;마이닝 정확도 차트 뷰&#41;](http://msdn.microsoft.com/library/bd215a68-1ad7-4046-9c44-ec8e2be13a64)   
 [저장 프로시저 호출](../../relational-databases/native-client-odbc-stored-procedures/calling-a-stored-procedure.md)  
  
  
