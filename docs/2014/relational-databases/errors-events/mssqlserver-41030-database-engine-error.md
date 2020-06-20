---
title: MSSQLSERVER_41030 | Microsoft 문서
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 41030 (Database Engine error)
ms.assetid: c85341ae-0fbf-42ae-9275-4cfe678238f0
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: d9c1b8c872ff32fdb4207ec3925334d14d25f813
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/18/2020
ms.locfileid: "85033328"
---
# <a name="mssqlserver_41030"></a>MSSQLSERVER_41030
    
## <a name="details"></a>세부 정보  
  
|||  
|-|-|  
|제품 이름|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|이벤트 ID|41030|  
|이벤트 원본|MSSQLSERVER|  
|구성 요소|SQLEngine|  
|심볼 이름|OPEN_CLUSTER_SUB_KEY|  
|메시지 텍스트|Windows Server 장애 조치(Failover) 클러스터링 레지스트리 하위 키 '%.*ls'을(를) 열지 못했습니다(오류 코드 %d).  부모 키는 클러스터 루트 키입니다.  WSFC 서비스가 실행 중이 아니거나 현재 상태에서 액세스할 수 없거나 지정된 인수가 올바르지 않습니다. 해당 가용성 그룹이 삭제된 경우 이 오류가 발생할 수 있습니다. 이 오류 코드에 대한 자세한 내용은 Windows 개발 설명서의 "시스템 오류 코드"를 참조하십시오.|  
  
## <a name="explanation"></a>설명  
 WSFC 클러스터가 제거된 경우 [!INCLUDE[ssHADR](../../includes/sshadr-md.md)]과 관련된 모든 레지스트리 키가 제거됩니다.  
  
## <a name="user-action"></a>사용자 동작  
 WSFC 클러스터를 다시 만든 후 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]의 인스턴스가 AlwaysOn에 설정된 모든 클러스터 노드에서 AlwaysOn을 해제한 다음 다시 설정합니다. 이 태스크에 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 구성 관리자를 사용할 수 있습니다.  
  
## <a name="see-also"></a>참고 항목  
 [AlwaysOn 가용성 그룹 &#40;SQL Server 사용 및 사용 안 함&#41;](../../database-engine/availability-groups/windows/enable-and-disable-always-on-availability-groups-sql-server.md)   
 [SQL Server의 WSFC&#40;Windows Server 장애 조치(failover) 클러스터링&#41;](../../sql-server/failover-clusters/windows/windows-server-failover-clustering-wsfc-with-sql-server.md)  
  
  
