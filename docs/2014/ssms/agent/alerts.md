---
title: 경고 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent alerts, event types
- SQL Server Agent alerts, names
- alerts [SQL Server], performance conditions
- alerts [SQL Server], about alerts
- WMI event responses [SQL Server Agent alerts]
- events [WMI]
- performance condition alerts [SQL Server Agent]
- alerts [SQL Server], event types
- SQL Server Agent alerts, performance conditions
- SQL Server Agent alerts, about alerts
- alerts [SQL Server], names
ms.assetid: 3f57d0f0-4781-46ec-82cd-b751dc5affef
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: b385e6b02807ed79e2becb127a16e76d04329764
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2020
ms.locfileid: "62473134"
---
# <a name="alerts"></a>경고
  이벤트는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서 생성되어 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 애플리케이션 로그에 입력됩니다. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에이전트는 응용 프로그램 로그를 읽고 사용자가 정의한 경고에 기록 된 이벤트를 비교 합니다. 
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트가 일치하는 내용을 찾으면 이벤트에 대해 자동화된 응답으로 경고가 발생합니다. 
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 이벤트를 모니터링할 뿐 아니라 성능 조건 및 WMI(Windows Management Instrumentation) 이벤트도 모니터링할 수 있습니다.  
  
 경고를 정의하려면 다음을 지정하십시오.  
  
-   경고의 이름입니다.  
  
-   경고를 트리거하는 이벤트 또는 성능 조건  
  
-   
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트에서 이벤트 또는 성능 조건에 대한 응답으로 수행하는 동작  
  
## <a name="naming-an-alert"></a>경고 명명  
 경고는 각각 이름이 있어야 합니다. 경고 이름은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스 내에서 고유해야 하며 **128** 자를 초과할 수 없습니다.  
  
## <a name="selecting-an-event-type"></a>이벤트 유형 선택  
 경고는 특정 유형의 이벤트에 응답합니다. 다음은 경고가 발생되는 이벤트 유형입니다.  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]이벤트  
  
-   
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 성능 조건  
  
-   WMI 이벤트  
  
 이벤트 유형에 따라 정확한 이벤트를 지정하는 데 사용되는 매개 변수가 결정됩니다.  
  
## <a name="specifying-a-sql-server-event"></a>SQL Server 이벤트 지정  
 하나 이상의 이벤트에 응답하여 경고가 발생하도록 지정할 수 있습니다. 다음 매개 변수를 사용하여 경고를 트리거하는 이벤트를 지정할 수 있습니다.  
  
-   **오류 번호**  
  
     
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 특정 오류가 발생하면 에이전트에서 경고를 표시합니다. 예를 들어 무단으로 DBCC(Database Console Commands)를 호출하려는 시도에 응답하도록 오류 번호 2571을 지정해야 합니다.  
  
-   **심각도 수준**  
  
     
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 특정 심각도에 이르는 오류가 발생하면 에이전트에서 경고를 표시합니다. 예를 들어 Transact-SQL 문의 구문 오류에 응답하도록 심각도 15를 지정할 수 있습니다.  
  
-   **Database**  
  
     
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트는 특정 데이터베이스에 이벤트가 발생할 때만 경고를 발생시킵니다. 이 옵션은 오류 번호 또는 심각도와 함께 적용됩니다. 예를 들어 프로덕션에 사용되는 데이터베이스와 보고에 사용되는 데이터베이스가 하나씩 인스턴스에 있는 경우 프로덕션 데이터베이스의 구문 오류에만 응답하도록 경고를 정의할 수 있습니다.  
  
-   **이벤트 텍스트**  
  
     
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트는 지정된 이벤트가 이벤트 메시지에 특정 텍스트 문자열을 포함할 때 경고를 발생시킵니다. 예를 들어 특정 테이블 또는 특정 제약 조건의 이름이 있는 메시지에 응답하도록 경고를 정의할 수 있습니다.  
  
## <a name="selecting-a-performance-condition"></a>성능 조건 선택  
 특정 성능 조건에 응답하여 경고가 발생하도록 지정할 수 있습니다. 이 경우 모니터링할 성능 카운터, 경고에 대한 임계값 및 경고가 발생할 경우 표시해야 하는 카운터 동작을 지정합니다. 성능 조건을 설정하려면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 새 경고 **의** 에이전트 **일반** 페이지 또는 **경고 속성** 대화 상자에서 다음 항목을 정의해야 합니다.  
  
