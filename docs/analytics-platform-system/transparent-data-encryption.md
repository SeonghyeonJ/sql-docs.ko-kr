---
title: 투명 한 데이터 암호화-병렬 데이터 웨어하우스 | Microsoft Docs
description: 투명 한 데이터 암호화 (TDE) 병렬 데이터 웨어하우스 (PDW)에 대 한 실시간 I/O 암호화 및 수행 특수 PDW 로그 파일 데이터 및 트랜잭션 로그 파일의 암호 해독 합니다. "
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: ea15a8fc5eaf066b5a64cf73192f64dd0078434e
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/28/2018
ms.locfileid: "52534087"
---
# <a name="transparent-data-encryption"></a>Transparent Data Encryption
보안 시스템 디자인, 중요한 자산 암호화 및 데이터베이스 서버에 대한 방화벽 구축과 같은 데이터베이스의 보안을 설정하기 위해 여러 가지 예방 조치를 취할 수 있습니다. 그러나 물리적 미디어 (예: 드라이브 또는 백업 테이프)가 도난 된 경우 악의적인 사용자만 복원 또는 데이터베이스를 연결 하 고 수 데이터를 찾아볼 합니다. 한 가지 해결 방법은 데이터베이스의 중요한 데이터를 암호화하고 인증서와 함께 데이터를 암호화하는 데 사용된 키를 보호하는 것입니다. 이 경우 키가 없으면 누구도 데이터를 사용할 수 없지만 이러한 보호 방법은 사전에 계획해야 합니다.  
  
*투명 한 데이터 암호화* (TDE)는 데이터의 실시간 I/O 암호화 및 해독을 수행 하 고 트랜잭션 로그 파일 및 특수 PDW에 대 한 로그 파일입니다. 이 암호화에서는 DEK(데이터베이스 암호화 키)를 사용하며 이 키는 복구하는 동안 사용할 수 있도록 데이터베이스 부트 레코드에 저장됩니다. DEK는 SQL Server PDW 마스터 데이터베이스에 저장 된 인증서를 사용 하 여 보호 하는 대칭 키입니다. TDE는 데이터 및 로그 파일을 의미하는 "유휴" 데이터를 보호하고 다양한 업계에서 확립된 법, 규정 및 지침에 부합하는 기능을 제공합니다. 이 기능은 소프트웨어 개발자가 기존 응용 프로그램을 변경 하지 않고 AES 및 3DES 암호화 알고리즘을 사용 하 여 데이터를 암호화할 수 있습니다.  
  
> [!IMPORTANT]  
> TDE는 PDW와 클라이언트 간에 전송 되는 데이터에 대 한 암호화를 제공 하지 않습니다. 클라이언트와 SQL Server PDW 데이터를 암호화 하는 방법에 대 한 자세한 내용은 참조 하세요. [인증서 프로 비전](provision-certificate.md)합니다.  
>   
> TDE는 이동 중인 또는 사용 하 여 데이터를 암호화 하지 않습니다. SQL Server PDW 내에서 PDW 구성 요소 간의 내부 트래픽을 암호화 되지 않습니다. 메모리 버퍼에 일시적으로 저장 된 데이터를 암호화 되지 않습니다. 이 위험을 완화 하려면 물리적으로 액세스 및 SQL Server PDW에 대 한 연결을 제어 합니다.  
  
보안이 설정된 후 올바른 인증서를 사용하여 데이터베이스를 복원할 수 있습니다.  
  
> [!NOTE]  
> TDE에 대 한 인증서를 만들 때 즉시 백업 해야 하기, 연결 된 개인 키와 함께 합니다. 인증서를 사용할 수 없게 되거나 다른 서버에서 데이터베이스를 복원하거나 연결해야 할 경우 인증서와 개인 키의 백업본이 있어야 합니다. 그렇지 않으면 데이터베이스를 열 수 없습니다. 데이터베이스에서 TDE를 해제하더라도 인증서 암호화는 그대로 유지해야 합니다. 데이터베이스가 암호화되지 않더라도 트랜잭션 로그 부분은 그대로 보호될 수 있으며, 일부 작업의 경우 데이터베이스 전체 백업을 수행할 때까지는 인증서가 필요할 수 있습니다. 만료 날짜가 지난 인증서도 여전히 데이터를 TDE로 암호화하고 해독하는 데 사용할 수 있습니다.  
  
