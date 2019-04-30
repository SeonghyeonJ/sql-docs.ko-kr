---
title: 유지 관리 계획(보고 및 로깅 페이지) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- sql12.swb.maint.reportinglogging.f1
ms.assetid: 3a30b17a-3deb-446f-900a-62f88934a90f
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 623507b4d9e52da376d4c83e4ee5c4d51b15dc39
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63186264"
---
# <a name="maintenance-plan-reporting-and-logging-page"></a>유지 관리 계획(보고 및 로깅 페이지)
  **보고 및 로깅** 대화 상자를 사용하여 유지 관리 계획이 실행될 때 생성되는 보고서와 로그를 구성할 수 있습니다.  
  
## <a name="options"></a>변수  
 **텍스트 파일 보고서 생성**  
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서 텍스트 파일 보고서를 기록하도록 할지 여부를 지정합니다.  
  
 **새 파일 만들기**  
 유지 관리 계획이 실행될 때마다 새 보고서 파일을 만듭니다. 기본적으로 보고서 파일은 해당 유지 관리 계획이 있는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스를 호스팅하는 컴퓨터의 기본 로그 폴더에 기록됩니다. 기본 로그 폴더는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 설치 중 설정합니다. 다른 폴더를 지정하려면 **폴더** 입력란에 전체 폴더 경로를 입력하거나 찾아보기 단추(**...**)를 클릭하고 원하는 폴더를 탐색합니다.  
  
 **파일에 추가**  
 각각의 계획을 실행하여 생성된 보고서를 **파일 이름** 입력란에 지정된 파일에 추가합니다. 찾아보기 단추를 클릭하고 대화 상자에서 파일을 선택하여 파일을 지정할 수도 있습니다.  
  
 **전자 메일 받는 사람에게 보고서 보내기**  
 유지 관리 계획의 실행 결과를 전자 메일로 보냅니다. 이 옵션은 데이터베이스 메일을 활성화하고 적절히 구성한 경우에만 사용할 수 있습니다.  
  
 **에이전트 운영자**  
 전자 메일을 받는 에이전트 운영자를 목록에서 선택합니다. 이 옵션은 메일을 활성화하고 적절히 구성한 경우에만 사용할 수 있습니다.  
  
 **확장 정보 기록**  
 로그에 추가 정보를 포함합니다. 이 옵션을 선택하면 저장되는 유지 관리 계획 기록의 크기가 커집니다.  
  
 **원격 서버에 기록**  
 원격 서버에 유지 관리 계획 기록을 작성합니다.  
  
 **연결**  
 원격 서버에 기록할 때 사용할 연결 정보를 지정합니다.  
  
 **새로 만들기**  
 **연결 속성** 대화 상자를 표시합니다. 원격 서버에 기록할 때 사용할 새 연결 정보를 구성하는 데 사용됩니다.  
  
## <a name="see-also"></a>관련 항목  
 [유지 관리 계획](maintenance-plans.md)   
 [데이터베이스 메일](../database-mail/database-mail.md)  
  
  
