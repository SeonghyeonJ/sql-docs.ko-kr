---
title: 백업 및 복원-병렬 데이터 웨어하우스 | Microsoft Docs
description: 데이터 백업 및 복원에 대 한 병렬 데이터 웨어하우스 (PDW)을 작동 하는 방법을 설명 합니다. 백업 및 복원 작업은 재해 복구에 사용 됩니다. 백업 및 복원 하나의 어플라이언스에서 다른 어플라이언스로 데이터베이스를 복사를 사용할 수 있습니다.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 01/19/2019
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 0b95d18eb38bbe0012235304747ca80b3dc19a79
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63200964"
---
# <a name="backup-and-restore"></a>Backup 및 Restore 메서드

데이터 백업 및 복원에 대 한 병렬 데이터 웨어하우스 (PDW)을 작동 하는 방법을 설명 합니다. 백업 및 복원 작업은 재해 복구에 사용 됩니다. 백업 및 복원 하나의 어플라이언스에서 다른 어플라이언스로 데이터베이스를 복사를 사용할 수 있습니다.  
    
## <a name="BackupRestoreBasics"></a>백업 및 복원 기본 사항

PDW *데이터베이스 백업* 어플라이언스에 원래 데이터베이스를 복원할 수 있도록 형식으로 저장 하는 어플라이언스 데이터베이스의 복사본입니다.  
  
PDW 데이터베이스 백업을 사용 하 여 만들어집니다 합니다 [데이터베이스 백업](../t-sql/statements/backup-database-parallel-data-warehouse.md) t-sql 문 및 사용에 대 한 서식이 지정 된는 [RESTORE DATABASE](../t-sql/statements/restore-database-parallel-data-warehouse.md) 문과 사용할 수 없는 다른 목적을 위해. 만 백업이 동일한 수 또는 더 많은 계산 노드를 사용 하 여 어플라이언스에 복원할 수 있습니다.  
  
<!-- MISSING LINKS
The [master database](master-database.md) is a SMP SQL Server database. It is backed up with the BACKUP DATABASE statement. To restore master, use the [Restore the Master Database](configuration-manager-restore-master-database.md) page of the Configuration Manager tool.  
-->
  
PDW는 어플라이언스 데이터베이스 백업 및 복원 하려면 SQL Server 백업 기술을 사용 합니다. SQL Server 백업 옵션은 백업 압축을 사용 하도록 미리 구성 됩니다. 압축, 체크섬, 블록 크기 및 버퍼 개수 등의 백업 옵션을 설정할 수 없습니다.  
  
데이터베이스 백업은 하나 이상의 백업 서버에서 고유한 고객 네트워크에 있는 저장 됩니다.  PDW는 사용자 데이터베이스 백업을 동시에 계산 노드에서 직접 백업 서버 하나에 쓰고 계산 노드에 병렬로 사용자 데이터베이스 백업을 백업 서버에서 직접 복원 합니다.  
  
백업은은 Windows 파일 시스템에서 백업 서버에서 파일의 집합으로 저장 됩니다. PDW 데이터베이스 백업은 PDW에만 복원할 수 있습니다. 그러나 표준 Windows 파일 백업 프로세스를 사용 하 여 데이터베이스 백업을 백업 서버에서 다른 위치에 보관할 수 있습니다. Backup server에 대 한 자세한 내용은 참조 하세요. [Acquire 백업 서버를 구성 하 고](acquire-and-configure-backup-server.md)입니다.  
  
## <a name="BackupTypes"></a>데이터베이스 백업 유형

백업이 필요한 데이터의 두 종류가 있습니다: 사용자 데이터베이스 및 시스템 데이터베이스 (예: master 데이터베이스). PDW는 트랜잭션 로그를 백업 하지 않습니다.  
  
전체 데이터베이스 백업에 전체 PDW 데이터베이스의 백업이입니다. 기본 백업 형식입니다. 사용자 데이터베이스의 전체 백업을 데이터베이스 사용자 및 데이터베이스 역할에 포함 되어 있습니다. 백업 마스터의 로그인을 포함합니다.  
  
차등 백업은 마지막 전체 백업 이후 모든 변경 내용을 포함합니다. 차등 백업은 일반적으로 전체 백업보다 시간이 적게 들며 더 자주 수행할 수 있습니다. 여러 차등 백업이 동일한 전체 백업의 기반으로 하는 경우 각 차등 이전 차등에 모든 변경 내용을 포함 합니다.  
  
예를 들어 매주 전체 백업 및 차등 백업은 매일 만들 수 있습니다. 사용자 데이터베이스, 전체 백업 및 마지막으로 복원 하려면 차등 (있는 경우)를 복원 해야 합니다.  
  