데이터베이스 파일 암호화는 페이지 수준에서 수행됩니다. 암호화된 데이터베이스의 페이지는 암호화된 후 디스크에 작성되고 메모리로 읽어 들일 때 암호가 해독됩니다. TDE로 암호화된 데이터베이스의 크기가 증가되지는 않습니다.  
  
다음 그림에서는 TDE 암호화 키의 계층 구조를 보여 줍니다.  
  
![계층을 보여 줍니다](media/tde-architecture.png "TDE_Architecture")  
  
## <a name="using-tde"></a>투명 한 데이터 암호화를 사용 하 여  
TDE를 사용하려면 다음 단계를 수행합니다. TDE를 지원 하려면 SQL Server PDW를 준비 하는 경우 처음 세 단계를 한 번 수행만 됩니다.  
  
1.  Master 데이터베이스에 마스터 키를 만듭니다.  
  
2.  사용 하 여 **가 sp_pdw_database_encryption** SQL Server PDW에서 TDE를 사용 하도록 설정 합니다. 이 작업 이후 임시 데이터의 보호를 보장 하기 위해 임시 데이터베이스를 수정 하 고 모든 활성 세션 임시 테이블이 있는 경우 시도 실패 합니다. **가 sp_pdw_database_encryption** PDW 시스템 로그에서 사용자 데이터 마스킹을 설정 합니다. (PDW 시스템 로그에서 사용자 데이터 마스킹에 대 한 자세한 내용은 참조 하세요. [sp_pdw_log_user_data_masking](../relational-databases/system-stored-procedures/sp-pdw-log-user-data-masking-sql-data-warehouse.md).)  
  
3.  사용 하 여 [sp_pdw_add_network_credentials](../relational-databases/system-stored-procedures/sp-pdw-add-network-credentials-sql-data-warehouse.md) 인증 하 고 인증서의 백업을 저장할 공유에 쓸 수 있는 자격 증명을 만들어야 합니다. 자격 증명을 의도 한 저장소 서버에 이미 있는 경우 기존 자격 증명을 사용할 수 있습니다.  
  
4.  Master 데이터베이스에서 마스터 키로 보호 되는 인증서를 만듭니다.  
  
5.  저장소 공유에 인증서를 백업 합니다.  
  
6.  사용자 데이터베이스에서 데이터베이스 암호화 키를 만들고 master 데이터베이스에 저장 된 인증서로 보호 합니다.  
  
7.  사용 된 `ALTER DATABASE` TDE를 사용 하 여 데이터베이스를 암호화 하는 문입니다.  
  
다음 예제에서는 암호화 된 `AdventureWorksPDW2012` 이라는 인증서를 사용 하 여 데이터베이스 `MyServerCert`SQL Server PDW에서 생성 합니다.  
  
**첫 번째: SQL Server PDW에서 TDE를 사용 하도록 설정 합니다.** 이 작업은 한 번만 필요 합니다.  
  
```sql  
USE master;  
GO  
  
-- Create a database master key in the master database  
CREATE MASTER KEY ENCRYPTION BY PASSWORD = '<UseStrongPasswordHere>';  
GO  
  
-- Enable encryption for PDW  
EXEC sp_pdw_database_encryption 1;  
GO  
  
-- Add a credential that can write to the share  
-- A credential created for a backup can be used if you wish  
EXEC sp_pdw_add_network_credentials 'SECURE_SERVER', '<domain>\<Windows_user>', '<password>';  
```  
  
