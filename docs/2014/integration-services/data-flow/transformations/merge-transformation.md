---
title: 병합 변환 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.mergetrans.f1
helpviewer_keywords:
- merging datasets [Integration Services]
- merging data [Integration Services]
- Merge transformation
- combining datasets
- datasets [Integration Services], merging
ms.assetid: cff8690c-07ac-46a0-aab5-20bd4848c677
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 322caa6b9be17e860afaa1e3526a3590df049820
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/03/2018
ms.locfileid: "52790955"
---
# <a name="merge-transformation"></a>병합 변환
  병합 변환은 두 개의 정렬된 데이터 세트를 단일 데이터 세트로 결합합니다. 각 데이터 세트의 행은 해당 키 열의 값을 기반으로 출력에 삽입됩니다.  
  
 데이터 흐름에 병합 변환을 포함하면 다음 태스크를 수행할 수 있습니다.  
  
-   테이블 및 파일과 같은 데이터 원본 두 개의 데이터 병합  
  
-   병합 변환을 중첩하여 복잡한 데이터 세트를 만듭니다.  
  
-   데이터 오류를 수정한 후 행 다시 병합  
  
 병합 변환은 UNION ALL 변환과 유사합니다. 다음과 같은 경우 병합 변환 대신 UNION ALL 변환을 사용합니다.  
  
-   변환 입력이 정렬되지 않는 경우  
  
-   결합된 출력을 정렬할 필요가 없는 경우  
  
-   변환에 둘 이상의 입력이 있는 경우  
  
## <a name="input-requirements"></a>입력 요구 사항  
 병합 변환에는 정렬된 데이터를 입력해야 합니다. 이러한 중요 요구 사항에 대한 자세한 내용은 [병합 및 병합 조인 변환을 위한 데이터 정렬](sort-data-for-the-merge-and-merge-join-transformations.md)을 참조하세요.  
  
 또한 병합 변환에 입력한 병합된 열에는 일치하는 메타데이터가 있어야 합니다. 예를 들어 숫자 데이터 형식의 열을 문자 데이터 형식의 열과 병합할 수는 없습니다. 데이터가 문자열 데이터 형식이면 두 번째 입력의 열 길이는 함께 병합될 첫 번째 입력의 열 길이보다 작거나 같아야 합니다.  
  
 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 디자이너에서 병합 변환용 사용자 인터페이스는 동일한 메타데이터가 있는 열을 자동으로 매핑합니다. 그런 다음 호환 가능한 데이터 형식의 다른 열을 수동으로 매핑할 수 있습니다.  
  
 이 변환에는 두 개의 입력과 하나의 출력이 있습니다. 오류 출력은 지원하지 않습니다.  
  
## <a name="configuration-of-the-merge-transformation"></a>병합 변환 구성  
 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 디자이너를 사용하거나 프로그래밍 방식으로 속성을 설정할 수 있습니다.  
  
 **병합 변환 편집기** 대화 상자에서 설정할 수 있는 속성에 대한 자세한 내용은 [Merge Transformation Editor](../../merge-transformation-editor.md)를 참조하십시오.  
  
 프로그래밍 방식으로 설정할 수 있는 속성에 대한 자세한 내용을 보려면 다음 항목 중 하나를 클릭하십시오.  
  
-   [Common Properties](../../common-properties.md)  
  
-   [변환 사용자 지정 속성](transformation-custom-properties.md)  
  
## <a name="related-tasks"></a>관련 작업  
 속성을 설정하는 방법에 대한 자세한 내용은 다음 항목을 참조하십시오.  
  
-   [데이터 흐름 구성 요소의 속성 설정](../set-the-properties-of-a-data-flow-component.md)  
  
-   [병합 및 병합 조인 변환을 위한 데이터 정렬](sort-data-for-the-merge-and-merge-join-transformations.md)  
  
## <a name="see-also"></a>관련 항목  
 [병합 조인 변환](merge-join-transformation.md)   
 [UNION ALL 변환](union-all-transformation.md)   
 [데이터 흐름](../data-flow.md)   
 [Integration Services 변환](integration-services-transformations.md)  
  
  
