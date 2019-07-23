---
title: 데이터베이스 미러링 모니터 시작(SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- monitoring database mirroring [SQL Server]
- Database Mirroring Monitor [SQL Server], starting
- database mirroring [SQL Server], monitoring
ms.assetid: 53165335-97ca-4f88-8e78-22f1839dee98
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 91430aacbfa65eb244592b342ccbf8503120d24b
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68048027"
---
# <a name="start-database-mirroring-monitor-sql-server-management-studio"></a>데이터베이스 미러링 모니터 시작(SQL Server Management Studio)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  데이터베이스 미러링 모니터는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서 시작한 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]모니터의 일부입니다.  
  
> [!NOTE]
>  일부 [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]버전에서는 데이터베이스 미러링 모니터를 사용할 수 없습니다. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]버전에서 지원되는 기능 목록은 [SQL Server 2016 버전에서 지원하는 기능](~/sql-server/editions-and-supported-features-for-sql-server-2016.md)을 참조하세요.  
  
### <a name="to-launch-the-database-mirroring-monitor"></a>데이터베이스 미러링 모니터를 시작하려면  
  
1.  주 서버 인스턴스에 연결한 다음 개체 탐색기에서 서버 이름을 클릭하여 서버 트리를 확장합니다.  
  
2.  **데이터베이스**를 확장하고 모니터링할 데이터베이스를 선택합니다.  
  
3.  데이터베이스를 마우스 오른쪽 단추로 클릭하고 **태스크**를 선택한 다음 **데이터베이스 미러링 모니터 시작**을 클릭합니다.  
  
4.  **데이터베이스 미러링 모니터** 대화 상자에서 **미러된 데이터베이스 등록** 을 클릭하여 미러된 데이터베이스를 하나 이상 등록합니다.  
  
    > [!NOTE]  
    >  한 파트너에서 데이터베이스를 등록하면 다른 파트너에서 해당 데이터베이스가 자동으로 등록됩니다. 모니터에 이미 다른 파트너 인스턴스에 대한 연결 자격 증명이 있으면 연결 시 해당 자격 증명이 사용됩니다. 그렇지 않으면 모니터는 Windows 인증을 사용하여 연결을 시도합니다. 서버 인스턴스 중 하나에 연결하는 데 사용되는 자격 증명을 변경하려는 경우 **[확인]을 클릭할 때 [서버 연결 관리] 대화 상자 표시**를 클릭합니다.  
  
 데이터베이스 미러링 모니터에 대한 자세한 내용은 [데이터베이스 미러링 모니터 개요](../../database-engine/database-mirroring/database-mirroring-monitor-overview.md)를 참조하세요.  
  
## <a name="see-also"></a>참고 항목  
 [데이터베이스 미러링&#40;SQL Server&#41;](../../database-engine/database-mirroring/database-mirroring-sql-server.md)   
 [Windows 인증을 사용하여 데이터베이스 미러링 세션 구성&#40;SQL Server Management Studio&#41;](../../database-engine/database-mirroring/establish-database-mirroring-session-windows-authentication.md)  
  
  
