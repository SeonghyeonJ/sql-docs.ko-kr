---
title: MSSQLSERVER_41301 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 41301 (Database Engine error)
ms.assetid: c6127e1e-2846-4ee9-bc42-2d896ea9730e
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: cb7ce5f35232dca89650079cec9d26151882277d
ms.sourcegitcommit: b57d98e9b2444348f95c83a24b8eea0e6c9da58d
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/21/2020
ms.locfileid: "86551478"
---
# <a name="mssqlserver_41301"></a>MSSQLSERVER_41301
    
## <a name="details"></a>세부 정보  
  
|attribute|값|  
|-|-|  
|제품 이름|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|이벤트 ID|41301|  
|이벤트 원본|MSSQLSERVER|  
|구성 요소|SQLEngine|  
|심볼 이름|COMMIT_DEPENDENCY_FAILURE|  
|메시지 텍스트|현재 트랜잭션이 종속성을 갖고 있는 이전 트랜잭션이 중단되어 현재 트랜잭션을 더 이상 커밋할 수 없습니다.|  
  
## <a name="explanation"></a>설명  
 종속성 오류가 발생하여 트랜잭션을 종료합니다.  
  
 종속 트랜잭션이 너무 많아도 이 오류가 발생할 수 있습니다. 모든 쓰기 트랜잭션은 제한된 수의 종속 트랜잭션을 가질 수 있습니다. 예를 들어, 너무 많은 읽기 트랜잭션에서 업데이트 트랜잭션에 대한 종속성을 가지려고 할 경우 이 오류가 발생할 수 있습니다.  
  
## <a name="user-action"></a>사용자 동작  
 트랜잭션에서 어떤 작업도 수행하지 않습니다. ROLLBACK TRAN을 호출하여 트랜잭션을 롤백합니다. 자세한 내용은 [메모리 내 OLTP&#40;메모리 내 최적화&#41;](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md)를 참조하세요.  
  
## <a name="see-also"></a>참고 항목  
 [AlwaysOn 가용성 그룹 활성화 및 비활성화&#40;SQL Server&#41;](../../database-engine/availability-groups/windows/enable-and-disable-always-on-availability-groups-sql-server.md)  
  
  
