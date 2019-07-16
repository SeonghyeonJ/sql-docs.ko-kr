---
title: sys.dm_hadr_cluster_members (TRANSACT-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 01/31/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_hadr_cluster_members_TSQL
- sys.dm_hadr_cluster_members
- dm_hadr_cluster_members_TSQL
- dm_hadr_cluster_members
dev_langs:
- TSQL
helpviewer_keywords:
- Availability Groups [SQL Server], monitoring
- Availability Groups [SQL Server], WSFC clusters
- sys.dm_hadr_cluster_members catalog view
ms.assetid: feb20b3a-8835-41d3-9a1c-91d3117bc170
author: MikeRayMSFT
ms.author: mikeray
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 8b28b708aabfdf3ec4e569aab6d8a95e2330b370
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67900762"
---
# <a name="sysdmhadrclustermembers-transact-sql"></a>sys.dm_hadr_cluster_members(Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에 대해 사용하도록 설정된 [!INCLUDE[ssHADR](../../includes/sshadr-md.md)]의 로컬 인스턴스를 호스팅하는 WSFC 노드에 WSFC 쿼럼이 있는 경우 쿼럼을 구성하는 각 멤버에 대한 행과 각 멤버의 상태를 반환합니다. 여기에 클러스터의 모든 노드 (의해 CLUSTER_ENUM_NODE 형식으로 반환 합니다 **Clusterenum** 함수) 및 디스크 또는 파일 공유 미러링 모니터 서버에 있는 경우. 지정된 구성원에 대해 반환되는 행에는 해당 구성원의 상태에 대한 정보가 들어 있습니다. 하나의 노드가 될 때 다운 되는 과반수 노드 쿼럼이 있는 5 노드 클러스터에 대 한 예를 들어 **sys.dm_hadr_cluster_members** 쿼리를 사용 하는 서버 인스턴스에서 [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] 쿼럼 가진 노드에 있는 **sys.dm_hadr_cluster_members** "NODE_DOWN"으로 다운 노드의 상태를 반영 합니다.  
  
 WSFC 노드에 쿼럼이 없으면 반환되는 행이 없습니다.  
  
 이 동적 관리 뷰를 사용하여 다음을 확인할 수 있습니다.  
  
-   WSFC 클러스트에서 현재 실행 중인 노드  
  
-   노드 과반수의 경우에 쿼럼이 손실되기 전에 WSFC 클러스터에서 추가로 허용할 수 있는 장애 횟수  

 > [!TIP]
 > 부터 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)],이 동적 관리 뷰에서 Always On 장애 조치 클러스터 인스턴스 Always On 가용성 그룹 외에도 지원 합니다.  
  
|열 이름|데이터 형식|Description|  
|-----------------|---------------|-----------------|  
|**member_name**|**nvarchar(128)**|구성원 이름이며, 컴퓨터 이름, 드라이브 문자 또는 파일 공유 경로일 수 있습니다.|  
|**member_type**|**tinyint**|구성원의 유형이며 다음 중 하나입니다.<br /><br /> 0 = WSFC 노드<br /><br /> 1 = 디스크 미러링 모니터<br /><br /> 2 = 파일 공유 미러링 모니터<br /><br /> 3 = 클라우드 감시|  
|**member_type_desc**|**nvarchar(50)**|에 대 한 설명을 **member_type**하나씩입니다.<br /><br /> CLUSTER_NODE<br /><br /> DISK_WITNESS<br /><br /> FILE_SHARE_WITNESS<br /><br /> CLOUD_WITNESS|  
|**member_state**|**tinyint**|구성원 상태이며 다음 중 하나입니다.<br /><br /> 0 = 오프라인<br /><br /> 1 = 온라인|  
|**member_state_desc**|**nvarchar(60)**|에 대 한 설명을 **member_state**하나씩입니다.<br /><br /> UP<br /><br /> 아래로|  
|**number_of_quorum_votes**|**tinyint**|이 쿼럼 구성원이 소유한 쿼럼 투표의 수입니다. No majority의 경우: 디스크만 쿼럼이 며, 기본값은 0입니다. 다른 쿼럼 유형의 경우 기본값은 1입니다.|  
  
## <a name="permissions"></a>사용 권한  
 을 실행하려면 서버에 대해 VIEW SERVER STATE 권한이 필요합니다.  
  
## <a name="examples"></a>예  
  
## <a name="see-also"></a>관련 항목  
 [Always On 가용성 그룹 동적 관리 뷰 및 함수&#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/always-on-availability-groups-dynamic-management-views-functions.md)   
 [AlwaysOn 가용성 그룹 카탈로그 뷰&#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/always-on-availability-groups-catalog-views-transact-sql.md)   
 [가용성 그룹 모니터링&#40;Transact-SQL&#41;](../../database-engine/availability-groups/windows/monitor-availability-groups-transact-sql.md)   
 [AlwaysOn 가용성 그룹 &#40;SQL Server&#41;](../../database-engine/availability-groups/windows/always-on-availability-groups-sql-server.md)  
  
  
