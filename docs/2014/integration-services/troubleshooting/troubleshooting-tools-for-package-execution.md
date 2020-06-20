---
title: 패키지 실행 문제 해결 도구 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Integration Services packages, troubleshooting
- SSIS packages, troubleshooting
- Integration Services, troubleshooting
- errors [Integration Services], troubleshooting
- packages [Integration Services], troubleshooting
ms.assetid: f18d6ff6-e881-444c-a399-730b52130e7c
author: janinezhang
ms.author: janinez
ms.openlocfilehash: e7aac9aa2dc6c7675414354c729f4537479ee8a1
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84972693"
---
# <a name="troubleshooting-tools-for-package-execution"></a>패키지 실행 문제 해결 도구
  [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 에서는 패키지를 완성 및 배포한 후 실행할 때 패키지 문제를 해결하는 데 사용할 수 있는 기능 및 도구를 제공합니다.  
  
 디자인 타임에 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 에서는 패키지 실행을 일시 중지하기 위한 중단점, 진행률 창 및 데이터가 데이터 흐름을 통과할 때 데이터를 감시하기 위한 데이터 뷰어를 제공합니다. 그러나 배포된 패키지를 실행할 때는 이러한 기능을 사용할 수 없습니다. 배포된 패키지의 문제를 해결하는 주요 방법은 다음과 같습니다.  
  
-   이벤트 처리기를 사용하여 패키지 오류 파악 및 처리  
  
-   오류 출력을 사용하여 잘못된 데이터 캡처  
  
-   로깅을 사용하여 패키지 실행 단계 추적  
  
 다음 팁과 기술을 사용하여 패키지 실행과 관련된 문제를 방지할 수도 있습니다.  
  
-   **트랜잭션을 사용하여 데이터 무결성 유지** 자세한 내용은 [Integration Services 트랜잭션](../integration-services-transactions.md)을 참조하세요.  
  
-   **검사점을 사용하여 실패한 지점에서 패키지 다시 시작** 자세한 내용은 [검사점을 사용하여 패키지 다시 시작](../packages/restart-packages-by-using-checkpoints.md)을 참조하세요.  
  
## <a name="catch-and-handle-package-errors-by-using-event-handlers"></a>이벤트 처리기를 사용하여 패키지 오류 파악 및 처리  
 이벤트 처리기를 사용하여 패키지 및 패키지의 개체에서 발생한 여러 이벤트에 대응할 수 있습니다.  
  
-   **OnError 이벤트의 이벤트 처리기 만들기** 이벤트 처리기에서 메일 보내기 태스크를 사용하여 관리자에게 오류를 알리거나, 스크립트 작업 및 사용자 지정 논리를 사용하여 문제 해결을 위한 시스템 정보를 가져오거나, 임시 리소스 또는 완전하지 않은 출력을 정리할 수 있습니다. 자세한 내용은 [Integration Services&#40;SSIS&#41; 이벤트 처리기](../integration-services-ssis-event-handlers.md)를 참조하세요.  
  
## <a name="troubleshoot-bad-data-by-using-error-outputs"></a>오류 출력을 사용하여 잘못된 데이터 문제 해결  
 여러 데이터 흐름 구성 요소에서 사용할 수 있는 오류 출력을 통해 오류가 들어 있는 행을 나중에 분석할 수 있도록 별도의 대상으로 보낼 수 있습니다.  
  
-   **오류 출력을 사용하여 잘못된 데이터 캡처** 오류가 들어 있는 행을 오류 테이블이나 텍스트 파일과 같은 별도의 대상으로 보냅니다. 오류 출력에는 행이 거부되도록 한 오류의 번호와 오류가 발생한 열의 ID가 들어 있는 두 개의 숫자 열이 자동으로 추가됩니다. 자세한 내용은 [데이터 오류 처리](../data-flow/error-handling-in-data.md)를 참조하세요.  
  
-   **오류 출력에 정보 추가** 오류 출력에 제공되는 두 개의 숫자 식별자 외에 설명 정보를 추가하여 오류 출력을 분석하기 쉽게 만들 수 있습니다.  
  
     **오류에 대 한 설명을 추가**합니다. 스크립트 구성 요소를 사용하여 오류 설명을 쉽게 찾을 수 있습니다. 자세한 내용은 [스크립트 구성 요소에 대 한 오류 출력 향상](../extending-packages-scripting-data-flow-script-component-examples/enhancing-an-error-output-with-the-script-component.md)을 참조 하세요.  
  
     **오류 열의 이름을 추가**합니다. 스크립트 구성 요소에서는 오류 출력에 저장된 열 ID에 해당하는 열 이름을 쉽게 찾을 수 없으므로 추가 단계가 필요합니다. 데이터 흐름의 각 열 ID는 해당 데이터 흐름 태스크 내에서 고유하며 디자인 타임에 패키지에 보관됩니다. 다음은 오류 출력에 열 이름을 추가하는 데 적절한 방법입니다. 
  
    1.  **열 이름의 조회 테이블을 만듭니다**. [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] API를 사용하여 저장된 각 패키지, 패키지의 각 데이터 흐름, 데이터 흐름의 각 개체 및 데이터 흐름 개체의 각 입/출력에 대해 반복하는 별도의 애플리케이션을 만듭니다. 이 애플리케이션은 각 열의 열 ID 및 이름을 부모 데이터 흐름 태스크의 ID 및 패키지의 ID와 함께 조회 테이블에 보관해야 합니다.  
  
    2.  **열 이름을 출력에 추가**합니다. 이전 단계에서 만든 조회 테이블에서 열 이름을 찾는 조회 변환을 오류 출력에 추가합니다. 조회할 때는 오류 출력의 열 ID, 시스템 변수 System::PackageID에서 사용할 수 있는 패키지 ID 및 시스템 변수 System::TaskID에서 사용할 수 있는 데이터 흐름 태스크의 ID를 사용할 수 있습니다.  
  
## <a name="troubleshoot-package-execution-by-using-operations-reports"></a>작업 보고서를 사용하여 패키지 실행 문제 해결  
 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 에서는 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 카탈로그에 배포된 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 패키지를 모니터링하는 데 도움이 되는 표준 작업 보고서가 제공됩니다. 이러한 패키지 보고서는 패키지 상태 및 기록을 보고 필요한 경우 실패 원인을 파악하는 데 도움이 됩니다.  
  
 자세한 내용은 [패키지 실행 보고서 문제 해결](troubleshooting-reports-for-package-execution.md)을 참조하세요.  
  
## <a name="troubleshoot-package-execution-by-using-ssisdb-views"></a>SSISDB 뷰를 사용하여 패키지 실행 문제 해결  
 패키지 실행 및 기타 작업 정보를 모니터링하기 위해 쿼리할 수 있는 다양한 SSISDB 데이터베이스 뷰가 제공됩니다. 자세한 내용은 [패키지 실행 및 기타 작업 모니터링](../performance/monitor-running-packages-and-other-operations.md)을 참조 하세요.  
  
## <a name="troubleshoot-package-execution-by-using-logging"></a>로깅을 사용하여 패키지 실행 문제 해결  
 로깅을 설정하여 실행하는 패키지에서 발생하는 문제를 대부분 추적할 수 있습니다. 로그 공급자는 지정된 이벤트에 대한 정보를 나중에 분석할 수 있도록 캡처하고 해당 정보를 데이터베이스 테이블, 플랫 파일, XML 파일 또는 지원되는 다른 출력 형식으로 저장합니다.  
  
-   **로깅 설정** 캡처할 이벤트와 정보 항목만 선택하여 로깅 출력을 구체화할 수 있습니다. 자세한 내용은 [Integration Services&#40;SSIS&#41; 로깅](../performance/integration-services-ssis-logging.md) 및 [Integration Services&#40;SSIS&#41; 로깅](../performance/integration-services-ssis-logging.md)을 참조하세요.  
  
-   **패키지의 Diagnostic 이벤트를 선택하여 공급자 문제 해결.** 외부 데이터 원본과의 패키지 상호 작용 문제를 해결하는 데 유용한 로깅 메시지가 있습니다. 자세한 내용은 [패키지 연결 문제 해결 도구](troubleshooting-tools-for-package-connectivity.md)을 참조하세요.  
  
-   **기본 로깅 출력 향상**. 로깅 기능은 일반적으로 패키지가 실행될 때마다 로깅 대상에 행을 추가합니다. 로깅 출력의 각 행이 패키지를 이름과 고유 식별자로 식별하고 패키지 실행을 고유 ExecutionID로 식별하더라도 단일 목록에 많은 양의 로깅 출력이 있으면 분석하기가 어려울 수 있습니다.  
  
     다음은 기본 로깅 출력을 향상시키고 보고서를 쉽게 생성할 수 있도록 하는 데 적절한 방법입니다.  
  
    1.  **각 패키지 실행을 기록하는 부모 테이블 만들기** 이 부모 테이블은 각 패키지 실행에 대한 단일 행만 포함하며, ExecutionID를 사용하여 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 로깅 테이블의 자식 레코드에 연결합니다. 각 패키지가 시작될 때 SQL 실행 태스크를 사용하여 이 새 행을 만들고 시작 시간을 기록할 수 있습니다. 그런 다음 패키지가 끝날 때 다른 SQL 실행 태스크를 사용하여 해당 행을 종료 시간, 기간 및 상태로 업데이트할 수 있습니다.  
  
    2.  **데이터 흐름에 감사 정보 추가** 감사 변환을 사용하여 데이터 흐름의 행에 각 행을 만들었거나 수정한 패키지 실행에 대한 정보를 추가할 수 있습니다. 감사 변환을 통해 PackageName 및 ExecutionInstanceGUID를 비롯한 9가지 정보를 사용할 수 있습니다. 자세한 내용은 [감사 변환](../data-flow/transformations/audit-transformation.md)을 참조하세요. 감사를 위해 각 행에도 포함할 사용자 지정 정보가 있는 경우 파생 열 변환을 사용하여 이 정보를 데이터 흐름의 행에 추가할 수 있습니다. 자세한 내용은 [파생 열 변환](../data-flow/transformations/derived-column-transformation.md)을 참조하세요.  
  
    3.  **행 개수 데이터 캡처** 행 개수 정보에 대한 별도의 테이블을 만듭니다. 이 테이블에서 패키지 실행의 각 인스턴스는 ExecutionID로 식별됩니다. 행 개수 변환을 사용하여 데이터 흐름의 중요 지점에서 일련의 변수에 행 개수를 저장합니다. 데이터 흐름이 끝난 후에는 나중에 분석 및 보고할 수 있도록 SQL 실행 태스크를 사용하여 일련의 값을 이 테이블의 행에 삽입합니다.  
  
     이 방법에 대한 자세한 내용은 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 백서 [Project REAL: 비즈니스 인텔리전스 ETL 디자인 방법](https://www.microsoft.com/download/details.aspx?id=14582)의 “ETL 감사 및 로깅” 섹션을 참조하세요.  
  
## <a name="troubleshoot-package-execution-by-using-debug-dump-files"></a>디버그 덤프 파일을 사용하여 패키지 실행 문제 해결  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]에서는 패키지 실행에 대한 정보를 제공하는 디버그 덤프 파일을 만들 수 있습니다. 자세한 내용은 [패키지 실행을 위한 덤프 파일 생성](generating-dump-files-for-package-execution.md)을 참조하세요.  
  
## <a name="troubleshoot-run-time-validation-issues"></a>런타임 유효성 검사 문제 해결  
 데이터 원본에 연결할 수 없거나 패키지의 이전 태스크가 실행 완료되기 전까지 패키지의 일부에 대해 유효성을 검사할 수 없는 경우가 있습니다. [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 에는 이러한 경우에 발생하는 유효성 검사 오류를 방지하는 데 유용한 다음과 같은 기능이 있습니다.  
  
-   **패키지가 로드될 때 유효하지 않은 패키지 요소의 DelayValidation 속성 구성** 구성이 유효하지 않은 패키지 요소의 `DelayValidation` 을 `True`로 설정하여 패키지가 로드될 때 유효성 검사 오류를 방지할 수 있습니다. 예를 들어 런타임에 SQL 실행 작업을 통해 테이블이 만들어지기 전까지는 존재하지 않는 대상 테이블을 사용하는 데이터 흐름 태스크가 있을 수 있습니다. `DelayValidation` 속성은 패키지 수준 또는 패키지에 포함된 개별 태스크 및 컨테이너 수준에서 설정할 수 있습니다.  
  
     `DelayValidation` 속성은 데이터 흐름 태스크에만 설정할 수 있고 개별 데이터 흐름 구성 요소에는 설정할 수 없습니다. 개별 데이터 흐름 구성 요소의 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.ValidateExternalMetadata%2A> 속성을 `false`로 설정하면 비슷한 효과를 얻을 수 있습니다. 그러나 이 속성 값이 `false`이면 구성 요소에서 외부 데이터 원본의 메타데이터에 대한 변경 내용을 인식하지 못하게 됩니다. <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.ValidateExternalMetadata%2A> 속성을 `true`로 설정하면 데이터베이스의 잠금으로 인한 차단 문제를 방지할 수 있습니다. 특히 패키지에서 트랜잭션을 사용하는 경우에 유용합니다.  
  
## <a name="troubleshoot-run-time-permissions-issues"></a>런타임 권한 문제 해결  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트를 사용하여 배포된 패키지를 실행하려고 할 때 오류가 발생하면 에이전트에서 사용하는 계정에 필요한 권한이 없는 것일 수 있습니다. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 작업에서 실행한 패키지의 문제를 해결하는 방법은 [SQL Server 에이전트 작업 단계에서 SSIS 패키지를 호출할 때 SSIS 패키지가 실행되지 않는다](https://support.microsoft.com/kb/918760)를 참조하십시오. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 작업에서 패키지를 실행하는 방법은 [패키지에 대한 SQL Server 에이전트 작업](../packages/sql-server-agent-jobs-for-packages.md)을 참조하세요.  
  
 Excel 또는 Access 데이터 원본에 액세스하려면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트에 TEMP 및 TMP 환경 변수로 지정되는 폴더에서 임시 파일을 읽고, 쓰고, 만들고, 삭제할 수 있는 사용 권한을 가진 계정이 있어야 합니다.  
  
## <a name="troubleshoot-64-bit-issues"></a>64비트 문제 해결  
  
-   **일부 데이터 공급자는 64비트 플랫폼에서 사용할 수 없습니다**. 특히 Excel 또는 Access 데이터 원본에 연결하는 데 필요한 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Jet OLE DB 공급자는 64비트 버전에서 사용할 수 없습니다.  
  
## <a name="troubleshoot-errors-without-a-description"></a>설명이 없는 오류 문제 해결  
 설명이 없는 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 오류가 발생할 경우 [Integration Services 오류 및 메시지 참조](../integration-services-error-and-message-reference.md) 에서 오류 번호로 조회하여 해당 오류에 대한 설명을 찾을 수 있습니다. 이 목록에는 현재 문제 해결 정보는 들어 있지 않습니다.  
  
## <a name="related-tasks"></a>관련 작업  
 [데이터 흐름 구성 요소에서 오류 출력 구성](../configure-an-error-output-in-a-data-flow-component.md)  
  
  
