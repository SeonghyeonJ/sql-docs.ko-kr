---
title: 활성 작업 대화 상자 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
f1_keywords:
- sql12.ssis.ssms.isoperations.executions.f1
- sql12.ssis.ssms.isoperations.general.f1
ms.assetid: 5bb0fcd6-0ce9-488a-85b8-25dddaa03cda
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: efb8341b4e7124e244b5994aa2f83c664348b865
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62772317"
---
# <a name="active-operations-dialog-box"></a>활성 작업 대화 상자
  **활성 작업** 대화 상자를 사용하여 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 서버에서 현재 실행 중인 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 작업(예: 배포, 유효성 검사 및 패키지 실행)의 상태를 볼 수 있습니다. 이 데이터는 SSISDB 카탈로그에 저장됩니다.  
  
 관련된 [!INCLUDE[tsql](../includes/tsql-md.md)] 뷰에 대한 자세한 내용은 [catalog.operations&#40;SSISDB 데이터베이스&#41;](/sql/integration-services/system-views/catalog-operations-ssisdb-database), [catalog.validations&#40;SSISDB 데이터베이스&#41;](/sql/integration-services/system-views/catalog-validations-ssisdb-database) 및 [catalog.executions&#40;SSISDB 데이터베이스&#41;](/sql/integration-services/system-views/catalog-executions-ssisdb-database)를 참조하세요.  
  
 **수행 작업**  
  
1.  [활성 작업 대화 상자 열기](#open_dialog)  
  
2.  [옵션 구성](#options)  
  
##  <a name="open_dialog"></a> 활성 작업 대화 상자 열기  
  
1.  [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)][!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)]열기  
  
2.  Microsoft SQL Server 데이터베이스 엔진 연결  
  
3.  개체 탐색기에서 **Integration Services** 노드를 확장하고 **SSISDB**를 마우스 오른쪽 단추로 클릭한 다음 **활성 작업**을 클릭합니다.  
  
##  <a name="options"></a> 옵션 구성  
  
### <a name="options"></a>변수  
 **형식**  
 작업 유형을 지정합니다. 다음의 가능한 값은는 **형식** 필드 및 해당 TRANSACT-SQL operations_type 열에 값 `catalog.operations` 보기.  
  
|||  
|-|-|  
|Integration Services 초기화|1|  
|작업 정리(SQL 에이전트 작업)|2|  
|프로젝트 버전 정리(SQL 에이전트 작업)|3|  
|프로젝트 배포|101|  
|프로젝트 복원|106|  
|패키지 실행 생성 및 시작|200|  
|작업 중지(유효성 검사 또는 실행 중지)|202|  
|프로젝트 유효성 검사|300|  
|패키지 유효성 검사|301|  
|카탈로그 구성|1000|  
  
 **중지**  
 현재 실행 중인 작업을 중지하려면 클릭합니다.  
  
  
