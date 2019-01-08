---
title: sp_helpdistributor (TRANSACT-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_helpdistributor_TSQL
- sp_helpdistributor
helpviewer_keywords:
- sp_helpdistributor
ms.assetid: 37b0983e-3b69-4f0f-977e-20efce0a0b97
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 63441a20a5ac4f6faed366c06fc55638073b09f4
ms.sourcegitcommit: 37310da0565c2792aae43b3855bd3948fd13e044
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/18/2018
ms.locfileid: "53591397"
---
# <a name="sphelpdistributor-transact-sql"></a>sp_helpdistributor(Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  배포자, 배포 데이터베이스, 작업 디렉터리에 대 한 정보를 나열 하 고 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 사용자 계정입니다. 이 저장 프로시저는 게시 데이터베이스를 포함한 모든 데이터베이스의 게시자에서 실행됩니다.  
  
 ![항목 링크 아이콘](../../database-engine/configure-windows/media/topic-link.gif "항목 링크 아이콘") [Transact-SQL 구문 규칙](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>구문  
  
```  
  
sp_helpdistributor [ [ @distributor= ] 'distributor' OUTPUT ]  
    [ , [ @distribdb= ] 'distribdb' OUTPUT ]  
    [ , [ @directory= ] 'directory' OUTPUT ]  
    [ , [ @account= ] 'account' OUTPUT ]  
    [ , [ @min_distretention= ] min_distretention OUTPUT ]  
    [ , [ @max_distretention= ] max_distretention OUTPUT ]  
    [ , [ @history_retention= ] history_retention OUTPUT ]  
    [ , [ @history_cleanupagent= ] 'history_cleanupagent' OUTPUT ]  
    [ , [ @distrib_cleanupagent = ] 'distrib_cleanupagent' OUTPUT ]  
    [ , [ @publisher = ] 'publisher' ]   
    [ , [ @local = ] 'local' ]  
    [ , [ @rpcsrvname= ] 'rpcsrvname' OUTPUT ]  
    [ , [ @publisher_type = ] 'publisher_type' OUTPUT ]  
```  
  
## <a name="arguments"></a>인수  
 [  **@distributor=**] **'**_배포자_**'** 출력  
 배포자의 이름입니다. 배포자가 **sysname**, 기본값은 **%**, 결과 집합을 반환 하는 유일한 값입니다.  
  
 [  **@distribdb=**] **'**_distribdb_**'** 출력  
 배포 데이터베이스의 이름입니다. *distribdb* 은 **sysname**, 기본값은 **%**, 결과 집합을 반환 하는 유일한 값입니다.  
  
 [  **@directory=**] **'**_디렉터리_**'** 출력  
 작업 디렉터리입니다. *디렉터리* 은 **nvarchar(255)**, 기본값은 **%**, 결과 집합을 반환 하는 유일한 값입니다.  
  
 [  **@account=**] **'**_계정_**' 출력**  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 사용자 계정입니다. *계정*은 **nvarchar(255)**, 기본값은 **%**, 결과 집합을 반환 하는 유일한 값입니다.  
  
 [  **@min_distretention=**] _min_distretention_**출력**  
 최소 배포 보존 기간(시간)입니다. *min_distretention* 됩니다 **int**, 기본값은 **-1**합니다.  
  
 [  **@max_distretention=**] _max_distretention_**출력**  
 최대 배포 보존 기간(시간)입니다. *max_distretention* 됩니다 **int**, 기본값은 **-1**합니다.  
  
 [  **@history_retention=**] _history_retention_**출력**  
 기록 보존 기간(시간)입니다. *history_retention* 됩니다 **int**, 기본값은 **-1**합니다.  
  
 [  **@history_cleanupagent=**] **'**_history_cleanupagent_**' 출력**  
 기록 정리 에이전트의 이름입니다. *history_cleanupagent* 은 **nvarchar(100)**, 기본값은 **%**, 결과 집합을 반환 하는 유일한 값입니다.  
  
 [  **@distrib_cleanupagent =**] **'**_distrib_cleanupagent_**' 출력**  
 배포 정리 에이전트의 이름입니다. *distrib_cleanupagent* 은 **nvarchar(100)**, 기본값은 **%**, 결과 집합을 반환 하는 유일한 값입니다.  
  
 [  **@publisher=**] **'**_게시자_**'**  
 게시자의 이름입니다. *게시자* 됩니다 **sysname**, 기본값은 NULL입니다.  
  
 [  **@local=**] **'**_로컬_**'**  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]가 로컬 서버 값을 가져야 하는지 여부입니다. *로컬* 됩니다 **nvarchar(5)**, 기본값은 NULL입니다.  
  
 [  **@rpcsrvname=**] **'**_rpcsrvname_**' 출력**  
 원격 프로시저 호출을 실행하는 서버의 이름입니다. *rpcsrvname* 은 **sysname**, 기본값은 **%**, 결과 집합을 반환 하는 유일한 값입니다.  
  
 [ **@publisher_type**=] **'**_publisher_type_**' 출력**  
 게시자의 게시자 유형입니다. *publisher_type* 은 **sysname**, 기본값은 **%**, 결과 집합을 반환 하는 유일한 값입니다.  
  
## <a name="result-sets"></a>결과 집합  
  
|열 이름|데이터 형식|Description|  
|-----------------|---------------|-----------------|  
|**배포자**|**sysname**|배포자의 이름입니다.|  
|**배포 데이터베이스**|**sysname**|배포 데이터베이스의 이름입니다.|  
|**디렉터리**|**nvarchar(255)**|작업 디렉터리의 이름입니다.|  
|**계정**|**nvarchar(255)**|Windows 사용자 계정의 이름입니다.|  
|**최소 배포 보존**|**int**|최소 배포 보존 기간입니다.|  
|**최대 배포 보존**|**int**|최대 배포 보존 기간입니다.|  
|**기록 보존**|**int**|기록 보존 기간입니다.|  
|**기록 정리 에이전트**|**nvarchar(100)**|기록 정리 에이전트의 이름입니다.|  
|**배포 정리 에이전트**|**nvarchar(100)**|배포 정리 에이전트의 이름입니다.|  
|**rpc 서버 이름**|**sysname**|원격 또는 로컬 배포자의 이름입니다.|  
|**rpc 로그인 이름**|**sysname**|원격 배포자로의 원격 프로시저 호출에 사용하는 로그인입니다.|  
|**게시자 유형**|**sysname**|게시자의 유형으로 다음 중 하나일 수 있습니다.<br /><br /> **MSSQLSERVER**<br /><br /> **ORACLE**<br /><br /> **ORACLE GATEWAY**|  
  
## <a name="return-code-values"></a>반환 코드 값  
 **0** (성공) 또는 **1** (실패)  
  
## <a name="remarks"></a>Remarks  
 **sp_helpdistributor** 모든 유형의 복제에 사용 됩니다.  
  
 하나 이상의 출력 매개 변수를 실행할 때 지정 된 경우 **sp_helpdistributor**, NULL로 설정 하는 모든 출력 매개 변수 종료 시 값이 할당 됩니다 및 결과 집합이 반환 됩니다. 출력 매개 변수가 지정되지 않으면 결과 집합이 반환됩니다.  
  
## <a name="permissions"></a>사용 권한  
 다음 결과 집합 열 또는 출력 매개 변수가의 멤버에 게 반환 됩니다 합니다 **sysadmin** 고정된 서버 역할 및 **db_owner** 게시 데이터베이스의 고정된 데이터베이스 역할:  
  
|결과 집합 열|출력 매개 변수|  
|-----------------------|----------------------|  
|account|**@account**|  
|min distrib retention|**@min_distretention**|  
|max distrib retention|**@max_distretention**|  
|history retention|**@history_retention**|  
|history cleanup agent|**@history_cleanupagent**|  
|distribution cleanup agent|**@distrib_cleanupagent**|  
|rpc login name|none|  
  
 다음 결과 집합 열은 배포자에서 게시가 허용된 게시 액세스 목록에 있는 사용자에게 반환됩니다.  
  
-   directory  
  
 다음 결과 집합 열은 모든 사용자에게 반환됩니다.  
  
|결과 집합 열|출력 매개 변수|  
|-----------------------|----------------------|  
|distributor|**@distributor**|  
|distribution database|**@distribdb**|  
|rpc server name|**@rpcsrvname**|  
|publisher type|**@publisher_type**|  
  
## <a name="see-also"></a>관련 항목:  
 [배포자 및 게시자 속성 보기 및 수정](../../relational-databases/replication/view-and-modify-distributor-and-publisher-properties.md)   
 [sp_adddistpublisher &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-adddistpublisher-transact-sql.md)   
 [sp_dropdistpublisher &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropdistpublisher-transact-sql.md)  
  
  