사용자 데이터베이스에 대 한 차등 백업 에서만 지원 됩니다. 마스터의 backup은 항상 전체 백업입니다.  
  
전체 기기를 백업 하기 위해 모든 사용자 데이터베이스의 백업 및 master 데이터베이스의 백업을 수행 해야 합니다.  
  
## <a name="BackupProc"></a>데이터베이스 백업 프로세스

다음 다이어그램에는 데이터베이스를 백업 하는 동안 데이터 흐름을 보여 줍니다.  
  
![PDW 백업 프로세스](media/backup-process.png "PDW 백업 프로세스")  
  
백업 프로세스는 다음과 같이 작동합니다.  
  
1.  사용자는 BACKUP DATABASE tsql 문을 제어 노드에 제출합니다.  
  
    -   백업 전체 또는 차등 백업 중 하나입니다.  
  
2.  사용자 데이터베이스에 대 한 제어 노드 (MPP 엔진) 병렬 데이터베이스 백업을 수행 하는 분산된 쿼리 계획을 만듭니다.  
  
3.  각 노드에 해당 백업 파일을 SQL Server 백업 기능을 사용 하 여 백업 서버 백업 복사본에 관여 합니다.  
  
    -   각 노드에 관련 백업 서버로 한 백업 파일 복사 합니다.  
  
    -   사용자 데이터베이스 백업 (전체 또는 차등)는 각 계산 노드 및 데이터베이스 사용자 및 데이터베이스 역할의 백업에 저장 된 데이터베이스의 부분 백업에 포함 됩니다.  
  
4.  어플라이언스의 InfiniBand 네트워크를 사용 하 여 병렬 백업을 수행 합니다.  
  
    -   PDW 병렬로 각 전체 및 차등 백업을 수행합니다. 그러나 여러 데이터베이스 백업이 동시에 실행 되지 않습니다. 각 백업 요청은 완료 이전에 제출 된 백업에 대 한 대기 해야 합니다.  
  
    -   Master 데이터베이스의 백업을만 제어 노드에서 데이터를 백업 합니다. 이 백업 유형은 순차적으로 수행 됩니다.  
  
5.  PDW 데이터베이스 백업이 어플라이언스 외부에 상주 하는 디렉터리에 저장 된 파일 그룹입니다. 네트워크 경로 및 디렉터리 이름으로 디렉터리 이름이 지정 됩니다. 디렉터리는 로컬 경로 수 없으며 어플라이언스에서 일 수 없습니다.  
  
6.  백업이 완료 되 면 원하는 경우 다른 위치에 백업 디렉터리를 복사 하는 Windows 파일 시스템을 사용할 수 있습니다.  
  
    -   백업에 계산 노드의 같거나 더 큰 수는 PDW 어플라이언스로만 복원할 수 있습니다.  
  
    -   복원을 수행 하기 전에 백업의 이름을 변경할 수 없습니다. 백업 디렉터리의 이름에는 원래 백업의 이름을 일치 해야 합니다. 백업의 원래 이름은 백업 디렉터리 내에 있는 backup.xml 파일에 있습니다. 다른 이름으로 데이터베이스를 복원 하려면 복원 명령에서 새 이름을 지정할 수 있습니다. 예를 들어 `RESTORE DATABASE MyDB1 FROM DISK = ꞌ\\10.192.10.10\backups\MyDB2ꞌ`을 참조하십시오.  
  
## <a name="RestoreModes"></a>데이터베이스 복원 모드

전체 데이터베이스 복원이 데이터베이스 백업에서 데이터를 사용 하 여 PDW 데이터베이스를 다시 만듭니다. 먼저 전체 백업을 복원 및 필요에 따라 하나의 차등 백업을 복원 하 여 데이터베이스 복원 수행 됩니다. 데이터베이스 복원에는 데이터베이스 사용자 및 데이터베이스 역할을 포함합니다.  
  
헤더만 복원 데이터베이스에 대 한 헤더 정보를 반환합니다. 어플라이언스로 데이터를 복원 하지 않습니다.  
  
어플라이언스 복원은 전체 어플라이언스에 복원 합니다. 여기에 모든 사용자 데이터베이스 및 master 데이터베이스를 복원 합니다.  
  
## <a name="RestoreProc"></a>복원 프로세스

다음 다이어그램에는 데이터베이스를 복원 하는 동안 데이터 흐름을 보여 줍니다.  
  
![복원 프로세스](media/restore-process.png "복원 프로세스")  
  
## <a name="restoring-to-an-appliance-with-the-same-number-of-compute-nodes"></a>동일한 수의 계산 노드 * *를 사용 하 여 어플라이언스에 복원  
  