**두 번째: 만들기 및 master 데이터베이스에서 인증서를 백업 합니다.** 이 작업은만 한 번 지정 해야 합니다. (권장) 각 데이터베이스에 대 한 별도 인증서가 있거나 인증서가 두 개를 사용 하 여 여러 데이터베이스를 보호할 수 있습니다.  
  
```sql  
-- Create certificate in master  
CREATE CERTIFICATE MyServerCert WITH SUBJECT = 'My DEK Certificate';  
GO  
  
-- Back up the certificate with private key  
BACKUP CERTIFICATE MyServerCert   
    TO FILE = '\\SECURE_SERVER\cert\MyServerCert.cer'  
    WITH PRIVATE KEY   
    (   
        FILE = '\\SECURE_SERVER\cert\MyServerCert.key',  
        ENCRYPTION BY PASSWORD = '<UseStrongPasswordHere>'   
    )   
GO  
```  
  
**마지막: DEK를 만들고 ALTER DATABASE를 사용 하 여 사용자 데이터베이스를 암호화 합니다.** 이 작업은 TDE로 보호 되는 각 데이터베이스에 대해 반복 됩니다.  
  
```sql  
USE AdventureWorksPDW2012;  
GO  
  
CREATE DATABASE ENCRYPTION KEY  
WITH ALGORITHM = AES_128  
ENCRYPTION BY SERVER CERTIFICATE MyServerCert;  
GO  
  
ALTER DATABASE AdventureWorksPDW2012 SET ENCRYPTION ON;  
GO  
```  
  
암호화 및 암호 해독 작업은 SQL Server가 백그라운드 스레드에서 예약 됩니다. 이 문서의 뒷부분에 표시 되는 목록에서 카탈로그 뷰 및 동적 관리 뷰를 사용 하 여 이러한 작업의 상태를 볼 수 있습니다.  
  
> [!CAUTION]  
> TDE가 사용된 데이터베이스의 백업 파일도 데이터베이스 암호화 키를 사용하여 암호화됩니다. 따라서 이러한 백업 파일을 복원하려면 데이터베이스 암호화 키를 보호하는 인증서를 사용할 수 있어야 합니다. 즉, 데이터베이스 백업뿐만 아니라 데이터 손실을 방지하기 위해 서버 인증서의 백업도 유지 관리해야 합니다. 인증서를 더 이상 사용할 수 없을 경우 데이터 손실이 발생합니다.  
  
## <a name="commands-and-functions"></a>명령 및 함수  
TDE 인증서는 다음 문에서 수락된 데이터베이스 마스터 키로 암호화되어야 합니다.  
  
다음 표에서는 TDE 명령 및 함수에 대한 링크와 설명을 제공합니다.  
  
|명령 또는 함수|용도|  
|-----------------------|-----------|  
|[CREATE DATABASE ENCRYPTION KEY](../t-sql/statements/create-database-encryption-key-transact-sql.md)|데이터베이스 암호화에 사용할 키를 만듭니다.|  
|[ALTER DATABASE ENCRYPTION KEY](../t-sql/statements/alter-database-encryption-key-transact-sql.md)|데이터베이스 암호화에 사용할 키를 변경합니다.|  
|[DROP DATABASE ENCRYPTION KEY](../t-sql/statements/drop-database-encryption-key-transact-sql.md)|데이터베이스 암호화에 사용한 키를 제거합니다.|  
|[ALTER DATABASE](../t-sql/statements/alter-database-transact-sql.md?tabs=sqlpdw)|TDE를 설정하는 데 사용된 **ALTER DATABASE** 옵션에 대해 설명합니다.|  
  
## <a name="catalog-views-and-dynamic-management-views"></a>카탈로그 뷰 및 동적 관리 뷰  
다음 표에서는 TDE 카탈로그 뷰 및 동적 관리 뷰를 보여 줍니다.  
  
