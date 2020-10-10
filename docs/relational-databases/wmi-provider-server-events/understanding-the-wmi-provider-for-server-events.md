---
title: 서버 이벤트용 WMI 공급자 이해
description: 서버 이벤트 용 WMI 공급자가 WMI(Windows Management Instrumentation)를 사용 하 여 관리 되는 WMI 개체로 SQL Server를 설정 하 여 이벤트를 모니터링 하는 방법을 알아봅니다.
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
helpviewer_keywords:
- architecture [WMI]
- SQL Server Agent [WMI]
- WMI Provider for Server Events, about WMI Provider for Server Events
ms.assetid: 8fd7bd18-76d0-4b28-8fee-8ad861441ab2
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 6187c97f246a8c4eb445fb0afe224922b2c57f03
ms.sourcegitcommit: 783b35f6478006d654491cb52f6edf108acf2482
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/09/2020
ms.locfileid: "91891963"
---
# <a name="understanding-the-wmi-provider-for-server-events"></a>서버 이벤트용 WMI 공급자 이해
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  서버 이벤트용 WMI 공급자는 WMI(Windows Management Instrumentation)를 사용하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]의 이벤트를 모니터링할 수 있도록 합니다. 이 공급자는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 를 관리 WMI 개체로 전환하여 작동됩니다. WMI에서는 이 공급자를 사용하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서 이벤트 알림을 생성할 수 있는 모든 이벤트를 사용할 수 있습니다. 또한 WMI와 상호 작용하는 관리 애플리케이션인 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트에서 이러한 이벤트에 응답할 수 있기 때문에 이전 버전의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트에서 처리하던 이벤트보다 다양한 이벤트를 처리할 수 있습니다.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트와 같은 관리 애플리케이션에서는 서버 이벤트용 WMI 공급자를 통해 WQL(WMI Query Language) 문을 실행하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 이벤트에 액세스할 수 있습니다. WQL은 몇 가지 WMI 관련 확장 기능이 포함된 SQL(구조적 쿼리 언어)의 단순화된 일부입니다. WQL을 사용할 경우 애플리케이션에서는 특정 데이터베이스나 데이터베이스 개체에 대해 이벤트 유형을 검색합니다. 서버 이벤트용 WMI 공급자는 쿼리를 이벤트 알림으로 변환하여 대상 데이터베이스의 이벤트 알림을 효율적으로 생성합니다. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 이벤트 알림이 작동하는 방식은 [서버 이벤트용 WMI 공급자 개념](./wmi-provider-for-server-events-concepts.md)을 참조하십시오. 쿼리할 수 이벤트는 [서버 이벤트용 WMI 공급자 클래스 및 라이브러리](../../relational-databases/wmi-provider-server-events/wmi-provider-for-server-events-classes-and-properties.md)에 나와 있습니다.  
  
 이벤트 알림으로 하여금 메시지를 보내도록 트리거하는 이벤트가 발생하면 메시지는 **SQL/Notifications/ProcessWMIEventProviderNotification/v1.0** 이라는 **msdb**에 미리 정의된 대상 서비스로 이동합니다. 대상 서비스는 **WMIEventProviderNotificationQueue** 라는 **msdb**에 미리 정의된 큐에 이 이벤트를 추가합니다. 서비스와 큐는 모두 공급자가에 처음 연결할 때 동적으로 만들어집니다 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . 그런 다음 공급자는이 큐에서 이벤트 데이터를 읽고 MOF (managed object format)로 변환한 후 응용 프로그램에 반환 합니다. 다음 그림에서 이 프로세스를 나타냅니다.  
  
 ![서버 이벤트용 WMI 공급자 흐름 다이어그램](../../relational-databases/wmi-provider-server-events/media/wmi-provider-functional-spec.gif "서버 이벤트용 WMI 공급자 흐름 다이어그램")  
  
 예를 들어 다음 WQL 쿼리를 참조하십시오.  
  
```  
SELECT * FROM DDL_DATABASE_LEVEL_EVENTS  
WHERE DatabaseName = 'AdventureWorks'  
```  
  
 이 쿼리에 대한 응답으로 서버 이벤트용 WMI 공급자는 대상 데이터베이스에 해당 이벤트 알림을 만듭니다.  
  
```  
USE AdventureWorks ;  
GO  
CREATE EVENT NOTIFICATION SQLWEP_76CF38C1_18BB_42DD_A7DC_C8820155B0E9  
    ON DATABASE  
    WITH FAN_IN  
    FOR DDL_DATABASE_LEVEL_EVENTS  
    TO SERVICE  
        'SQL/Notifications/ProcessWMIEventProviderNotification/v1.0',   
        'A7E5521A-1CA6-4741-865D-826F804E5135';  
GO  
```  
  
 이 예에서 `SQLWEP_76CF38C1_18BB_42DD_A7DC_C8820155B0E9` 는 [!INCLUDE[tsql](../../includes/tsql-md.md)] 접두사와 GUID로 구성된 `SQLWEP_` 식별자입니다. `SQLWEP`는 각 식별자의 GUID를 새로 만듭니다. `A7E5521A-1CA6-4741-865D-826F804E5135` 절의 `TO SERVICE` 값은 **msdb** 데이터베이스의 Broker 인스턴스를 식별하는 GUID입니다.  
  
 WQL로 작업하는 방법은 [서버 이벤트용 WMI 공급자에 WQL 사용](https://technet.microsoft.com/library/ms180524\(v=sql.105\).aspx)을 참조하십시오.  
  
 관리 애플리케이션에서는 공급자가 정의한 WMI 네임스페이스에 연결하여 서버 이벤트용 WMI 공급자를 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스에 전달합니다. Windows WMI 서비스는 이 네임스페이스를 공급자 DLL인 Sqlwep.dll에 매핑하여 메모리에 로드합니다. 공급자는 각 인스턴스에 대 한 서버 이벤트에 대 한 WMI 네임 스페이스를 관리 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 하며 형식은 \\ \\ \\ 입니다. *root*\Microsoft\SqlServer\ServerEvents \\ *instance_name*입니다. 여기서 *instance_name* 은 MSSQLSERVER입니다. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]인스턴스의 WMI 네임스페이스에 연결하는 방법은 [서버 이벤트용 WMI 공급자에 WQL 사용](https://technet.microsoft.com/library/ms180524\(v=sql.105\).aspx)을 참조하십시오.  
  
 공급자 DLL인 Sqlwep.dll은 서버에 있는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스의 수에 관계없이 서버 운영 체제의 WMI 호스트 서비스에 한 번만 로드됩니다.  
  
 서버 이벤트용 WMI 공급자를 사용하는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 관리 애플리케이션에 대한 예는 [예제: 서버 이벤트용 WMI 공급자를 사용하여 SQL Server 에이전트 경고 만들기](./sample-creating-a-sql-server-agent-alert-with-the-wmi-provider.md)를 참조하십시오. 관리 코드에서 서버 이벤트용 WMI 공급자를 사용하는 관리 애플리케이션에 대한 예는 [예제: 관리 코드에서 WMI 이벤트 공급자 사용](./sample-using-the-wmi-event-provider-with-the-net-framework.md)을 참조하십시오. SDK에 대 한 자세한 내용은 SDK에도 제공 됩니다 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] .  
  
## <a name="see-also"></a>참고 항목  
 [서버 이벤트용 WMI 공급자 개념](./wmi-provider-for-server-events-concepts.md)  
  
