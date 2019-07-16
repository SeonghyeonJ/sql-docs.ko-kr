---
title: 서버 이벤트 용 WMI 공급자에 WQL 사용 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
helpviewer_keywords:
- queries [WMI]
- query language [WMI]
- WMI Query Language [WMI]
- WQL [WMI]
- WMI Provider for Server Events, WQL
ms.assetid: 58b67426-1e66-4445-8e2c-03182e94c4be
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 18c4b6448438ebb8c95f999569d51edfecf04206
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/15/2019
ms.locfileid: "68211582"
---
# <a name="using-wql-with-the-wmi-provider-for-server-events"></a>서버 이벤트용 WMI 공급자에 WQL 사용
  관리 응용 프로그램은 서버 이벤트용 WMI 공급자를 통해 WQL(WMI Query Language) 문을 실행하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 이벤트에 액세스합니다. WQL은 몇 가지 WMI 관련 확장 기능이 포함된 SQL(구조적 쿼리 언어)의 단순화된 일부입니다. WQL을 사용할 경우 응용 프로그램은 특정 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스, 데이터베이스 또는 데이터베이스 개체(현재 지원되는 유일한 개체는 큐임)에 대해 이벤트 유형을 검색합니다. 쿼리 또는 데이터베이스 범위 또는 개체 범위 이벤트 알림에 대 한 대상 데이터베이스에서 만든 이벤트 알림을를 변환 하는 서버 이벤트 용 WMI 공급자를 **마스터** 서버 범위 이벤트에 대 한 데이터베이스 알림입니다.  
  
 예를 들어 다음 WQL 쿼리를 살펴보십시오.  
  
