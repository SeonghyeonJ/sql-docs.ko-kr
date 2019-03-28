---
title: sp_helpmergesubscription (TRANSACT-SQL) | Microsoft Docs
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
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 4643cfc08db68e5369cfca25d2de76d314ffb347
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/27/2019
ms.locfileid: "58530675"
---
# <a name="sphelpmergesubscription-transact-sql"></a>sp_helpmergesubscription(Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  밀어넣기 및 끌어오기 모두에 대한 구독 정보를 병합 게시로 반환합니다. 이 저장 프로시저는 게시 데이터베이스의 게시자 또는 구독 데이터베이스의 재게시 구독자에서 실행됩니다.  
  
 ![항목 링크 아이콘](../../database-engine/configure-windows/media/topic-link.gif "항목 링크 아이콘") [Transact-SQL 구문 규칙](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
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
`[ @publication = ] 'publication'` 게시의 이름이입니다. *게시* 됩니다 **sysname**, 기본값은 **%** 합니다. 게시는 이미 존재하고 있어야 하며 식별자에 적용되는 규칙을 준수해야 합니다. Null 인 경우 또는 **%**, 현재 데이터베이스의 모든 구독과 병합 게시에 대 한 정보가 반환 됩니다.  
  
`[ @subscriber = ] 'subscriber'` 구독자의 이름이입니다. *구독자* 됩니다 **sysname**, 기본값은 **%** 합니다. NULL 또는 %인 경우 지정한 게시에 대한 모든 구독에 관한 정보가 반환됩니다.  
  
`[ @subscriber_db = ] 'subscriber_db'` 구독 데이터베이스의 이름이입니다. *subscriber_db*됩니다 **sysname**, 기본값은 **%**, 모든 구독 데이터베이스에 대 한 정보를 반환 하는 합니다.  
  
`[ @publisher = ] 'publisher'` 게시자의 이름이입니다. 게시자는 유효한 서버여야 합니다. *게시자*됩니다 **sysname**, 기본값은 **%**, 모든 게시자에 대 한 정보를 반환 하는 합니다.  
  
`[ @publisher_db = ] 'publisher_db'` 게시자 데이터베이스의 이름이입니다. *publisher_db*됩니다 **sysname**, 기본값은 **%**, 모든 게시자 데이터베이스에 대 한 정보를 반환 하는 합니다.  
  
`[ @subscription_type = ] 'subscription_type'` 구독의 유형이입니다. *subscription_type*됩니다 **nvarchar(15)**, 이며 다음이 값 중 하나일 수 있습니다.  
  
|값|Description|  
|-----------|-----------------|  
|**푸시** (기본값)|밀어넣기 구독|  
|**pull**|끌어오기 구독|  
|**both**|밀어넣기 및 끌어오기 구독|  
  
`[ @found = ] 'found'OUTPUT` 가 반환 하는 행을 나타내는 플래그입니다. *찾을*됩니다 **int** 및 기본값은 NULL 사용 하 여 출력 매개 변수를 합니다. **1** 은 게시를 찾았음을 나타냅니다. **0** 게시를 찾지 못했음을 나타냅니다.  
  
## <a name="result-sets"></a>결과 집합  
  
|열 이름|데이터 형식|Description|  
|-----------------|---------------|-----------------|  
|**subscription_name**|**sysname**|구독의 이름입니다.|  
|**publication**|**sysname**|게시의 이름입니다.|  
|**publisher**|**sysname**|게시자의 이름입니다.|  
|**publisher_db**|**sysname**|게시자 데이터베이스의 이름입니다.|  
|**subscriber**|**sysname**|구독자의 이름입니다.|  
|**subscriber_db**|**sysname**|구독 데이터베이스의 이름입니다.|  
|**상태**|**int**|다음은 구독의 상태입니다.<br /><br /> **0** = 모든 작업이 시작 되기를 기다리고 있습니다<br /><br /> **1** = 하나 이상의 작업이 시작 됩니다<br /><br /> **2** = 모든 작업이 성공적으로 실행<br /><br /> **3** = 하나 이상의 작업이 실행 중입니다<br /><br /> **4** = 모든 작업이 예약 되었으며 유휴 상태<br /><br /> **5** = 하나 이상의 작업 이전에 실패 한 후 실행 하려고 합니다.<br /><br /> **6** = 하나 이상의 작업이 성공적으로 실행에 실패 했습니다|  
|**subscriber_type**|**int**|구독자의 유형입니다.|  
|**subscription_type**|**int**|구독 유형:<br /><br /> **0** = Push<br /><br /> **1** = 끌어오기<br /><br /> **2** = Both|  
|**priority**|**float(8)**|구독의 우선 순위를 표시하는 숫자입니다.|  
|**sync_type**|**tinyint**|구독 동기화 유형입니다.|  
|**description**|**nvarchar(255)**|해당 병합 구독에 대한 간단한 설명입니다.|  
|**merge_jobid**|**binary(16)**|병합 에이전트의 작업 ID입니다.|  
|**full_publication**|**tinyint**|구독이 전체 게시 또는 필터링된 게시를 위한 것인지 여부를 표시합니다.|  
|**offload_enabled**|**bit**|복제 에이전트의 오프로드 실행이 구독자에서 실행되도록 설정되었는지 여부를 지정합니다. NULL인 경우 게시자에서 실행됩니다.|  
|**offload_server**|**sysname**|에이전트가 실행되는 서버의 이름입니다.|  
|**use_interactive_resolver**|**int**|조정 상태 동안 대화형 해결 프로그램의 사용 여부를 반환합니다. 하는 경우 **0**, 대화형 해결 프로그램을 사용 하지 않습니다.|  
|**hostname**|**sysname**|구독 값을 기준으로 필터링 할 때 제공 된 값을 [HOST_NAME](../../t-sql/functions/host-name-transact-sql.md) 함수입니다.|  
|**subscriber_security_mode**|**smallint**|구독자의 보안 모드 위치 **1** Windows 인증을 의미 하 고 **0** 의미 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인증 합니다.|  
|**subscriber_login**|**sysname**|구독자의 로그인 이름입니다.|  
|**subscriber_password**|**sysname**|실제 구독자 암호는 반환되지 않습니다. 결과에서 마스킹를 "**\*\*\*\*\*\***" 문자열입니다.|  
  
## <a name="return-code-values"></a>반환 코드 값  
 **0** (성공) 또는 **1** (실패)  
  
## <a name="remarks"></a>Remarks  
 **sp_helpmergesubscription** 병합 복제에서 게시자 또는 재게시 구독자에 저장 하는 구독 정보를 반환 하는 데 사용 됩니다.  
  
 익명 구독에 대 한 합니다 *subscription_type*값은 항상 **1** (끌어오기). 그러나 실행 해야 합니다 [sp_helpmergepullsubscription](../../relational-databases/system-stored-procedures/sp-helpmergepullsubscription-transact-sql.md) 익명 구독에 대 한 정보에 대 한 구독자의 합니다.  
  
## <a name="permissions"></a>사용 권한  
 멤버만 합니다 **sysadmin** 고정 서버 역할을 합니다 **db_owner** 고정된 데이터베이스 역할 또는 구독이 속하는 게시에 대 한 게시 액세스 목록에서 실행할 수 있습니다 **sp_ helpmergesubscription**합니다.  
  
## <a name="see-also"></a>관련 항목  
 [sp_addmergesubscription &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addmergesubscription-transact-sql.md)   
 [sp_changemergesubscription &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changemergesubscription-transact-sql.md)   
 [sp_dropmergesubscription &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropmergesubscription-transact-sql.md)   
 [시스템 저장 프로시저&#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
