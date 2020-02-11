---
title: 튜닝 권장 구성 보기 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Database Engine [SQL Server], tutorials
ms.assetid: e4e690c9-434f-4b01-b4de-0b905323ddd6
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: fe8d52d898db35698155518646f074e7167687a0
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66110175"
---
# <a name="viewing-tuning-recommendations"></a>튜닝 권장 구성 보기
  이 태스크에서는 [작업 튜닝](lesson-1-1-tuning-a-workload.md)에서 만든 튜닝 세션을 사용 합니다. MyScript [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] [!INCLUDE[tsql](../../includes/tsql-md.md)] 스크립트를 사용 하 여 데이터베이스를 튜닝 하면 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 튜닝 관리자의 **권장** 구성 탭에 해당 결과가 표시 됩니다. 다음 태스크에서는 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 튜닝 관리자 GUI (그래픽 사용자 인터페이스)의 **권장** 구성 탭을 소개 하 고 튜닝 세션 결과에 대해 제공 하는 정보를 탐색 하는 과정을 안내 합니다.  
  
### <a name="view-tuning-recommendations"></a>튜닝 권장 구성 보기  
  
1.  
  [!INCLUDE[ssDE](../../includes/ssde-md.md)] 튜닝 관리자를 시작합니다. 
  [데이터베이스 엔진 튜닝 관리자 시작](../../relational-databases/performance/database-engine-tuning-advisor.md)을 참조하세요. 
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 작업 튜닝 [연습에서 사용한 것과 동일한](lesson-1-1-tuning-a-workload.md)인스턴스에 연결해야 합니다.  
  
2.  
  **세션 모니터** 창에서 **MySession** 을 두 번 클릭합니다. [!INCLUDE[ssDE](../../includes/ssde-md.md)]튜닝 관리자에서 이전 튜닝 세션의 세션 정보를 로드 하 고 **권장** 구성 탭을 표시 합니다 [!INCLUDE[ssDE](../../includes/ssde-md.md)] . 모든 튜닝 옵션 기본값을 적용 하 고 **튜닝 옵션** 탭에서 분할을 선택 **하지** 않았기 때문에 튜닝 관리자에서 **파티션 권장 구성이** 없습니다.  
  
3.  
  **권장 구성** 탭에서 탭 페이지 맨 아래의 스크롤 막대를 사용하여 모든 **인덱스 권장 구성** 열을 볼 수 있습니다. 각 행은 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 튜닝 관리자에서 권장하는 데이터베이스 개체(인덱스 또는 인덱싱된 뷰)가 삭제되는지 만들어지는지 나타냅니다. 맨 오른쪽 열로 스크롤하여 **정의**를 클릭합니다. [!INCLUDE[ssDE](../../includes/ssde-md.md)]튜닝 관리자에 해당 행에서 데이터베이스 개체를 만들거나 삭제 하는 [!INCLUDE[tsql](../../includes/tsql-md.md)] 스크립트를 볼 수 있는 **SQL 스크립트 미리 보기** 창이 표시 됩니다. 
  **닫기** 를 클릭하여 미리 보기 창을 닫습니다.  
  
     링크를 포함하는 **정의** 를 찾기 힘든 경우 탭 페이지 맨 아래에 있는 **기존 개체 표시** 확인란의 선택을 취소합니다. 그러면 표시되는 행 수가 줄어듭니다. 이 확인란의 선택을 취소하면 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 튜닝 관리자에서 권장 구성을 생성한 개체만 표시합니다. 현재 **데이터베이스에 있는 모든 데이터베이스 개체를 보려면** 기존 개체 표시 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 확인란을 선택합니다. 탭 페이지 오른쪽의 스크롤 막대를 사용하여 모든 개체를 볼 수 있습니다.  
  
4.  
  **인덱스 권장 구성** 창의 표를 마우스 오른쪽 단추로 클릭합니다. 바로 가기 메뉴에서 권장 구성을 선택하거나 권장 구성의 선택을 취소할 수 있습니다. 표 텍스트의 글꼴을 변경할 수도 있습니다.  
  
5.  
  **동작** 메뉴에서 **권장 구성 저장** 을 클릭하여 모든 권장 구성을 하나의 [!INCLUDE[tsql](../../includes/tsql-md.md)] 스크립트에 저장합니다. 스크립트 이름을 `MySessionRecommendations.sql`로 지정합니다.  
  
     
  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 의 쿼리 편집기에서 MySessionRecommendations.sql 스크립트를 열어 봅니다. 쿼리 편집기에서 스크립트를 실행하여 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 예제 데이터베이스에 권장 구성을 적용할 수 있지만 이렇게 하지 마십시오. 쿼리 편집기에서 스크립트를 실행하지 않고 닫습니다.  
  
     또는 **튜닝 관리자의** 동작 **메뉴에서** 권장 구성 적용 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 을 클릭하여 권장 구성을 적용할 수도 있지만 이 연습에서는 이러한 권장 구성을 지금 적용하지 마세요.  
  
6.  
  **권장 구성** 탭에 권장 구성이 2개 이상 있는 경우 **인덱스 권장 구성** 표에서 데이터베이스 개체를 나열하는 행의 일부를 지웁니다.  
  
7.  
  **동작** 메뉴에서 **권장 구성 평가**를 클릭합니다. 
  [!INCLUDE[ssDE](../../includes/ssde-md.md)] 튜닝 관리자에서 MySession의 원래 권장 구성의 하위 집합을 평가할 수 있는 새 튜닝 세션이 만들어집니다.  
  
8.  새 `EvaluateMySession` **세션 이름**으로를 입력 하 고 도구 모음에서 **분석 시작** 단추를 클릭 합니다. 이 새 튜닝 세션에 대해 2단계와 3단계를 반복하여 해당 권장 구성을 볼 수 있습니다.  
  
## <a name="summary"></a>요약  
 MySession 튜닝 세션에 대한 **권장 구성** 탭의 내용을 보고 새 EvaluateMySession 튜닝 세션에서 해당 권장 구성의 하위 집합을 평가했습니다.  
  
 튜닝 권장 구성의 하위 집합 평가는 세션 실행 후 튜닝 옵션을 변경해야 할 경우에 필요할 수 있습니다. 예를 들어 세션에 대한 튜닝 옵션을 지정할 때 인덱싱된 뷰를 고려하도록 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 튜닝 관리자에 요청했지만 권장 구성이 생성된 후 인덱싱된 뷰를 사용하지 않도록 결정하는 경우를 가정해 봅니다. 그런 다음 작업 메뉴에서 **권장 구성 평가** 옵션을 **** 사용 하 여 튜닝 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 관리자가 인덱싱된 뷰를 고려 하지 않고 세션을 다시 평가 하도록 할 수 있습니다. 
  **권장 구성 평가** 옵션을 사용하면 이전에 생성된 권장 구성이 현재 물리적 디자인에 가상으로 적용되어 두 번째 튜닝 세션의 물리적 디자인에 전달됩니다.  
  
 추가 튜닝 결과 정보는 이 단원의 다음 태스크에 설명된 **보고서** 탭에서 볼 수 있습니다.  
  
## <a name="next-task-in-lesson"></a>단원의 다음 태스크  
 [튜닝 보고서 보기](lesson-1-3-viewing-tuning-reports.md)  
  
  
