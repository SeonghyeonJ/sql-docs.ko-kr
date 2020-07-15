---
title: EKM provider enabled 서버 구성 옵션 | Microsoft Docs
description: "\"EKM provider enabled\" 옵션에 대해 알아봅니다. 이 옵션은 SQL Server에서 확장 가능 키 관리 디바이스 지원을 제어합니다. 이 옵션을 설정하거나 해제하는 방법을 알아봅니다."
ms.custom: ''
ms.date: 03/02/2017
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
f1_keywords:
- external encryption provider
helpviewer_keywords:
- EKM provider enabled option
ms.assetid: da58ed50-3a13-4172-9065-960559d8f383
author: markingmyname
ms.author: maghan
ms.openlocfilehash: be9e074cd3d58571a0db9646648207b26b1512b3
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85772517"
---
# <a name="ekm-provider-enabled-server-configuration-option"></a>EKM provider enabled 서버 구성 옵션
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  **EKM provider enabled** 옵션은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 확장 가능 키 관리 디바이스 지원을 제어합니다. 기본적으로 이 옵션은 해제되어 있습니다.  
  
 이 기능을 사용하거나 사용하지 않도록 설정하려면 다음 **sp_configure** 명령 중 하나를 실행하세요.  
  
```  
/* Enable the external encryption provider option */  
sp_configure 'EKM provider enabled', 1  
/* Disable the external encryption provider option */  
sp_configure 'EKM provider enabled', 0  
```  
  
> [!NOTE]
>  이 옵션은 일부 [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]버전에서 사용할 수 없습니다. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]버전에서 지원되는 기능 목록은 [SQL Server 2016 버전에서 지원하는 기능](~/sql-server/editions-and-supported-features-for-sql-server-2016.md)을 참조하세요.  
  
## <a name="see-also"></a>참고 항목  
 [확장 가능 키 관리 &#40;EKM&#41;](../../relational-databases/security/encryption/extensible-key-management-ekm.md)   
 [서버 구성 옵션&#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md)   
 [리소스 사용 모니터링&#40;시스템 모니터&#41;](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)   
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)   
 [RECONFIGURE&#40;Transact-SQL&#41;](../../t-sql/language-elements/reconfigure-transact-sql.md)  
  
  

