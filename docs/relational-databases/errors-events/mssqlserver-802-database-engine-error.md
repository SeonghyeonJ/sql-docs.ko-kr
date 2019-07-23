---
title: MSSQLSERVER_802 - 데이터베이스 엔진 오류 | Microsoft 문서
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 802 (Database Engine error)
ms.assetid: 5892ed24-4dcb-4bf9-a8a4-a7ca898832d5
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: f880cd41cdde662913099e06ef93eacc17d94265
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68007040"
---
# <a name="mssqlserver802---database-engine-error"></a>MSSQLSERVER_802 - 데이터베이스 엔진 오류
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>세부 정보  
  
|||  
|-|-|  
|제품 이름|SQL Server|  
|이벤트 ID|802|  
|이벤트 원본|MSSQLSERVER|  
|구성 요소|SQLEngine|  
|심볼 이름|NO_BUFS|  
|메시지 텍스트|버퍼 풀에 사용할 수 있는 메모리가 부족합니다.|  
  
## <a name="explanation"></a>설명  
버퍼 풀이 가득 찼고 버퍼 풀을 더 이상 늘릴 수 없을 때 발생합니다.  
  
## <a name="user-action"></a>사용자 동작  
다음 목록은 메모리 오류 문제를 해결하는 데 도움이 되는 일반적인 단계를 간략히 설명합니다.  
  
1.  다른 애플리케이션 또는 서비스가 현재 서버의 메모리를 사용 중인지 확인합니다. 중요도가 낮은 애플리케이션이나 서비스에서 메모리를 덜 사용하도록 다시 구성합니다.  
  
2.  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **: 버퍼 관리자**, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **: Memory Manager**에 대한 성능 모니터 카운터 수집을 시작합니다.  
  
3.  다음 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 메모리 구성 매개 변수를 확인합니다.  
  
    -   **max server memory**  
  
    -   **min server memory**  
  
    -   **min memory per query**  
  
    비정상적인 설정이 있는지 확인하고 필요할 경우 수정합니다. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]의 향상된 메모리 요구 사항을 확인합니다. 기본 설정은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 온라인 설명서의 "서버 구성 옵션 설정"을 참조하십시오.  
  
4.  DBCC MEMORYSTATUS 출력 결과를 확인하고 이러한 오류 메시지가 표시될 때 이 값이 어떻게 변경되는지 관찰합니다.  
  
5.  동시 세션 및 현재 실행 중인 쿼리 수와 같은 작업을 확인합니다.  
  
다음 동작으로 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 사용할 수 있는 메모리를 늘릴 수 있습니다.  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 외에 다른 애플리케이션이 리소스를 사용 중인 경우 이 애플리케이션을 중지하거나 별도의 서버에서 실행합니다.  
  
-   **max server memory**를 구성한 경우 설정값을 늘립니다.  
  
다음 DBCC 명령을 실행하여 몇 가지 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 메모리 캐시를 비웁니다.  
  
-   DBCC FREESYSTEMCACHE  
  
-   DBCC FREESESSIONCACHE  
  
-   DBCC FREEPROCCACHE  
  
문제가 지속되면 추가적인 조사를 수행하고 작업을 줄여야 할 수 있습니다.  
  
