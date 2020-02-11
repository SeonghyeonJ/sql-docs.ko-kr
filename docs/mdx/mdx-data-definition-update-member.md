---
title: UPDATE MEMBER 문 (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 73a2bf2973d8c4f8f9bf9ac886728fb45250343f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68038141"
---
# <a name="mdx-data-definition---update-member"></a>MDX 데이터 정의 - UPDATE MEMBER


  기존 계산 멤버를 업데이트합니다.  
  
## <a name="syntax"></a>구문  
  
```  
  
UPDATE MEMBER Cube_Name.Member_Name   
   AS MDX_Expression  
      [,Property_Name = Property_Value, ...n]  
......[,SCOPE_ISOLATION = CUBE]  
```  
  
## <a name="arguments"></a>인수  
 *Cube_Name*  
 멤버가 포함된 큐브의 이름을 지정하는 유효한 문자열입니다.  
  
 *Member_Name*  
 기존 멤버의 이름을 지정하는 유효한 문자열입니다.  
  
 *MDX_Expression*  
 멤버가 업데이트되는 유효한 MDX 식입니다.  
  
 *Property_Name*  
 계산 멤버 속성의 이름을 지정하는 유효한 문자열입니다.  
  
 *Property_Value*  
 계산 멤버의 속성 값을 지정하는 유효한 스칼라 식입니다.  
  
## <a name="remarks"></a>설명  
 UPDATE MEMBER 문은 다른 계산에 따라 이 멤버의 상대적 우선 순위는 보존하면서 기존 계산 멤버를 업데이트합니다. 따라서 UPDATE MEMBER 문을 사용하여 SOLVEORDER를 변경할 수 없습니다.  
  
 UPDATE MEMBER 문은 큐브의 MDX 스크립트에 지정할 수 없습니다.  
  
 현재 연결된 큐브가 아닌 다른 큐브를 지정하면 오류가 발생합니다. 따라서 큐브 이름에서 CURRENTCUBE를 사용하여 현재 큐브를 표시해야 합니다.  
  
 OLE DB에 의해 정의되는 멤버 속성에 대한 자세한 내용은 OLE DB 설명서를 참조하십시오.  
  
## <a name="standard-properties"></a>표준 속성  
 각 멤버에는 기본 속성 집합이 있습니다. 다음 표에서는 이 기본 속성에 대해 설명합니다.  
  
|속성 식별자|의미|  
|-------------------------|-------------|  
|FORMAT_STRING|클라이언트 응용 프로그램에서 셀 값을 표시 하는 데 사용할 수 있는 Office 스타일 서식 문자열입니다.|  
|VISIBLE|계산 멤버를 스키마 행 집합에서 볼 수 있는지 여부를 나타내는 값입니다. [AddCalculatedMembers](../mdx/addcalculatedmembers-mdx.md) 함수를 사용 하 여 집합에 표시 되는 계산 멤버를 추가할 수 있습니다. 0이 아닌 값은 계산 멤버를 볼 수 있음을 나타냅니다. 이 속성의 기본값은 *표시*됩니다.<br /><br /> 볼 수 없는 계산 멤버는 일반적으로 더 복잡한 계산 멤버에서 중간 단계로 사용됩니다. 이런 계산 멤버는 측정값과 같은 다른 종류의 멤버가 참조할 수도 있습니다.|  
|NON_EMPTY_BEHAVIOR|빈 셀을 확인할 때 계산 멤버의 동작을 결정하기 위해 MDX가 사용하는 측정값 또는 집합입니다.|  
|CAPTION|클라이언트 애플리케이션이 멤버를 표시하기 위해 사용하는 캡션을 지정하는 문자열 값입니다.|  
|DISPLAY_FOLDER|클라이언트 애플리케이션이 멤버를 표시하는 표시 폴더의 경로를 지정하는 문자열 값입니다. 폴더 수준 구분 기호는 클라이언트 애플리케이션에서 정의합니다. 에서 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]제공 하는 도구와 클라이언트의 경우에는\\백슬래시 ()가 수준 구분 기호입니다. 정의 멤버에 대해 여러 표시 폴더를 제공하려면 세미콜론(;)을 사용하여 폴더를 구분하십시오.|  
|ASSOCIATED_MEASURE_GROUP|이 멤버를 연결할 측정값 그룹의 이름입니다.|  
  
## <a name="see-also"></a>참고 항목  
 [DROP MEMBER 문 &#40;MDX&#41;](../mdx/mdx-data-definition-drop-member.md)   
 [CREATE MEMBER 문 &#40;MDX&#41;](../mdx/mdx-data-definition-create-member.md)   
 [Mdx 데이터 정의 문은 MDX를 &#40;&#41;](../mdx/mdx-data-definition-statements-mdx.md)  
  
  
