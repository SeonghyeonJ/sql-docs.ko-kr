---
title: 열 Null 비율 프로필 요청 옵션(데이터 프로파일링 태스크) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Data Profiling Task Editor
ms.assetid: 157ef8e4-fd23-4f81-8194-eebf74e9fd86
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 470fcd41ed1605374ee3a5c4d5bb69b8b44c0c0d
ms.sourcegitcommit: c8e1553ff3fdf295e8dc6ce30d1c454d6fde8088
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/22/2020
ms.locfileid: "86923983"
---
# <a name="column-null-ratio-profile-request-options-data-profiling-task"></a>열 Null 비율 프로필 요청 옵션(데이터 프로파일링 태스크)

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]


  **프로필 요청** 페이지의 **요청 속성** 창을 사용하여 요청 창에서 선택한 **열 Null 비율 프로필 요청** 의 옵션을 설정할 수 있습니다. 열 Null 비율 프로필은 선택한 열에 있는 Null 값의 비율을 보고합니다. 이 프로필을 사용하면 예기치 않게 높은 열 내 Null 값의 비율과 같은 데이터 문제를 식별할 수 있습니다. 예를 들어 열 Null 비율 프로필은 ZIP Code/Postal Code 열을 프로파일링하는 중 허용 불가능한 수준으로 높은 누락된 코드 비율을 검색할 수 있습니다.  
  
> [!NOTE]  
>  이 항목에서 설명하는 옵션은 **데이터 프로파일링 태스크 편집기** 의 **프로필 요청 페이지**에 나타납니다. 편집기의 이 페이지에 대한 자세한 내용은 [데이터 프로파일링 태스크 편집기&#40;프로필 요청 페이지&#41;](../../integration-services/control-flow/data-profiling-task-editor-profile-requests-page.md)를 참조하세요.  
  
 데이터 프로파일링 태스크를 사용하는 방법에 대한 자세한 내용은 [데이터 프로파일링 태스크 설정](../../integration-services/control-flow/setup-of-the-data-profiling-task.md)을 참조하세요. 데이터 프로필 뷰어를 사용하여 데이터 프로파일링 태스크의 출력을 분석하는 방법에 대한 자세한 내용은 [데이터 프로필 뷰어](../../integration-services/control-flow/data-profile-viewer.md)를 참조하세요.  
  
## <a name="request-properties-options"></a>요청 속성 옵션  
 **열 Null 비율 프로필 요청**에 대해 **요청 속성** 창에는 다음 옵션 그룹이 표시됩니다.  
  
-   **데이터**- **TableOrView** 및 **Column** 옵션이 포함되어 있습니다.  
  
-   **일반**  
  
### <a name="data-options"></a>데이터 옵션  
 **ConnectionManager**  
 .NET Data Provider for [!INCLUDE[vstecado](../../includes/vstecado-md.md)] (SqlClient)를 사용하여 프로파일링할 테이블이나 뷰가 포함된 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터베이스에 연결하는 기존 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 연결 관리자를 선택합니다.  
  
 **TableOrView**  
 프로파일링할 열이 포함된 기존 테이블이나 뷰를 선택합니다.  
  
 자세한 내용은 이 항목의 "TableorView 옵션" 섹션을 참조하십시오.  
  
 **열**  
 프로파일링할 기존 열을 선택합니다. 모든 열을 프로파일링하려면 **(\*)** 를 선택합니다.  
  
 자세한 내용은 이 항목의 "열 옵션" 섹션을 참조하십시오.  
  
#### <a name="tableorview-options"></a>TableOrView 옵션  
 **스키마**  
 선택한 테이블이 속해 있는 스키마를 지정합니다. 이 옵션은 읽기 전용입니다.  
  
 **테이블**  
 선택한 테이블의 이름을 표시합니다. 이 옵션은 읽기 전용입니다.  
  
#### <a name="column-options"></a>열 옵션  
 **IsWildCard**  
 **(\*)** 와일드카드가 선택되었는지 여부를 지정합니다. 이 옵션은 모든 열을 프로파일링하도록 **(\*)** 를 선택한 경우 **True**로 설정됩니다. 프로파일링할 개별 열을 선택한 경우에는 **False** 로 설정됩니다. 이 옵션은 읽기 전용입니다.  
  
 **ColumnName**  
 선택한 열의 이름을 표시합니다. 이 옵션은 모든 열을 프로파일링하도록 **(\*)** 를 선택한 경우 비어 있습니다. 이 옵션은 읽기 전용입니다.  
  
 **StringCompareOptions**  
 이 옵션은 열 Null 비율 프로필에 적용되지 않습니다.  
  
### <a name="general-options"></a>일반 옵션  
 **RequestID**  
 이 프로필 요청을 식별할 설명이 포함된 이름을 입력합니다. 일반적으로 자동 생성된 값은 변경하지 않아도 됩니다.  
  
## <a name="see-also"></a>참고 항목  
 [데이터 프로파일링 태스크 편집기&#40;일반 페이지&#41;](../../integration-services/control-flow/data-profiling-task-editor-general-page.md)   
 [단일 테이블 빠른 프로필 형식&#40;데이터 프로파일링 태스크&#41;](../../integration-services/control-flow/single-table-quick-profile-form-data-profiling-task.md)  
  
  
