---
title: 논리적 아키텍처 (Analysis Services-다차원 데이터) | Microsoft Docs
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: olap
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 6b6b33ffbf59cf05bc5455d3daac437e9e79407c
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/15/2019
ms.locfileid: "68165608"
---
# <a name="understanding-microsoft-olap-logical-architecture"></a>Microsoft OLAP 논리 아키텍처 이해
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 서버 및 클라이언트 구성 요소를 사용 하 여 온라인 분석 처리 (OLAP)와 비즈니스 인텔리전스 응용 프로그램에 대 한 데이터 마이닝 기능을 제공 합니다.  
  
-   [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 의 서버 구성 요소는 Microsoft Windows 서비스로 구현됩니다. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 각 인스턴스를 사용 하 여 동일한 컴퓨터에서 여러 인스턴스를 지원 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 를 별도 Windows 서비스 인스턴스로 구현 합니다.  
  
-   클라이언트는 웹 서비스로 노출되어 명령을 실행하고 응답을 수신하는 SOAP 기반 프로토콜인 공용 표준 XMLA(XML for Analysis)를 사용하여 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 와 통신합니다. 또한 XMLA를 통해 클라이언트 개체 모델이 제공되며 이는 ADOMD.NET과 같은 관리 공급자나 네이티브 OLE DB 공급자 중 하나를 사용하여 액세스할 수 있습니다.  
  
-   다음 언어를 사용 하 여 쿼리 명령은 실행할 수 있습니다. SQL, 다차원 식 (MDX), 분석용 업계 표준 쿼리 언어인 또는 확장 DMX (Data Mining), 데이터 마이닝 지향 업계 표준 쿼리 언어인 합니다. 또한 ASSL(Analysis Services Scripting Language)을 사용하여 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 데이터베이스 개체를 관리할 수도 있습니다.  
  
 또한 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]에서는 서로 연결되지 않은 여러 클라이언트의 응용 프로그램이 로컬에 저장된 다차원 데이터를 검색할 수 있도록 하는 로컬 큐브 엔진을 지원합니다. 자세한 내용은 참조 하세요. [Analysis Services 개발을 위한 클라이언트 아키텍처 요구 사항](../../../analysis-services/multidimensional-models/olap-physical/client-architecture-requirements-for-analysis-services-development.md)  
  
## <a name="in-this-section"></a>섹션 내용  
 **논리적 아키텍처 개요**  
 [논리 아키텍처 개요 &#40;Analysis Services-다차원 데이터&#41;](../../../analysis-services/multidimensional-models/olap-logical/logical-architecture-overview-analysis-services-multidimensional-data.md)  
  
 **서버 개체**  
 [서버 개체 &#40;Analysis Services-다차원 데이터&#41;](../../../analysis-services/multidimensional-models/olap-logical/server-objects-analysis-services-multidimensional-data.md)  
  
 **데이터베이스 개체**  
 [데이터베이스 개체 & #40; Analysis Services-다차원 데이터 & #41;](../../../analysis-services/multidimensional-models/olap-logical/database-objects-analysis-services-multidimensional-data.md)  
  
 **Dimension 개체**  
 [차원 개체 &#40;Analysis Services-다차원 데이터&#41;](../../../analysis-services/multidimensional-models-olap-logical-dimension-objects/dimension-objects-analysis-services-multidimensional-data.md)  
  
 **큐브 개체**  
 [큐브 개체 &#40;Analysis Services-다차원 데이터&#41;](../../../analysis-services/multidimensional-models-olap-logical-cube-objects/cube-objects-analysis-services-multidimensional-data.md)  
  
 **사용자 액세스 보안**  
 [사용자 액세스 보안 아키텍처](http://msdn.microsoft.com/library/71b44e10-2bd0-44f7-8de9-7c8f5b7ac082)  
  
## <a name="see-also"></a>관련 항목  
 [Microsoft OLAP 아키텍처 이해](../../../analysis-services/multidimensional-models/olap-physical/understanding-microsoft-olap-architecture.md)   
 [물리적 아키텍처 &#40;Analysis Services-다차원 데이터&#41;](../../../analysis-services/multidimensional-models/olap-physical/understanding-microsoft-olap-physical-architecture.md)  
  
  
