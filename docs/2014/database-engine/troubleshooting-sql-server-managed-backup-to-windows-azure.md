---
title: Backup to Windows Azure 관리 되는 SQL Server 문제 해결 | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
ms.assetid: a34d35b0-48eb-4ed1-9f19-ea14754650da
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: fd68f6f8bcb83bfbc980be0809e12141403e4012
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62842580"
---
# <a name="troubleshooting-sql-server-managed--backup-to-windows-azure"></a>Microsoft Azure에 대한 SQL Server 관리되는 백업 문제 해결
  이 항목에서는 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] 작업 중 발생할 수 있는 오류를 해결하는 데 사용할 수 있는 태스크 및 도구에 대해 설명합니다.  
  
## <a name="overview"></a>개요  
 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]에는 검사 및 문제 해결 단계가 내장되어 있어 많은 내부 오류가 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] 프로세스에 의해 자체 해결됩니다.  
  
 이러한 사례의 예로 로그의 바꿈이 발생 하는 백업 파일의 삭제 체인에 영향을 주는 복구- [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] 로그 체인에서 중단을 식별 하 여 즉시 실행 되도록 백업을 예약 합니다. 그러나 상태를 모니터링하여 수동 작업이 필요한 오류를 해결하는 것이 좋습니다.  
  
 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]은 시스템 저장 프로시저, 시스템 뷰 및 확장 이벤트를 사용하여 이벤트 및 오류를 기록합니다. 시스템 뷰 및 저장 프로시저는 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] 구성 정보, 예약된 백업의 백업 상태 및 확장 이벤트에서 검색한 오류를 제공합니다. [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]은 확장 이벤트를 사용하여 문제 해결에 사용할 오류를 검색합니다. 이벤트 기록 외에도 SQL Server 스마트 관리 정책은 오류 및 문제 또는 알림을 제공하는 전자 메일 알림 작업에 사용되는 상태를 제공합니다. 자세한 내용은 참조 [모니터 SQL Server Managed Backup to Windows Azure](../relational-databases/backup-restore/sql-server-managed-backup-to-microsoft-azure.md)합니다.  
  
 또한 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]은 Microsoft Azure Storage에 수동으로 백업할 때(URL에 대한 SQL Server 백업) 사용되는 동일한 로깅을 사용합니다. URL 백업 수행에 대 한 자세한 내용은 관련 문제에서 문제 해결 섹션을 참조 [SQL Server Backup to URL Best Practices and Troubleshooting](../relational-databases/backup-restore/sql-server-backup-to-url-best-practices-and-troubleshooting.md)  
  
### <a name="general-troubleshooting-steps"></a>일반 문제 해결 단계  
  
1.  오류 및 경고에 대한 전자 메일을 수신하도록 전자 메일 알림을 설정하십시오.  
  
     또는 주기적으로 `smart_admin.fn_get_health_status`를 실행하여 집계된 오류 및 개수를 확인할 수도 있습니다. 예를 들어 `number_of_invalid_credential_errors`는 스마트 백업에서 백업을 시도했지만 잘못된 자격 증명 오류가 발생한 횟수입니다. `Number_of_backup_loops` 및 `number_of_retention_loops`는 오류가 아니지만 백업 스레드와 보존 스레드가 데이터베이스 목록을 검색한 횟수를 나타냅니다. 일반적으로, @begin_time 고 @end_time 를 제공 하지 않은 함수는 지난 30 분 동안의 정보를 표시 하는 0이 아닌 값이 두 열에 대 한 일반적으로 표시 되어야 합니다. 두 열의 값이 0이면 오버로드된 시스템이나 응답하지 않는 시스템을 의미합니다. 자세한 내용은 **시스템 문제 해결** 이 항목의 뒷부분에 나오는 섹션입니다.  
  
2.  오류 및 기타 관련 이벤트에 대한 자세한 내용을 보려면 확장 이벤트 로그를 검토하십시오.  
  
3.  문제를 해결하려면 로그의 정보를 사용하십시오.  시스템 문제 또는 오류의 경우 서비스나 SQL Server 에이전트를 다시 시작해야 할 수 있습니다.  
  
### <a name="common-causes-of-errors"></a>오류의 일반적인 원인  
 다음은 오류를 일으키는 일반적인 원인 목록입니다.  
  
1.  **SQL 자격 증명 변경:** [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]에서 사용되는 자격 증명 이름이 변경되거나 삭제되면 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]이 백업을 수행할 수 없습니다. 이 변경은 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] 구성 설정에 적용되어야 합니다.  
  
2.  **저장소 액세스 키 값 변경:** Windows Azure 계정에 대해 저장소 키 값이 변경되었지만 SQL 자격 증명이 새 값으로 업데이트되지 않은 경우 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]은 저장소에 인증할 때 실패하고 이 계정을 사용하도록 구성된 데이터베이스를 백업하지 못합니다.  
  
