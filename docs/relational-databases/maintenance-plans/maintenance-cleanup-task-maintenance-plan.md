---
title: 유지 관리 정리 태스크(유지 관리 계획) | Microsoft 문서
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- sql13.swb.maint.cleanup.f1
helpviewer_keywords:
- Maintenance Cleanup Task dialog box
ms.assetid: 022b679c-6799-4c13-9185-814224a20412
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: bd0f58fc45889bfef8701538bebc4ec94af85944
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/30/2020
ms.locfileid: "68115745"
---
# <a name="maintenance-cleanup-task-maintenance-plan"></a>유지 관리 정리 태스크(유지 관리 계획)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  **유지 관리 정리 태스크** 를 사용하여 유지 관리 계획에서 만든 텍스트 보고서와 데이터베이스 백업 파일을 포함하여 유지 관리 계획과 관련된 오래된 파일을 제거할 수 있습니다.  
  
> [!NOTE]  
>  유지 관리 정리 태스크에서는 지정된 디렉터리의 하위 폴더에 있는 파일을 자동으로 삭제하지 않습니다. 이 기능은 유지 관리 정리 태스크를 사용하여 파일을 삭제하는 악의적 공격의 가능성을 줄여 줍니다. 첫 번째 수준의 하위 폴더를 삭제하려는 경우 **첫 번째 수준의 하위 폴더 포함**을 선택해야 합니다.  
  
## <a name="options"></a>옵션  
 **연결**  
 현재 연결을 표시합니다.  
  
 **새로 만들기**  
 이 태스크를 수행할 때 사용할 새 서버 연결을 만듭니다. 아래에서는 **새 연결** 대화 상자에 대해 설명합니다.  
  
 **백업 파일**  
 백업 파일을 삭제합니다.  
  
 **유지 관리 계획 텍스트 보고서**  
 이전에 실행한 유지 관리 계획의 텍스트 보고서를 삭제합니다.  
  
 **특정 파일 삭제**  
 **파일 이름** 상자에 표시되는 특정 파일을 삭제합니다.  
  
 **파일 이름**  
 삭제할 파일의 경로와 이름입니다.  
  
 **확장명에 따라 폴더 검색 및 파일 삭제**  
 지정한 확장명을 가진 파일을 지정한 폴더에서 모두 삭제합니다. 예를 들어 Tuesday 폴더에서 확장명이 .bak인 백업 파일을 모두 삭제할 수 있습니다.  
  
 **폴더**  
 삭제할 파일이 있는 폴더의 경로와 이름입니다.  
  
 **파일 확장명**  
 삭제할 파일의 파일 확장명을 제공합니다. 확장명 앞뒤에 다른 문자를 포함하지 마세요(예: BAK 또는 TRN 사용). 
  
 **첫 번째 수준의 하위 폴더 포함**  
 **폴더** 아래의 첫 번째 하위 폴더에서 **파일 확장명**에 지정된 확장명을 갖는 파일을 삭제합니다.  
  
 **태스크 런타임에 파일의 보존 기간에 따라 파일 삭제**  
 **다음보다 오래된 파일 삭제** 상자에 숫자와 시간 단위를 제공하여 삭제할 파일의 최소 보존 기간을 지정합니다.  
  
 **다음보다 오래된 파일 삭제**  
 숫자와 시간 단위(일, 주, 월 또는 년)를 제공하여 삭제할 파일의 최소 보존 기간을 지정합니다. 지정한 시간대 이전의 파일은 삭제됩니다.  
  
 **T-SQL 보기**  
 선택한 옵션을 기반으로 서버에 대해 수행한 이 태스크의 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문을 표시합니다.  
  
> [!NOTE]  
>  영향을 받은 개체 수가 많은 경우에는 표시하는 데 시간이 오래 걸릴 수 있습니다.  
  
## <a name="new-connection-dialog-box"></a>새 연결 대화 상자  
 **연결 이름**  
 새 연결의 이름을 입력합니다.  
  
 **서버 이름 선택 또는 입력**  
 이 태스크를 수행할 때 연결할 서버를 선택합니다.  
  
 **...**  
 사용 가능한 서버 목록이 보이도록 선택합니다.  
  
 **서버 로그온 정보 입력**  
 서버에 대한 인증 방법을 지정합니다.  
  
 **Windows NT 통합 보안 사용**  
 Microsoft Windows 인증을 사용하여 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 인스턴스에 연결합니다.  
  
 **특정 사용자 이름 및 암호 사용**  
 SQL Server 인증을 사용하여 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 인스턴스에 연결합니다. 이 옵션은 사용할 수 없습니다.  
  
 **사용자 이름**  
 인증 시 사용할 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 로그인을 입력합니다. 이 옵션은 사용할 수 없습니다.  
  
 **암호**  
 인증 시 사용할 암호를 입력합니다. 이 옵션은 사용할 수 없습니다.  
  
## <a name="see-also"></a>참고 항목  
 [유지 관리 계획](../../relational-databases/maintenance-plans/maintenance-plans.md)  
  
  
