---
title: 식 대화 상자 (보고서 작성기) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10040"
helpviewer_keywords:
- expressions
ms.assetid: e89c4d97-5d41-4b55-8695-79329edac15d
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: c6f12a39c1456c179187654445947de9ee7d87a9
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66109153"
---
# <a name="expression-dialog-box-report-builder"></a>식 대화 상자(보고서 작성기)
  사용 된 **식** 쓸 대화 상자 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] 식이 보고서 항목 속성입니다. 식을 사용하여 색, 글꼴 및 테두리를 비롯한 여러 속성을 설정할 수 있습니다. 런타임에 보고서 처리기는 식을 계산하고 그 결과로 속성의 값을 대체합니다.  
  
 **식** 대화 상자에는 코드 창, 범주 트리, 범주 항목, 설명 창 및 예 창이 있습니다. 합니다 **식** 대화 상자는 상황에 맞는, 사용 중인 식 범주에 따라 범주 항목과 설명이 변경 됩니다. 자세한 내용은 [식 예제 &#40;보고서 작성기 및 SSRS&#41;](report-design/expression-examples-report-builder-and-ssrs.md)합니다 [식 &#40;보고서 작성기 및 SSRS&#41;](report-design/expressions-report-builder-and-ssrs.md)  
  
## <a name="expression-constructs"></a>식 생성  
 식은 등호(=)로 시작하며 상수, 리터럴, 연산자, 기본 제공 필드에 대한 참조, 기본 제공 컬렉션, 기본 제공 함수, [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] 런타임 라이브러리 함수, [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 공용 언어 런타임 클래스 및 사용자 지정 함수를 포함할 수 있습니다. 다음 목록에서는 식에 추가할 수 있는 범주와 값에 대해 설명합니다.  
  
 **에 대 한 식 설정:**  _\<PropertyName>_  
 식을 정의하는 속성의 이름입니다. 이 속성은 속성 창에서 이름으로 설정할 수도 있습니다.  
  
 **상수**  
 상수에 기반을 두는 속성에 대한 이 속성에 유효한 미리 정의된 값 목록을 제공합니다. 예를 들어 색에 기반을 두는 속성은 유효한 색 이름을 보여 줍니다. 부울 데이터 형식의 속성인 경우 값은 `True` 및 `False`입니다.  
  
 식을 지원하는 모든 항목을 상수로 설정할 수 있는 것은 아닙니다. 속성을 상수 값으로 설정할 수 없는 경우 설명 창에 이러한 정보가 표시됩니다.  
  
 **기본 제공 필드**  
 식에 사용할 수 있는 전역 컬렉션의 항목 목록을 제공합니다. 일부 컬렉션은 보고서를 서버로 게시한 이후에만 지원됩니다. 자세한 내용은 [식의 기본 제공 컬렉션&#40;보고서 작성기 및 SSRS&#41;](report-design/built-in-collections-in-expressions-report-builder.md)을 참조하세요.  
  
 **매개 변수**  
 보고서 매개 변수 목록을 제공합니다.  
  
 **필드 (**  _\<데이터 집합 선택 >_ **)**  
 데이터 세트 범주에 선택된 데이터 세트에 대한 필드 목록을 표시합니다. 필드를 두 번 클릭하여 필드를 **식** 상자에 복사할 수 있습니다.  
  
 **데이터 집합**  
 사용 가능한 데이터 세트의 목록을 제공하고 데이터 세트의 멤버 필드를 표시합니다.  
  
 **변수**  
 보고서 변수의 목록을 표시합니다. 자세한 내용은 [보고서 및 그룹 변수 컬렉션 참조&#40;보고서 작성기 및 SSRS&#41;](report-design/built-in-collections-report-and-group-variables-references-report-builder.md)를 참조하세요.  
  
 **연산자**  
 계산 또는 문자열 조작에 포함할 수 있는 연산자를 표시합니다. 자세한 내용은 [식의 연산자&#40;보고서 작성기 및 SSRS&#41;](report-design/operators-in-expressions-report-builder-and-ssrs.md)를 참조하세요.  
  
 **일반 함수**  
 일반 함수를 형식에 따라 그룹화하여 표시합니다. 항목 창에서 함수를 선택하면 설명과 예가 표시됩니다.  
  
 일반 함수에는 기본 제공 보고서 및 집계 함수, [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] 런타임 라이브러리 함수, 그리고 <xref:System.Math> 및 <xref:System.Convert> 네임스페이스의 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] CLR(공용 언어 런타임) 클래스가 포함됩니다. 범주 목록에 나타나지 않는 CLR 클래스와 외부 어셈블리에 대한 참조를 추가할 수도 있습니다. 자세한 내용은 [보고서 디자이너의 식에 포함된 사용자 지정 코드 및 어셈블리 참조&#40;SSRS&#41;](report-design/custom-code-and-assembly-references-in-expressions-in-report-designer-ssrs.md)를 참조하세요.  
  
## <a name="options"></a>변수  
 코드 창  
 창 맨 위에 있는 코드 창을 사용하여 식을 입력할 수 있습니다. **식** 대화 상자를 열면 코드 창에 식이 포함됩니다. 이러한 식을 바꾸거나 수정할 수 있습니다. 함수 호출, 연산자, 상수, 필드, 매개 변수, 전역 컬렉션의 항목 및 사용자 지정 코드에 대한 참조를 추가할 수 있습니다. 코드 창에는 변경 내용이 표시됩니다.  
  
 빨강 물결선 밑줄은 구문 오류를 나타냅니다. 오류 메시지를 보려면 밑줄이 그어진 텍스트를 포인터로 가리킵니다.  
  
 전역 컬렉션 용어 다음에 문장 구분 기호를 입력하면 사용 가능한 멤버 또는 속성이 포함된 드롭다운 목록이 표시됩니다. 드롭다운 목록에서 처음 몇 자를 입력한 다음 탭 키를 누르면 선택 내용을 자동으로 채울 수 있습니다.  
  
 함수 이름 뒤에 왼쪽 괄호를 붙여 입력하면 매개 변수와 함수 반환 값에 대한 정보를 제공하는 도구 설명이 표시됩니다.  
  
 **범주**  
 식의 범주를 표시합니다. 범주를 선택하면 식을 만들기 위한 컨텍스트가 설정되고 항목 창의 유효한 값 목록이 변경됩니다. 예를 들어 입력란 값에 대 한 식에 대 한 일반 함수를 확장 하 고 집계 함수 선택 표시할 `Avg`, `Count`, 및 다른 함수를 합니다 **항목** 창입니다.  
  
 **항목**  
 선택된 범주에 대한 유효한 값의 목록을 표시합니다. 코드 창의 삽입 지점에 항목에 대한 식 텍스트를 추가하려면 항목을 두 번 클릭합니다.  
  
 **값**  
 선택하는 범주와 항목에 따라 세 번째 창에는 설명, 샘플 식 또는 유효한 값 목록이 포함됩니다. 대화 상자의 가장자리를 끌어서 샘플 영역을 넓힐 수 있습니다.  
  
## <a name="see-also"></a>관련 항목  
 [식&#40;보고서 작성기 및 SSRS&#41;](report-design/expressions-report-builder-and-ssrs.md)   
 [보고서 항목 서식 지정&#40;보고서 작성기 및 SSRS&#41;](report-design/formatting-report-items-report-builder-and-ssrs.md)   
 [숫자 및 날짜 서식 지정&#40;보고서 작성기 및 SSRS&#41;](report-design/formatting-numbers-and-dates-report-builder-and-ssrs.md)   
 [매개 변수 컬렉션 참조&#40;보고서 작성기 및 SSRS&#41;](report-design/built-in-collections-parameters-collection-references-report-builder.md)   
 [그룹 식 예&#40;보고서 작성기 및 SSRS&#41;](report-design/group-expression-examples-report-builder-and-ssrs.md)   
 [필터 수식 예&#40;보고서 작성기 및 SSRS&#41;](report-design/filter-equation-examples-report-builder-and-ssrs.md)   
 [데이터 집합 필드 컬렉션 참조 &#40;보고서 작성기 및 SSRS&#41;](report-design/built-in-collections-dataset-fields-collection-references-report-builder.md)   
 [집계 함수 참조&#40;보고서 작성기 및 SSRS&#41;](report-design/report-builder-functions-aggregate-functions-reference.md)   
 [식의 데이터 형식&#40;보고서 작성기 및 SSRS&#41;](report-design/data-types-in-expressions-report-builder-and-ssrs.md)   
 [색 선택 대화 상자 &#40;보고서 작성기 및 SSRS&#41;](../../2014/reporting-services/select-color-dialog-box-report-builder-and-ssrs.md)  
  
  
