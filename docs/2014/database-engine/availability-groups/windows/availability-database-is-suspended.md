---
title: 가용성 데이터베이스가 일시 중지됨 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.agdashboard.drp1notsuspended.issues.f1
helpviewer_keywords:
- Availability Groups [SQL Server], policies
ms.assetid: 6baee70f-848c-4e86-b20d-78875c0f82cb
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c2656c53dd151825cd10e54e5b63e5ac0a2cee1f
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84937144"
---
# <a name="availability-database-is-suspended"></a>가용성 데이터베이스가 일시 중지됨
    
## <a name="introduction"></a>소개  
  
|||  
|-|-|  
|**정책 이름**|가용성 데이터베이스 일시 중지 상태|  
|**문제점**|가용성 데이터베이스가 일시 중지됨|  
|**범주**|**Warning**|  
|**패싯에**|가용성 데이터베이스|  
  
## <a name="description"></a>Description  
 이 정책은 보조 데이터베이스("보조 데이터베이스 복제본"이라고도 함)의 데이터 이동 상태를 확인합니다. 데이터 이동이 일시 중지되는 경우 정책은 비정상 상태에 있습니다. 그렇지 않으면 정책은 정상 상태입니다.  
  
> [!NOTE]  
>   이 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]릴리스의 경우 가능한 원인 및 해결 방법에 대한 자세한 내용은 TechNet Wiki의 [가용성 데이터베이스가 일시 중지됨](https://go.microsoft.com/fwlink/p/?LinkId=220860) 을 참조하십시오.  
  
## <a name="possible-causes"></a>가능한 원인  
 이 가용성 데이터베이스의 데이터 동기화는 다음과 같은 이유로 일시 중지되었을 수 있습니다.  
  
-   오류가 발생하여 시스템에서 데이터 동기화를 일시 중지했을 수 있습니다.  
  
-   데이터베이스 관리자가 유지 보수를 위해 데이터 동기화를 일시 중지했을 수 있습니다.  
  
## <a name="possible-solution"></a>가능한 해결 방법  
 데이터 동기화를 다시 시작합니다. 문제가 계속되면 이벤트 로그에서 가용성 그룹을 확인하여 시스템에서 데이터 이동이 일시 중지된 이유를 진단합니다.  
  
## <a name="see-also"></a>참고 항목  
 [AlwaysOn 가용성 그룹 &#40;SQL Server 개요&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [AlwaysOn 대시보드 사용&#40;SQL Server Management Studio&#41;](use-the-always-on-dashboard-sql-server-management-studio.md)  
  
  