|카탈로그 뷰 또는 동적 관리 뷰|용도|  
|-------------------------------------------|-----------|  
|[sys.databases](../relational-databases/system-catalog-views/sys-databases-transact-sql.md)|데이터베이스 정보를 보여 주는 카탈로그 뷰입니다.|  
|[sys.certificates](../relational-databases/system-catalog-views/sys-certificates-transact-sql.md)|데이터베이스의 인증서를 보여 주는 카탈로그 뷰입니다.|  
|[sys.dm_pdw_nodes_database_encryption_keys](../relational-databases/system-dynamic-management-views/sys-dm-pdw-nodes-database-encryption-keys-transact-sql.md)|데이터베이스 및 데이터베이스의 암호화 상태에 사용 되는 암호화 키에 대 한 각 노드에 대 한 정보를 제공 하는 동적 관리 뷰.|  
  
## <a name="permissions"></a>사용 권한  
위에 표시된 표에서 설명한 것처럼 TDE의 기능 및 명령에는 각각의 사용 권한 요구 사항이 있습니다.  
  
TDE와 관련 된 메타 데이터를 보려면이 필요 합니다 `CONTROL SERVER` 권한.  
  
## <a name="considerations"></a>고려 사항  
처리 중인 데이터베이스 암호화 작업에 대해 재암호화를 검색하는 동안에는 데이터베이스에 대한 유지 관리 작업이 비활성화됩니다.  
  
사용 하 여 데이터베이스 암호화 상태를 확인할 수는 **sys.dm_pdw_nodes_database_encryption_keys** 동적 관리 뷰. 자세한 내용은 참조는 *카탈로그 뷰 및 동적 관리 뷰* 이 문서의 이전 섹션입니다.  
  
### <a name="restrictions"></a>Restrictions  
다음 작업을 허용 하지 않습니다 합니다 `CREATE DATABASE ENCRYPTION KEY`, `ALTER DATABASE ENCRYPTION KEY`, `DROP DATABASE ENCRYPTION KEY`, 또는 `ALTER DATABASE...SET ENCRYPTION` 문.  
  
-   데이터베이스 삭제  
  
-   사용 하는 `ALTER DATABASE` 명령입니다.  
  
-   데이터베이스 백업을 시작합니다.  
  
-   데이터베이스 복원을 시작합니다.  
  
다음 작업 또는 조건 수 없게 합니다 `CREATE DATABASE ENCRYPTION KEY`, `ALTER DATABASE ENCRYPTION KEY`, `DROP DATABASE ENCRYPTION KEY`, 또는 `ALTER DATABASE...SET ENCRYPTION` 문입니다.  
  
-   `ALTER DATABASE` 명령이 실행 됩니다.  
  
-   데이터 백업이 실행 중인 경우  
  
데이터베이스 파일을 만들 때 TDE가 사용하도록 설정되어 있으면 즉시 파일 초기화를 사용할 수 없습니다.  
  
### <a name="areas-not-protected-by-tde"></a>TDE로 보호 되지 않는 영역  
TDE는 외부 테이블을 보호 하지 않습니다.  
  
TDE는 진단 세션을 보호 하지 않습니다. 사용자는 주의 해야 합니다. 사용 중인 진단 세션 동안 중요 한 매개 변수를 사용 하 여 쿼리 합니다. 더 이상 필요 없는으로 중요 한 정보를 표시 하는 진단 세션을 삭제 해야 합니다.  
  
TDE로 보호 되는 데이터에는 SQL Server PDW 메모리에 배치 되었을 때 암호가 해독 됩니다. 메모리 덤프는 어플라이언스에서 특정 문제가 발생할 때 생성 됩니다. 파일 나타내는 콘텐츠 메모리 문제 모양 당시를 덤프 하 및 암호화 되지 않은 형식에서 중요 한 데이터를 포함할 수 있습니다. 메모리 덤프의 내용은 다른 사용자와 공유 하기 전에 검토 해야 합니다.  
  
Master 데이터베이스 TDE로 보호 되지 않습니다. Master 데이터베이스에 사용자 데이터가 없습니다, 있지만 로그인 이름과 같은 정보가 포함지 않습니다.  
  
