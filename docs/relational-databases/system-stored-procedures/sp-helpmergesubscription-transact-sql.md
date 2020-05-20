---
title: sp_helpmergesubscription (Transact-sql) | Microsoft Docs
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_helpmergesubscription
- sp_helpmergesubscription_TSQL
helpviewer_keywords:
- sp_helpmergesubscription
ms.assetid: da564112-f769-4e67-9251-5699823e8c86
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: e790d110fc45708c7aa2be76db3890c8d1bc7f13
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/05/2020
ms.locfileid: "82834480"
---
# <a name="sp_helpmergesubscription-transact-sql"></a>sp_helpmergesubscription(Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  밀어넣기 및 끌어오기 모두에 대한 구독 정보를 병합 게시로 반환합니다. 이 저장 프로시저는 게시 데이터베이스의 게시자 또는 구독 데이터베이스의 재게시 구독자에서 실행됩니다.  
  
 ![항목 링크 아이콘](../../database-engine/configure-windows/media/topic-link.gif "항목 링크 아이콘") [Transact-SQL 구문 표기 규칙](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>구문  
  
```  
  
sp_helpmergesubscription [ [ @publication=] 'publication']  
    [ , [ @subscriber=] 'subscriber']  
    [ , [ @subscriber_db=] 'subscriber_db']  
    [ , [ @publisher=] 'publisher']  
    [ , [ @publisher_db=] 'publisher_db']  
    [ , [ @subscription_type=] 'subscription_type']  
    [ , [ @found=] 'found' OUTPUT]  
```  
  
## <a name="arguments"></a>인수  
`[ @publication = ] 'publication'`게시의 이름입니다. *게시* 는 **sysname**이며 기본값은 **%** 입니다. 게시는 이미 존재하고 있어야 하며 식별자에 적용되는 규칙을 준수해야 합니다. NULL 또는 인 경우 **%** 현재 데이터베이스의 모든 병합 게시 및 구독에 대 한 정보가 반환 됩니다.  
  
`[ @subscriber = ] 'subscriber'`구독자의 이름입니다. *구독자* 는 **sysname**이며 기본값은 **%** 입니다. NULL 또는 %인 경우 지정한 게시에 대한 모든 구독에 관한 정보가 반환됩니다.  
  
`[ @subscriber_db = ] 'subscriber_db'`구독 데이터베이스의 이름입니다. *subscriber_db*는 **sysname**이며 기본값은 **%** 모든 구독 데이터베이스에 대 한 정보를 반환 하는입니다.  
  
`[ @publisher = ] 'publisher'`게시자의 이름입니다. 게시자는 유효한 서버여야 합니다. *publisher*는 **sysname**이며 기본값은 **%** 모든 게시자에 대 한 정보를 반환 하는입니다.  
  
`[ @publisher_db = ] 'publisher_db'`게시자 데이터베이스의 이름입니다. *publisher_db*는 **sysname**이며 기본값은 **%** 모든 게시자 데이터베이스에 대 한 정보를 반환 하는입니다.  
  
`[ @subscription_type = ] 'subscription_type'`구독의 유형입니다. *subscription_type*은 **nvarchar (15)** 이며 다음 값 중 하나일 수 있습니다.  
  
|값|설명|  
|-----------|-----------------|  
|**push** (기본값)|밀어넣기 구독|  
|**서브스크립션을**|끌어오기 구독|  
|**양방향**|밀어넣기 및 끌어오기 구독|  
  
`[ @found = ] 'found'OUTPUT`반환 하는 행을 나타내는 플래그입니다. *검색*된 **int** 및 OUTPUT 매개 변수 이며 기본값은 NULL입니다. **1** 은 게시가 발견 되었음을 나타냅니다. **0** 은 게시를 찾을 수 없음을 나타냅니다.  
  
## <a name="result-sets"></a>결과 집합  
  
|열 이름|데이터 형식|Description|  
|-----------------|---------------|-----------------|  
|**subscription_name**|**sysname**|구독의 이름입니다.|  
|**게시물**|**sysname**|게시의 이름입니다.|  
|**발행자**|**sysname**|게시자의 이름입니다.|  
|**publisher_db**|**sysname**|게시자 데이터베이스의 이름입니다.|  
|**구독자**|**sysname**|구독자의 이름입니다.|  
|**subscriber_db**|**sysname**|구독 데이터베이스의 이름입니다.|  
|**status**|**int**|다음은 구독의 상태입니다.<br /><br /> **0** = 모든 작업이 시작 되기를 기다리고 있습니다.<br /><br /> **1** = 하나 이상의 작업이 시작 됩니다.<br /><br /> **2** = 모든 작업이 성공적으로 실행 되었습니다.<br /><br /> **3** = 하나 이상의 작업이 실행 중입니다.<br /><br /> **4** = 모든 작업이 예약 되 고 유휴 상태입니다.<br /><br /> **5** = 이전 실패 후 하나 이상의 작업을 실행 하려고 합니다.<br /><br /> **6** = 하나 이상의 작업이 성공적으로 실행 되지 못했습니다.|  
|**subscriber_type**|**int**|구독자의 유형입니다.|  
|**subscription_type**|**int**|구독 유형:<br /><br /> **0** = 푸시<br /><br /> **1** = 끌어오기<br /><br /> **2** = 모두|  
|**priority**|**float (8)**|구독의 우선 순위를 표시하는 숫자입니다.|  
|**sync_type**|**tinyint**|구독 동기화 유형입니다.|  
|**한**|**nvarchar(255)**|해당 병합 구독에 대한 간단한 설명입니다.|  
|**merge_jobid**|**binary(16)**|병합 에이전트의 작업 ID입니다.|  
|**full_publication**|**tinyint**|구독이 전체 게시 또는 필터링된 게시를 위한 것인지 여부를 표시합니다.|  
|**offload_enabled**|**bit**|복제 에이전트의 오프로드 실행이 구독자에서 실행되도록 설정되었는지 여부를 지정합니다. NULL인 경우 게시자에서 실행됩니다.|  
|**offload_server**|**sysname**|에이전트가 실행되는 서버의 이름입니다.|  
|**use_interactive_resolver**|**int**|조정 상태 동안 대화형 해결 프로그램의 사용 여부를 반환합니다. **0**인 경우 대화형 해결 프로그램을 사용 하지 않습니다.|  
|**hostname**|**sysname**|구독이 [HOST_NAME](../../t-sql/functions/host-name-transact-sql.md) 함수의 값으로 필터링 될 때 제공 되는 값입니다.|  
|**subscriber_security_mode**|**smallint**|구독자의 보안 모드입니다. **1** 은 Windows 인증을 의미 하 고 **0** 은 인증을 의미 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 합니다.|  
|**subscriber_login**|**sysname**|구독자의 로그인 이름입니다.|  
|**subscriber_password**|**sysname**|실제 구독자 암호는 반환되지 않습니다. 결과는 "" 문자열로 마스킹 됩니다 **\*\*\*\*\*\*** .|  
  
## <a name="return-code-values"></a>반환 코드 값  
 **0** (성공) 또는 **1** (실패)  
  
## <a name="remarks"></a>설명  
 **sp_helpmergesubscription** 는 병합 복제에서 게시자 또는 재게시 구독자에 저장 된 구독 정보를 반환 하는 데 사용 됩니다.  
  
 익명 구독의 경우 *subscription_type*값은 항상 **1** (끌어오기)입니다. 그러나 익명 구독에 대 한 정보는 구독자에서 [sp_helpmergepullsubscription](../../relational-databases/system-stored-procedures/sp-helpmergepullsubscription-transact-sql.md) 를 실행 해야 합니다.  
  
## <a name="permissions"></a>사용 권한  
 **Sysadmin** 고정 서버 역할의 멤버, **db_owner** 고정 데이터베이스 역할의 멤버 또는 구독이 속한 게시에 대 한 게시 액세스 목록의 멤버만 **sp_helpmergesubscription**실행할 수 있습니다.  
  
## <a name="see-also"></a>참고 항목  
 [Transact-sql&#41;sp_addmergesubscription &#40;](../../relational-databases/system-stored-procedures/sp-addmergesubscription-transact-sql.md)   
 [Transact-sql&#41;sp_changemergesubscription &#40;](../../relational-databases/system-stored-procedures/sp-changemergesubscription-transact-sql.md)   
 [Transact-sql&#41;sp_dropmergesubscription &#40;](../../relational-databases/system-stored-procedures/sp-dropmergesubscription-transact-sql.md)   
 [시스템 저장 프로시저&#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
