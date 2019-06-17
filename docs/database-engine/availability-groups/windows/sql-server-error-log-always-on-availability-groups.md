---
title: SQL Server 오류 로그(Always On 가용성 그룹)(SQL Server) | Microsoft Docs
ms.custom: ag-guide
ms.date: 06/13/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
ms.assetid: 39d0c98d-75af-4dd1-b908-30d31af56f2a
author: rothja
ms.author: jroth
manager: jroth
ms.openlocfilehash: 175903b154f0c95bcbb033526b96006dace5b036
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/07/2019
ms.locfileid: "66803549"
---
# <a name="sql-server-error-log-always-on-availability-groups"></a>SQL Server 오류 로그(Always On 가용성 그룹)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  SQL Server 오류 로그는 다음과 같은 Always On 가용성 그룹에 영향을 주는 이벤트를 보고합니다.  
  
-   WSFC(Windows Server 장애 조치(Failover) 클러스터링) 클러스터와 통신    
-   가용성 복제본의 상태 전환    
-   가용성 데이터베이스의 상태 전환    
-   주 복제본과 보조 복제본 간 가용성 데이터베이스의 연결 상태    
-   가용성 그룹 엔드포인트의 상태    
-   가용성 그룹 수신기의 상태    
-   SQL Server 리소스 DLL(WSFC 클러스터에서 실행) 및 SQL Server 인스턴스 간의 임대 시간(자세한 내용은 [작동 방법: SQL Server Always On 임대 시간 제한](https://blogs.msdn.com/b/psssql/archive/2012/09/07/how-it-works-sql-server-alwayson-lease-timeout.aspx) 참조)    
-   가용성 그룹의 오류 이벤트  

다음과 같은 현상은 SQL Server 오류 로그를 검토해야 합니다.  

-   가용성 데이터베이스에 액세스할 수 없음    
-   예기치 않은 가용성 그룹 장애 조치(failover)    
-   예기치 않게 확인 중 상태의 가용성 그룹    
-   비활성화 상태의 가용성 그룹  
  
자세한 내용은[SQL Server 오류 로그 보기&#40;SQL Server Management Studio&#41;](~/relational-databases/performance/view-the-sql-server-error-log-sql-server-management-studio.md)를 참조하세요.  
  
  