### <a name="transparent-data-encryption-and-transaction-logs"></a>투명한 데이터 암호화 및 트랜잭션 로그  
TDE를 사용 하려면 데이터베이스를 설정 하면 다음 가상 트랜잭션 로그를 강제로 가상 트랜잭션 로그의 남은 부분 영구 삭제 작업의 효과 가집니다. 이렇게 하면 데이터베이스에 암호화가 설정된 후 트랜잭션 로그에 남아 있는 일반 텍스트가 없습니다. 확인 하 여 각 PDW 노드에 로그 파일 암호화의 상태를 찾을 수 있습니다 합니다 `encryption_state` 열에는 `sys.dm_pdw_nodes_database_encryption_keys` 이 예제와 같이 보기:  
  
```sql  
WITH dek_encryption_state AS   
(  
    SELECT ISNULL(db_map.database_id, dek.database_id) AS database_id, encryption_state  
    FROM sys.dm_pdw_nodes_database_encryption_keys AS dek  
        INNER JOIN sys.pdw_nodes_pdw_physical_databases AS node_db_map  
           ON dek.database_id = node_db_map.database_id AND dek.pdw_node_id = node_db_map.pdw_node_id  
        LEFT JOIN sys.pdw_database_mappings AS db_map  
            ON node_db_map .physical_name = db_map.physical_name  
        INNER JOIN sys.dm_pdw_nodes AS nodes  
            ON nodes.pdw_node_id = dek.pdw_node_id  
    WHERE dek.encryptor_thumbprint <> 0x  
)  
SELECT TOP 1 encryption_state  
       FROM dek_encryption_state  
       WHERE dek_encryption_state.database_id = DB_ID('AdventureWorksPDW2012 ')  
       ORDER BY (CASE encryption_state WHEN 3 THEN -1 ELSE encryption_state END) DESC;  
```  
  
데이터베이스 암호화 키를 변경하기 전에 트랜잭션 로그에 작성된 모든 데이터는 이전 데이터베이스 암호화 키를 사용하여 암호화됩니다.  
  
### <a name="pdw-activity-logs"></a>PDW 활동 로그  
SQL Server PDW에 문제 해결을 위한 로그의 집합을 유지 관리 합니다. (Note,이 트랜잭션 로그, SQL Server 오류 로그 또는 Windows 이벤트 로그입니다.) 이러한 PDW 활동 로그에는 사용자 데이터를 포함할 수 있는 일반 텍스트로 전체 문을 포함할 수 있습니다. 일반적인 예로 **삽입** 하 고 **업데이트** 문입니다. 사용자 데이터 마스킹 수 명시적으로 설정 또는 해제를 사용 하 여 **sp_pdw_log_user_data_masking**합니다. SQL Server PDW에서 암호화를 자동으로 사용 하 여 보호 PDW 활동 로그의 사용자 데이터 마스킹 설정 합니다. **sp_pdw_log_user_data_masking** TDE를 사용 하지 않을 때 문을 마스크 하기 위해 사용할 수도 있지만 문제를 분석 하는 Microsoft 지원 팀의 기능을 크게 절감할 수 있으므로 권장 하지 않습니다.  
  
### <a name="transparent-data-encryption-and-the-tempdb-system-database"></a>투명한 데이터 암호화 및 tempdb 시스템 데이터베이스  
사용 하 여 암호화가 설정 된 경우 tempdb 시스템 데이터베이스가 암호화 됩니다 [가 sp_pdw_database_encryption](../relational-databases/system-stored-procedures/sp-pdw-database-encryption-sql-data-warehouse.md)합니다. 모든 데이터베이스에서 TDE를 사용 하려면 먼저 이것이 필요 합니다. 이 SQL Server PDW의 동일한 인스턴스에 암호화 되지 않은 데이터베이스에 대 한 성능에 영향을 할 수 있습니다.  
  
## <a name="key-management"></a>키 관리  
데이터베이스 암호화 키 (DEK) master 데이터베이스에 저장 된 인증서로 보호 됩니다. 이러한 인증서는 master 데이터베이스의 데이터베이스 마스터 키 (DMK)로 보호 됩니다. DMK는 SMK (서비스 마스터 키)에서 TDE에 사용할 수 있도록 보호 해야 합니다.  
  
