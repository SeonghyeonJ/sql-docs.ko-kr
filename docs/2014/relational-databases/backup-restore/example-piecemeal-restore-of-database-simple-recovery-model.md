---
title: '예제: 데이터베이스의 증분 복원(단순 복구 모델) | Microsoft 문서'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- piecemeal restores [SQL Server], simple recovery model
- restore sequences [SQL Server], piecemeal
- simple recovery model [SQL Server], RESTORE examples
ms.assetid: 9834b14a-4e56-4654-b190-c2a38624b6b4
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: c2e44148d1cd250e575b46f83b7d801d40fc47b8
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2020
ms.locfileid: "62921611"
---
# <a name="example-piecemeal-restore-of-database-simple-recovery-model"></a>예제: 데이터베이스의 증분 복원(단순 복구 모델)
  증분 복원 시퀀스는 주 파일 그룹에서 시작하여 모든 읽기/쓰기 파일 그룹, 보조 파일 그룹의 순서로 파일 그룹 수준에서 데이터베이스를 복원하고 복구합니다.  
  
 이 예에서 `adb` 데이터베이스는 재해 발생 후 새 컴퓨터에 복원됩니다. 데이터베이스는 단순 복구 모델을 사용하고 있습니다. 재해가 발생하기 전에 모든 파일 그룹은 온라인 상태입니다. 파일 그룹 `A` 및 `C` 는 읽기/쓰기가 가능하며 파일 그룹 `B` 는 읽기 전용입니다. 가장 최근의 부분 백업 이전에 파일 그룹 `B` 는 읽기 전용 파일이 되었으며 주 파일 그룹과 읽기/쓰기가 가능한 보조 파일 그룹인 `A` 와 `C`를 포함합니다. 파일 그룹 `B` 가 읽기 전용 파일이 된 후에 파일 그룹 `B` 의 별도 파일 백업이 수행되었습니다.  
  
## <a name="restore-sequences"></a>복원 시퀀스  
  
1.  주 파일 그룹과 파일 그룹 `A` 및 `C`를 부분 복원합니다.  
  
    ```  
    RESTORE DATABASE adb FILEGROUP='A',FILEGROUP='C'   
       FROM partial_backup   
       WITH PARTIAL, RECOVERY;  
  
    ```  
  
     이 시점에서 주 파일 그룹과 파일 그룹 `A` 와 `C` 가 온라인입니다. 파일 그룹 `B` 의 모든 파일은 복구 보류 상태이고 이 파일 그룹은 오프라인입니다.  
  
2.  파일 그룹 `B`를 온라인 복원합니다.  
  
    ```  
    RESTORE DATABASE adb FILEGROUP='B' FROM backup WITH RECOVERY;  
  
    ```  
  
     이제 모든 파일 그룹이 온라인입니다.  
  
## <a name="additional-examples"></a>추가 예  
  
-   [예제: 일부 파일 그룹만 증분 복원&#40;단순 복구 모델&#41;](example-piecemeal-restore-of-only-some-filegroups-simple-recovery-model.md)  
  
-   [예제: 읽기 전용 파일의 온라인 복원&#40;단순 복구 모델&#41;](example-online-restore-of-a-read-only-file-simple-recovery-model.md)  
  
-   [예제: 데이터베이스의 증분 복원&#40;전체 복구 모델&#41;](example-piecemeal-restore-of-database-full-recovery-model.md)  
  
-   [예제: 일부 파일 그룹만 증분 복원&#40;전체 복구 모델&#41;](example-piecemeal-restore-of-only-some-filegroups-full-recovery-model.md)  
  
-   [예제: 읽기-쓰기 파일의 온라인 복원&#40;전체 복구 모델&#41;](example-online-restore-of-a-read-write-file-full-recovery-model.md)  
  
-   [예제: 읽기 전용 파일 온라인 복원&#40;전체 복구 모델&#41;](example-online-restore-of-a-read-only-file-full-recovery-model.md)  
  
## <a name="see-also"></a>참고 항목  
 [온라인 복원&#40;SQL Server&#41;](online-restore-sql-server.md)   
 [BACKUP&#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql)   
 [RESTORE&#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql)   
 [증분 복원&#40;SQL Server&#41;](piecemeal-restores-sql-server.md)  
  
  
