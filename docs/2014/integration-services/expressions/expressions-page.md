---
title: 식 페이지 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.expressionspage.f1
helpviewer_keywords:
- Expressions Page dialog box
ms.assetid: c9016ec6-11c1-4ebd-b2a7-0fa6631fd9e4
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 4cb37061fd90f8662ee6670bb558e99035c792e7
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62898035"
---
# <a name="expressions-page"></a>식 페이지
  **식** 페이지를 사용하여 속성 식을 편집하고 **속성 식 편집기** 및 **식 작성기** 대화 상자에 액세스할 수 있습니다.  
  
 속성 식은 패키지 실행 시 속성 값을 업데이트합니다. 패키지, 태스크, 컨테이너, 연결 관리자 및 일부 데이터 흐름 구성 요소의 속성에 속성 식을 사용할 수 있습니다. 식이 평가되고 그 결과가 패키지 및 패키지 개체를 구성할 때 설정한 속성 값 대신 사용됩니다. 식에는 식 언어가 제공하는 함수 및 연산자와 변수가 포함될 수 있습니다. 예를 들어 "Weather forecast for " 문자열이 포함된 변수 값과 GETDATE() 함수의 반환 결과를 연결하여 "Weather forecast for 4/5/2006" 문자열을 만들면 메일 보내기 태스크의 제목 줄을 생성할 수 있습니다.  
  
 식을 작성하고 속성 식을 사용하는 방법은 [Integration Services&#40;SSIS&#41; 식](integration-services-ssis-expressions.md) 및 [패키지에서 속성 식 사용](use-property-expressions-in-packages.md)을 참조하세요.  
  
## <a name="options"></a>변수  
 **식(...)**  
 **속성 식 편집기** 대화 상자를 열려면 줄임표를 클릭합니다. 자세한 내용은 [Property Expressions Editor](property-expressions-editor.md)를 참조하세요.  
  
 **\<속성 이름>**  
 **식 작성기** 대화 상자를 열려면 줄임표를 클릭합니다. 자세한 내용은 [Expression Builder](expression-builder.md)를 참조하세요.  
  
## <a name="see-also"></a>관련 항목  
 [Integration Services&#40;SSIS&#41; 변수](../integration-services-ssis-variables.md)   
 [시스템 변수](../system-variables.md)   
 [Integration Services&#40;SSIS&#41; 식](integration-services-ssis-expressions.md)  
  
  
