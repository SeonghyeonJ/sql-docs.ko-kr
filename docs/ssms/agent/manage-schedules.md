---
title: 일정 관리 | Microsoft 문서
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql13.ag.job.manageschedules.f1
ms.assetid: f56c0736-dccc-41d2-afcf-71344aff143a
author: markingmyname
ms.author: maghan
manager: craigg
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 56e8fcb2048b4d741708beff3fae2267981be475
ms.sourcegitcommit: bb5484b08f2aed3319a7c9f6b32d26cff5591dae
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/06/2019
ms.locfileid: "65105398"
---
# <a name="manage-schedules"></a>일정 관리
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> 현재 [Azure SQL Database Managed Instance](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance)에서 일부 SQL Server 에이전트 기능이 지원됩니다. 자세한 내용은 [SQL Server에서 Azure SQL Database Managed Instance T-SQL 차이점](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent)을 참조하세요.

[!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 작업 일정의 속성을 확인하고 변경할 수 있습니다.  
  
## <a name="options"></a>옵션  
**사용 가능한 일정**  
이 사용자가 사용할 수 있는 일정을 나열합니다. 작업 및 일정은 소유자가 동일해야 합니다. 따라서 이 목록에는 작업의 소유자가 소유한 일정만 표시됩니다.  
  
**이름**  
일정 이름을 표시합니다.  
  
**Enabled**  
일정을 사용하려면 이 옵션을 선택합니다.  
  
**설명**  
일정에서 작업을 실행하는 조건을 설명합니다.  
  
**이 일정 내의 작업**  
일정에 연결된 작업 번호를 나열합니다. 작업의 속성을 보려면 번호를 클릭합니다.  
  
**새로 만들기**  
새 일정을 만들려면 이 단추를 클릭합니다.  
  
**Delete**  
선택한 일정을 삭제하려면 이 단추를 클릭합니다.  
  
**속성**  
선택한 일정의 속성을 변경하려면 이 단추를 클릭합니다.  
  
## <a name="see-also"></a>참고 항목  
[일정을 만들고 작업에 연결](../../ssms/agent/create-and-attach-schedules-to-jobs.md)  
  
