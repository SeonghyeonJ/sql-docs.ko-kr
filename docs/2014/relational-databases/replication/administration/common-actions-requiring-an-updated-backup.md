---
title: 업데이트된 백업이 필요한 일반 동작 | Microsoft 문서
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- recovery [SQL Server replication], actions requiring a backup
- restoring [SQL Server replication], actions requiring a backup
- backups [SQL Server replication], actions requiring a backup
ms.assetid: a5975bf4-183e-42e3-b7d1-ad02f89d2e1d
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 184bda56568cfcedbc07183bd2be7fdde7a789e4
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62705032"
---
# <a name="common-actions-requiring-an-updated-backup"></a>업데이트된 백업이 필요한 일반 동작
  정기적인 로그 백업을 수행할 경우 모든 복제 관련 변경 내용은 로그 백업에 캡처됩니다. 로그 백업을 수행하지 않는 경우 복제 스키마 또는 토폴로지에 변경 작업을 수행한 후 게시, 배포, 구독, **msdb**및 **master** 데이터베이스 백업을 수행합니다.  
  
## <a name="publication-database"></a>게시 데이터베이스  
 다음 작업 후 게시 데이터베이스를 백업합니다.  
  
-   새 게시 만들기  
  
-   필터링을 포함한 게시 속성 변경  
  
-   기존 게시에 아티클 추가  
  
-   구독을 게시 차원에서 다시 초기화  
  
-   게시된 테이블의 스키마 변경  
  
-   [sp_addscriptexec&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addscriptexec-transact-sql)를 사용한 요청 시 스크립트 수행  
  
-   아티클 속성 변경  
  
-   게시 삭제  
  
-   아티클 삭제  
  
-   복제 해제  
  
## <a name="distribution-database"></a>배포 데이터베이스  
 다음 작업 후 배포 데이터베이스를 백업합니다.  
  
-   복제 에이전트 프로필 만들기 또는 수정  
  
-   복제 에이전트 프로필 매개 변수 수정  
  
-   밀어넣기 구독의 일정을 비롯한 복제 에이전트 속성 변경  
  
-   ID 범위 자동 관리 기능으로 새로운 범위의 ID 지정  
  
## <a name="subscription-database"></a>구독 데이터베이스  
 다음 작업 후 구독 데이터베이스를 백업합니다.  
  
-   구독 속성 변경  
  
-   게시자에서 병합 구독 속성 변경  
  
-   구독 삭제  
  
-   복제 해제  
  
## <a name="msdb-database"></a>msdb 데이터베이스  
 다음 작업 후 해당 노드에서 **msdb** 시스템 데이터베이스를 백업합니다.  
  
-   복제 활성화 또는 비활성화  
  
-   배포자에서 배포 데이터베이스 추가 또는 삭제  
  
-   게시자에서 데이터베이스에 게시 활성화 또는 비활성화  
  
-   배포자에서 복제 에이전트 프로필 만들기 또는 수정  
  
-   배포자에서 복제 에이전트 프로필 매개 변수 수정  
  
-   배포자에서 밀어넣기 구독의 일정을 비롯한 복제 에이전트 속성 변경  
  
-   구독자에서 밀어넣기 구독의 일정을 비롯한 복제 에이전트 속성 변경  
  
-   배포자 및 구독자에서 변환 가능한 구독을 사용하는 트랜잭션 게시와 연결된 DTS 패키지 만들기  
  
-   배포자 및 구독자에서 변환 가능한 구독 추가 또는 삭제  
  
## <a name="master-database"></a>master 데이터베이스  
 다음 작업 후 해당 노드에서 **master** 시스템 데이터베이스를 백업합니다.  
  
-   복제 활성화 또는 비활성화  
  
-   배포자에서 배포 데이터베이스 추가 또는 삭제  
  
-   게시자에서 데이터베이스에 게시 활성화 또는 비활성화  
  
-   게시자의 데이터베이스에 첫 번째 게시 추가 또는 마지막 게시 삭제  
  
-   구독자의 데이터베이스에 첫 번째 구독 추가 또는 마지막 구독 삭제  
  
-   게시자 및 배포자의 배포 게시자에서 게시자 활성화 또는 비활성화  
  
## <a name="see-also"></a>관련 항목  
 [SQL Server 데이터베이스 백업 및 복원](../../backup-restore/back-up-and-restore-of-sql-server-databases.md)   
 [복제된 데이터베이스 백업 및 복원](back-up-and-restore-replicated-databases.md)  
  
  
