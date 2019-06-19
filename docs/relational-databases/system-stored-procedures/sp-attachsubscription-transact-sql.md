---
title: sp_attachsubscription (TRANSACT-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_attachsubscription
- sp_attachsubscription_TSQL
helpviewer_keywords:
- sp_attachsubscription
ms.assetid: b9bbda36-a46a-4327-a01e-9cd632e4791b
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 47e1eec1aaa8162565f481b2d82982781e1a3c8c
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62996103"
---
# <a name="spattachsubscription-transact-sql"></a>sp_attachsubscription(Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  기존 구독 데이터베이스를 임의의 구독자에 연결합니다. 이 저장 프로시저는 master 데이터베이스의 새 구독자에서 실행됩니다.  
  
> [!IMPORTANT]  
>  이 기능은 더 이상 사용되지 않으며 후속 릴리스에서 제거될 예정입니다. 새로운 개발 작업에서는 이 기능을 사용하면 안 됩니다. 매개 변수가 있는 필터를 사용하여 분할된 병합 게시의 경우 구독을 대량으로 초기화하는 작업을 간단하게 만들어 주는 분할된 스냅숏의 새 기능을 사용하는 것이 좋습니다. 자세한 내용은 [Snapshots for Merge Publications with Parameterized Filters](../../relational-databases/replication/create-a-snapshot-for-a-merge-publication-with-parameterized-filters.md)을 참조하세요. 분할되지 않은 게시의 경우 백업을 사용하여 구독을 초기화할 수 있습니다. 자세한 내용은 [스냅숏 없이 트랜잭션 구독 초기화](../../relational-databases/replication/initialize-a-transactional-subscription-without-a-snapshot.md)에서 수동으로 구독을 초기화하는 방법에 대해 설명합니다.  
  
 ![항목 링크 아이콘](../../database-engine/configure-windows/media/topic-link.gif "항목 링크 아이콘") [Transact-SQL 구문 규칙](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>구문  
  
```  
  
sp_attachsubscription [ @dbname = ] 'dbname'  
        , [ @filename = ] 'filename'  
    [ , [ @subscriber_security_mode = ] 'subscriber_security_mode' ]  
    [ , [ @subscriber_login = ] 'subscriber_login' ]  
    [ , [ @subscriber_password = ] 'subscriber_password' ]  
    [ , [ @distributor_security_mode = ] distributor_security_mode ]   
    [ , [ @distributor_login = ] 'distributor_login' ]   
    [ , [ @distributor_password = ] 'distributor_password' ]   
    [ , [ @publisher_security_mode = ] publisher_security_mode ]   
    [ , [ @publisher_login = ] 'publisher_login' ]   
    [ , [ @publisher_password = ] 'publisher_password' ]   
    [ , [ @job_login = ] 'job_login' ]   
    [ , [ @job_password = ] 'job_password' ]   
    [ , [ @db_master_key_password = ] 'db_master_key_password' ]  
```  
  
## <a name="arguments"></a>인수  
`[ @dbname = ] 'dbname'` 대상 구독 데이터베이스 이름으로 지정 하는 문자열이입니다. *dbname* 됩니다 **sysname**, 기본값은 없습니다.  
  
`[ @filename = ] 'filename'` 이름 및 주 MDF의 실제 위치 (**마스터** 데이터 파일). *filename* 됩니다 **nvarchar(260)** , 기본값은 없습니다.  
  
`[ @subscriber_security_mode = ] 'subscriber_security_mode'` 동기화 시 구독자에 연결할 때 사용 하 여 구독자의 보안 모드가입니다. *subscriber_security_mode* 됩니다 **int**, 기본값은 NULL입니다.  
  
> [!NOTE]  
>  Windows 인증을 사용해야 합니다. 하는 경우 *subscriber_security_mode* 아닙니다 **1** (Windows 인증) 오류가 반환 됩니다.  
  
`[ @subscriber_login = ] 'subscriber_login'` 동기화 시 구독자에 연결할 때 사용할 구독자 로그인 이름이입니다. *subscriber_login* 됩니다 **sysname**, 기본값은 NULL입니다.  
  
> [!NOTE]  
>  이 매개 변수는 더 이상 사용되지 않으며 이전 버전 스크립트와의 호환성을 위해서만 유지 관리됩니다. 하는 경우 *subscriber_security_mode* 아닙니다 **1** 하 고 *subscriber_login* 는 지정 하면 오류가 반환 됩니다.  
  
`[ @subscriber_password = ] 'subscriber_password'` 구독자 암호가입니다. *subscriber_password* 됩니다 **sysname**, 기본값은 NULL입니다.  
  
> [!NOTE]  
>  이 매개 변수는 더 이상 사용되지 않으며 이전 버전 스크립트와의 호환성을 위해서만 유지 관리됩니다. 하는 경우 *subscriber_security_mode* 아닙니다 **1** 하 고 *subscriber_password* 는 지정 하면 오류가 반환 됩니다.  
  
`[ @distributor_security_mode = ] distributor_security_mode` 동기화 시 배포자에 연결할 때 사용할 보안 모드가입니다. *distributor_security_mode* 됩니다 **int**, 기본값은 **0**합니다. **0** 지정 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인증 합니다. **1** Windows 인증을 지정 합니다. [!INCLUDE[ssNoteWinAuthentication](../../includes/ssnotewinauthentication-md.md)]  
  
`[ @distributor_login = ] 'distributor_login'` 동기화 시 배포자에 연결할 때 사용할 배포자 로그인이입니다. *distributor_login* 필요한 경우 *distributor_security_mode* 로 설정 되어 **0**합니다. *distributor_login* 됩니다 **sysname**, 기본값은 NULL입니다.  
  
`[ @distributor_password = ] 'distributor_password'` 배포자 암호가입니다. *distributor_password* 필요한 경우 *distributor_security_mode* 로 설정 되어 **0**합니다. *distributor_password* 됩니다 **sysname**, 기본값은 NULL입니다. 변수의 *distributor_password* 120 미만의 유니코드 문자 여야 합니다.  
  
> [!IMPORTANT]  
>  빈 암호를 사용하지 마세요. 강력한 암호를 사용하세요. 가능한 경우 런타임 시 사용자에게 보안 자격 증명을 입력하라는 메시지가 표시됩니다. 자격 증명을 스크립트 파일에 저장해야 하는 경우에는 파일에 무단으로 액세스하지 못하도록 보안을 설정해야 합니다.  
  
`[ @publisher_security_mode = ] publisher_security_mode` 동기화 시 게시자에 연결할 때 사용할 보안 모드가입니다. *publisher_security_mode* 됩니다 **int**, 기본값은 **1**합니다. 하는 경우 **0**, 지정 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인증 합니다. 하는 경우 **1**, Windows 인증을 지정 합니다. [!INCLUDE[ssNoteWinAuthentication](../../includes/ssnotewinauthentication-md.md)]  
  
`[ @publisher_login = ] 'publisher_login'` 동기화 시 게시자에 연결할 때 사용할 로그인이입니다. *publisher_login* 됩니다 **sysname**, 기본값은 NULL입니다.  
  
`[ @publisher_password = ] 'publisher_password'` 게시자에 연결할 때 암호가 사용 됩니다. *publisher_password* 됩니다 **sysname**, 기본값은 NULL입니다. 변수의 *publisher_password* 120 미만의 유니코드 문자 여야 합니다.  
  
> [!IMPORTANT]  
>  빈 암호를 사용하지 마세요. 강력한 암호를 사용하세요. 가능한 경우 런타임 시 사용자에게 보안 자격 증명을 입력하라는 메시지가 표시됩니다. 자격 증명을 스크립트 파일에 저장해야 하는 경우에는 파일에 무단으로 액세스하지 못하도록 보안을 설정해야 합니다.  
  
`[ @job_login = ] 'job_login'` 에이전트가 실행 되는 Windows 계정의 로그인이입니다. *job_login* 됩니다 **nvarchar(257)** , 기본값은 없습니다. 이 Windows 계정은 에이전트가 배포자에 연결할 때 항상 사용됩니다.  
  
`[ @job_password = ] 'job_password'` 에이전트가 실행 되는 Windows 계정의 암호가입니다. *job_password* 됩니다 **sysname**, 기본값은 없습니다. 변수의 *job_password* 120 미만의 유니코드 문자 여야 합니다.  
  
> [!IMPORTANT]  
>  가능한 경우 런타임 시 사용자에게 보안 자격 증명을 입력하라는 메시지가 표시됩니다. 자격 증명을 스크립트 파일에 저장해야 하는 경우에는 파일에 무단으로 액세스하지 못하도록 보안을 설정해야 합니다.  
  
`[ @db_master_key_password = ] 'db_master_key_password'` 사용자 정의 데이터베이스 마스터 키의 암호가입니다. *db_master_key_password* 됩니다 **nvarchar(524)** , 기본값은 NULL입니다. 하는 경우 *db_master_key_password* 지정 하지 않으면 기존 데이터베이스 마스터 키를 삭제 하 고 다시 생성 됩니다.  
  
> [!IMPORTANT]  
>  가능한 경우 런타임 시 사용자에게 보안 자격 증명을 입력하라는 메시지가 표시됩니다. 자격 증명을 스크립트 파일에 저장해야 하는 경우에는 파일에 무단으로 액세스하지 못하도록 보안을 설정해야 합니다.  
  
## <a name="return-code-values"></a>반환 코드 값  
 **0** (성공) 또는 **1** (실패)  
  
## <a name="remarks"></a>Remarks  
 **sp_attachsubscription** 스냅숏 복제, 트랜잭션 복제 및 병합 복제에 사용 됩니다.  
  
 게시 보존 기간이 만료된 경우에는 구독을 게시에 연결할 수 없습니다. 보존 기간이 경과된 구독을 지정하면 구독을 연결할 때 또는 구독을 처음으로 동기화할 때 오류가 발생합니다. 게시 보존 기간을 사용 하 여 게시 **0** (제한 없음)은 무시 됩니다.  
  
## <a name="permissions"></a>사용 권한  
 멤버는 **sysadmin** 고정된 서버 역할을 실행할 수 있습니다 **sp_attachsubscription**합니다.  
  
## <a name="see-also"></a>관련 항목  
 [시스템 저장 프로시저&#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