3.  **Windows Azure 저장소 계정에 변경 내용:** 해당 SQL 자격 증명을 변경하지 않고 저장소 계정을 삭제하거나 이름을 바꾸면 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]이 실패하고 백업이 수행되지 않습니다. 저장소 계정을 삭제한 경우에는 데이터베이스가 올바른 저장소 계정 정보로 다시 구성되었는지 확인하십시오. 저장소 계정의 이름이 변경되거나 키 값이 변경되면 이러한 변경 사항이 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]에서 사용하는 SQL 자격 증명에도 반영되도록 해야 합니다.  
  
4.  **데이터베이스 속성 변경:** 복구 모델을 변경하거나 이름을 변경하면 백업이 실패할 수 있습니다.  
  
5.  **복구 모델 변경:** 데이터베이스의 복구 모델이 전체 또는 대량 로그에서 단순 모델로 변경되면 백업이 중지되고 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]에서 데이터베이스를 건너뜁니다. 자세한 내용은 참조 하세요. [SQL Server Managed Backup to Windows Azure: 상호 운용성 및 공존 성](../../2014/database-engine/sql-server-managed-backup-to-windows-azure-interoperability-and-coexistence.md)  
  
### <a name="most-common-error-messages-and-solutions"></a>가장 일반적인 오류 메시지 및 해결 방법  
  
1.  **오류 설정 또는 구성 시 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]:**  
  
     오류: " 저장소 URL에 액세스 하지 못했습니다. 올바른 SQL 자격 증명을 제공... ": SQL 자격 증명과 관련하여 이러한 오류가 발생할 수 있습니다.  이러한 경우에 이름 제공한 SQL 자격 증명 및 SQL 자격 증명-storage 계정 이름 및 저장소 액세스 키를 저장 된 정보를 검토 하 고 현재 및 유효 해야 합니다.  
  
     오류: "... 시스템 데이터베이스 이므로... 데이터베이스를 구성할 수 없습니다". 이 오류는 시스템 데이터베이스에 대해 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]을 설정하려고 할 때 발생합니다.  [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]은 시스템 데이터베이스 백업을 지원하지 않습니다.  시스템 데이터베이스에 대한 백업을 구성하려면 유지 관리 계획 등 다른 SQL Server 백업 기술을 사용하십시오.  
  
     오류: "... 제공... 보존 기간 "합니다. 데이터베이스 또는 인스턴스에 대한 보존 기간을 처음으로 구성할 때 이러한 값을 지정하지 않은 경우 보존 기간 관련 오류가 발생할 수 있습니다. 1-30 이외의 값을 지정한 경우에도 오류가 발생할 수 있습니다. 보존 기간에 대해 허용된 값은 1-30의 숫자입니다.  
  
2.  **전자 메일 알림 오류:**  
  
     오류: "데이터베이스 메일은 사용할 수 없습니다..."-전자 메일 알림을 설정 했지만 데이터베이스 메일이 인스턴스에서 구성 되지 경우이 오류가 나타납니다. [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]의 상태에 대한 알림을 수신하려면 인스턴스에서 데이터베이스 메일을 구성해야 합니다. 데이터베이스 메일을 활성화 하는 방법에 대 한 정보를 참조 하세요 [데이터베이스 메일 구성](../relational-databases/database-mail/configure-database-mail.md)합니다. 또한 알림에 데이터베이스 메일을 사용하도록 SQL Server 에이전트를 설정해야 합니다. 자세한 내용은 [시작 하기 전에](../relational-databases/database-mail/configure-sql-server-agent-mail-to-use-database-mail.md#BeforeYouBegin)입니다.  
  
     다음은 전자 메일 알림과 관련하여 표시될 수 있는 오류 번호의 목록입니다.  
  
    -   오류 번호: 45209  
  
    -   오류 번호: 45210  
  
    -   오류 번호: 45211  
  
3.  **연결 오류:**  
  
    -   **SQL 연결 관련 오류:** 이러한 오류는 SQL Server 인스턴스에 연결할 때 문제가 있으면 발생합니다. 확장 이벤트는 관리 채널을 통해 이러한 유형의 오류를 노출합니다. 다음은 이러한 유형의 연결 문제와 관련된 오류에 대해 표시될 수 있는 두 가지 확장 이벤트입니다.  
  
         event_type = SqlError인 FileRetentionAdminXEvent. 이 오류에 대한 자세한 내용은 해당 이벤트의 error_code, error_message 및 stack_trace를 참조하십시오. Error_code는 SqlException의 오류 번호입니다.  
  
         다음 메시지/메시지 접두사가 포함된 SmartBackupAdminXevent:  
  
         *"Windows Azure 기본 설정으로 SQL Server Managed Backup을 구성 하는 동안 내부 오류가 발생 했습니다. 예를 들어 있습니다. 일시적인 오류일 수 있습니다. "*  
  
         *"아마도 SQL Server 연결 문제가 발생 했습니다. 현재 반복에서 데이터베이스를 건너뜁니다. "*  
  
         *"실패 한 로그 사용 정보를 쿼리 합니다. 일시적인 실패일 수 있습니다. 현재 반복에서 데이터베이스를 건너뜁니다. "*  
  
         *"SSMBackup2WA 에이전트 메타 데이터를 로드 하는 동안 발생 한 SQL 예외입니다. 일시적인 실패일 수 있습니다. 작업을 다시 시도 됩니다. "*  
  
         *"SSMBackup2WA... 하는 동안 SQL 예외를 발생 했습니다. "*  
  
    -   **저장소 계정 연결 오류:**  
  
         event_type = XstoreError인 FileRetentionAdminXEvent에서 스토리지 예외가 보고됩니다. 이 오류에 대한 자세한 내용은 해당 이벤트의 error_message 및 stack_trace를 참조하십시오.  
  
         SQL Server 관리되는 백업이 URL에 대한 백업 기술을 기반으로 하므로 스토리지 연결과 관련된 오류는 두 기능에 모두 적용됩니다. 문제 해결 단계에 대 한 자세한 내용은 참조 하세요. **문제 해결 섹션** 의 합니다 [SQL Server Backup to URL Best Practices and Troubleshooting](../relational-databases/backup-restore/sql-server-backup-to-url-best-practices-and-troubleshooting.md) 문서.  
  
### <a name="troubleshooting-system-issues"></a>시스템 문제 해결  
 시스템(SQL Server, SQL Server 에이전트)에 문제가 있는 몇 가지 시나리오와 해당 문제가 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]에 미치는 영향은 다음과 같습니다.  
  
