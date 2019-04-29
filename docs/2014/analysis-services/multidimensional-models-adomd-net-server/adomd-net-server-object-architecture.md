---
title: ADOMD.NET 서버 개체 아키텍처 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- ADOMD.NET, object model
- object model [ADOMD.NET]
ms.assetid: bdc81de9-b390-4654-b62a-cd6c0c9ca10d
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 1333f91630cb822c85dd283a40a2cb06db3dffb1
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62727887"
---
# <a name="adomdnet-server-object-architecture"></a>ADOMD.NET 서버 개체 아키텍처
  ADOMD.NET 서버 개체는 사용자 정의 함수 (Udf) 또는 저장된 프로시저를 만드는 데 사용할 수 있는 도우미 개체 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]합니다.  
  
> [!NOTE]  
>  `Microsoft.AnalysisServices.AdomdServer` 네임스페이스 및 이러한 개체를 사용하려면 msmgdsrv.dll에 대한 참조를 UDF 프로젝트 또는 저장 프로시저에 추가해야 합니다.  
  
 ![ADOMD.NET 서버에서 개체 관계를 보여 줍니다](../../../2014/analysis-services/dev-guide/media/adomdnetserverobjectmodel.gif "ADOMD.NET 서버에서 개체 관계를 보여 줍니다.")  
ADOMD.NET 개체 모델  
  
 ADOMD.NET 개체 계층 구조와의 상호 작용은 일반적으로 다음 표에 설명된 최상위 레이어에 있는 하나 이상의 개체에서 시작됩니다.  
  
|수행할 작업|사용 개체|  
|--------|---------------------|  
|MDX(Multidimensional Expressions) 식 평가|<xref:Microsoft.AnalysisServices.AdomdServer.Expression><br /> <xref:Microsoft.AnalysisServices.AdomdServer.Expression> 개체는 MDX 식을 실행하고 지정된 튜플에서 해당 식을 평가하는 방법을 제공합니다.|  
|전체 MDX 문을 생성하지 않고 MDX 함수를 실행할 수 있는 지원 제공|<xref:Microsoft.AnalysisServices.AdomdServer.MDX><br /> <xref:Microsoft.AnalysisServices.AdomdServer.MDX> 개체를 사용하면 <xref:Microsoft.AnalysisServices.AdomdServer.Expression> 개체를 사용하지 않고 미리 정의된 MDX 함수를 호출할 수 있으므로 편리합니다. <xref:Microsoft.AnalysisServices.AdomdServer.MDX> 개체의 추가 함수는 이후 릴리스에서 사용할 수 있습니다.|  
|UDF의 현재 실행 컨텍스트 표현|<xref:Microsoft.AnalysisServices.AdomdServer.Context><br /> <xref:Microsoft.AnalysisServices.AdomdServer.Context> 개체는 현재 큐브 또는 마이닝 모델과 같은 정보와 다양한 메타데이터 컬렉션을 노출합니다. <xref:Microsoft.AnalysisServices.AdomdServer.Context> 개체의 주요 용도 중 하나는 <xref:Microsoft.AnalysisServices.AdomdServer.Hierarchy.CurrentMember%2A> 개체의 <xref:Microsoft.AnalysisServices.AdomdServer.Hierarchy> 속성입니다. UDF 또는 저장 프로시저의 작성자는 이 속성을 사용하여 쿼리가 실행되는 특정 차원의 멤버를 기준으로 결정을 내릴 수 있습니다.|  
|집합 및 튜플 만들기|<xref:Microsoft.AnalysisServices.AdomdServer.SetBuilder>, <xref:Microsoft.AnalysisServices.AdomdServer.TupleBuilder><br /> <xref:Microsoft.AnalysisServices.AdomdServer.SetBuilder>는 변경할 수 없는 집합을 만드는 방법을 제공하고 <xref:Microsoft.AnalysisServices.AdomdServer.TupleBuilder>는 변경할 수 없는 튜플을 만드는 방법을 제공합니다.|  
|MDX 언어의 6가지 기본 유형 간의 암시적 변환 및 캐스트 지원|<xref:Microsoft.AnalysisServices.AdomdServer.MDXValue><br /> <xref:Microsoft.AnalysisServices.AdomdServer.MDXValue> 개체는 다음 형식 간의 암시적 변환 및 캐스트를 제공합니다.<br /><br /> -   <xref:Microsoft.AnalysisServices.AdomdServer.Hierarchy><br />-   <xref:Microsoft.AnalysisServices.AdomdServer.Level><br />-   <xref:Microsoft.AnalysisServices.AdomdServer.Member><br />-   <xref:Microsoft.AnalysisServices.AdomdServer.Tuple><br />-   <xref:Microsoft.AnalysisServices.AdomdServer.Set><br />-스칼라 또는 값 형식|  
  
## <a name="see-also"></a>관련 항목  
 [ADOMD.NET 서버 프로그래밍](https://docs.microsoft.com/bi-reference/adomd/multidimensional-models-adomd-net-server/adomd-net-server-programming)  
  
  
