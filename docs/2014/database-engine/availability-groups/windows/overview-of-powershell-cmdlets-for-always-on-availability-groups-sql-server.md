---
title: AlwaysOn 가용성 그룹에 대 한 PowerShell Cmdlet 개요 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], PowerShell cmdlets
- Availability Groups [SQL Server], about
- PowerShell [SQL Server], cmdlets
ms.assetid: b3fef0d5-b6d7-4386-a0f0-d06c165ad4de
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 4996a1026b4c85b105efc09b8381913f7a47942a
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2020
ms.locfileid: "62789460"
---
# <a name="overview-of-powershell-cmdlets-for-alwayson-availability-groups-sql-server"></a>AlwaysOn 가용성 그룹에 대한 PowerShell Cmdlet 개요(SQL Server)
  [!INCLUDE[msCoName](../../../includes/msconame-md.md)] PowerShell은 시스템 관리를 위해 특별히 설계된 태스크 기반 명령줄 셸이자 스크립팅 언어입니다. [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 은 가용성 그룹, 가용성 복제본 및 가용성 데이터베이스를 배포, 관리 및 모니터링할 수 있도록 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 에 PowerShell cmdlet 집합을 제공합니다.  
  
> [!NOTE]  
>  PowerShell cmdlet은 작업을 시작하여 완료할 수 있습니다. 이것이 원하는 작업(예: 가용성 그룹 장애 조치)이 완료되었음을 나타내는 것은 아닙니다. 작업 시퀀스를 스크립팅하는 경우 작업 상태를 확인하고 작업이 완료되는 동안 기다려야 할 수 있습니다.  
  
 이 항목에서는 다음 태스크 집합에 대한 cmdlet에 대해 설명합니다.  
  
-   [AlwaysOn 가용성 그룹에 대한 서버 인스턴스 구성](#ConfiguringServerInstance)  
  
-   [데이터베이스 및 트랜잭션 로그 백업 및 복원](#BnRcmdlets)  
  
-   [가용성 그룹 만들기 및 관리](#DeployManageAGs)  
  
-   [가용성 그룹 수신기 만들기 및 관리](#AGlisteners)  
  
-   [가용성 복제본 만들기 및 관리](#DeployManageARs)  
  
-   [가용성 데이터베이스 추가 및 관리](#DeployManageDbs)  
  
-   [가용성 그룹 상태 모니터링](#MonitorTblshtAGs)  
  
> [!NOTE]  
>  Cmdlet을 사용 하 여 작업 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 을 수행 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 하는 방법을 설명 하는 온라인 설명서의 항목 목록은 [AlwaysOn 가용성 그룹 &#40;&#41;SQL Server 개요 ](overview-of-always-on-availability-groups-sql-server.md)의 "관련 태스크" 섹션을 참조 하세요.  
  
##  <a name="ConfiguringServerInstance"></a>AlwaysOn 가용성 그룹에 대 한 서버 인스턴스 구성  
  
|Cmdlet|Description|지원되는 위치|  
|-------------|-----------------|------------------|  
|`Disable-SqlAlwaysOn`|서버 인스턴스에서 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 기능을 사용하지 않도록 설정합니다.|
  `Path`, `InputObject` 또는 `Name` 매개 변수에 지정된 서버 인스턴스( [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 을 지원하는 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]버전이어야 함)|  
|`Enable-SqlAlwaysOn`|[!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 기능을 지원하는 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 의 인스턴스에서 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 을 사용하도록 설정합니다. 지원 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]에 대 한 자세한 내용은 [AlwaysOn 가용성 그룹 &#40;SQL Server&#41;에 대 한 필수 조건, 제한 사항 및 권장 사항 ](prereqs-restrictions-recommendations-always-on-availability.md)을 참조 하세요.|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 을 지원하는 모든 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]버전|  
|`New-SqlHadrEndPoint`|서버 인스턴스에서 새 데이터베이스 미러링 엔드포인트를 만듭니다. 이 엔드포인트는 주 데이터베이스와 보조 데이터베이스 간에 데이터를 이동하는 데 필요합니다.|다음의 모든 인스턴스 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]|  
|`Set-SqlHadrEndpoint`|기존 데이터베이스 미러링 엔드포인트의 속성(예: 이름, 상태 또는 인증 속성)을 변경합니다.|[!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]을 지원하고 데이터베이스 미러링 엔드포인트가 부족한 서버 인스턴스|  
  
##  <a name="BnRcmdlets"></a> Backing Up and Restoring Databases and Transaction Logs  
  
|Cmdlet|Description|지원되는 위치|  
|-------------|-----------------|------------------|  
|`Backup-SqlDatabase`|데이터 또는 로그 백업을 만듭니다.|온라인 데이터베이스( [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]의 경우 주 복제본을 호스팅하는 서버 인스턴스의 데이터베이스)|  
|`Restore-SqlDatabase`|백업을 복원합니다.|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 의 인스턴스( [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]의 경우 보조 복제본을 호스팅하는 서버 인스턴스)<br /><br /> **&#42;&#42; 중요 &#42;&#42;** 보조 데이터베이스를 준비 하는 경우 모든 `-NoRecovery` `Restore-SqlDatabase` 명령에서 매개 변수를 사용 해야 합니다.|  
  
 cmdlet을 사용하여 보조 데이터베이스를 준비하는 방법은 [가용성 그룹에 대한 보조 데이터베이스 수동 준비&#40;SQL Server&#41;](manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md)를 참조하세요.  
  
##  <a name="DeployManageAGs"></a> Creating and Managing an Availability Group  
  
|Cmdlet|Description|지원되는 위치|  
|-------------|-----------------|------------------|  
|`New-SqlAvailabilityGroup`|새 가용성 그룹을 만듭니다.|주 복제본을 호스팅할 서버 인스턴스|  
|`Remove-SqlAvailabilityGroup`|가용성 그룹을 삭제합니다.|HADR 사용 서버 인스턴스|  
|`Set-SqlAvailabilityGroup`|가용성 그룹의 속성을 설정하고 가용성 그룹을 온라인/오프라인으로 전환합니다.|주 복제본을 호스팅하는 서버 인스턴스|  
|`Switch-SqlAvailabilityGroup`|다음 형식의 장애 조치 중 하나를 시작합니다.<br /><br /> 가용성 그룹의 강제 장애 조치(failover)(데이터가 손실될 수 있음)<br /><br /> 가용성 그룹 수동 장애 조치(failover)|대상 보조 복제본을 호스팅하는 서버 인스턴스|  
  
##  <a name="AGlisteners"></a> Creating and Managing an Availability Group Listener  
  
|Cmdlet|Description|지원되는 위치|  
|------------|-----------------|------------------|  
|`New-SqlAvailabilityGroupListener`|새 가용성 그룹 수신기를 만들고 기존 가용성 그룹에 연결합니다.|주 복제본을 호스팅하는 서버 인스턴스|  
|`Set-SqlAvailabilityGroupListener`|기존 가용성 수신기에서 포트 설정을 수정합니다.|주 복제본을 호스팅하는 서버 인스턴스|  
|`Add-SqlAvailabilityGroupListenerStaticIp`|기존 가용성 그룹 수신기 구성에 고정 IP 주소를 추가합니다. IP 주소는 서브넷이 있는 IPv4 주소이거나 IPv6 주소일 수 있습니다.|주 복제본을 호스팅하는 서버 인스턴스|  
  
##  <a name="DeployManageARs"></a> Creating and Managing an Availability Replica  
  
|Cmdlet|Description|지원되는 위치|  
|-------------|-----------------|------------------|  
|**New-SqlAvailabilityReplica**|새 가용성 복제본을 만듭니다. 
  `-AsTemplate` 매개 변수를 사용하여 새 가용성 복제본별로 하나의 메모리 내 가용성 복제본 개체를 만들 수 있습니다.|주 복제본을 호스팅하는 서버 인스턴스|  
|`Join-SqlAvailabilityGroup`|보조 복제본을 가용성 그룹에 조인합니다.|보조 복제본을 호스팅하는 서버 인스턴스|  
|**Remove-SqlAvailabilityReplica**|가용성 복제본을 삭제합니다.|주 복제본을 호스팅하는 서버 인스턴스|  
|`Set-SqlAvailabilityReplica`|가용성 복제본의 속성을 설정합니다.|주 복제본을 호스팅하는 서버 인스턴스|  
  
##  <a name="DeployManageDbs"></a> Adding and Managing an Availability Database  
  
|Cmdlet|Description|지원되는 위치|  
|-------------|-----------------|------------------|  
|**Add-SqlAvailabilityDatabase**|주 복제본에서 데이터베이스를 가용성 그룹에 추가합니다.<br /><br /> 보조 복제본에서 보조 데이터베이스를 가용성 그룹에 조인합니다.|가용성 복제본을 호스팅하는 모든 서버 인스턴스(주 복제본과 보조 복제본의 동작이 서로 다름)|  
|**Remove-SqlAvailabilityDatabase**|주 복제본에서 데이터베이스를 가용성 그룹에서 제거합니다.<br /><br /> 보조 복제본에서 로컬 보조 데이터베이스를 로컬 보조 복제본에서 제거합니다.|가용성 복제본을 호스팅하는 모든 서버 인스턴스(주 복제본과 보조 복제본의 동작이 서로 다름)|  
|`Resume-SqlAvailabilityDatabase`|일시 중지된 가용성 데이터베이스에 대한 데이터 이동을 재개합니다.|데이터베이스가 일시 중지된 서버 인스턴스|  
|`Suspend-SqlAvailabilityDatabase`|가용성 데이터베이스에 대한 데이터 이동을 일시 중지합니다.|가용성 복제본을 호스팅하는 서버 인스턴스|  
  
##  <a name="MonitorTblshtAGs"></a> Monitoring Availability Group Health  
 다음 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] cmdlet을 사용하면 가용성 그룹과 가용성 그룹의 복제본 및 데이터베이스의 상태를 모니터링할 수 있습니다.  
  
> [!IMPORTANT]  
>  이 cmdlet을 실행하려면 연결, 서버 상태 보기 및 모든 정의 보기 권한이 있어야 합니다.  
  
|Cmdlet|Description|지원되는 위치|  
|------------|-----------------|------------------|  
|`Test-SqlAvailabilityGroup`|SQL Server PBM(정책 기반 관리) 정책을 평가하여 가용성 그룹의 상태를 평가합니다.|가용성 복제본을 호스팅하는 서버 인스턴스*|  
|`Test-SqlAvailabilityReplica`|SQL Server PBM(정책 기반 관리) 정책을 평가하여 가용성 복제본의 상태를 평가합니다.|가용성 복제본을 호스팅하는 서버 인스턴스*|  
|`Test-SqlDatabaseReplicaState`|SQL Server PBM(정책 기반 관리) 정책을 평가하여 모든 조인된 가용성 복제본에 대한 가용성 데이터베이스 상태를 평가합니다.|가용성 복제본을 호스팅하는 서버 인스턴스*|  
  
 *가용성 그룹의 모든 가용성 복제본에 대한 정보를 보려면 주 복제본을 호스팅하는 서버 인스턴스를 사용합니다.  
  
 자세한 내용은 [AlwaysOn 정책을 사용 하 여 가용성 그룹의 상태 보기 &#40;SQL Server&#41;](use-always-on-policies-to-view-the-health-of-an-availability-group-sql-server.md)를 참조 하세요.  
  
## <a name="see-also"></a>참고 항목  
 [AlwaysOn 가용성 그룹 &#40;SQL Server 개요&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md)  
  
  
