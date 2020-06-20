---
title: '자습서: 계속 연결된 서버 간 데이터 복제 | Microsoft 문서'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- tutorials [SQL Server replication]
- replication [SQL Server], tutorials
- wizards [SQL Server replication]
ms.assetid: 7b18a04a-2c3d-4efe-a0bc-c3f92be72fd0
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 8c63e48d4c5f5bfad6fe50155cd7fd7a088c2178
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/18/2020
ms.locfileid: "85047621"
---
# <a name="tutorial-replicating-data-between-continuously-connected-servers"></a>자습서: 계속 연결된 서버 간 데이터 복제
  복제는 계속 연결된 서버 간에 데이터를 이동할 때 발생하는 문제를 해결하는 좋은 방법입니다. 복제 마법사를 사용하면 복제 토폴로지를 쉽게 구성하고 관리할 수 있습니다. 이 자습서에서는 계속 연결된 서버에 대해 복제 토폴로지를 구성하는 방법에 대해 설명합니다.  
  
## <a name="what-you-will-learn"></a>학습 내용  
 이 자습서에서는 트랜잭션 복제를 사용하여 한 데이터베이스의 데이터를 다른 데이터베이스에 게시하는 방법을 보여 줍니다. 첫 단원에서는 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 를 사용하여 게시를 만드는 방법을 보여 줍니다. 이후 단원에서는 구독을 만들고 이에 대해 유효성을 검사하는 방법과 대기 시간을 측정하는 방법을 보여 줍니다.  
  
## <a name="requirements"></a>요구 사항  
 이 자습서는 기본적인 데이터베이스 작업에는 익숙하지만 복제에 대한 경험은 풍부하지 않은 사용자를 위한 것입니다. 이 자습서를 사용하려면 이전 자습서인 [복제용 서버 준비](tutorial-preparing-the-server-for-replication.md)를 완료해야 합니다.  
  
 이 자습서를 사용하려면 시스템에 다음 구성 요소가 있어야 합니다.  
  
-   게시자 서버(원본)  
  
    -   Express( [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]) 또는[!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]를 제외한 [!INCLUDE[ssEW](../../includes/ssew-md.md)]의 모든 버전. 이들 버전은 복제 게시자가 될 수 없습니다.  
  
    -   [!INCLUDE[ssSampleDBUserInputNonLocal](../../includes/sssampledbuserinputnonlocal-md.md)] 예제 데이터베이스. 보안을 위해 예제 데이터베이스는 기본적으로 설치되지 않습니다.  
  
-   구독자 서버(대상)  
  
    -   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]를 제외한 [!INCLUDE[ssEW](../../includes/ssew-md.md)]의 모든 버전. [!INCLUDE[ssEW](../../includes/ssew-md.md)] 는 트랜잭션 복제에서 구독자가 될 수 없습니다.  
  
    > [!NOTE]  
    >  복제는 기본적으로 [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] 에 설치되지 않습니다.  
  
> [!NOTE]  
>  에서는 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] **sysadmin** 고정 서버 역할의 멤버인 로그인을 사용 하 여 게시자 및 구독자에 연결 해야 합니다.  
  
 **이 자습서를 완료 하는 데 소요 되는 예상 시간: 30 분**  
  
## <a name="lessons-in-this-tutorial"></a>이 자습서의 단원  
  
-   [1단원: 트랜잭션 복제를 사용하여 데이터 게시](lesson-1-publishing-data-using-transactional-replication.md)  
  
-   [2단원: 트랜잭션 게시에 구독 만들기](lesson-2-creating-a-subscription-to-the-transactional-publication.md)  
  
-   [3단원: 구독 유효성 검사 및 대기 시간 측정](lesson-3-validating-the-subscription-and-measuring-latency.md)  
  
 [자습서 시작](transactional/transactional-replication.md)  
  
## <a name="see-also"></a>참고 항목  
 [복제 프로그래밍 개념](concepts/replication-programming-concepts.md)  
  
  
