---
title: SSMA 콘솔 (AccessToSQL) 실행 | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: aa1bf665-8dc0-4259-b36f-46ae67197a43
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: 97425a6795889f72b329280ff70f9638378e7799
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68006564"
---
# <a name="executing-the-ssma-console-accesstosql"></a>SSMA 콘솔 (AccessToSQL) 실행
Microsoft는 강력한 파일 명령 스크립트 및 실행 하 고 SSMA 작업을 제어 하는 명령줄 옵션을 제공 합니다. 결과 섹션을 자세히 설명 동일 합니다.  
  
## <a name="project--script-file-commands"></a>프로젝트 스크립트 파일 명령  
프로젝트 만들기, 열기, 저장 및 프로젝트를 기존 프로젝트 명령 핸들입니다.  
  
**Command**  
  
create-new-project: 새 SSMA 프로젝트를 만듭니다.  
  
**스크립트**  
  
-   `project-folder` 만든 가져오기 프로젝트의 폴더를 나타냅니다.  
  
-   `project-name` 프로젝트의 이름을 나타냅니다. {string}  
  
-   `overwrite-if-exists`선택적 특성 기존 프로젝트를 덮어써야 하는 경우를 나타냅니다. {부울}  
  
-   `project-type` 선택적 특성이입니다.  다음 옵션은 프로젝트 형식에 대해 사용할 수 있습니다.  
  
    -   sql-server-2005  
  
    -   sql-server-2008  
  
    -   sql-server-2012  
  
    -   sql-server-2014  
  
    -   sql-server-2016  
  
    -   sql-azure  
  
    기본값은 "sql server 2008"입니다.  
  
**예제:**  
  
```xml  
<create-new-project  
  
  project-folder="<project-folder>"  
  
  project-name="<project-name>"  
  
  overwrite-if-exists="<true/false>"  
  
  project-type="<sql-server-2008 | sql-server-2005 | sql-server-2012 | sql-server-2014 | sql-azure>"  
  
/>  
```  
' 덮어쓰기--있는 경우 ' 특성은 **false** 기본적으로 합니다.  
  
특성이 ' 프로젝트 형식 ' **sql server-2008** 기본적으로 합니다.  
  
**Command**  
  
오픈-프로젝트: 기존 프로젝트를 엽니다.  
  
**스크립트**  
  
-   `project-folder` 만든 가져오기 프로젝트의 폴더를 나타냅니다. 이 명령은 지정된 된 폴더가 없는 경우 실패 합니다.  {string}  
  
-   `project-name` 프로젝트의 이름을 나타냅니다. 이 명령은 지정 된 프로젝트가 존재 하지 않는 경우 실패 합니다.  {string}  
  
**구문 예제:**  
  
```xml  
<open-project  
  
  project-folder="<project-folder>"  
  
  project-name="<project-name>"  
  
/>  
```  
**참고:** SSMA에 대 한 액세스 콘솔 응용 프로그램 이전 버전과 호환성을 지원합니다. SSMA의 이전 버전에서 만든 프로젝트를 열 수 있습니다.  
  
**Command**  
  
save-project: 마이그레이션 프로젝트를 저장합니다.  
  
**스크립트**  
  
**구문 예제:**  
  
```xml  
<save-project/>  
```  
**Command**  
  
close-project: 마이그레이션 프로젝트를 닫습니다.  
  
**스크립트**  
  
**구문 예제:**  
  
```xml  
<close-project  
  
  if-modified="<save/error/ignore>"   (optional)  
  
/>  
```  
' If 수정한 날짜 ' 특성은 선택적 **무시** 기본적으로 합니다.  
  
## <a name="database-connection-script-file-commands"></a>데이터베이스 연결 스크립트 파일 명령  
데이터베이스 연결 명령을 데이터베이스에 연결 하는 데 도움이 됩니다.  
  
합니다 **찾아보기** UI의 기능은 콘솔에서 지원 되지 않습니다.  
  
합니다 **windows 인증** 하 고 **포트** SQL Azure 연결할 때 매개 변수가 적용 됩니다.  
  