시스템 (예: 암호를 제공) 사람이 개입할 필요 없이 키에 액세스할 수 있습니다. 인증서를 사용할 수 없는 경우 시스템 오류 적절 한 인증서 사용 가능할 때까지 DEK를 해독할 수 없는 메시지가 출력 됩니다.  
  
인증서 보호에 사용할 하나의 어플라이언스에서 다른 데이터베이스를 이동 하는 경우 해당 ' 대상 서버의 DEK를 먼저 복원 해야 합니다. 그런 다음 데이터베이스는 일반적으로 복원할 수 있습니다. 자세한 내용은 표준 SQL Server 설명서를 참조 하세요 [다른 SQL Server로 TDE 보호 데이터베이스 이동](https://technet.microsoft.com/library/ff773063.aspx)합니다.  
  
Dek를 암호화 하는 인증서를 사용 하는 데이터베이스 백업이으로 보존 됩니다. 백업 인증서 개인 키 없이 인증서를 사용할 수 없으므로 데이터베이스 복원에 대 한 인증서 개인 키를 포함 해야 합니다. 이러한 인증서에 개인 키 백업 인증서 복원을 위해 제공 해야 하는 암호로 보호 하는 별도 파일에 저장 됩니다.  
  
## <a name="restoring-the-master-database"></a>Master 데이터베이스 복원  
사용 하 여 master 데이터베이스를 복원할 수 있습니다 **DWConfig**, 재해 복구의 일부로.  
  
-   제어 노드 변경 되지 않은 경우 master 데이터베이스는 master 데이터베이스의 백업을 수행한 동일한 채 어플라이언스에 복원 되는 DMK 및 모든 인증서를 읽을 수 추가 작업 없이입니다.  
  
-   다양 한 기기 마스터 데이터베이스를 복원 또는 제어 노드에 master 데이터베이스 백업 이후 변경 된 경우 DMK를 다시 생성 하기 위해 추가 단계를 수행 해야 합니다.  
  
    1.  DMK를 엽니다.  
  
        ```sql  
        OPEN MASTER KEY DECRYPTION BY PASSWORD = '<password>';  
        ```  
  
    2.  SMK는 암호화를 추가 합니다.  
  
        ```sql  
        ALTER MASTER KEY   
            ADD ENCRYPTION BY SERVICE MASTER KEY;  
        ```  
  
    3.  어플라이언스를 다시 시작 합니다.  
  
## <a name="upgrade-and-replacing-virtual-machines"></a>업그레이드 및 Virtual Machines를 대체 합니다.  
DMK를 업그레이드 또는 대체 VM 수행한 어플라이언스에서 있으면 DMK를 암호 매개 변수로 제공 되어야 합니다.  
  
업그레이드 동작의 예입니다. 대체 `**********` DMK 암호를 사용 하 여 합니다.  
  
`setup.exe /Action=ProvisionUpgrade ... DMKPassword='**********'  `  
  
가상 컴퓨터를 교체할 수 작업의 예입니다.  
  
`setup.exe /Action=ReplaceVM ... DMKPassword='**********'  `  
  
DB 사용자는 암호화 되 고 DMK 암호를 지정 하지 않은 경우에 업그레이드 하는 동안 업그레이드 작업이 실패 합니다. 바꾸기를 하는 동안 DMK 있으면 올바른 암호를 제공 하지 않으면 작업이 건너뜁니다 DMK 복구 단계입니다. 작업에는 추가 단계가 필요한 지를 나타내기 위해 끝에 오류가 보고 됩니다 있지만 바꾸기 VM 작업 끝에 다른 단계를 모두 완료 됩니다. 설치 로그에서 (에 있는 **\ProgramData\Microsoft\Microsoft SQL Server Parallel Data Warehouse\100\Logs\Setup\\< 타임 스탬프 > \Detail-Setup**), 후반부에 다음 경고가 표시 됩니다.  
  
