---
title: sys.dm_pdw_component_health_active_alerts (TRANSACT-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: conceptual
ms.assetid: c53e4a36-b841-424a-b8e2-255b1878deb6
author: stevestein
ms.author: sstein
monikerRange: '>= aps-pdw-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 7378b5f4f87c2511909aef6b75c412b6043e8c71
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67899553"
---
# <a name="sysdmpdwcomponenthealthactivealerts-transact-sql"></a>sys.dm_pdw_component_health_active_alerts (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  활성 경고 저장 [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] 구성 요소입니다.  
  
|열 이름|데이터 형식|설명|범위|  
|-----------------|---------------|-----------------|-----------|  
|pdw_node_id|**int**|고유 식별자를 [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] 노드.<br /><br /> pdw_node_id "," component_id "," component_instance_id "," alert_id, "및" alert_instance_id이이 보기에 대 한 키를 형성합니다.|NOT NULL|  
|component_id|**int**|ID 구성 요소입니다. 참조 [sys.pdw_health_components &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-pdw-health-components-transact-sql.md)합니다.<br /><br /> pdw_node_id "," component_id "," component_instance_id "," alert_id, "및" alert_instance_id이이 보기에 대 한 키를 형성합니다.|NOT NULL|  
|component_instance_id|**nvarchar(255)**|pdw_node_id "," component_id "," component_instance_id "," alert_id, "및" alert_instance_id이이 보기에 대 한 키를 형성합니다.|NOT NULL|  
|alert_id|**int**|경고 유형에 대 한 ID입니다. 참조 [sys.pdw_health_alerts &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-pdw-health-alerts-transact-sql.md)합니다.<br /><br /> pdw_node_id "," component_id "," component_instance_id "," alert_id, "및" alert_instance_id이이 보기에 대 한 키를 형성합니다.|NOT NULL|  
|alert_instance_id|**nvarchar(36)**|지정된 된 경고의 인스턴스를 식별합니다.<br /><br /> pdw_node_id "," component_id "," component_instance_id "," alert_id, "및" alert_instance_id이이 보기에 대 한 키를 형성합니다.|NOT NULL|  
|current_value|**nvarchar(255)**|경고 StatusChange 유형인 경우 사용 합니다. 현재 구성 요소 상태입니다. 값은 임계값 유형의 경고에 대 한 NULL입니다. 참조 [sys.pdw_health_alerts &#40;TRANSACT-SQL&#41; ](../../relational-databases/system-catalog-views/sys-pdw-health-alerts-transact-sql.md) 경고 유형 목록에 대 한 합니다.|NULL|  
|previous_value|**nvarchar(255)**|경고 StatusChange 유형인 경우 사용 합니다. 이전 구성 요소 상태입니다. 값은 임계값 유형의 경고에 대 한 NULL입니다. 참조 [sys.pdw_health_alerts &#40;TRANSACT-SQL&#41; ](../../relational-databases/system-catalog-views/sys-pdw-health-alerts-transact-sql.md) 경고 유형 목록에 대 한 합니다.|NULL|  
|create_time|**datetime**|경고가 생성 된 날짜 및 시간입니다.|NOT NULL|  
  
 이 보기에 의해 보존 된 최대 행에 대 한 내용은의 "최소 및 최대 값"를 참조 합니다 [!INCLUDE[pdw-product-documentation](../../includes/pdw-product-documentation-md.md)]합니다.  
  
## <a name="see-also"></a>관련 항목  
 [SQL Data Warehouse 및 병렬 데이터 웨어하우스 동적 관리 뷰 &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
