---
title: 개인 설정을 통해 OLAP 확장 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- Analysis Services, extensibility
ms.assetid: 348e49fc-4390-43c1-9b6c-61b386ff4373
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 74c5b777dda06cf70a6afa2e6384eb2a3587d431
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62725987"
---
# <a name="extending-olap-through-personalizations"></a>개별화를 통해 OLAP 확장
  Microsoft [!INCLUDE[ssASCurrent](../../../includes/ssascurrent-md.md)]에서는 MDX(Multidimensional Expressions) 및 DMX(Data Mining Extension) 언어와 함께 사용할 수 있는 다양한 내장 함수를 제공합니다. 이러한 함수를 사용하여 표준 통계 계산을 비롯하여 계층에서의 멤버 이동에 이르는 모든 작업을 수행할 수 있습니다. 그러나 복잡하고 강력한 다른 제품에서도 그렇듯이 제품의 기능을 더 확장할 필요성은 언제나 있기 마련입니다.  
  
 따라서 표준 기능이 충분하지 않을 때마다 업무 요구 사항을 완전히 충족시키기 위해 Analysis Services에서는 서비스 인스턴스에 어셈블리 및 개인 설정 확장 프로그램을 추가하는 기능을 제공합니다.  
  
## <a name="assemblies"></a>어셈블리  
 어셈블리를 사용하면 MDX와 DMX의 비즈니스 기능을 확장할 수 있습니다. 원하는 기능을 작성하여 DLL(동적 연결 라이브러리)과 같은 라이브러리에 추가한 후 이 라이브러리를 Analysis Services 인스턴스 또는 Analysis Services 데이터베이스에 어셈블리로 추가하면 됩니다. 그런 다음 MDX 및 DMX 식, 프로시저, 계산, 동작 및 클라이언트 애플리케이션에서 라이브러리의 공용 메서드를 사용자 정의 함수로 사용할 수 있습니다.  
  
## <a name="personalized-extensions"></a>개인 설정 확장 프로그램  
 SQL Server Analysis Services 개인 설정 확장 프로그램은 플러그 인 아키텍처 구현 개념의 토대입니다. Analysis Services 개인 설정 확장 프로그램은 기존 관리 어셈블리 아키텍처를 간단하고 유용하게 수정하는 한 방법이며, Analysis Services <xref:Microsoft.AnalysisServices.AdomdServer> 개체 모델, MDX(Multidimensional Expression) 구문 및 스키마 행 집합을 통해 노출됩니다.  
  
## <a name="see-also"></a>관련 항목  
 [다차원 모델 어셈블리 관리](../multidimensional-model-assemblies-management.md)   
 [Analysis Services 개인 설정 확장 프로그램](analysis-services-personalization-extensions.md)  
  
  