-   **Sqlservr.exe가 응답 하지 않거나 작동 중지 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] 실행 됩니다.** SQL Server가 작동하지 않는 경우 SQL 에이전트가 정상적으로 종료되고 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]도 중지되며 이벤트가 SQL Agent.out 파일에 기록됩니다.  
  
     SQL Server가 응답하지 않는 경우 이벤트가 관리 채널에 기록됩니다.  이벤트 로그의 예:  
  
     *Sql 오류 (엔진이 응답 하지 않거나 sqlexception: SqlException:*    
     *오류 코드, 메시지 및 스택 추적에에서 표시할 추가 정보와 함께 관리 채널 xevent를 같은:*    
    *"아마도 SQL Server 연결 문제가 발생 했습니다. 현재 반복에서 데이터베이스를 건너뜁니다 "*  
  
-   **SQL 에이전트가 응답 하지 않거나 작동 중지 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] 실행 됩니다.**  
  
     SQL 에이전트가 작동하지 않는 경우 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]도 중지되고 이벤트가 관리 채널에 기록됩니다. 이는 SQL Server가 응답하지 않는 시나리오와 유사합니다.  
  
     SQL 에이전트가 응답하지 않는 경우 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]이 백업 작업을 계속할 수 없으며 이벤트가 관리 채널에 기록됩니다. 이벤트 로그의 예:  
  
     *중지 작업: 관리 채널 xevent를 참조 하세요.*    
    *"SQL server에서 진행률 업데이트를 수신 되지 않았습니다 둘" + Constants.DBBackupInfoMsgMaxWaitTime + "데이터베이스 백업에 대 한 시간입니다.   SSM 클라우드 백업이 계속 대기 합니다. "*  
  
 전자 메일 알림을 사용 하도록 설정한 경우 포함 하는 알림을 받습니다 **백업 루프 수** 하 고 **보존 루프 수**입니다. 이러한 두 열 중 하나나 둘 다에 대해 알림에서 반환되는 값이 0인 경우 시스템이 응답하지 않음을 나타낼 수도 있습니다.  
  
> [!WARNING]  
>  보고서에 대한 결과를 생성하는 내부 프로세스에서는 엔진 진단 로그가 SQL 에이전트 오류 로그와 동일한 위치에 있는 것으로 가정합니다. 이 로그는 기본적으로 SQL Server 인스턴스의 오류 로그와 같은 폴더에 있습니다. 엔진 진단 로그가 SQL 에이전트 오류 로그 위치가 아닌 위치로 이동하는 경우 시스템에서 스마트 백업 진단 로그를 찾을 수 없으므로 전자 메일 알림의 보고서가 올바르지 않을 수 있습니다. 예를 들어 값이 표시 될 수 있습니다 **0** 모든 필드에는 백업 루프 수 및 보존 루프 수를 포함 하 여 보고 합니다. 진단 로그를 다른 위치로 이동하는 이 경우에 시스템이 응답하지 않는 것이 아니라 시스템에서 진단 로그를 찾지 못하는 것일 수 있습니다. 먼저 진단 로그와 SQL 에이전트 오류 로그가 동일한 위치에 있는지 확인하십시오. 진단 로그의 현재 위치를 확인 하려면 사용할 수 있습니다 [sys.dm_os_server_diagnostics_log_configurations](/sql/relational-databases/system-dynamic-management-views/sys-dm-os-server-diagnostics-log-configurations)합니다. `path` 열 진단 로그는 엔진의 현재 위치를 반환 합니다.  SQL 에이전트 오류 로그와 동일한 폴더에 두는 것이 있어야 합니다. `dbo.sp_get_sqlagent_properties` 저장 프로시저를 사용하여 SQL 에이전트 오류 로그 경로를 가져올 수 있습니다.  
  
 오류의 세부 정보를 보려면 확장 이벤트 로그를 확인하십시오. 오류를 수정하거나 SQL Server 에이전트를 다시 시작하여 상황을 해결하십시오.  
  
  
