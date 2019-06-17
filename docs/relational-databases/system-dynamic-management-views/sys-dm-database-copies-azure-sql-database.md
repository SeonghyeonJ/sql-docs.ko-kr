---
title: sys.dm_database_copies (Azure SQL Database) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.service: sql-database
ms.reviewer: ''
ms.topic: language-reference
f1_keywords:
- dm_database_copies_TSQL
- sys.dm_database_copies
- dm_database_copies
- sys.dm_database_copies_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- dm_database_copies
- sys.dm_database_copies
ms.assetid: d03d4657-86d1-4496-97e6-cc3bc292e0b1
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: 6b5a0a656693d66e701642c9c2202c2862136a54
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62741967"
---
# <a name="sysdmdatabasecopies-azure-sql-database"></a>sys.dm_database_copies(Azure SQL Database)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

  데이터베이스 복사본에 대한 정보를 반환합니다.  
  
지역에서 복제 링크에 대 한 정보를 반환 하려면 사용 합니다 [sys.geo_replication_links](../../relational-databases/system-dynamic-management-views/sys-geo-replication-links-azure-sql-database.md) 하거나 [sys.dm_geo_replication_link_status](../../relational-databases/system-dynamic-management-views/sys-dm-geo-replication-link-status-azure-sql-database.md) 보기 (SQL Database V12에서 사용 가능).
  
  
|열 이름|데이터 형식|Description|  
|-----------------|---------------|-----------------|  
|**database_id**|**int**|`sys.databases` 뷰의 현재 데이터베이스 ID입니다.|  
|**start_date**|**datetimeoffset**|지역의 [!INCLUDE[ssSDS](../../includes/sssds-md.md)] 데이터 센터에서 데이터베이스 복사가 시작된 UTC 시간입니다.|  
|**modify_date**|**datetimeoffset**|지역의 [!INCLUDE[ssSDS](../../includes/sssds-md.md)] 데이터 센터에서 데이터베이스 복사가 완료된 UTC 시간입니다. 새 데이터베이스는 현 시점에서 주 데이터베이스와 트랜잭션 일관성이 유지됩니다. 완료 정보는 1 분 마다 업데이트 됩니다.<br /><br />Percent_complete 필드의 마지막 업데이트를 반영 하는 UTC 시간입니다.|  
|**percent_complete**|**real**|복사된 바이트의 백분율입니다. 값은 0에서 100 사이입니다. [!INCLUDE[ssSDS](../../includes/sssds-md.md)]는 자동으로 장애 조치와 같은 몇 가지 오류에서 복구하고 데이터베이스 복사를 다시 시작 수 있습니다. 이 경우 percent_complete는 0에서 다시 시작합니다.|  
|**error_code**|**int**|복사하는 동안 발생한 오류를 나타내는 코드 0보다 큰 경우. 오류가 발생하지 않은 경우 값은 0과 같습니다.|  
|**error_desc**|**nvarchar(4096)**|복사하는 동안 발생한 오류에 대한 설명입니다.|  
|**error_severity**|**int**|데이터베이스 복사가 실패한 경우 16을 반환합니다.|  
|**error_state**|**int**|복사가 실패한 경우 1을 반환합니다.|  
|**copy_guid**|**uniqueidentifier**|복사 작업의 고유 ID입니다.|  
|**partner_server**|**sysname**|복사본을 만든 SQL Database 서버 이름입니다.|  
|**partner_database**|**sysname**|파트너 서버에 있는 데이터베이스 복사본의 이름입니다.|  
|**replication_state**|**tinyint**|이 데이터베이스에 대 한 연속 복사 복제의 상태입니다. 값은 다음과 같습니다.<br /><br /> 0 = 보류 중입니다. 데이터베이스 복사본을 만드는 예약 되었지만 필요한 준비 단계는 아직 완료 되지 않았거나 시드 할당량에 의해 일시적으로 차단 됩니다.<br /><br /> 1 = Seeding 합니다. 시드 되는 데이터베이스 복사는 완벽 하 게를 아직 동기화 하지 원본 데이터베이스입니다. 이 상태의 복사본을 연결할 수 없습니다. 시드 진행 중인 작업을 취소 하려면 데이터베이스 복사를 삭제 해야 합니다.|  
|**replication_state_desc**|**nvarchar(256)**|replication_state에 대한 설명으로, 다음 중 하나입니다.<br /><br /> PENDING<br /><br /> SEEDING<br />|  
|**maximum_lag**|**int**|예약 된 필드입니다.|  
|**is_continuous_copy**|**bit**|0 =  Returns 0|  
|**is_target_role**|**bit**|0 = 원본 데이터베이스<br /><br /> 1 = 데이터베이스 복사|  
|**is_interlink_connected**|bit|예약 된 필드입니다.|  
|**is_offline_secondary**|bit|예약 된 필드입니다.|  
  
## <a name="permissions"></a>사용 권한  
 이 보기는 에서만 사용할 수는 **마스터** 데이터베이스 서버 수준 보안 주체 로그인 합니다.  
  
## <a name="remarks"></a>Remarks  
 사용할 수는 **sys.dm_database_copies** 뷰에서 **마스터** 원본 또는 대상 데이터베이스 [!INCLUDE[ssSDS](../../includes/sssds-md.md)] 서버. 데이터베이스 복사가 완료 된 시점과 새 데이터베이스가 온라인으로의 행을 **sys.dm_database_copies** 뷰가 자동으로 제거 됩니다.  
  
  
