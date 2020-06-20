---
title: 복제된 데이터베이스 업그레이드 | Microsoft Docs
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
helpviewer_keywords:
- merge replication database upgrades [SQL Server replication]
- replication [SQL Server], upgrading
- transactional replication, upgrading databases
- snapshot replication [SQL Server], upgrading databases
- upgrading replicated databases
ms.assetid: 9926a4f7-bcd8-4b9b-9dcf-5426a5857116
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 326a94820876b40128428aac58e47c650ce122b8
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84931890"
---
# <a name="upgrade-replicated-databases"></a>복제된 데이터베이스 업그레이드
  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]은 이전 버전의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 복제된 데이터베이스를 업그레이드할 수 있도록 지원합니다. 따라서 노드 업그레이드 중에 다른 노드의 작업을 중지할 필요가 없으며 한 토폴로지 내에서 지원되는 버전과 관련된 규칙만 잘 지키면 됩니다.  
  
-   배포자는 게시자 버전 이상인 모든 버전일 수 있습니다. 많은 경우에 배포자는 게시자와 동일한 인스턴스에 있습니다.  
  
-   게시자는 배포자 버전 이하인 모든 버전일 수 있습니다.  
  
-   구독자 버전은 게시 유형에 따라 달라집니다.  
  
    -   트랜잭션 게시에 대한 구독자는 게시자의 두 가지 버전 중 어떤 버전이든 될 수 있습니다. 예를 들어 실행 중인 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 게시자는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 구독자를 가질 수 있으며 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 게시자는 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 구독자를 가질 수 있습니다.  
  
    -   병합 게시에 대한 구독자는 게시자 버전 이하인 모든 버전일 수 있습니다.  
  
> [!NOTE]  
>  이 항목은 설치 도움말 설명서와 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 온라인 설명서에서 사용할 수 있습니다. 설치 도움말 설명서에서 굵게 표시된 항목 링크는 온라인 설명서에만 제공되는 항목을 나타냅니다.  
  
## <a name="run-the-log-reader-agent-for-transactional-replication-before-upgrade"></a>업그레이드 전에 트랜잭션 복제용 로그 판독기 에이전트 실행  
 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]로 업그레이드하기 전에 게시된 테이블의 커밋된 모든 트랜잭션을 로그 판독기 에이전트가 처리했는지 확인해야 합니다. 모든 트랜잭션이 처리되었는지 확인하려면 트랜잭션 게시를 포함하는 각 데이터베이스에 대해 다음 단계를 수행하십시오.  
  
1.  데이터베이스에서 로그 판독기 에이전트가 실행 중인지 확인합니다. 기본적으로 에이전트는 계속 실행됩니다.  
  
2.  게시된 테이블에 대한 사용자 동작을 중지합니다.  
  
3.  로그 판독기 에이전트가 배포 데이터베이스로 트랜잭션을 복사할 때까지 기다린 다음 에이전트를 중지합니다.  
  
4.  [sp_replcmds](/sql/relational-databases/system-stored-procedures/sp-replcmds-transact-sql) 를 실행하여 모든 트랜잭션이 처리되었는지 확인합니다. 이 프로시저의 결과 집합은 비어 있어야 합니다.  
  
5.  [sp_replflush](/sql/relational-databases/system-stored-procedures/sp-replflush-transact-sql) 를 실행하여 sp_replcmds의 연결을 닫습니다.  
  
6.  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]로 서버를 업그레이드합니다.  
  
7.  업그레이드 후에 자동으로 시작되지 않는 경우 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 및 로그 판독기 에이전트를 다시 시작합니다.  
  
