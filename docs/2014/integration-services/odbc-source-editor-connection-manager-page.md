---
title: ODBC 원본 편집기 (연결 관리자 페이지) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.ssis.designer.odbcsource.connection.f1
ms.assetid: e2c8dc83-6394-4d6c-9232-97e94be72431
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b0935ba4cd76a458bd26438556bab56e6cfa091c
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/26/2020
ms.locfileid: "85424260"
---
# <a name="odbc-source-editor-connection-manager-page"></a>ODBC 원본 편집기(연결 관리자 페이지)
  **ODBC 원본 편집기** 대화 상자의 **연결 관리자** 페이지를 사용하여 원본의 ODBC 연결 관리자를 선택할 수 있습니다. 이 페이지를 사용하면 데이터베이스에서 테이블이나 뷰를 선택할 수도 있습니다.  
  
 ODBC 원본에 대한 자세한 내용은 [ODBC Source](data-flow/odbc-source.md)을 참조하십시오.  
  
## <a name="task-list"></a>작업 목록  
 **ODBC 원본 편집기의 연결 관리자 페이지를 열려면**  
  
-   [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]에서 ODBC 원본이 있는 [!INCLUDE[ssISCurrent](../includes/ssiscurrent-md.md)] 패키지를 엽니다.  
  
-   **데이터 흐름** 탭에서 ODBC 원본을 두 번 클릭합니다.  
  
## <a name="options"></a>옵션  
  
### <a name="connection-manager"></a>ODBC 대상 편집기  
 목록에서 기존 ODBC 연결 관리자를 선택 하거나 **새로** 만들기를 클릭 하 여 새 연결을 만듭니다. 어느 ODBC 지원 데이터베이스에나 연결할 수 있습니다.  
  
### <a name="new"></a>단추를 사용하여 새  
 **새로 만들기**를 클릭합니다. 새 ODBC 연결 관리자를 만들 수 있는 **ODBC 연결 관리자 편집기 구성** 대화 상자가 열립니다.  
  
### <a name="data-access-mode"></a>데이터 액세스 모드  
 원본에서 데이터를 선택하는 방법을 선택합니다. 옵션은 다음 표에 표시되어 있습니다.  
  
|옵션|설명|  
|------------|-----------------|  
|테이블 이름|ODBC 데이터 원본에 있는 테이블이나 뷰에서 데이터를 검색합니다. 이 옵션을 선택할 경우 다음 목록에서 값을 선택합니다.|  
||**테이블 또는 뷰 이름**: 목록에서 사용 가능한 테이블 또는 뷰를 선택하거나 테이블을 식별할 수 있는 정규식을 입력합니다.|  
||이 목록에는 처음 1000개의 테이블만 포함되어 있습니다. 데이터베이스에 포함되어 있는 테이블이 1000개를 넘는 경우 테이블 이름의 시작 부분을 입력하거나 와일드카드(*)를 통해 이름의 일부를 입력하여 사용할 테이블을 표시합니다.|  
|SQL 명령|SQL 쿼리를 사용하여 ODBC 데이터 원본에서 데이터를 검색합니다. 사용할 원본 데이터베이스의 구문으로 쿼리를 작성해야 합니다. 이 옵션을 선택할 경우 다음 중 한 가지 방법으로 쿼리를 입력합니다.|  
||**SQL 명령 텍스트** 필드에 SQL 쿼리 텍스트를 입력합니다.|  
||**찾아보기** 를 클릭하여 텍스트 파일에서 SQL 쿼리를 로드합니다.|  
||**쿼리 구문 분석** 을 클릭하여 쿼리 텍스트의 구문을 확인합니다.|  
  
### <a name="preview"></a>미리 보기  
 **미리 보기** 를 클릭하면 선택한 테이블 또는 뷰에서 추출된 최대 200개의 데이터 행을 볼 수 있습니다.  
  
## <a name="see-also"></a>참고 항목  
 [ODBC 원본 사용자 지정 속성](data-flow/odbc-source-custom-properties.md)   
 [ODBC 원본 편집기 &#40;열 페이지&#41;](../../2014/integration-services/odbc-source-editor-columns-page.md)   
 [ODBC 원본 편집기&#40;오류 출력 페이지&#41;](../../2014/integration-services/odbc-source-editor-error-output-page.md)  
  
  
