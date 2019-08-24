---
title: sp_addsubscription (Transact-sql) | Microsoft Docs
ms.date: 10/28/2015
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.custom: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_addsubscription
- sp_addsubscription_TSQL
helpviewer_keywords:
- sp_addsubscription
ms.assetid: 61ddf287-1fa0-4c1a-8657-ced50cebf0e0
author: stevestein
ms.author: sstein
ms.openlocfilehash: c57822529290a6ae4c3e1b5c96f712dbd626d04d
ms.sourcegitcommit: 728a4fa5a3022c237b68b31724fce441c4e4d0ab
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/03/2019
ms.locfileid: "68769033"
---
# <a name="sp_addsubscription-transact-sql"></a>sp_addsubscription(Transact-SQL)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md.md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

  게시에 구독을 추가하고 구독자 상태를 설정합니다. 이 저장 프로시저는 게시 데이터베이스의 게시자에서 실행됩니다.  
  
 ![항목 링크 아이콘](../../database-engine/configure-windows/media/topic-link.gif "항목 링크 아이콘") [Transact-SQL 구문 규칙](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>구문  
  
```  
  
sp_addsubscription [ @publication = ] 'publication'  
    [ , [ @article = ] 'article']  
    [ , [ @subscriber = ] 'subscriber' ]  
    [ , [ @destination_db = ] 'destination_db' ]  
        [ , [ @sync_type = ] 'sync_type' ]  
    [ , [ @status = ] 'status'  
        [ , [ @subscription_type = ] 'subscription_type' ]  
    [ , [ @update_mode = ] 'update_mode' ]  
    [ , [ @loopback_detection = ] 'loopback_detection' ]  
    [ , [ @frequency_type = ] frequency_type ]  
    [ , [ @frequency_interval = ] frequency_interval ]  
    [ , [ @frequency_relative_interval = ] frequency_relative_interval ]  
    [ , [ @frequency_recurrence_factor = ] frequency_recurrence_factor ]  
    [ , [ @frequency_subday = ] frequency_subday ]  
    [ , [ @frequency_subday_interval = ] frequency_subday_interval ]  
    [ , [ @active_start_time_of_day = ] active_start_time_of_day ]  
    [ , [ @active_end_time_of_day = ] active_end_time_of_day ]  
    [ , [ @active_start_date = ] active_start_date ]  
    [ , [ @active_end_date = ] active_end_date ]  
    [ , [ @optional_command_line = ] 'optional_command_line' ]  
    [ , [ @reserved = ] 'reserved' ]  
    [ , [ @enabled_for_syncmgr= ] 'enabled_for_syncmgr' ]  
    [ , [ @offloadagent= ] remote_agent_activation]  
    [ , [ @offloadserver= ] 'remote_agent_server_name' ]  
    [ , [ @dts_package_name= ] 'dts_package_name' ]  
    [ , [ @dts_package_password= ] 'dts_package_password' ]  
    [ , [ @dts_package_location= ] 'dts_package_location' ]  
    [ , [ @distribution_job_name= ] 'distribution_job_name' ]  
    [ , [ @publisher = ] 'publisher' ]  
    [ , [ @backupdevicetype = ] 'backupdevicetype' ]  
    [ , [ @backupdevicename = ] 'backupdevicename' ]  
    [ , [ @mediapassword = ] 'mediapassword' ]  
    [ , [ @password = ] 'password' ]  
    [ , [ @fileidhint = ] fileidhint ]  
    [ , [ @unload = ] unload ]  
    [ , [ @subscriptionlsn = ] subscriptionlsn ]  
    [ , [ @subscriptionstreams = ] subscriptionstreams ]  
    [ , [ @subscriber_type = ] subscriber_type ]  
    [ , [ @memory_optimized = ] memory_optimized ]  
```  
  
## <a name="arguments"></a>인수  
 [ @publication=] '*게시*'  
 게시의 이름입니다. *게시* 는 **sysname**이며 기본값은 없습니다.  
  
 [ @article=] '*article*'  
 게시를 구독하는 아티클입니다. *article* 은 **sysname**이며 기본값은 all입니다. all인 경우 해당 게시의 모든 아티클에 구독이 추가됩니다. Oracle 게시자의 경우 all 또는 NULL 값만 지원됩니다.  
  
 [ @subscriber=] '*구독자*'  
 구독자의 이름입니다. *구독자* 는 **sysname**이며 기본값은 NULL입니다.  
  
 [ @destination_db=] '*destination_db*'  
 복제된 데이터를 추가할 대상 데이터베이스의 이름입니다. *destination_db* 는 **sysname**이며 기본값은 NULL입니다. NULL 인 경우 *destination_db* 는 게시 데이터베이스의 이름으로 설정 됩니다. Oracle 게시자의 경우 *destination_db* 을 지정 해야 합니다. SQL Server 이외 구독자의 경우 *destination_db*에 대 한 (기본 대상) 값을 지정 합니다.  
  
 [ @sync_type=] '*sync_type*'  
 구독 동기화 유형입니다. *sync_type* 는 **nvarchar (255)** 이며 다음 값 중 하나일 수 있습니다.  
  
|값|설명|  
|-----------|-----------------|  
|none|게시된 테이블에 대한 스키마 및 초기 데이터가 구독자에 이미 있습니다.<br /><br /> 참고: 이 옵션은 더 이상 사용 되지 않습니다. 대신 replication support only를 사용하십시오.|  
|automatic(기본값)|게시된 테이블의 스키마 및 초기 데이터가 구독자에게 먼저 전송됩니다.|  
|replication support only|필요한 경우 구독자에서 업데이트 구독을 지원하는 아티클 사용자 지정 저장 프로시저 및 트리거의 자동 생성을 제공합니다. 이 옵션은 게시된 테이블에 대한 스키마 및 초기 데이터가 구독자에 이미 있다고 가정합니다. 피어 투 피어 트랜잭션 복제 토폴로지를 구성하는 경우 토폴로지의 모든 노드에 있는 데이터가 동일해야 합니다. 자세한 내용은 [Peer-to-Peer Transactional Replication](../../relational-databases/replication/transactional/peer-to-peer-transactional-replication.md)을 참조하세요.<br /><br /> *SQL Server 되지 않은 게시에 대 한 구독에 대해서는 지원 되지 않습니다.*|  
|initialize with backup|게시된 테이블의 스키마 및 초기 데이터는 게시 데이터베이스의 백업에서 가져옵니다. 구독자에 게시 데이터베이스 백업에 대한 액세스 권한이 있다고 가정합니다. 백업에 대 한 백업 및 미디어 유형의 위치는 *backupdevicename* 이름 및 *backupdevicetype*에서 지정 합니다. 이 옵션을 사용하는 경우 구성 중에 피어 투 피어 트랜잭션 복제 토폴로지를 정지할 필요가 없습니다.<br /><br /> *SQL Server 되지 않은 게시에 대 한 구독에 대해서는 지원 되지 않습니다.*|  
|initialize from lsn|피어 투 피어 트랜잭션 복제 토폴로지에 노드를 추가할 때 사용합니다. 관련된 모든 트랜잭션이 새 노드에 복제되도록 하려면 @subscriptionlsn을 함께 사용합니다. 이 옵션은 게시된 테이블에 대한 스키마 및 초기 데이터가 구독자에 이미 있다고 가정합니다. 자세한 내용은 [Peer-to-Peer Transactional Replication](../../relational-databases/replication/transactional/peer-to-peer-transactional-replication.md)을 참조하세요.|  
  
> [!NOTE]  
>  시스템 테이블 및 데이터는 항상 전송됩니다.  
  
 [ @status=] '*status*'  
 동기화 상태입니다. *status* 는 **sysname**이며 기본값은 NULL입니다. 이 매개 변수를 명시적으로 설정하지 않으면 복제 시 자동으로 다음 값 중 하나로 설정됩니다.  
  
|값|설명|  
|-----------|-----------------|  
|active|구독이 초기화되고 변경 내용을 받아들일 준비가 되었습니다. 이 옵션은 *sync_type* 값이 none, initialize with backup 또는 replication support only 인 경우에 설정 됩니다.|  
|subscribed|구독을 초기화해야 합니다. 이 옵션은 *sync_type* 값이 automatic 인 경우에 설정 됩니다.|  
  
 [ @subscription_type=] '*subscription_type*'  
 구독 유형입니다. *subscription_type* 은 **nvarchar (4)** 이며 기본값은 push입니다. push 또는 pull이 될 수 있습니다. 밀어넣기 구독의 배포 에이전트는 배포자에 있으며 끌어오기 구독의 배포 에이전트는 구독자에 있습니다. *subscription_type* 를 가져와서 게시자에 게 알려진 명명 된 끌어오기 구독을 만들 수 있습니다. 자세한 내용은 [게시 구독](../../relational-databases/replication/subscribe-to-publications.md)을 참조하세요.  
  
> [!NOTE]  
>  익명 구독은 이 저장 프로시저를 사용할 필요가 없습니다.  
  
 [ @update_mode=] '*update_mode*'  
 업데이트의 유형입니다. *update_mode* 은 **nvarchar (30)** 이며 다음 값 중 하나일 수 있습니다.  
  
|값|설명|  
|-----------|-----------------|  
|read only(기본값)|구독이 읽기 전용입니다. 구독자의 변경 내용이 게시자에 전달되지 않습니다.|  
|sync tran|즉시 업데이트 구독에 대한 지원을 설정합니다. Oracle 게시자에 대해서는 지원되지 않습니다.|  
|queued tran|지연 업데이트 구독을 설정합니다. 구독자에서 데이터를 수정하고 큐에 저장한 후 게시자에 전파할 수 있습니다. Oracle 게시자에 대해서는 지원되지 않습니다.|  
|failover|즉시 업데이트를 기본으로 사용하고 장애 조치(Failover)로 지연 업데이트를 사용합니다. 구독자에서 데이터를 수정하고 게시자에 즉시 전파할 수 있습니다. 게시자와 구독자가 연결되지 않은 경우 구독자와 게시자가 다시 연결될 때까지 구독자의 데이터 수정 내용이 큐에 저장되도록 업데이트 모드를 변경할 수 있습니다. Oracle 게시자에 대해서는 지원되지 않습니다.|  
|queued failover|구독을 지연 업데이트 구독으로 설정하며 즉시 업데이트 모드로 변경할 수 있는 기능을 포함합니다. 구독자에서 데이터를 수정한 후 구독자와 게시자가 연결될 때까지 수정 내용을 큐에 저장할 수 있습니다. 지속적 연결이 설정되는 경우 업데이트 모드를 즉시 업데이트로 변경할 수 있습니다. Oracle 게시자에 대해서는 지원되지 않습니다.|  
  
 구독 중인 게시에서 DTS를 허용 하는 경우에는 synctran 및 큐에 대기 된 tran 값을 사용할 수 없습니다.  
  
 [ @loopback_detection=] '*loopback_detection*'  
 배포 에이전트가 구독자에서 발생한 트랜잭션을 다시 구독자에게 보낼지 여부를 지정합니다. *loopback_detection* 은 **nvarchar (5)** 이며 다음 값 중 하나일 수 있습니다.  
  
|값|설명|  
|-----------|-----------------|  
|true|배포 에이전트가 구독자에서 발생한 트랜잭션을 다시 구독자에게 보내지 않습니다. 양방향 트랜잭션 복제에 사용됩니다. 자세한 내용은 [Bidirectional Transactional Replication](../../relational-databases/replication/transactional/bidirectional-transactional-replication.md)를 참조하세요.|  
|false|배포 에이전트가 구독자에서 발생한 트랜잭션을 다시 구독자에게 보냅니다.|  
|NULL(기본값)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 구독자에 대해서는 자동으로 true로 설정되고 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 이외 구독자에 대해서는 자동으로 false로 설정됩니다.|  
  
 [ @frequency_type=] *frequency_type*  
 배포 태스크를 예약하는 빈도입니다. *frequency_type* 은 int 이며 다음 값 중 하나일 수 있습니다.  
  
|값|설명|  
|-----------|-----------------|  
|1|한 번|  
|2|요청 시|  
|4|일별|  
|8|매주|  
|16|매월|  
|32|매월 상대적|  
|64 (기본값)|자동 시작|  
|128|되풀이|  
  
 [ @frequency_interval=] *frequency_interval*  
 *Frequency_type*에 의해 설정 된 빈도에 적용 되는 값입니다. *frequency_interval* 은 **int**이며 기본값은 NULL입니다.  
  
 [ @frequency_relative_interval=] *frequency_relative_interval*  
 배포 에이전트의 날짜입니다. 이 매개 변수는 *frequency_type* 이 32 (매월 상대적)로 설정 된 경우에 사용 됩니다. *frequency_relative_interval* 은 **int**이며 다음 값 중 하나일 수 있습니다.  
  
|값|설명|  
|-----------|-----------------|  
|1|첫째|  
|2|Second|  
|4|셋째|  
|8|넷째|  
|16|마지막|  
|NULL(기본값)||  
  
 [ @frequency_recurrence_factor=] *frequency_recurrence_factor*  
 *Frequency_type*에서 사용 하는 되풀이 비율입니다. *frequency_recurrence_factor* 은 **int**이며 기본값은 NULL입니다.  
  
 [ @frequency_subday=] *frequency_subday*  
 정의된 기간 동안 다시 예약하는 빈도(분)입니다. *frequency_subday* 은 **int**이며 다음 값 중 하나일 수 있습니다.  
  
|값|설명|  
|-----------|-----------------|  
|1|한 번|  
|2|Second|  
|4|Minute|  
|8|Hour|  
|NULL||  
  
 [ @frequency_subday_interval=] *frequency_subday_interval*  
 *Frequency_subday*에 대 한 간격입니다. *frequency_subday_interval* 은 **int**이며 기본값은 NULL입니다.  
  
 [ @active_start_time_of_day=] *active_start_time_of_day*  
 하루 중에서 배포 에이전트가 처음으로 실행되도록 예약된 시간이며 HHMMSS 형식으로 표시됩니다. *active_start_time_of_day* 은 **int**이며 기본값은 NULL입니다.  
  
 [ @active_end_time_of_day=] *active_end_time_of_day*  
 하루 중에서 배포 에이전트가 마지막으로 실행되도록 예약된 시간이며 HHMMSS 형식으로 표시됩니다. *active_end_time_of_day* 은 **int**이며 기본값은 NULL입니다.  
  
 [ @active_start_date=] *active_start_date*  
 배포 에이전트가 처음으로 실행되도록 예약된 날짜이며 YYYYMMDD 형식으로 표시됩니다. *active_start_date* 은 **int**이며 기본값은 NULL입니다.  
  
 [ @active_end_date=] *active_end_date*  
 배포 에이전트가 마지막으로 실행되도록 예약된 날짜이며 YYYYMMDD 형식으로 표시됩니다. *active_end_date* 은 **int**이며 기본값은 NULL입니다.  
  
 [ @optional_command_line=] '*optional_command_line*'  
 실행할 선택적 명령 프롬프트입니다. *optional_command_line* 는 **nvarchar (4000)** 이며 기본값은 NULL입니다.  
  
 [ @reserved=] '*reserved*'  
 [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
 [ @enabled_for_syncmgr=] '*enabled_for_syncmgr*'  
 Windows 동기화 관리자를 통해 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 구독을 동기화 할 수 있는지 여부입니다. *enabled_for_syncmgr* 은 **nvarchar (5)** 이며 기본값은 FALSE입니다. false인 경우 구독이 Windows 동기화 관리자에 등록되지 않습니다. true인 경우에는 구독이 Windows 동기화 관리자에 등록되며 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]를 시작하지 않고 구독을 동기화할 수 있습니다. Oracle 게시자에 대해서는 지원되지 않습니다.  
  
 [ @offloadagent= ] '*remote_agent_activation*'  
 에이전트를 원격으로 활성화할 수 있음을 나타냅니다. *remote_agent_activation* 는 **bit** 이며 기본값은 0입니다.  
  
> [!NOTE]  
>  이 매개 변수는 더 이상 사용되지 않으며 이전 버전의 스크립트와의 호환성을 위해서만 유지 관리됩니다.  
  
 [ @offloadserver= ] '*remote_agent_server_name*'  
 원격 활성화에 사용할 서버의 네트워크 이름을 지정합니다. *remote_agent_server_name*는 **sysname**이며 기본값은 NULL입니다.  
  
 [ @dts_package_name= ] '*dts_package_name*'  
 DTS(데이터 변환 서비스) 패키지의 이름을 지정합니다. *dts_package_name* 는 **sysname** 이며 기본값은 NULL입니다. 예를 들어 DTSPub_Package의 패키지를 지정하려면 매개 변수가 `@dts_package_name = N'DTSPub_Package'`가 되어야 합니다. 이 매개 변수는 밀어넣기 구독에 사용할 수 있습니다. DTS 패키지 정보를 끌어오기 구독에 추가하려면 sp_addpullsubscription_agent를 사용하십시오.  
  
 [ @dts_package_password= ] '*dts_package_password*'  
 패키지의 암호를 지정합니다. *dts_package_password* 는 **sysname** 이며 기본값은 NULL입니다.  
  
> [!NOTE]  
>  *Dts_package_name* 가 지정 된 경우 암호를 지정 해야 합니다.  
  
 [ @dts_package_location= ] '*dts_package_location*'  
 패키지 위치를 지정합니다. *dts_package_location* 은 **nvarchar (12)** 이며 기본값은 배포자입니다. 패키지 위치는 distributor 또는 subscriber일 수 있습니다.  
  
 [ @distribution_job_name= ] '*distribution_job_name*'  
 [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
 [ @publisher= ] '*publisher*'  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 이외[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 게시자를 지정 합니다. *publisher* 는 **sysname**이며 기본값은 NULL입니다.  
  
> [!NOTE]  
>  게시자에 대해 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 게시자를 지정 하면 안 됩니다.  
  
 [ @backupdevicetype= ] '*backupdevicetype*'  
 백업에서 구독자를 초기화할 때 사용되는 백업 디바이스의 유형을 지정합니다. *backupdevicetype* 은 **nvarchar (20)** 이며 다음 값 중 하나일 수 있습니다.  
  
|값|설명|  
|-----------|-----------------|  
|logical(기본값)|백업 디바이스가 논리적 디바이스입니다.|  
|disk|백업 디바이스가 디스크 드라이브입니다.|  
|tape|백업 디바이스가 테이프 드라이브입니다.|  
  
 *backupdevicetype* 는 *sync_method*가 initialize_with_backup로 설정 된 경우에만 사용 됩니다.  
  
 [ @backupdevicename= ] '*backupdevicename*'  
 백업에서 구독자를 초기화할 때 사용되는 디바이스의 이름을 지정합니다. *backupdevicename* 이름은 **nvarchar (1000)** 이며 기본값은 NULL입니다.  
  
 [ @mediapassword= ] '*mediapassword*'  
 미디어를 포맷할 때 암호를 설정한 경우 미디어 세트의 암호를 지정합니다. *mediapassword* 는 **sysname**이며 기본값은 NULL입니다.  
  
> [!NOTE]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]  
  
 [ @password= ] '*password*'  
 백업을 만들 때 암호를 설정한 경우 백업의 암호를 지정합니다. *password*는 **sysname**이며 기본값은 NULL입니다.  
  
 [ @fileidhint= ] *fileidhint*  
 복원할 백업 세트의 서수 값을 식별합니다. *fileidhint* 은 **int**이며 기본값은 NULL입니다.  
  
 [ @unload= ] *unload*  
 백업으로 초기화를 완료한 후 테이프 백업 디바이스를 언로드할지 여부를 지정합니다. *unload* 는 **bit**이며 기본값은 1입니다. 1은 테이프가 언로드되기 야 함을 나타냅니다. *unload* 는 *backupdevicetype* 가 tape 인 경우에만 사용 됩니다.  
  
 [ @subscriptionlsn= ] *subscriptionlsn*  
 구독에서 피어 투 피어 트랜잭션 복제 토폴로지에 노드 변경 내용을 배달하기 시작할 LSN(로그 시퀀스 번호)을 지정합니다. 모든 관련 트랜잭션이 @sync_type 새 노드에 복제 되도록 하려면 initialize from lsn 값과 함께 사용 합니다. 자세한 내용은 [Peer-to-Peer Transactional Replication](../../relational-databases/replication/transactional/peer-to-peer-transactional-replication.md)을 참조하세요.  
  
 [ @subscriptionstreams= ] *subscriptionstreams*  
 단일 스레드를 사용할 때 나타나는 여러 가지 트랜잭션 특징을 유지하면서 변경 내용의 일괄 처리를 구독자에 대해 병렬로 적용하기 위해 배포 에이전트당 허용된 연결 수입니다. *subscriptionstreams* 은 **tinyint**이며 기본값은 NULL입니다. 1에서 64 사이의 값 범위가 지원됩니다. 이외 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 구독자, Oracle 게시자 또는 피어 투 피어 구독에 대해서는이 매개 변수가 지원 되지 않습니다. 구독 스트림을 사용할 때마다 agent_id가 NULL로 설정된 상태로 추가 행이 msreplication_subscriptions 테이블(스트림당 1개)에 추가됩니다.  
  
> [!NOTE]  
>  Subscriptionstreams는 [!INCLUDE[tsql](../../includes/tsql-md.md)]을 제공하도록 구성된 아티클에 대해서는 작동하지 않습니다. subscriptionstreams를 사용하려면 대신 저장 프로시저 호출을 제공하도록 아티클을 구성하십시오.  
  
 [ @subscriber_type=] *subscriber_type*  
 구독자의 유형입니다. *subscriber_type* 은 **tinyint**이며 다음 값 중 하나일 수 있습니다.  
  
|값|설명|  
|-----------|-----------------|  
|0(기본값)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]구독자|  
|1|ODBC 데이터 원본 서버|  
|2|[!INCLUDE[msCoName](../../includes/msconame-md.md)] Jet 데이터베이스|  
|3|OLE DB 공급자|  
  
 [ @memory_optimized=] *memory_optimized*  
 구독에서 메모리 액세스에 최적화 된 테이블을 지원함을 나타냅니다. *memory_optimized* 은 **bit**입니다. 여기서 1은 true이 고 구독은 메모리 액세스에 최적화 된 테이블을 지원 합니다.  
  
## <a name="return-code-values"></a>반환 코드 값  
 0(성공) 또는 1(실패)  
  
## <a name="remarks"></a>설명  
 sp_addsubscription은 스냅샷 복제 및 트랜잭션 복제에 사용됩니다.  
  
 sysadmin 고정 서버 역할의 멤버가 밀어넣기 구독을 만들기 위해 sp_addsubscription을 실행할 경우 배포 에이전트 작업이 암시적으로 생성되어 SQL Server 에이전트 서비스 계정에서 실행됩니다. [Sp_addpushsubscription_agent](../../relational-databases/system-stored-procedures/sp-addpushsubscription-agent-transact-sql.md) 를 실행 하 고 및 @job_login @job_password에 대 한 다른 에이전트 특정 Windows 계정의 자격 증명을 지정 하는 것이 좋습니다. 자세한 내용은 [복제 에이전트 보안 모델](../../relational-databases/replication/security/replication-agent-security-model.md)을 참조하세요.  
  
 sp_addsubscription은 ODBC 및 OLE DB 구독자가 다음과 같은 게시에 액세스하는 것을 막습니다.  
  
-   [Sp_addpublication](../../relational-databases/system-stored-procedures/sp-addpublication-transact-sql.md)에 대 한 호출에서 네이티브 *sync_method* 를 사용 하 여를 만들었습니다.  
  
-   *Pre_creation_cmd* 매개 변수 값이 3 (truncate) 인 [sp_addarticle](../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md) 저장 프로시저를 사용 하 여 게시에 추가 된 아티클을 포함 합니다.  
  
-   *Update_mode* 를 sync tran으로 설정 하려고 시도 합니다.  
  
-   매개 변수가 있는 문을 사용하도록 구성된 아티클이 있는 게시  
  
 또한 게시에 *allow_queued_tran* 옵션이 true로 설정 되어 있는 경우 (게시자에 적용할 수 있을 때까지 구독자에서 변경 내용 대기 가능) 아티클의 타임 스탬프 열은 **타임 스탬프로**스크립팅 됩니다. 해당 열에 대 한 변경 내용은 구독자로 전송 됩니다. 구독자는 타임스탬프 열 값을 생성하고 업데이트합니다. ODBC 또는 OLE DB 구독자의 경우 *allow_queued_tran* 이 true로 설정 된 게시를 구독 하 고 타임 스탬프 열이 있는 아티클을 구독 하려고 하면 sp_addsubscription가 실패 합니다.  
  
 구독에서 DTS 패키지를 사용 하지 않는 경우 *allow_transformable_subscriptions*로 설정 된 게시를 구독할 수 없습니다. 게시의 테이블을 DTS 구독과 DTS가 아닌 구독 양쪽 모두에 복제해야 할 경우 각 구독 유형당 하나씩 두 개의 게시를 만들어야 합니다.  
  
 **sync_type** 옵션 *replication support only*, *initialize with backup*또는 *initialize from lsn*을 선택할 때는 설치 스크립트가 배포 데이터베이스에 기록되도록 **sp_addsubscription**을 실행한 후 로그 판독기 에이전트를 실행해야 합니다. 로그 판독기 에이전트는 **sysadmin** 고정 서버 역할의 멤버인 계정으로 실행되어야 합니다. **sync_type** 옵션이 *Automatic*으로 설정된 경우 특별한 로그 판독기 에이전트 동작이 필요하지 않습니다.  
  
## <a name="permissions"></a>사용 권한  
 sysadmin 고정 서버 역할 또는 db_owner 고정 데이터베이스 역할의 멤버만 sp_addsubscription을 실행할 수 있습니다. 끌어오기 구독의 경우 게시 액세스 목록의 로그인이 있는 사용자는 sp_addsubscription을 실행할 수 있습니다.  
  
## <a name="example"></a>예제  
 [!code-sql[HowTo#sp_addtranpushsubscription_agent](../../relational-databases/replication/codesnippet/tsql/sp-addsubscription-trans_1.sql)]  
  
## <a name="see-also"></a>관련 항목  
 [ssSDSFull](../../relational-databases/replication/create-a-push-subscription.md)   
 [SQL Server 이외 구독자에 대한 구독 만들기](../../relational-databases/replication/create-a-subscription-for-a-non-sql-server-subscriber.md)   
 [게시 구독](../../relational-databases/replication/subscribe-to-publications.md)   
 [sp_addpushsubscription_agent &#40;transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-addpushsubscription-agent-transact-sql.md)   
 [sp_changesubstatus &#40;transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-changesubstatus-transact-sql.md)   
 [sp_dropsubscription &#40;transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-dropsubscription-transact-sql.md)   
 [sp_helpsubscription &#40;transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-helpsubscription-transact-sql.md)   
 [시스템 저장 프로시저&#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
