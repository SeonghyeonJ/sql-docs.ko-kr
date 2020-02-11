---
title: sp_helpmergepullsubscription (Transact-sql) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_helpmergepullsubscription
- sp_helpmergepullsubscription_TSQL
helpviewer_keywords:
- sp_helpmergepullsubscription
ms.assetid: 6f3125f3-0dfa-40bd-b725-8aa1591234f6
author: stevestein
ms.author: sstein
ms.openlocfilehash: c92ea8e2f172d9cb5b40559c2a7b77a60153065b
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68137708"
---
# <a name="sp_helpmergepullsubscription-transact-sql"></a>sp_helpmergepullsubscription(Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  구독자에 있는 끌어오기 구독에 대한 정보를 반환합니다. 이 저장 프로시저는 구독 데이터베이스의 구독자에서 실행됩니다.  
  
 ![항목 링크 아이콘](../../database-engine/configure-windows/media/topic-link.gif "항목 링크 아이콘") [Transact-SQL 구문 표기 규칙](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>구문  
  
```  
  
sp_helpmergepullsubscription [ [ @publication=] 'publication']  
    [ , [ @publisher=] 'publisher']  
    [ , [ @publisher_db=] 'publisher_db']  
    [ , [ @subscription_type=] 'subscription_type']  
```  
  
## <a name="argument"></a>인수  
`[ @publication = ] 'publication'`게시의 이름입니다. *게시* 는 **sysname**이며 기본값은 **%** 입니다. *게시가* 인 **%** 경우 현재 데이터베이스의 모든 병합 게시 및 구독에 대 한 정보가 반환 됩니다.  
  
`[ @publisher = ] 'publisher'`게시자의 이름입니다. *publisher*는 **sysname**이며 기본값은 **%** 입니다.  
  
`[ @publisher_db = ] 'publisher_db'`게시자 데이터베이스의 이름입니다. *publisher_db*는 **sysname**이며 기본값은 **%** 입니다.  
  
`[ @subscription_type = ] 'subscription_type'`끌어오기 구독을 표시할지 여부입니다. *subscription_type*은 **nvarchar (10)** 이며 기본값은 **' pull '** 입니다. 유효한 값은 **' push '**, **' pull '** 또는 **' both '** 입니다.  
  
## <a name="result-sets"></a>결과 집합  
  
|열 이름|데이터 형식|Description|  
|-----------------|---------------|-----------------|  
|**subscription_name**|**nvarchar (1000)**|구독의 이름입니다.|  
|**게시물**|**sysname**|게시의 이름입니다.|  
|**발행자**|**sysname**|게시자의 이름입니다.|  
|**publisher_db**|**sysname**|게시자 데이터베이스의 이름입니다.|  
|**구독자**|**sysname**|구독자의 이름입니다.|  
|**subscription_db**|**sysname**|구독 데이터베이스의 이름입니다.|  
|**업무**|**int**|구독 상태입니다.<br /><br /> **0** = 비활성 구독<br /><br /> **1** = 활성 구독<br /><br /> **2** = 삭제 된 구독<br /><br /> **3** = 분리 된 구독<br /><br /> **4** = 연결 된 구독<br /><br /> **5** = 구독이 업로드를 사용 하 여 다시 초기화 되도록 표시 되었습니다.<br /><br /> **6** = 구독을 연결 하지 못했습니다.<br /><br /> **7** = 백업에서 구독 복원 됨|  
|**subscriber_type**|**int**|구독자의 유형입니다.<br /><br /> **1** = 전역<br /><br /> **2** = 로컬<br /><br /> **3** = 익명|  
|**subscription_type**|**int**|구독 유형:<br /><br /> **0** = 푸시<br /><br /> **1** = 끌어오기<br /><br /> **2** = 익명|  
|**우선 순위**|**float (8)**|구독 우선 순위입니다. 값은 **100.00**미만 이어야 합니다.|  
|**sync_type**|**tinyint**|구독 동기화 유형입니다.<br /><br /> **1** = 자동<br /><br /> **2** = 스냅숏이 사용 되지 않습니다.|  
|**한**|**nvarchar(255)**|해당 끌어오기 구독에 관한 간략한 설명입니다.|  
|**merge_jobid**|**binary (16)**|병합 에이전트의 작업 ID입니다.|  
|**enabled_for_syncmgr**|**int**|
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] 동기화 관리자를 통해 구독을 동기화할 수 있는지 여부입니다.|  
|**last_updated**|**nvarchar (26)**|병합 에이전트가 구독의 동기화를 마지막으로 성공한 시각입니다.|  
|**publisher_login**|**sysname**|게시자 로그인 이름입니다.|  
|**publisher_password**|**sysname**|게시자 암호입니다.|  
|**publisher_security_mode**|**int**|게시자의 보안 모드를 지정합니다.<br /><br /> **** =  0[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인증<br /><br /> **1** = Windows 인증|  
|**총판**|**sysname**|배포자의 이름입니다.|  
|**distributor_login**|**sysname**|배포자의 로그인 이름입니다.|  
|**distributor_password**|**sysname**|배포자 암호입니다.|  
|**distributor_security_mode**|**int**|배포자의 보안 모드를 지정합니다.<br /><br /> **** =  0[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인증<br /><br /> **1** = Windows 인증|  
|**ftp_address**|**sysname**|이전 버전과의 호환성을 위해서만 사용 가능합니다. 배포자용 FTP(파일 전송 프로토콜) 서비스의 네트워크 주소입니다.|  
|**ftp_port**|**int**|이전 버전과의 호환성을 위해서만 사용 가능합니다. 배포자용 FTP 서비스의 포트 번호입니다.|  
|**ftp_login**|**sysname**|이전 버전과의 호환성을 위해서만 사용 가능합니다. FTP 서비스 연결에 사용되는 사용자 이름입니다.|  
|**ftp_password**|**sysname**|이전 버전과의 호환성을 위해서만 사용 가능합니다. FTP 서비스에 연결할 때 사용되는 사용자 암호입니다.|  
|**alt_snapshot_folder**|**nvarchar(255)**|기본 위치가 아니거나 기본 위치에 추가된 위치일 경우, 스냅샷 폴더가 저장되는 위치입니다.|  
|**working_directory**|**nvarchar(255)**|해당 옵션이 지정된 경우 FTP를 사용하여 스냅샷 파일이 전송될 디렉터리의 정규화된 경로입니다.|  
|**use_ftp**|**bit**|구독이 인터넷을 통해 게시를 구독하고 있으며 FTP 주소 속성이 구성되었습니다. **0**인 경우 구독은 FTP를 사용 하지 않습니다. **1**인 경우 구독은 FTP를 사용 합니다.|  
|**offload_agent**|**bit**|에이전트가 활성화되어 원격으로 실행될 수 있는지 여부를 지정합니다. **0**인 경우 에이전트를 원격으로 활성화할 수 없습니다.|  
|**offload_server**|**sysname**|원격 활성화에 필요한 서버의 이름입니다.|  
|**use_interactive_resolver**|**int**|조정 상태 동안 대화형 해결 프로그램의 사용 여부를 반환합니다. **0**인 경우 대화형 해결 프로그램을 사용 하지 않습니다.|  
|**subid**|**uniqueidentifier**|구독자의 ID입니다.|  
|**dynamic_snapshot_location**|**nvarchar(255)**|스냅샷 파일을 저장한 폴더의 경로입니다.|  
|**last_sync_status**|**int**|동기화 상태입니다.<br /><br /> **1** = 시작 중<br /><br /> **2** = 성공<br /><br /> **3** = 진행 중<br /><br /> **4** = 유휴 상태<br /><br /> **5** = 이전 실패 후 다시 시도 하는 중<br /><br /> **6** = 실패<br /><br /> **7** = 유효성 검사 실패<br /><br /> **8** = 유효성 검사 통과<br /><br /> **9** = 종료 요청|  
|**last_sync_summary**|**sysname**|마지막 동기화 결과에 관한 설명입니다.|  
|**use_web_sync**|**bit**|HTTPS를 통해 구독을 동기화 할 수 있는지 여부를 지정 합니다. 여기서 값 **1** 은이 기능을 사용할 수 있음을 의미 합니다.|  
|**internet_url**|**nvarchar(260)**|웹 동기화를 위한 복제 수신기의 위치를 나타내는 URL입니다.|  
|**internet_login**|**nvarchar(128)**|기본 인증을 사용하여 웹 동기화를 호스팅하는 웹 서버에 연결할 때 병합 에이전트가 사용하는 로그인입니다.|  
|**internet_password**|**nvarchar (524)**|기본 인증을 사용하여 웹 동기화를 호스팅하는 웹 서버에 연결할 때 병합 에이전트가 사용하는 로그인 암호입니다.|  
|**internet_security_mode**|**int**|웹 동기화를 호스팅하는 웹 서버에 연결할 때 사용하는 인증 모드입니다. 값 **1** 은 Windows 인증을 의미 하 고, 값 **0** 은 인증 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 을 의미 합니다.|  
|**internet_timeout**|**int**|웹 동기화 요청이 만료되기 전까지의 시간(초)입니다.|  
|**n**|**nvarchar(128)**|매개 변수가 있는 행 필터의 WHERE 절에서이 함수를 사용 하는 경우 [HOST_NAME](../../t-sql/functions/host-name-transact-sql.md) 에 대해 오버 로드 된 값을 지정 합니다.|  
|**job_login**|**nvarchar(512)**|병합 에이전트가 실행 되는 Windows 계정으로, *도메인*\\*사용자 이름*형식으로 반환 됩니다.|  
|**job_password**|**sysname**|보안상의 이유로**\*\*\*\*\*항상\*"\*"\*이 반환\*** 됩니다.|  
  
## <a name="return-code-values"></a>반환 코드 값  
 **0** (성공) 또는 **1** (실패)  
  
## <a name="remarks"></a>설명  
 **sp_helpmergepullsubscription** 는 병합 복제에 사용 됩니다. 결과 집합에서 **last_updated** 반환 되는 날짜는 *YYYYMMDD hh: mm: ss. fff*로 지정 됩니다.  
  
## <a name="permissions"></a>사용 권한  
 **Sysadmin** 고정 서버 역할 및 **db_owner** 고정 데이터베이스 역할의 멤버만 **sp_helpmergepullsubscription**을 실행할 수 있습니다.  
  
## <a name="see-also"></a>참고 항목  
 [Transact-sql&#41;sp_addmergepullsubscription &#40;](../../relational-databases/system-stored-procedures/sp-addmergepullsubscription-transact-sql.md)   
 [Transact-sql&#41;sp_changemergepullsubscription &#40;](../../relational-databases/system-stored-procedures/sp-changemergepullsubscription-transact-sql.md)   
 [Transact-sql&#41;sp_dropmergepullsubscription &#40;](../../relational-databases/system-stored-procedures/sp-dropmergepullsubscription-transact-sql.md)   
 [복제 저장 프로시저&#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
