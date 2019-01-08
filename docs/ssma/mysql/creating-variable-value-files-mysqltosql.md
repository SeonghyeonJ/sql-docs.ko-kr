---
title: 변수 값 파일 만들기 (MySQLToSQL) | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Creating variable value files
- variable value file validation
ms.assetid: 1dc56a7b-8e3a-4576-ad4f-47050bf7e28a
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 73919295dbd53cbaaca3847d5be119e5fe2d0bb7
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/28/2018
ms.locfileid: "52530148"
---
# <a name="creating-variable-value-files-mysqltosql"></a>변수 값 파일 만들기(MySQLToSQL)
변수 값 파일은 다른 서버 마이그레이션에서 자주 변경 하는 원본 또는 대상 서버 이름과 같은 명령의 매개 변수 값을 비교 하는 XML 파일입니다. 많은 수의 데이터베이스 마이그레이션 수행 하는 경우 원본 서버의 각 값을 저장 하는 것에 대 한 여러 변수 파일을 만든 마스터 스크립트 파일의 참조를 **-v** 명령줄에서 전환 합니다. 이 여러 변수 파일에서 변수 값을 사용 하 여 몇 가지 스크립트 파일에 정적 값을 유지 관리에 도움이 됩니다.  
  
> [!NOTE]  
> 1.  변수 이름은 접두사를 $ (달러) 기호가 붙습니다. 변수를 변수 값 파일에서 값이 지정 되지 않은 경우 상태일 콘솔 실행 프로세스의 결과 스크립트 파일의 구문 분석 하는 동안 오류가 발생 합니다.  
> 2.  이스케이프 문자 **$** 됩니다 **$$** 합니다. 매개 변수 또는 정적 값의 값이 있으면 **$** (달러) 기호, 한 다음 **$$** 변수 대신 문자로 취급 되도록 지정 해야 합니다.  
> 3.  유지 관리를 위해 변수를 선언할 수 내부 `'variable-group'` 사용자의 논리적 분리에 대 한 요소 변수를 정의 합니다.  이 요소의 사용 필수 아닙니다.  
  
**예:**  
  
**예제 1:**  
  
```xml  
<!--Sample of variable value file commands-->  
  
<variables>  
  
  <variable-group name="ProjectSpecs">  
  
    <variable name="$project_folder$" value="<folder-name>"/>  
  
    <variable name="$project_name$" value="<project-name>"/>  
  
    <variable name="$project_overwrite$" value="<true/false>"/>  
  
    <variable name="$project_type$" value="<project-type>"/>  
  
  </variable-group>  
  
</variables>  
```  
**예제 2:**  
  
```xml  
<!--Sample of variable value file commands-->  
  
<variables>  
  
  <variable-group name="SQLServerParams">  
  
    <variable-group name="SqlServerConnectionParams">  
  
      <variable name="$TargetUserName$ value="<user-name>"/>  
  
      <variable name="$TargetServerName$" value="<server-name>"/>  
  
      <variable name="$TargetDB$" value="<database-name>"/>  
  
      <variable name="$TargetPassword$" value="<password>"/>  
  
      <variable name="$TrustedConnection$" value="<true/false>"/>  
  
    </variable-group>  
  
    <variable-group name="SqlServerObjectParams">  
  
      <variable name="$ObjectName1$" value="<object-name>"/>  
  
      <variable name="$ObjectName2$" value="<object-name>"/>  
  
    </variable-group>  
  
  </variable-group>  
  
</variables>  
```  
  
## <a name="variable-value-file-validation"></a>변수 값 파일 유효성 검사  
사용자 스키마 정의 파일에 대해 자신의 변수 값 파일을 쉽게 확인할 수 있습니다 **'ConsoleScriptVariablesSchema.xsd'** 'Schemas' 폴더에서 사용할 수 있습니다.  
  
## <a name="next-step"></a>다음 단계  
운영 콘솔에서 다음 단계 [서버 연결 파일 만들기 &#40;MySQLToSQL&#41;](../../ssma/mysql/creating-the-server-connection-files-mysqltosql.md)  
  
## <a name="see-also"></a>관련 항목:  
[서버 연결 파일 (MySQL) 만들기](https://msdn.microsoft.com/df0e970c-da0b-4118-b359-c9dcbbad16d6)  
  
