---
title: Trustworthy 속성을 사용하도록 미러 데이터베이스 설정(Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- TRUSTWORTHY database option
- mirror database [SQL Server]
- database mirroring [SQL Server], security
ms.assetid: 6993b076-78ef-453e-b0ea-e341b8e5ee3e
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 29cafc7e9669ca322571ff171961dd64cab114cf
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62754334"
---
# <a name="set-up-a-mirror-database-to-use-the-trustworthy-property-transact-sql"></a>Trustworthy 속성을 사용하도록 미러 데이터베이스 설정(Transact-SQL)
  데이터베이스를 백업하면 TRUSTWORTHY 데이터베이스 속성이 OFF로 설정됩니다. 따라서 새 미러 데이터베이스의 TRUSTWORTHY는 항상 OFF입니다. 장애 조치(Failover) 후 데이터베이스를 신뢰할 수 있어야 하는 경우에는 미러링이 시작된 다음 추가 설정 단계가 필요합니다.  
  
> [!NOTE]  
>  이 데이터베이스 속성에 대한 자세한 내용은 [TRUSTWORTHY 데이터베이스 속성](../../relational-databases/security/trustworthy-database-property.md)을 참조하세요.  
  
## <a name="procedure"></a>절차  
  
#### <a name="to-setup-a-mirror-database-to-use-the-trustworthy-property"></a>Trustworthy 속성을 사용하도록 미러 데이터베이스를 설정하려면  
  
1.  주 서버 인스턴스에서 주 데이터베이스의 Trustworthy 속성이 설정되었는지 확인합니다.  
  
    ```  
    SELECT name, database_id, is_trustworthy_on FROM sys.databases   
    ```  
  
     자세한 내용은 [sys.databases&#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql)를 참조하세요.  
  
2.  미러링을 시작한 후 데이터베이스가 현재 주 데이터베이스이고 세션에서 동기 운영 모드를 사용 중이며 세션이 이미 동기화되었는지 확인합니다.  
  
    ```  
    SELECT database_id, mirroring_role, mirroring_safety_level_desc, mirroring_state_desc FROM sys.database_mirroring  
    ```  
  
     자세한 내용은 [sys.database_mirroring&#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-mirroring-transact-sql)을 참조하세요.  
  
3.  미러링 세션이 동기화되면 수동으로 미러 데이터베이스에 대한 장애 조치를 수행합니다.  
  
     SQL Server Management Studio 또는 Transact-SQL을 사용하여 이 작업을 수행할 수 있습니다.  
  
    -   [데이터베이스 미러링 세션 수동 장애 조치(failover)&#40;SQL Server Management Studio&#41;](manually-fail-over-a-database-mirroring-session-sql-server-management-studio.md)  
  
    -   [데이터베이스 미러링 세션 수동 장애 조치(failover)&#40;Transact-SQL&#41;](manually-fail-over-a-database-mirroring-session-transact-sql.md)  
  
4.  다음 ALTER DATABASE 명령을 사용하여 Trustworthy 데이터베이스 속성을 설정합니다.  
  
    ```  
    ALTER DATABASE <database_name> SET TRUSTWORTHY ON  
    ```  
  
     자세한 내용은 [ALTER DATABASE&#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql)를 참조하세요.  
  
5.  필요에 따라 수동으로 다시 장애 조치를 수행하여 원래 주 서버로 되돌립니다.  
  
6.  필요에 따라 SAFETY를 OFF로 설정하고 WITNESS도 OFF로 설정되었는지 확인하여 비동기 성능 우선 모드로 전환합니다.  
  
     Transact-SQL을 사용하는 경우  
  
    -   [데이터베이스 미러링 세션에서 트랜잭션 보안 변경&#40;Transact-SQL&#41;](change-transaction-safety-in-a-database-mirroring-session-transact-sql.md)  
  
    -   [데이터베이스 미러링 세션에서 미러링 모니터 서버 제거&#40;SQL Server&#41;](remove-the-witness-from-a-database-mirroring-session-sql-server.md)  
  
     SQL Server Management Studio를 사용하는 경우  
  
    -   [Windows 인증을 사용하여 데이터베이스 미러링 세션 구성&#40;SQL Server Management Studio&#41;](establish-database-mirroring-session-windows-authentication.md)  
  
## <a name="see-also"></a>관련 항목  
 [TRUSTWORTHY 데이터베이스 속성](../../relational-databases/security/trustworthy-database-property.md)   
 [암호화된 미러 데이터베이스 설정](set-up-an-encrypted-mirror-database.md)  
  
  