-   **Object**  
  
     개체는 모니터링할 성능의 영역입니다.  
  
-   **카운터**  
  
     카운터는 모니터링할 영역의 특성입니다.  
  
-   **인스턴스**  
  
     
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스는 모니터링할 특성의 특정 인스턴스(있는 경우)를 정의합니다.  
  
-   **경고 발생 카운터** 및 **값**  
  
     경고의 임계값과 경고를 생성하는 동작입니다. 임계값은 숫자입니다. 동작은 값에 지정된 숫자 **미만**, **동일**또는 **초과**중 하나입니다. 
  **값** 은 성능 조건 카운터를 나타내는 숫자입니다. 예를 들어 **Lock Wait Time** 이 30분을 초과할 때 성능 개체 **SQLServer:Locks** 에 대해 경고가 발생하도록 설정하려면 **초과** 를 선택하고 **값으로30을 지정**합니다.  
  
     다른 예로 **tempdb** 의 사용 가능한 공간이 1000KB 미만일 때 성능 개체 **SQLServer:Transactions** 에 대해 경고가 발생하도록 지정할 수도 있습니다. 이렇게 설정하려면 **Free space in tempdb (KB)** 카운터, **미만**및 **값****1000**을 선택합니다.  
  
    > [!NOTE]  
    >  성능 데이터를 주기적으로 샘플링하므로 도달할 임계값과 성능 경고의 발생 간에 몇 초 정도 지연될 수 있습니다.  
  
## <a name="selecting-a-wmi-event"></a>WMI 이벤트 선택  
 특정 WMI 이벤트에 응답하여 경고가 발생하도록 지정할 수 있습니다. WMI 이벤트를 선택하려면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 새 경고 **의** 에이전트 **일반** 페이지 또는 **경고 속성** 대화 상자에서 다음을 정의해야 합니다.  
  
-   **네임스페이스**  
  
     
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트는 이벤트에 대해 쿼리하도록 제공되는 WMI 네임스페이스에 WMI 클라이언트로 등록됩니다.  
  
-   **쿼리**  
  
     
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트는 제공된 WQL(Windows Management Instrumentation Query Language) 문을 사용하여 특정 이벤트를 식별할 수 있습니다.  
  
 다음은 공통 태스크에 대한 링크입니다.  
  
 **메시지 번호를 기반으로 경고를 만들려면**  
  
-   [SQL Server Management Studio](create-an-alert-using-an-error-number.md)  
  
-   [Transact-SQL](/sql/relational-databases/system-stored-procedures/sp-add-alert-transact-sql)  
  
 **심각도 수준을 기반으로 경고를 만들려면**  
  
-   [SQL Server Management Studio](create-an-alert-using-severity-level.md)  
  
-   [Transact-SQL](/sql/relational-databases/system-stored-procedures/sp-add-alert-transact-sql)  
  
 **WMI 이벤트를 기반으로 경고를 만들려면**  
  
-   [SQL Server Management Studio](create-a-wmi-event-alert.md)  
  
-   [Transact-SQL](/sql/relational-databases/system-stored-procedures/sp-add-alert-transact-sql)  
  
 **경고에 대 한 응답을 정의 하려면**  
  
-   [SQL Server Management Studio](../sql-server-management-studio-ssms.md)  
  
-   [Transact-SQL](/sql/relational-databases/system-stored-procedures/sp-add-notification-transact-sql)  
  
 **사용자 정의 이벤트 오류 메시지를 만들려면**  
  
-   [Transact-SQL](/sql/relational-databases/system-stored-procedures/sp-addmessage-transact-sql)  
  
 **사용자 정의 이벤트 오류 메시지를 수정 하려면**  
  
-   [Transact-SQL](/sql/relational-databases/system-stored-procedures/sp-altermessage-transact-sql)  
  
 **사용자 정의 이벤트 오류 메시지를 삭제 하려면**  
  
-   [Transact-SQL](/sql/relational-databases/system-stored-procedures/sp-dropmessage-transact-sql)  
  
 **경고를 비활성화 하거나 다시 활성화 하려면**  
  
-   [SQL Server Management Studio](disable-or-reactivate-an-alert.md)  
  
-   [Transact-SQL](/sql/relational-databases/system-stored-procedures/sp-update-alert-transact-sql)  
  
## <a name="see-also"></a>참고 항목  
 [SQL Server 개체 사용](../../relational-databases/performance-monitor/use-sql-server-objects.md)  
  
  
