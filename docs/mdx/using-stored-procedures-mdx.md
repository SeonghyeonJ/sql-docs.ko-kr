---
title: 저장된 프로시저 사용 (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 0d4d455ed7bd804f4c2d4ce036c00f85fd94629f
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63251577"
---
# <a name="using-stored-procedures-mdx"></a>저장 프로시저 사용(MDX)


  .NET 저장 프로시저 또는 사용자 정의 함수를 작성하여 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 및 MDX(Multidimensional Expressions)의 기능을 확장할 수 있습니다. 자세한 내용은 참조 하세요. [ADOMD.NET 서버 프로그래밍](https://docs.microsoft.com/bi-reference/adomd/multidimensional-models-adomd-net-server/adomd-net-server-programming)  
  
 저장 프로시저를 참조하거나 호출할 때는 함수 이름 뒤에 괄호를 지정합니다. 괄호 안에는 매개 변수로 전달할 데이터를 제공하는 식(인수)을 지정할 수 있습니다. 함수를 호출할 때는 모든 괄호에 대해 인수 값을 제공해야 하며 사용자 정의 함수에서 매개 변수가 정의된 순서와 같은 순서로 인수 값을 지정해야 합니다.  
  
 다음 예제 쿼리에서는 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 서버에 SampleAssembly라는 어셈블리가 등록되어 있다고 가정합니다.  
  
```  
SELECT SampleAssembly.RandomSample([Geography].[State-Province].Members, 5) on ROWS,   
[Date].[Calendar].[Calendar Year] on COLUMNS  
FROM [Adventure Works]  
WHERE [Measures].[Reseller Freight Cost]  
```  
  
> [!NOTE]  
>  *저장 프로시저* 에서 사용 되는 용어는 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 이런이 유형의 함수에 대 한 합니다. 이전 버전의 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 이러한 유형의 함수를 호출 *사용자 정의 함수*합니다.  
  
## <a name="types-of-stored-procedures"></a>저장 프로시저 유형  
 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]는 COM 및 CLR 어셈블리를 모두 지원합니다. CLR 어셈블리에 적용되는 향상된 보안 기능 때문에 CLR 어셈블리를 권장합니다. 서버에 Microsoft Office Excel이 설치되어 있으면 Excel 기능도 사용할 수 있습니다.  
  
> [!NOTE]  
>  Microsoft VBA(Visual Basic for Applications) COM 어셈블리는 자동으로 등록됩니다.  
  
## <a name="see-also"></a>관련 항목  
 [함수 &#40;MDX 구문&#41;](../mdx/functions-mdx-syntax.md)  
  
  
