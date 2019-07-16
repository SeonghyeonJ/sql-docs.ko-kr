---
title: sys.availability_group_listener_ip_addresses (TRANSACT-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- availability_group_listener_ip_addresses
- sys.availability_group_listener_ip_addresses
- availability_group_listener_ip_addresses_TSQL
- sys.availability_group_listener_ip_addresses_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- Availability Groups [SQL Server], monitoring
- Availability Groups [SQL Server], listeners
- sys.availability_group_listener_ip_addresses catalog view
ms.assetid: e515fa6b-1354-4110-9b70-ab2e6164c992
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: a9c66e12ec326ba5021de0829b0d7cc479f858c1
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67997590"
---
# <a name="sysavailabilitygrouplisteneripaddresses-transact-sql"></a>sys.availability_group_listener_ip_addresses(Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  WSFC(Windows Server 장애 조치(Failover) 클러스터링) 클러스터에 있는 Always On 가용성 그룹 수신기에 연결되는 모든 IP 주소에 대해 하나의 행을 반환합니다.  
  
 기본 키: **listener_id** + **ip_address** + **ip_sub_mask**  
  
  
|열 이름|데이터 형식|설명|  
|-----------------|---------------|-----------------|  
|**listener_id**|**nvarchar(36)**|WSFC(Windows Server 장애 조치(Failover) 클러스터링) 클러스터의 리소스 GUID입니다.|  
|**ip_address**|**nvarchar(48)**|가용성 그룹 수신기에 대해 구성된 가상 IP 주소입니다. 단일 IPv4 또는 IPv6 주소를 반환합니다.|  
|**ip_subnet_mask**|**nvarchar(15)**|가용성 그룹 수신기에 대해 구성되는 IPv4 주소(있는 경우)에 대해 구성된 IP 서브넷 마스크입니다.<br /><br /> NULL = IPv6 서브넷|  
|**is_dhcp**|**bit**|IP 주소가 DHCP에 의해 구성되어 있는지 여부를 나타내며 다음 중 하나입니다.<br /><br /> 0 = IP 주소가 DHCP에 의해 구성되어 있지 않습니다.<br /><br /> 1 = IP 주소가 DHCP에 의해 구성되어 있습니다.|  
|**network_subnet_ip**|**nvarchar(48)**|IP 주소가 속한 서브넷을 지정하는 네트워크 서브넷 IP 주소입니다.|  
|**network_subnet_prefix_length**|**int**|IP 주소가 속한 서브넷의 네트워크 서브넷 접두사 길이입니다.|  
|**network_subnet_ipv4_mask**|**nvarchar(45)**|IP 주소가 속한 서브넷의 네트워크 서브넷 마스크입니다. **network_subnet_ipv4_mask** 의 WITH DHCP 절에서 DHCP < network_subnet_option > 옵션을 지정 하는 [CREATE AVAILABILITY GROUP](../../t-sql/statements/create-availability-group-transact-sql.md) 하거나 [ALTER AVAILABILITY GROUP](../../t-sql/statements/alter-availability-group-transact-sql.md) [!INCLUDE[tsql](../../includes/tsql-md.md)] 문입니다.<br /><br /> NULL = IPv6 서브넷|  
|**state**|**tinyint**|WSFC 클러스터의 IP 리소스 ONLINE/OFFLINE 상태이며 다음 중 하나입니다.<br /><br /> 1 = 온라인. IP 리소스가 온라인 상태입니다.<br /><br /> 0 = 오프라인. IP 리소스가 오프라인 상태입니다.<br /><br /> 2 = 온라인 보류 중. IP 리소스가 오프라인 상태이지만 온라인으로 전환되고 있습니다.<br /><br /> 3 = 실패. IP 리소스가 온라인 상태로 전환되었지만 실패했습니다.|  
|**state_desc**|**nvarchar(60)**|에 대 한 설명을 **상태**하나씩입니다.<br /><br /> ONLINE<br /><br /> OFFLINE<br /><br /> ONLINE_PENDING<br /><br /> FAILED|  
  
## <a name="security"></a>보안  
  
### <a name="permissions"></a>사용 권한  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 자세한 내용은 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)을 참조하세요.  
  
## <a name="see-also"></a>관련 항목  
 [SQL Server 시스템 카탈로그 FAQ](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)   
 [카탈로그 뷰&#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)  
  
  