데이터를 복원할 때 어플라이언스는 원본 어플라이언스 및 대상 어플라이언스에 계산 노드의 수를 검색 합니다. 계산 노드의 두 어플라이언스를 사용 하는 같은 수 복원 프로세스는 다음과 같이 작동 합니다.  
  
1.  데이터베이스 백업을 복원 해야 하는 비 어플라이언스 백업 서버에서 Windows 파일 공유에 있습니다. 최상의 성능을 위해이 서버는 어플라이언스의 InfiniBand 네트워크에 연결 됩니다.  
  
2.  사용자가 제출를 [RESTORE DATABASE](../t-sql/statements/restore-database-parallel-data-warehouse.md) tsql 문을 제어 노드에 있습니다.  
  
    -   복원은 전체 복원 또는 헤더 복원 합니다. 전체 백업을 복원 하 고 차등 백업을 필요에 따라 복원 하는 전체 복원 합니다.  
  
3.  제어 노드 (MPP 엔진) 병렬 데이터베이스 복원을 수행 하는 분산된 쿼리 계획을 만듭니다.  
  
    -   SQL ServerPDW 병렬로 사용자 데이터베이스의 복원을 수행합니다. 그러나 여러 데이터베이스 백업 및 복원 실행 되지 않습니다 동시에. MPP 엔진은 각 복원 문에; 큐에 배치 이전에 제출 된 백업에 대 한 대기 하 고 복원 요청을 완료 해야 합니다.  
  
    -   Master 데이터베이스의 복원을 제어 노드에; 데이터 복원 복원은 순차적으로 수행 됩니다.  
  
    -   헤더 정보를 복원 빠른 작업 및 계산 또는 제어 노드에 모든 데이터를 복원 하지 않습니다. 대신 제어 노드는 쿼리 출력으로 결과 반환합니다.  
  
4.  백업 파일은 어플라이언스 InfiniBand 네트워크를 통해 일반적으로 올바른 계산 노드에 병렬로 복사 가져옵니다.  
  
5.  각 계산 노드에 사용자 데이터베이스의 해당 부분을 복원합니다. 모든 복원이 성공적으로 완료 되지 않으면, 경우 모든 데이터베이스를 제거 하 고 복원 성공적으로 완료 합니다.  
  
## <a name="restoring-to-an-appliance-with-a-larger-number-of-compute-nodes"></a>컴퓨팅 노드 수가 더 많은 어플라이언스에 복원  
  
컴퓨팅 노드 수가 많은 어플라이언스로 백업을 복원하면 컴퓨팅 노드 수에 비례하여 할당된 데이터베이스 크기가 커집니다.  
  
예를 들어 60gb의 데이터베이스를 2 개 노드 어플라이언스 (노드당 30GB)에서 6 개 노드 어플라이언스를 복원할 때 SQL Server PDW 6 개 노드 어플라이언스에서 180 GB 데이터베이스 (6. 노드 노드당 30GB를 사용 하 여 됨)를 만듭니다. SQL Server PDW는 처음에 원본 구성과 일치 하도록 2 개 노드로 데이터베이스를 복원 하 고 6 개 노드 모두에 데이터를 다시 배포 합니다.  
  
재배포 후 각 계산 노드에 적은 실제 데이터와 더 작은 원본 어플라이언스에서 각 계산 노드에 비해 더 많은 여유 공간을 포함 됩니다. 데이터베이스에 더 많은 데이터를 추가하려면 추가 공간을 사용합니다. 복원 된 데이터베이스 크기가 필요한 것 보다 큰 경우 사용할 수 있습니다 [ALTER DATABASE](../t-sql/statements/alter-database-transact-sql.md?tabs=sqlpdw) 데이터베이스 파일 크기를 축소 합니다.  
  
## <a name="related-tasks"></a>관련 작업  
  
|백업 및 복원 태스크|Description|  
|---------------------------|---------------|  
|백업 서버로 서버를 준비 합니다.|[백업 서버 획득 및 구성](acquire-and-configure-backup-server.md)|  
|데이터베이스를 백업 합니다.|[데이터베이스 백업](../t-sql/statements/backup-database-parallel-data-warehouse.md)|  
|데이터베이스를 복원 합니다.|[데이터베이스 복원](../t-sql/statements/restore-database-parallel-data-warehouse.md)|    

<!-- MISSING LINKS

|Create a disaster recovery plan.|[Create a Disaster Recovery Plan](create-disaster-recovery-plan.md)|
|Restore the master database.|To restore the master database, use the [Restore the master database](configuration-manager-restore-master-database.md) page in the Configuration Manager tool.| 
|Copy a database from one appliance to another appliance.|[Copy a PDW database to another appliance](copy-pdw-database-to-another-appliance.md).|  
|Monitor backups and restores.|[Monitor backups and restores](monitor-backup-and-restore.md)|  

-->