## <a name="run-agents-for-merge-replication-after-upgrade"></a>업그레이드 후 병합 복제를 위한 에이전트 실행  
 업그레이드 후에 각 병합 게시에 대해 스냅샷 에이전트를 실행하고 각 구독에 대해 병합 에이전트를 실행하여 복제 메타데이터를 업데이트합니다. 구독을 다시 초기화할 필요가 없으므로 새 스냅샷을 적용하지 않아도 됩니다. 구독 메타데이터는 업그레이드 후에 병합 에이전트가 처음 실행될 때 업데이트됩니다. 즉, 게시자를 업그레이드하는 동안 구독 데이터베이스를 온라인 활성 상태로 유지할 수 있습니다.  
  
 병합 복제는 게시 및 구독 데이터베이스의 많은 시스템 테이블에 게시 및 구독 메타데이터를 저장합니다. 스냅샷 에이전트를 실행하면 게시 메타데이터가 업데이트되고 병합 에이전트를 실행하면 구독 메타데이터가 업데이트됩니다. 따라서 게시 스냅샷을 생성하기만 하면 됩니다. 병합 게시에 매개 변수가 있는 필터가 사용되면 각 파티션은 스냅샷도 갖게 됩니다. 이러한 분할된 스냅샷은 업데이트하지 않아도 됩니다.  
  
 에이전트는 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], 복제 모니터 또는 명령줄에서 실행합니다. 스냅샷 에이전트를 실행하는 방법은 다음 항목을 참조하십시오.  
  
-   [초기 스냅샷 만들기 및 적용](../../../2014/relational-databases/replication/create-and-apply-the-initial-snapshot.md)  
  
-   [복제 에이전트 시작 및 중지&#40;SQL Server Management Studio&#41;](../../relational-databases/replication/agents/start-and-stop-a-replication-agent-sql-server-management-studio.md)  
  
-   [초기 스냅샷 만들기 및 적용](../../../2014/relational-databases/replication/create-and-apply-the-initial-snapshot.md)  
  
-   [Replication Agent Executables Concepts](../../../2014/relational-databases/replication/concepts/replication-agent-executables-concepts.md)  
  
 병합 에이전트를 실행하는 방법은 다음 항목을 참조하십시오.  
  
-   [끌어오기 구독 동기화](../../../2014/relational-databases/replication/synchronize-a-pull-subscription.md)  
  
-   [밀어넣기 구독 동기화](../../../2014/relational-databases/replication/synchronize-a-push-subscription.md)  
  
 병합 복제를 사용하는 토폴로지에서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 를 업그레이드한 후에 새 기능을 사용하려면 모든 게시의 게시 호환성 수준을 변경합니다.  
  
## <a name="upgrading-to-standard-workgroup-or-express-editions"></a>Standard, Workgroup 또는 Express Edition으로 업그레이드  
 한 에디션의 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 에서 다른 에디션으로 업그레이드하기 전에 현재 사용 중인 기능이 업그레이드할 에디션에서 지원되는지 확인하십시오. 자세한 내용은 [SQL Server 2014 버전에서 지 원하는 기능](../../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md)에서 복제에 대 한 섹션을 참조 하세요.  
  
## <a name="web-synchronization-for-merge-replication"></a>병합 복제에 대한 웹 동기화  
 병합 복제에 대한 웹 동기화 옵션을 사용하려면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 복제 수신기(replisapi.dll)를 동기화에 사용되는 인터넷 정보 서비스(IIS) 서버의 가상 디렉터리에 복사해야 합니다. 웹 동기화를 구성할 때는 웹 동기화 구성 마법사를 실행하여 가상 디렉터리에 파일을 복사합니다. IIS 서버에 설치된 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 구성 요소를 업그레이드하는 경우에는 COM 디렉터리의 replisapi.dll을 IIS 서버의 가상 디렉터리에 수동으로 복사해야 합니다. 웹 동기화를 구성하는 방법은 [웹 동기화 구성](../../../2014/relational-databases/replication/configure-web-synchronization.md)을 참조하세요.  
  
## <a name="restoring-a-replicated-database-from-an-earlier-version"></a>이전 버전에서 복제된 데이터베이스 복원  
 이전 버전에서 복제된 데이터베이스의 백업을 복원할 때 복제 설정이 유지되게 하려면 백업 당시의 서버 및 데이터베이스와 같은 이름의 서버 및 데이터베이스에 복원합니다.  
  
## <a name="see-also"></a>참고 항목  
 [복제 관리 FAQ](../../relational-databases/replication/administration/frequently-asked-questions-for-replication-administrators.md)   
 [복제의 이전 버전과의 호환성](../../../2014/relational-databases/replication/replication-backward-compatibility.md)   
 [지원되는 버전 및 에디션 업그레이드](../../database-engine/install-windows/supported-version-and-edition-upgrades.md)   
 [SQL Server 2014로 업그레이드](upgrade-sql-server.md)  
  
  
