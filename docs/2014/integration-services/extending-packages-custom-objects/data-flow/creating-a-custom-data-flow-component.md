---
title: 사용자 지정 데이터 흐름 구성 요소 만들기 | Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- design-time component interface [Integration Services]
- custom data flow components [Integration Services], about data flow components
- custom data flow components [Integration Services]
- data flow components [Integration Services]
- data flow components [Integration Services], developing
ms.assetid: 9d96bcf5-eba8-44bd-b113-ed51ad0d0521
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 1703d70b7760cad2198b3565ce3fc47d44cac409
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/26/2020
ms.locfileid: "62768945"
---
# <a name="creating-a-custom-data-flow-component"></a>사용자 지정 데이터 흐름 구성 요소 만들기
  [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)]에서 데이터 흐름 태스크는 개발자가 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]와 관리형 코드를 사용하여 사용자 지정 데이터 흐름의 원본, 변환 및 대상 구성 요소를 만들 수 있게 해 주는 개체 모델을 제공합니다.  
  
 데이터 흐름 태스크는 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100> 인터페이스를 포함하는 구성 요소와 구성 요소 간의 데이터 이동을 정의하는 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSPath100> 개체의 컬렉션으로 구성됩니다.  
  
> [!NOTE]  
>  사용자 지정 공급자를 만들 경우 ProviderDescriptors.xml 파일을 메타데이터 열 값으로 업데이트해야 합니다.  
  
## <a name="design-time-and-run-time"></a>디자인 타임 및 런타임  
 실행 전 데이터 흐름 태스크에서 증분 변경 작업이 수행될 때 해당 데이터 흐름 태스크는 디자인 타임 상태에 있다고 합니다. 변경 작업에는 구성 요소의 추가 또는 제거, 구성 요소를 연결하는 경로 개체의 추가 또는 제거, 구성 요소의 메타데이터 변경 등이 포함됩니다. 메타데이터가 변경되면 구성 요소에서는 변경 내용을 모니터링하고 그에 따라 반응할 수 있습니다. 예를 들어 변경에 대한 응답으로 구성 요소에서는 특정 변경 작업을 허용하지 않거나 추가 변경 작업을 수행할 수 있습니다. 디자인 타임에 디자이너는 디자인 타임 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSDesigntimeComponent100> 인터페이스를 통해 구성 요소와 상호 작용합니다.  
  
 실행 시 데이터 흐름 태스크에서는 구성 요소의 시퀀스를 검사하고, 실행 계획을 준비하고, 작업 계획을 실행하는 작업자 스레드의 풀을 관리합니다. 각 작업자 스레드는 데이터 흐름 태스크 내부의 일부 작업을 수행하지만 작업자 스레드의 주요 태스크는 런타임 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSRuntimeComponent100> 인터페이스를 통해 구성 요소의 메서드를 호출하는 것입니다.  
  
## <a name="creating-a-component"></a>구성 요소 만들기  
 데이터 흐름 구성 요소를 만들려면 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent> 기본 클래스에서 클래스를 파생시키고 <xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute> 클래스를 적용한 다음 기본 클래스의 적절한 메서드를 재정의합니다. <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent>는 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSDesigntimeComponent100> 및 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSRuntimeComponent100> 인터페이스를 구현하고 구성 요소에서 재정의할 수 있는 메서드를 제공합니다.  
  
 프로젝트에는 구성 요소에서 사용되는 개체에 따라 다음 어셈블리 중 일부 또는 모두에 대한 참조가 필요합니다.  
  
|기능|참조할 어셈블리|가져올 네임스페이스|  
|-------------|---------------------------|-------------------------|  
|디자이너의|Microsoft.SqlServer.PipelineHost|<xref:Microsoft.SqlServer.Dts.Pipeline>|  
|데이터 흐름 래퍼|Microsoft.SqlServer.DTSPipelineWrap|<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper>|  
|런타임|Microsoft.SQLServer.ManagedDTS|<xref:Microsoft.SqlServer.Dts.Runtime>|  
|런타임 래퍼|Microsoft.SqlServer.DTSRuntimeWrap|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper>|  
  
 다음 코드 예에서는 기본 클래스에서 파생되는 간단한 구성 요소를 보여 주고 <xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute>를 적용합니다. DTSPipelineWrap 어셈블리에 대한 참조를 추가해야 합니다.  
  
```csharp  
using System;  
using Microsoft.SqlServer.Dts.Pipeline;  
using Microsoft.SqlServer.Dts.Pipeline.Wrapper;  
  
namespace Microsoft.Samples.SqlServer.Dts  
{  
    [DtsPipelineComponent(DisplayName = "SampleComponent", ComponentType = ComponentType.Transform )]  
    public class BasicComponent: PipelineComponent  
    {  
        // TODO: Override the base class methods.  
    }  
}  
```  
  
```vb  
Imports Microsoft.SqlServer.Dts.Pipeline  
Imports Microsoft.SqlServer.Dts.Pipeline.Wrapper  
  
<DtsPipelineComponent(DisplayName:="SampleComponent", ComponentType:=ComponentType.Transform)> _  
Public Class BasicComponent  
  
    Inherits PipelineComponent  
  
    ' TODO: Override the base class methods.  
  
End Class  
```  
  
![Integration Services 아이콘 (작은 아이콘)](../../media/dts-16.gif "Integration Services 아이콘(작은 아이콘)")  **은 최신 상태로 유지 Integration Services**<br /> Microsoft의 최신 다운로드, 문서, 예제 및 비디오와 커뮤니티에서 선택된 솔루션을 보려면 MSDN의 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 페이지를 방문하세요.<br /><br /> [MSDN의 Integration Services 페이지를 방문하세요.](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> 이러한 업데이트에 대한 자동 알림을 받으려면 해당 페이지에서 제공하는 RSS 피드를 구독하세요.  
  
## <a name="see-also"></a>참고 항목  
 [데이터 흐름 구성 요소의 사용자 인터페이스 개발](developing-a-user-interface-for-a-data-flow-component.md)  
  
  