' 만들기 스크립트 파일 '에 대 한 자세한 내용은 참조 하세요. [스크립트 파일 만들기 &#40;AccessToSQL&#41;](../../ssma/access/creating-script-files-accesstosql.md)합니다.  
  
**Command**  
  
connect-source-database  
  
-   원본 데이터베이스에 연결을 수행 하 고 원본 데이터베이스의 메타 데이터의 일부 높은 수준의 메타 데이터를 로드 합니다.  
  
-   원본에 대 한 연결을 설정할 수 없는 경우 오류가 생성 되 고 콘솔 응용 프로그램 추가 실행 중지  
  
**스크립트**  
  
서버 정의 서버 연결 파일 또는 스크립트 파일의 서버 섹션에서 각 연결에 대해 정의 된 이름 특성에서 검색 됩니다.  
  
**구문 예제:**  
  
```xml  
<connect-source-database  server="<server-unique-name>"/>  
```  
**Command**  
  
로드-액세스-데이터베이스: Access 데이터베이스 파일을 로드 하는 데 사용  
  
**스크립트**  
  
**구문 예제:**  
  
```xml  
<load-access-database  database-file="<Access-database>"/>  
```  
로 구분하거나 여러  
  
```xml  
<load-access-database>  
  
  <access-database database-file="<Access-database1>"/>  
  
  <access-database database-file="<Access-database2>"/>  
  
</load-access-database>  
```  
**Command**  
  
force-load-source/target-database  
  
-   원본 메타 데이터를 로드합니다.  
  
-   마이그레이션 프로젝트를 오프 라인으로 작업을 수행 하는 데 유용 합니다.  
  
-   원본/대상에 대 한 연결을 설정할 수 없는 경우 오류가 생성 되 고 콘솔 응용 프로그램 추가 실행 중지  
  
**스크립트**  
  
하나 이상의 메타 베이스 노드 명령줄 매개 변수로 필요합니다.  
  
**구문 예제:**  
  
```xml  
<force-load  
  
  object-name="<object-name>"  
  
  metabase="<source/target>"/>  
```  
로 구분하거나 여러  
  
```xml  
<force-load>  
  
  <metabase-object object-name="<object-name>"/>  
  
</force-load>  
```  
**Command**  
  
reconnect-source-database  
  
-   원본 데이터베이스에 다시 연결 되지만 연결 원본 데이터베이스 명령과 달리 메타 데이터를 로드 하지 않습니다.  
  
-   오류가 생성 됩니다 (다시) 소스를 사용 하 여 연결을 설정할 수 없는 경우 및 콘솔 응용 프로그램 실행이 중지 되 더 합니다.  
  
**스크립트**  
  
**구문 예제:**  
  
```xml  
<reconnect-source-database  server="<server-unique-name>"/>  
```  
**Command**  
  
connect-target-database  
  
-   대상 SQL Server 또는 SQL Azure 데이터베이스에 연결 하 고 메타 데이터가 아니라 하지만 대상 데이터베이스의 높은 수준 메타 데이터를 완전히 로드 합니다.  
  
-   대상에 대 한 연결을 설정할 수 없는 경우 오류가 생성 되 고 콘솔 응용 프로그램 실행이 중지 되 더 합니다.  
  
**스크립트**  
  
서버 정의 검색 하 여 서버 연결 파일 또는 스크립트 파일의 서버 섹션에서 각 연결에 대해 정의 된 이름 특성  
  
**구문 예제:**  
  
```xml  
<connect-target-database  server="<server-unique-name>"/>  
```  
**Command**  
  
reconnect-target-database  
  
-   대상 데이터베이스에 다시 연결 되지만 연결 대상 데이터베이스 명령과 달리 메타 데이터를 로드 하지 않습니다.  
  
-   오류가 생성 됩니다 (다시) 대상에 대 한 연결을 설정할 수 없는 경우 및 콘솔 응용 프로그램 실행이 중지 되 더 합니다.  
  
**스크립트**  
  
**구문 예제:**  
  
```xml  
<reconnect-target-database  server="<server-unique-name>"/>  
```  
  
## <a name="report-script-file-commands"></a>보고서 스크립트 파일 명령  
SSMA 콘솔의 다양 한 작업의 성능에는 보고서를 생성 하는 보고서 명령입니다.  
  
**Command**  
  
generate-assessment-report  
  
-   원본 데이터베이스에서 평가 보고서를 생성합니다.  
  
-   이 명령을 실행 하기 전에 원본 데이터베이스 연결을 수행 하지 않는 경우 오류가 생성 되 고 콘솔 응용 프로그램을 종료 합니다.  
  
-   명령 실행 하는 동안 원본 데이터베이스 서버에 연결 하지 못한 결과도 콘솔 응용 프로그램을 종료 합니다.  
  
**스크립트**  
  
-   `assessment-report-folder:` 평가 보고서를 저장할 수 있는 폴더를 지정 합니다. (선택 사항 특성)  
  
-   `object-name:` 평가 보고서 생성 (은 개별 개체 이름 또는 그룹 개체 이름)에 대 한 것으로 간주 하는 개체를 지정 합니다.  
  
-   `object-type:` (개체 범주 지정 된 경우 개체 형식에는 "범주" 됩니다) 개체 이름 특성에 지정 된 개체의 유형을 지정 합니다.  
  
-   `assessment-report-overwrite:` 이미 있는 경우 평가 보고서 폴더를 덮어쓸 것인지를 지정 합니다.  
  
    **기본값:** false입니다. (선택 사항 특성)  
  
-   `write-summary-report-to:` 보고서를 생성할 경로 지정 합니다.  
  
    폴더 경로 언급 된 경우 다음 파일을 이름별 **AssessmentReport&lt;n&gt;합니다. XML** 만들어집니다. (선택 사항 특성)  
  
    보고서를 만드는 두 가지 추가 하위 범주에 있습니다.  
  
    -   `report-errors` (= "true/false", 기본값은 "false" (선택적 특성)으로)  
  
    -   `verbose` (= "true/false", 기본값은 "false" (선택적 특성)으로)  
  
**구문 예제:**  
  
```xml  
<generate-assessment-report  
  
  object-name="ssma.Procedures"  
  
  object-type="category"  
  
  write-summary-report-to="<file>"             (optional)  
  
  verbose="<true/false>"                       (optional)  
  
  report-errors="<true/false>"                 (optional)  
  
  conversion-report-folder="<folder>"          (optional)  
  
  conversion-report-overwrite="<true/false>"   (optional)  
  
/>  
```  
로 구분하거나 여러  
  
```xml  
<generate-assessment-report  
  
  conversion-report-folder="<folder>"            (optional)  
  
  conversion-report-overwrite="<true/false>"     (optional)  
  
>  
    <metabase-object object-name="ssma.Procedures"  
  
        object-type="category"/>  
  
</generate-assessment-report>  
```  
  
## <a name="migration-script-file-commands"></a>마이그레이션 스크립트 파일 명령  
마이그레이션 명령은 소스 스키마에 대상 데이터베이스 스키마를 변환 및 대상 서버에 데이터를 마이그레이션합니다.  
  
마이그레이션 명령에 대 한 설정 기본 콘솔 출력은 'Full' 출력 보고서와 자세한 오류 보고 하지 않습니다. 원본 개체 트리의 루트 노드에서 요약 합니다.  
  
**Command**  
  
convert-schema  
  
-   대상 스키마에 원본에서 스키마 변환을 수행합니다.  
  
-   이 명령을 실행 하기 전에 원본 또는 대상 데이터베이스 연결 수행 되지 않습니다 또는 명령 실행 하는 동안 소스 또는 대상 데이터베이스 서버에 연결할 수 없는 경우 오류가 생성 되 고 콘솔 응용 프로그램이 종료 됩니다.  
  
**스크립트**  
  
-   `conversion-report-folder:` 평가 보고서를 저장할 수 있는 폴더를 지정 합니다. (선택 사항 특성)  
  
-   `object-name:` 스키마 (은 개별 개체 이름 또는 그룹 개체 이름)을 변환 하기 위한 것으로 간주 하는 원본 개체를 지정 합니다.  
  
-   `object-type:` (개체 범주 지정 된 경우 개체 형식에는 "범주" 됩니다) 개체 이름 특성에 지정 된 개체의 유형을 지정 합니다.  
  
-   `conversion-report-overwrite:` 이미 있는 경우 평가 보고서 폴더를 덮어쓸 것인지를 지정 합니다.  
  
    **기본값:** false입니다. (선택 사항 특성)  
  
-   `write-summary-report-to:` 보고서를 생성할 경로 지정 합니다.  
  
    폴더 경로 언급 된 경우 다음 파일을 이름별 **SchemaConversionReport&lt;n&gt;합니다. XML** 만들어집니다. (선택 사항 특성)  
  
    보고서를 만드는 두 가지 추가 하위 범주에 있습니다.  
  
    -   `report-errors` (= "true/false", 기본값은 "false" (선택적 특성)으로)  
  
    -   `verbose` (= "true/false", 기본값은 "false" (선택적 특성)으로)  
  
**구문 예제:**  
  
```xml  
<convert-schema  
  
  object-name="ssma.Procedures"  
  
  object-type="category"  
  write-summary-report-to="<filepath/folder>"     (optional)  
  
  verbose="<true/false>"                          (optional)  
  
  report-errors="<true/false>"                    (optional)  
  
  conversion-report-folder="<folder>"             (optional)  
  
  conversion-report-overwrite="<true/false>"      (optional)  
  
/>  
```  
로 구분하거나 여러  
  
```xml  
<convert-schema  
  
  conversion-report-folder="<folder>"         (optional)  
  
  conversion-report-overwrite="<true/false>"  (optional)  
  
  <metabase-object object-name="ssma.Procedures"  
  
    object-type="category"/>  
  
</convert-schema>  
```  
**Command**  
  
데이터 마이그레이션  
  
1.  대상에 원본 데이터를 마이그레이션합니다.  
  
**스크립트**  
  
-   `object-name:` 마이그레이션에 대 한 것으로 간주 하는 원본 개체를 지정 합니다. 데이터 (해당 수 있는 개별 개체 이름 또는 그룹 개체 이름).  
  
-   `object-type:` (개체 범주 지정 된 경우 개체 형식에는 "범주" 됩니다) 개체 이름 특성에 지정 된 개체의 유형을 지정 합니다.  
  
-   `write-summary-report-to:` 보고서를 생성할 경로 지정 합니다.  
  
    폴더 경로 언급 된 경우 다음 파일을 이름별 **DataMigrationReport&lt;n&gt;합니다. XML** 만들어집니다. (선택 사항 특성)  
  
    보고서를 만드는 두 가지 추가 하위 범주에 있습니다.  
  
    -   `report-errors` (= "true/false", 기본값은 "false" (선택적 특성)으로)  
  
    -   `verbose` (= "true/false", 기본값은 "false" (선택적 특성)으로)  
  
**구문 예제:**  
  
```xml  
<migrate-data  
  
  write-summary-report-to="<filepath/folder>"  
  
  report-errors="true" verbose="true">  
  
    <metabase-object object-name="ssma.TT1"/>  
  
    <metabase-object object-name="ssma.TT2"/>  
  
    <metabase-object object-name="ssma.TT3"/>  
  
    <data-migration-connection  
  
      source-use-last-used="true"/source-server="<server-unique-name>"  
  
      target-use-last-used="true"/target-server="<server-unique-name>"/>  
  
</migrate-data>  
```  
로 구분하거나 여러  
  
```xml  
<migrate-data  
  
  object-name="ssma.Tables"  
  
  object-type="category"  
  
  write-summary-report-to="<filepath/folder>"  
  
  report-errors="true" verbose="true"/>  
```  
**Command**  
  
링크-테이블: 이 명령은 대상 테이블에 (Access) 원본 테이블을 연결합니다.  
  
**스크립트**  
  
**구문 예제:**  
  
```xml  
<link-tables>  
  
  <metabase-object object-name="AccessDatabase.table1" object-type="Tables"/>  
  
  <metabase-object object-name="AccessDatabase.table2" object-type="Tables"/>  
  
</link-tables>  
```  
로 구분하거나 여러  
  
```xml  
<link-tables>  
  
  <metabase-object object-name="AccessDatabase.Tables" object-type="category"/>  
  
</link-tables>  
```  
**Command**  
  
연결 해제-테이블: 이 명령은 대상 테이블에서 원본 (Access) 테이블을 연결 해제합니다.  
  
**스크립트**  
  
**구문 예제:**  
  
```xml  
<unlink-tables>  
  
  <metabase-object object-name="AccessDatabase.table1" object-type="Tables"/>  
  
  <metabase-object object-name="AccessDatabase.table2" object-type="Tables"/>  
  
</unlink-tables>  
```  
로 구분하거나 여러  
  
```xml  
<unlink-tables>  
  
  <metabase-object object-name="AccessDatabase.Tables" object-type="category"/>  
  
</unlink-tables>  
```  
  
## <a name="migration-preparation-script-file-commands"></a>마이그레이션 준비 스크립트 파일 명령  
마이그레이션 준비 명령 소스 및 대상 데이터베이스 간의 스키마 매핑을 시작합니다.  
  
**Command**  
  
map-schema: 대상 스키마에 원본 데이터베이스의 스키마 매핑.  
  
**스크립트**  
  
-   `source-schema` 마이그레이션할 예정 소스 스키마를 지정 합니다.  
  
-   `sql-server-schema` 원하는 위치로 마이그레이션해야 대상 스키마를 지정 합니다.  
  
**구문 예제:**  
  
```xml  
<map-schema source-schema="source-schema"  
  
            sql-server-schema="target-schema"/>  
```  
  
## <a name="manageability-commands"></a>관리 명령  
관리 효율성 명령 도움말 원본 데이터베이스와 대상 데이터베이스 개체를 동기화 합니다.  
  
마이그레이션 명령에 대 한 설정 기본 콘솔 출력은 'Full' 출력 보고서와 자세한 오류 보고 하지 않습니다. 원본 개체 트리의 루트 노드에서 요약 합니다.  
  
**Command**  
  
동기화 대상  
  
1.  대상 데이터베이스를 사용 하 여 대상 개체를 동기화합니다.  
  
2.  이 명령은 원본 데이터베이스에 대해 실행 될 경우 오류가 발생 합니다.  
  
3.  이 명령을 실행 하기 전에 대상 데이터베이스 연결을 수행 되지 않습니다 또는 명령 실행 하는 동안 대상 데이터베이스 서버에 연결할 수 없는 경우 오류가 생성 되 고 콘솔 응용 프로그램이 종료 됩니다.  
  
**스크립트**  
  
1.  `object-name:` 대상 데이터베이스 (은 개별 개체 이름 또는 그룹 개체 이름)을 사용 하 여 동기화에 대 한 것으로 간주 하는 대상 개체를 지정 합니다.  
  
2.  `object-type:` (개체 범주 지정 된 경우 개체 형식에는 "범주" 됩니다) 개체 이름 특성에 지정 된 개체의 유형을 지정 합니다.  
  
3.  `on-error:` 동기화 오류 경고 또는 오류도 지정할지 여부를 지정 합니다. 오류 발생 시에 대 한 사용 가능한 옵션:  
  
    -   report-total-as-warning  
  
    -   report-each-as-warning  
  
    -   스크립트 실패  
  
4.  `report-errors-to:` 동기화 작업 (선택 사항 특성) 폴더 경로 지정 하는 경우 다음 파일 이름에 대 한 오류 보고서의 위치를 지정 **TargetSynchronizationReport.XML** 만들어집니다.  
  
**구문 예제:**  
  
```xml  
<synchronize-target  
  
  object-name="ots_triggers.dbo"  
  
  on-error="<report-total-as-warning|  
  
             report-each-as-warning|  
  
             fail-script>"              (optional)  
  
  report-errors-to="<file-name>"        (optional)  
  
/>  
```  
로 구분하거나 여러  
  
```xml  
<synchronize-target  
  
  object-name="ssma.dbo.Procedures"  
  
  object-type="category"/>  
```  
로 구분하거나 여러  
  
```xml  
<synchronize-target>  
  
  <metabase-object object-name="ssma.dbo.TT1"/>  
  
  <metabase-object object-name="ssma.dbo.TT2"/>  
  
  <metabase-object object-name="ssma.dbo.TT3"/>  
  
</synchronize-target>  
```  
**Command**  
  
데이터베이스에서 새로 고침  
  
-   데이터베이스에서 원본 개체를 새로 고칩니다.  
  
-   이 명령은 대상 데이터베이스에 대해 실행 될 경우 오류가 생성 됩니다.  
  
**스크립트**  
  
하나 이상의 메타 베이스 노드 명령줄 매개 변수로 필요합니다.  
  
1.  `object-name:` (은 개별 개체 이름 또는 그룹 개체 이름)는 원본 데이터베이스에서 새로 고침에 대 한 것으로 간주 하는 원본 개체를 지정 합니다.  
  
2.  `object-type:` (개체 범주 지정 된 경우 개체 형식에는 "범주" 됩니다) 개체 이름 특성에 지정 된 개체의 유형을 지정 합니다.  
  
3.  `on-error:` 경고 또는 오류 새로 고침 오류를 지정할지 여부를 지정 합니다. 오류 발생 시에 대 한 사용 가능한 옵션:  
  
    -   report-total-as-warning  
  
    -   report-each-as-warning  
  
    -   스크립트 실패  
  
4.  `report-errors-to:` 새로 고침 작업 (선택 사항 특성) 폴더 경로 지정 하는 경우 다음 파일 이름에 대 한 오류 보고서의 위치를 지정 **SourceDBRefreshReport.XML** 만들어집니다.  
  
**구문 예제:**  
  
```xml  
<refresh-from-database  
  
  object-name="ssma.TT1"  
  
  on-error="<report-total-as-warning|  
  
             report-each-as-warning|  
  
             fail-script>"              (optional)  
  
  report-errors-to="<file-name>"        (optional)  
  
/>  
```  
로 구분하거나 여러  
  
```xml  
<refresh-from-database  
  
  object-name="ssma.Procedures"  
  
  object-type="category"/>  
```  
로 구분하거나 여러  
  
```xml  
<refresh-from-database>  
  
  <metabase-object object-name="ssma.TT_1"/>  
  
</refresh-from-database>  
```  
  
## <a name="script-generation-script-file-commands"></a>스크립트 생성 스크립트 파일 명령  
콘솔 출력 스크립트 파일에 저장 하는 명령 도움말 스크립트 생성 합니다.  
  
**Command**  
  
save-as-script  
  
때 언급 된 파일 개체의 스크립트를 저장 하는 데 메타 베이스 = 대상, 위치에 스크립트를 가져옵니다 하 고 대상 데이터베이스에서 실행 하는 동일한 동기화 명령에는 대신이 방법을 사용 합니다.  
  
**스크립트**  
  
하나 이상의 메타 베이스 노드 명령줄 매개 변수로 필요합니다.  
  
-   `object-name:` 해당 스크립트를 저장할 수는 개체를 지정 합니다. (은 개별 개체 이름 또는 그룹 개체 이름)  
  
-   `object-type:` (개체 범주 지정 된 경우 개체 형식에는 "범주" 됩니다) 개체 이름 특성에 지정 된 개체의 유형을 지정 합니다.  
  
-   `metabase:` 원본 인지를 지정 하거나 메타 베이스를 대상 지정 합니다.  
  
-   `destination:` 경로 또는 파일 이름이 제공 되지 않으면 다음 파일 이름 형식 (object_name 특성 값).out에서 스크립트를 저장할 수에 있는 폴더를 지정 합니다.  
  
-   `overwrite:` true 이면 다음이 있는 경우 덮어씁니다 동일한 파일 이름입니다. 값 (true/false)이 있습니다.  
  
**구문 예제:**  
  
```xml  
<save-as-script  
  
  metabase="<source/target>"  
  
  object-name="ssma.dbo.Procedures"  
  
  object-type="category"  
  
  destination="<file/folder>"  
  
  overwrite="<true/false>"             (optional)  
  
/>  
```  
로 구분하거나 여러  
  
```xml  
<save-as-script  
  
  metabase="<source/target>"  
  
  destination="<file/folder>"  
  
    <metabase-object object-name="ssma.dbo.Procedures"  
  
                     object-type="category"/>  
  
</save-as-script>  
```  
  
## <a name="next-step"></a>다음 단계  
명령줄 옵션에 대 한 자세한 내용은 [SSMA 콘솔의 명령줄 옵션 &#40;AccessToSQL&#41; ](../../ssma/access/command-line-options-in-ssma-console-accesstosql.md) 합니다.  
  
샘플 콘솔 스크립트 파일에 대 한 내용은 참조 하세요 [샘플 콘솔 스크립트 FilesExecuting SSMA 콘솔 작업 &#40;AccessToSQL&#41;](../../ssma/access/working-sample-console-script-filesexecuting-ssma-console-accesstosql.md)  
  
다음 단계는 프로젝트 요구 사항에 따라 달라 집니다.  
  
-   암호 또는 내보내기 지정 하기 위한 암호 가져오기 /를 참조 하십시오 [관리 암호 &#40;AccessToSQL&#41;](../../ssma/access/managing-passwords-accesstosql.md)합니다.  
  
-   보고서 생성을 참조 하세요 [보고서 생성 &#40;AccessToSQL&#41;](../../ssma/access/generating-reports-accesstosql.md)합니다.  
  
-   콘솔에서 문제 해결을 참조 하세요 [문제 해결 &#40;AccessToSQL&#41;](../../ssma/access/troubleshooting-accesstosql.md)합니다.  
  
