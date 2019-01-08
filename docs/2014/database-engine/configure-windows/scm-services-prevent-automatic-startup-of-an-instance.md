---
title: SQL Server (SQL Server 구성 관리자) 인스턴스의 자동 시작 방지 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- automatic SQL Server startup
- SQL Server, stopping
- SQL Server, automatic startup
- canceling automatic startup
- stopping SQL Server
- preventing automatic startups [SQL Server]
ms.assetid: 782663cf-f3d7-4cc6-b621-21e4550f0322
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: d296f9a73138dd2a93cec5f3ae6ca62d257fd2fb
ms.sourcegitcommit: 04dd0620202287869b23cc2fde998a18d3200c66
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/30/2018
ms.locfileid: "52640064"
---
# <a name="prevent-automatic-startup-of-an-instance-of-sql-server-sql-server-configuration-manager"></a>SQL Server 인스턴스의 자동 시작 방지(SQL Server 구성 관리자)
  이 항목에서는 SQL Server 구성 관리자를 사용하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 인스턴스가 자동으로 시작되지 않도록 방지하는 방법에 대해 설명합니다. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 는 일반적으로 자동으로 시작되도록 구성됩니다. 인스턴스의 시작 모드를 수동으로 설정하면 이러한 구성을 변경할 수 있습니다.  
  
##  <a name="SSMSProcedure"></a> SQL Server 구성 관리자 사용  
  
#### <a name="to-prevent-automatic-startup-of-an-instance-of-sql-server"></a>SQL Server 인스턴스의 자동 시작을 방지하려면  
  
1.  **시작** 메뉴에서 **모든 프로그램**, [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)], **구성 도구**를 차례로 가리킨 다음 **SQL Server 구성 관리자**를 클릭합니다.  
  
2.  SQL Server 구성 관리자에서 **서비스**를 확장한 다음 **SQL Server**를 클릭합니다.  
  
3.  세부 정보 창에서 **MSSQLServer**를 마우스 오른쪽 단추로 클릭한 다음 **속성**을 클릭합니다.  
  
4.  에 **SQL Server \<***instancename***> 속성** 대화 상자를 **속성** 상자에서 값을 설정 **시작 모드**하 **수동**합니다.  
  
5.  **확인**을 클릭하여 **SQL Server \<***instancename***> 속성** 대화 상자를 닫은 다음, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]구성 관리자를 닫습니다.  
  
## <a name="see-also"></a>관련 항목:  
 [데이터베이스 엔진, SQL Server 에이전트 또는 SQL Server Browser 서비스 시작, 중지, 일시 중지, 재개 및 다시 시작](start-stop-pause-resume-restart-sql-server-services.md)  
  
  