`*** WARNING \*\*\* DMK is detected in master database, but could not be recovered automatically! The DMK password was either not provided or is incorrect!  `
  
PDW에서 이러한 문을 수동으로 실행 하 고 DMK를 복구 하려면 그 후에 어플라이언스를 다시 시작:  
  
```sql
OPEN MASTER KEY DECRYPTION BY PASSWORD = '<DMK password>';  
ALTER MASTER KEY ADD ENCRYPTION BY SERVICE MASTER KEY;  
```
  
단계를 사용 합니다 **master 데이터베이스 복원** 단락 데이터베이스를 복구 하 고 어플라이언스를 다시 시작 합니다.  
  
DMK 전의 작업 후 복구 되지 않아 하지만 경우에 데이터베이스를 쿼리할 때 다음 오류 메시지가 발생 합니다.  
  
```sql
Msg 110806;  
A distributed query failed: Database '<db_name>' cannot be opened due to inaccessible files or insufficient memory or disk space. See the SQL Server errorlog for details.
```  
  
## <a name="performance-impact"></a>성능에 미치는 영향  
TDE의 성능 영향을 해야 하는 데이터, 저장 하는 방법 및 SQL Server PDW에서 워크 로드 활동의 type을의 형식에 따라 다릅니다. TDE로 보호 하는 경우 읽기 다음 데이터를 암호 해독 또는 암호화 및 다음 데이터를 쓰기의 I/O CPU 집약적 작업이는 다른 CPU 집약적인 작업을 동시에 발생 하는 경우 더 많은 영향을 주지. TDE 암호화 하기 때문에 `tempdb`, TDE 암호화 되지 않은 데이터베이스의 성능에 영향을 줄 수 있습니다. 성능의 정확한 아이디어를 가져오려면 데이터 및 쿼리 작업을 사용 하 여 전체 시스템을 테스트 해야 합니다.  
  
## <a name="related-content"></a>관련 내용  
다음 링크를 SQL Server 암호화를 관리 하는 방법에 대 한 일반 정보를 포함 합니다. 이러한 문서는 SQL Server 암호화 하지만 이러한 문서 필요가 없습니다 SQL Server PDW에 대 한 정보 및 SQL Server PDW에 없는 기능에 이야기를 이해 하면 도움이 됩니다.  
  
-   [SQL Server 암호화](../relational-databases/security/encryption/sql-server-encryption.md)  
  
-   [암호화 계층](../relational-databases/security/encryption/encryption-hierarchy.md)  
  
-   [SQL Server 및 데이터베이스 암호화 키](../relational-databases/security/encryption/sql-server-and-database-encryption-keys-database-engine.md)  

  
## <a name="see-also"></a>관련 항목:  
[ALTER DATABASE](../t-sql/statements/alter-database-transact-sql.md?tabs=sqlpdw)  
[마스터 키 만들기](../t-sql/statements/create-master-key-transact-sql.md)  
[CREATE DATABASE ENCRYPTION KEY](../t-sql/statements/create-database-encryption-key-transact-sql.md)  
[BACKUP CERTIFICATE](../t-sql/statements/backup-certificate-transact-sql.md)  
[sp_pdw_database_encryption](../relational-databases/system-stored-procedures/sp-pdw-database-encryption-sql-data-warehouse.md)  
[sp_pdw_database_encryption_regenerate_system_keys](../relational-databases/system-stored-procedures/sp-pdw-database-encryption-regenerate-system-keys-sql-data-warehouse.md)  
[sp_pdw_log_user_data_masking](../relational-databases/system-stored-procedures/sp-pdw-log-user-data-masking-sql-data-warehouse.md)  
[sys.certificates](../relational-databases/system-catalog-views/sys-certificates-transact-sql.md)  
[sys.dm_pdw_nodes_database_encryption_keys](../relational-databases/system-dynamic-management-views/sys-dm-pdw-nodes-database-encryption-keys-transact-sql.md)  
  
