---
title: 캐싱, 새로 고침 및 복제 모니터 성능 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- monitoring performance [SQL Server replication], Replication Monitor
- cache [SQL Server], replication
- Replication Monitor, caching
- refreshing data
- Replication Monitor, refreshing
ms.assetid: a2d8b666-ed41-4f86-b2b8-c8e118416ab7
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 5d61c50c68033b3add4b52063980bf5caa042369
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62667371"
---
# <a name="caching-refresh-and-replication-monitor-performance"></a>캐싱, 새로 고침 및 복제 모니터 성능
  [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 복제 모니터는 프로덕션 시스템 내의 많은 컴퓨터를 효율적으로 모니터링하도록 설계되었습니다. 계산을 수행하고 데이터를 수집하기 위해 복제 모니터가 사용하는 쿼리는 정기적으로 캐시되며 새로 고쳐집니다. 캐싱을 사용하면 복제 모니터에서 여러 페이지를 볼 때 필요한 쿼리 및 계산의 수를 줄일 수 있고 여러 사용자에 대해 모니터링을 확장할 수 있습니다.  
  
 캐시 새로 고침은 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 에이전트 작업, 즉 **배포에 대한 복제 모니터링 리프레셔**로 처리됩니다. 이 작업은 계속 실행되지만 캐시 새로 고침 일정은 이전 새로 고침 후 일정 시간 동안 대기한 다음 실행됩니다.  
  
-   캐시를 마지막으로 만든 이후에 에이전트 기록을 변경 경우 대기 시간은 최소: 4초 또는 이전 캐시를 만드는 데 소요된 시간입니다.  
  
-   캐시 마지막 이후에 에이전트 기록을 변경 하지 경우 만든 (수 다른 변경 내용이 있었는지), 대기 시간은 최대: 30 초 또는 이전 캐시를 만드는 데 소요 된 시간의 양입니다.  
  
## <a name="refreshing-the-replication-monitor-user-interface"></a>복제 모니터 사용자 인터페이스 새로 고침  
 다음과 같은 방법으로 복제 모니터 사용자 인터페이스를 새로 고칠 수 있습니다.  
  
-   기본적으로 주 복제 모니터 창(모든 탭 포함)은 자동으로 5초마다 새로 고쳐집니다. 자동 새로 고침으로 인해 캐시가 새로 고쳐지지는 않으며 사용자 인터페이스는 캐시에서 가장 최신 버전의 데이터를 표시합니다. 게시자 설정을 편집하여 게시자와 연결된 모든 창에 사용되는 새로 고침 빈도를 사용자 지정할 수 있습니다. 또한 게시자에 대한 자동 새로 고침을 해제할 수 있습니다.  
  
-   복제 모니터에 표시되는 세부 정보 창은 동기화를 수행 중인 병합 구독에 관련된 창을 제외하고 기본적으로 자동 새로 고침되지 않습니다. 세부 정보 창이 자동으로 새로 고쳐지도록 지정한 경우 이 창은 주 복제 모니터 창과 같은 일정으로 새로 고쳐집니다.  
  
-   F5 키를 누르거나 복제 모니터 트리의 노드를 마우스 오른쪽 단추로 클릭하고 **새로 고침**을 클릭하여 모든 창을 수동으로 새로 고칠 수 있습니다. 수동으로 새로 고침을 수행하면 캐시도 새로 고쳐집니다.  
  
 자세한 내용은 [복제 모니터에서 데이터 새로 고침](refresh-data-in-replication-monitor.md)을 참조하세요.  
  
## <a name="performance-considerations"></a>성능 고려 사항  
 복제 모니터는 효율적으로 실행되도록 설계되었지만 다음 사항에 유의하는 것이 좋습니다.  
  
-   게시 또는 구독의 수가 많은 경우 사용자 인터페이스에 대한 자동 새로 고침 횟수를 줄이십시오.  
  
-   여러 복제 모니터 인스턴스를 동시에 실행하지 마십시오.  
  
-   많은 배포자를 등록한 다음 복제 모니터가 자동으로 이러한 모든 배포자에 연결하도록 설정하지 마십시오.  
  
## <a name="see-also"></a>관련 항목  
 [복제 유지 관리 작업 실행&#40;SQL Server Management Studio&#41;](../../../ssms/sql-server-management-studio-ssms.md)   
 [복제 모니터링](../monitoring-replication.md)  
  
  