```  
SELECT * FROM DDL_DATABASE_LEVEL_EVENTS WHERE DatabaseName = 'AdventureWorks'  
```  
  
 이 쿼리에서 WMI 공급자는 대상 서버에서 이벤트 알림과 동등한 항목을 생성합니다.  
  
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
  
 WQL 쿼리(`FROM`)의 `DDL_DATABASE_LEVEL_EVENTS` 절에 있는 인수는 이벤트 알림을 만들 수 있는 유효한 모든 이벤트일 수 있습니다. `SELECT` 및 `WHERE` 절의 인수는 이벤트 또는 해당 부모 이벤트와 연결된 이벤트 속성을 지정할 수 있습니다. 유효한 이벤트 및 이벤트 속성의 목록을 참조 하세요 [Event Notifications (Database Engine)](https://technet.microsoft.com/library/ms182602.aspx)합니다.  
  
 서버 이벤트용 WMI 공급자가 명시적으로 지원하는 WQL 구문은 다음과 같습니다. 추가 WQL 구문을 지정할 수도 있지만 해당 구문은 이 공급자와 관련이 없으며 대신 WMI 호스트 서비스에 의해 구문 분석됩니다. WMI 쿼리 언어에 대한 자세한 내용은 MSDN(Microsoft Developer Network)의 WQL 설명서를 참조하십시오.  
  
## <a name="syntax"></a>구문  
  
```  
  
SELECT { event_property [ ,...n ] | * }  
FROM event_type   
WHERE where_condition  
```  
  
## <a name="arguments"></a>인수  
 *event_property*  
 이벤트의 속성입니다. 이러한 예로 `PostTime`, `SPID` 및 `LoginName`이 있습니다. 에 나열 된 각 이벤트를 조회할 [Server 이벤트 클래스 및 속성에 대 한 WMI 공급자](wmi-provider-for-server-events-classes-and-properties.md) 여 포함 된 속성을 확인 하려면. 예를 들어 DDL_DATABASE_LEVEL_EVENTS 이벤트는 `DatabaseName` 및 `UserName` 속성을 포함합니다. 또한 부모 이벤트에서 `SQLInstance`, `LoginName`, `PostTime`, `SPID` 및 `ComputerName` 속성을 상속합니다.  
  
 **,** *...n*  
 함을 *event_property* 쿼리할 수 있습니다 여러 번 쉼표로 구분 합니다.  
  
 \*  
 이벤트와 관련된 모든 속성이 쿼리되도록 지정합니다.  
  
 *event_type*  
 이벤트 알림을 만들 수 있는 모든 이벤트입니다. 사용 가능한 이벤트 목록을 참조 하세요 [Server 이벤트 클래스 및 속성에 대 한 WMI 공급자](https://technet.microsoft.com/library/ms186449.aspx)합니다. 사실은 *이벤트 유형을* 이름은 동일 하 게 해당 *event_type* | *event_group* 수동으로 이벤트 알림을 만들 때 지정할 수 있습니다 CREATE EVENT NOTIFICATION을 사용 하 여 예가 *이벤트 유형을* 포함 CREATE_TABLE, LOCK_DEADLOCK, DDL_USER_EVENTS 및 trc_database가 있습니다.  
  
> [!NOTE]  
>  DDL과 같은 작업을 수행하는 특정 시스템 저장 프로시저에서 이벤트 알림이 발생할 수도 있습니다. 이벤트 알림을 테스트하여 실행된 시스템 저장 프로시저에 대한 응답을 확인합니다. 예를 들어 CREATE TYPE 문 및 **sp_addtype** 저장된 프로시저 모두 CREATE_TYPE 이벤트에서 생성 되는 이벤트 알림을 발생 합니다. 그러나 합니다 **sp_rename** 저장된 프로시저 이벤트 알림을 발생 하지 않습니다. 자세한 내용은[DDL 이벤트](../triggers/ddl-events.md)합니다.  
  
 *where_condition*  
 이루어져 WHERE 절 쿼리 조건자가 *event_property* 이름 및 논리 및 비교 연산자입니다. 합니다 *where_condition* 대상 데이터베이스의 해당 이벤트 알림이 등록 된 범위를 결정 합니다. 특정 스키마 또는 쿼리 하는 개체를 대상으로 필터로 사용할 수도 있습니다 *event_type 합니다.* 자세한 내용은 이 항목의 뒷부분에 나오는 주의 섹션을 참조하십시오.  
  
 `=` 피연산자만 `DatabaseName`, `SchemaName` 및 `ObjectName`과 함께 사용할 수 있습니다. 다른 식은 이러한 이벤트 속성과 함께 사용할 수 없습니다.  
  
## <a name="remarks"></a>설명  
 합니다 *where_condition* 서버 이벤트 용 WMI 공급자의 구문은 다음을 결정 합니다.  
  
-   지정 된 검색할 공급자가는 범위 *event_type*: 서버 수준, 데이터베이스 수준 또는 개체 수준 (현재 지원 되는 유일한 개체는 큐). 궁극적으로 이 범위는 대상 데이터베이스에 생성되는 이벤트 알림 유형을 결정합니다. 이 프로세스를 이벤트 알림 등록이라고 합니다.  
  
-   필요한 경우 등록이 수행되는 데이터베이스, 스키마 및 개체입니다.  
  
 서버 이벤트용 WMI 공급자는 아래에서 위로, 첫 번째 일치 알고리즘을 사용하여 기본 EVENT NOTIFICATION에 대한 가능한 가장 좁은 범위를 생성합니다. 이 알고리즘은 서버의 내부 활동과 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 및 WMI 호스트 프로세스 인스턴스 간의 네트워크 트래픽을 최소화합니다. 공급자를 검사 합니다 *event_type* FROM 절 및 WHERE 절에 조건을 지정 하 고 가능한 가장 좁은 범위로 기본 EVENT NOTIFICATION을 등록 하려고 합니다. 공급자는 가장 좁은 범위를 등록할 수 없는 경우 등록에 성공할 때까지 연속적으로 더 높은 범위에 등록을 시도합니다. 가장 높은 범위인 서버 수준에 도달했지만 실패하는 경우 소비자에게 오류를 반환합니다.  
  
 예를 들어 경우 DatabaseName = **'** AdventureWorks **'** WHERE 절에서 공급자의 이벤트 알림을 등록 하려고 하는 지정 된 된 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 데이터베이스입니다. [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 데이터베이스가 있고 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]에 이벤트 알림을 만드는 데 필요한 권한이 호출 클라이언트에 있으면 등록이 성공합니다. 그렇지 않으면 서버 수준에서 이벤트 알림이 등록됩니다. WMI 클라이언트에 필요한 사용 권한이 있으면 등록이 성공합니다. 하지만 이 시나리오에서는 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 데이터베이스를 만들 때까지 이벤트가 클라이언트에 반환되지 않습니다.  
  
 합니다 *where_condition* 특정 데이터베이스, 스키마 또는 개체에 대 한 쿼리를 추가로 제한 하는 필터 역할도 할 수 있습니다. 예를 들어 다음 WQL 쿼리를 살펴보십시오.  
  
```  
SELECT * FROM ALTER_TABLE   
WHERE DatabaseName = 'AdventureWorks' AND SchemaName = 'Sales'   
    AND ObjectType='Table' AND ObjectName = 'SalesOrderDetail'  
```  
  
 등록 프로세스의 결과에 따라 이 WOL 쿼리를 데이터베이스 또는 서버 수준에서 등록할 수 있습니다. 하지만 서버 수준에서 등록된 경우에도 공급자는 궁극적으로 `ALTER_TABLE` 테이블에 적용되지 않는 모든 `AdventureWorks.Sales.SalesOrderDetail` 이벤트를 필터링합니다. 즉, 공급자는 특정 테이블에서 발생하는 `ALTER_TABLE` 이벤트의 속성만 반환합니다.  
  
 `DatabaseName='AW1'` OR `DatabaseName='AW2'`와 같은 복합 식을 지정하면 두 개의 개별 이벤트 알림 대신 서버 범위에서 단일 이벤트 알림이 등록됩니다. 호출 클라이언트에 사용 권한이 있으면 등록이 성공합니다.  
  
 하는 경우 `SchemaName='X' AND ObjectType='Y' AND ObjectName='Z'` 를 모두 지정 합니다 `WHERE` 절을 시도 하는 개체에 직접 이벤트 알림이 등록 됩니다 `Z` 스키마에서 `X`합니다. 클라이언트에 사용 권한이 있으면 등록이 성공합니다. 현재 개체 수준 이벤트는 지원 큐에 대해서만 하 고 QUEUE_ACTIVATION 동안만 *event_type*합니다.  
  
 임의의 특정 범위에서 모든 이벤트를 쿼리할 수는 없습니다. 예를 들어 Lock_Deadlock과 같은 추적 이벤트나 TRC_LOCKS와 같은 추적 이벤트 그룹의 WQL 쿼리는 서버 수준에서만 등록할 수 있습니다. 이와 유사하게, CREATE_ENDPOINT 이벤트 및 DDL_ENDPOINT_EVENTS 이벤트 그룹도 서버 수준에서만 등록할 수 있습니다. 이벤트 등록에 대 한 적절 한 범위에 대 한 자세한 내용은 참조 하세요. [이벤트 알림 디자인](https://technet.microsoft.com/library/ms175854\(v=sql.105\).aspx)합니다. WQL을 등록 하려고 시도 하는 쿼리 갖는 *event_type* 만 등록할 수 있습니다 서버 수준 항상 변경 됩니다 서버 수준에서. WMI 클라이언트에 사용 권한이 있으면 등록이 성공합니다. 그렇지 않으면 오류가 클라이언트에 반환됩니다. 하지만 경우에 따라 이벤트에 해당하는 속성을 기반으로 WHERE 절을 서버 수준 이벤트의 필터로 사용할 수 있습니다. 예를 들어 많은 추적 이벤트에는 WHERE 절에 필터로 사용할 수 있는 `DatabaseName` 속성이 있습니다.  
  
 서버 범위 이벤트 알림의 만들어집니다는 **마스터** 데이터베이스를 사용 하 여 메타 데이터를 쿼리할 수는 [sys.server_event_notifications](/sql/relational-databases/system-catalog-views/sys-server-event-notifications-transact-sql) 카탈로그 뷰.  
  
 데이터베이스 범위 또는 개체 범위 이벤트 알림은 지정한 데이터베이스에서 생성 되 고 사용 하 여 메타 데이터를 쿼리할 수는 [sys.event_notifications](/sql/relational-databases/system-catalog-views/sys-event-notifications-transact-sql) 카탈로그 뷰에 있습니다. 카탈로그 뷰에 해당 데이터베이스 이름을 접두사로 추가해야 합니다.  
  
## <a name="examples"></a>예  
  
### <a name="a-querying-for-events-at-the-server-scope"></a>A. 서버 범위에서 이벤트 쿼리  
 다음 WQL 쿼리는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스에서 발생하는 `SERVER_MEMORY_CHANGE` 추적 이벤트의 모든 이벤트 속성을 검색합니다.  
  
```  
SELECT * FROM SERVER_MEMORY_CHANGE  
```  
  
### <a name="b-querying-for-events-at-the-database-scope"></a>2\. 데이터베이스 범위에서 이벤트 쿼리  
 다음 WQL 쿼리는 `AdventureWorks` 데이터베이스에서 발생하고 `DDL_DATABASE_LEVEL_EVENTS` 이벤트 그룹에 속한 이벤트의 특정 이벤트 속성을 검색합니다.  
  
```  
SELECT SPID, SQLInstance, DatabaseName FROM DDL_DATABASE_LEVEL_EVENTS   
WHERE DatabaseName = 'AdventureWorks'   
```  
  
### <a name="c-querying-for-events-at-the-database-scope-filtering-by-schema-and-object"></a>3\. 스키마 및 개체로 필터링하여 데이터베이스 범위에서 이벤트 쿼리  
 다음 쿼리는 `ALTER_TABLE` 테이블에서 발생하는 `AdventureWorks.Sales.SalesOrderDetail` 이벤트의 모든 이벤트 속성을 검색합니다.  
  
```  
SELECT * FROM ALTER_TABLE   
WHERE DatabaseName = 'AdventureWorks' AND SchemaName = 'Sales'   
    AND ObjectType='Table' AND ObjectName = 'SalesOrderDetail'  
```  
  
## <a name="see-also"></a>관련 항목  
 [용 WMI 공급자 서버 이벤트 개념](https://technet.microsoft.com/library/ms180560.aspx)   
 [이벤트 알림 (데이터베이스 엔진)](https://technet.microsoft.com/library/ms182602.aspx)  
  
  
