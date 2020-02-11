---
title: Previous 함수(보고서 작성기 및 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 403a9384-6ca4-42e8-97ca-ac3f6fe4316b
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 540bf8367ba32fbebe4e27ee6e2cd3e1aa01ae0d
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66105196"
---
# <a name="previous-function-report-builder-and-ssrs"></a>Previous 함수(보고서 작성기 및 SSRS)
  지정된 범위 내에서 항목의 이전 인스턴스에 대한 지정된 집계 값 또는 값을 반환합니다.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="syntax"></a>구문  
  
```  
  
Previous(expression, scope)  
```  
  
#### <a name="parameters"></a>매개 변수  
 *expression*  
 (`Variant` 또는 `Binary`) 데이터를 식별하거나 이전 값을 검색하기 위한 식입니다(예: `Fields!Fieldname.Value` 또는 `Sum(Fields!Fieldname.Value)`).  
  
 *범위*  
 (`String`) 선택 사항입니다. 식으로 지정 된 이전 값을 검색할 범위를 지정 하`Nothing` 는 [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]그룹 또는 데이터 영역의 이름 이거나 null (의 경우)입니다. **  
  
## <a name="return-type"></a>반환 형식  
 
  `Variant` 또는 `Binary`를 반환합니다.  
  
## <a name="remarks"></a>설명  
 
  `Previous` 함수는 모든 정렬 및 필터링이 적용된 다음 지정된 범위에서 계산된 식의 이전 값을 반환합니다.  
  
 *식* 에 집계가 포함 되지 않은 경우이 함수 `Previous` 는 기본적으로 보고서 항목의 현재 범위를 설정 합니다.  
  
 세부 정보 그룹에서 `Previous`를 사용하여 세부 행의 이전 인스턴스에 필드 참조 값을 지정합니다.  
  
> [!NOTE]  
>  함수 `Previous` 는 세부 정보 그룹의 필드 참조만 지원 합니다. 예를 들어 세부 정보 그룹의 입력란에서 `=Previous(Fields!Quantity.Value)` 는 이전 행의 `Quantity` 필드에 대한 데이터를 반환합니다. 첫 번째 행에서 이 식은 Null(`Nothing`의 경우 [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)])을 반환합니다.  
  
 *식* 에 기본 범위를 사용 하는 집계 함수가 포함 된 `Previous` 경우는 집계 함수 호출에 지정 된 범위의 이전 인스턴스 내에서 데이터를 집계 합니다.  
  
 *식* 에 기본값 이외의 범위를 지정 하는 집계 함수가 포함 된 경우 `Previous` 함수의 *범위* 매개 변수는 집계 함수 호출에 지정 된 범위에 대해 포함 하는 범위 여야 합니다.  
  
 , `Level` `InScope` `Previous` 및 함수는 expression 매개 변수에 사용할 수 없습니다. ** `Aggregate` 집계 함수에 대해 *recursive* 매개 변수를 지정할 수 없습니다.  
  
 자세한 내용은 [집계 함수 참조&#40;보고서 작성기 및 SSRS&#41;](report-builder-functions-aggregate-functions-reference.md) 및 [합계, 집계 및 기본 제공 컬렉션의 식 범위&#40;보고서 작성기 및 SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md)를 참조하세요.  
  
## <a name="examples"></a>예  
  
### <a name="description"></a>Description  
 다음 코드 예는 데이터 영역의 기본 데이터 행에 배치될 경우 이전 행의 `LineTotal` 필드에 대한 값을 제공합니다.  
  
### <a name="code"></a>코드  
  
```  
=Previous(Fields!LineTotal.Value)  
```  
  
### <a name="description"></a>Description  
 다음 예에서는 월 중 특정 일에 대한 판매 합계를 계산하고 이전 연도의 해당 월 및 일에 대한 이전 값을 계산하는 식을 보여 줍니다. `GroupbyDay`자식 그룹에 속하는 행의 셀에 식이 추가됩니다. 부모 그룹은 `GroupbyMonth`이며 이 그룹의 부모 그룹은 `GroupbyYear`입니다. 식은 GroupbyDay(기본 범위)에 대한 결과와 `GroupbyYear` ( `GroupbyMonth`부모 그룹의 부모)에 대한 결과를 표시합니다.  
  
 예를 들어 `Year`라는 부모 그룹을 가진 데이터 영역의 경우 자식 그룹의 이름은 `Month`이고 이 그룹의 자식 그룹 이름은 `Day` 가 됩니다(3수준 중첩). `=Previous(Sum(Fields!Sales.Value,"Day"),"Year")` 그룹과 관련된 행에서 `Day` 식을 사용하면 이전 연도의 동일 월 및 일에 대한 판매 값이 반환됩니다.  
  
### <a name="code"></a>코드  
  
```  
=Sum(Fields!Sales.Value) & " " & Previous(Sum(Fields!Sales.Value,"GroupbyDay"),"GroupbyYear")  
```  
  
## <a name="see-also"></a>참고 항목  
 [보고서에 사용되는 식&#40;보고서 작성기 및 SSRS&#41;](expression-uses-in-reports-report-builder-and-ssrs.md)   
 [식 예&#40;보고서 작성기 및 SSRS&#41;](expression-examples-report-builder-and-ssrs.md)   
 [식의 데이터 형식&#40;보고서 작성기 및 SSRS&#41;](expressions-report-builder-and-ssrs.md)   
 [합계, 집계 및 기본 제공 컬렉션의 식 범위&#40;보고서 작성기 및 SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md)  
  
  
