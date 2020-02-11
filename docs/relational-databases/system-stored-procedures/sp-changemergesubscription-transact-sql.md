---
title: sp_changemergesubscription (Transact-sql) | Microsoft Docs
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_changemergesubscription_TSQL
- sp_changemergesubscription
helpviewer_keywords:
- sp_changemergesubscription
ms.assetid: fd820f35-c189-4e2d-884d-b60c1c469f58
author: stevestein
ms.author: sstein
ms.openlocfilehash: c205bab104bd81eda3e7d14dc30844352caa7f66
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68124866"
---
# <a name="sp_changemergesubscription-transact-sql"></a>sp_changemergesubscription(Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  선택한 병합 밀어넣기 구독에 대한 속성을 변경합니다. 이 저장 프로시저는 게시 데이터베이스의 게시자에서 실행됩니다.  
  
> [!IMPORTANT]  
>  게시자를 원격 배포자로 구성할 경우 *job_login* 및 *job_password*를 비롯한 모든 매개 변수에 제공된 값이 일반 텍스트로 배포자에게 전송됩니다. 이 저장 프로시저를 실행하기 전에 게시자와 해당 원격 배포자 간 연결을 암호화해야 합니다. 자세한 내용은 [데이터베이스 엔진에 암호화 연결 사용 &#40;SQL Server 구성 관리자&#41;을 ](../../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md)참조 하세요.  
  
## <a name="syntax"></a>구문  
  
```  
  
sp_changemergesubscription [ [ @publication= ] 'publication' ]  
    [ , [ @subscriber= ] 'subscriber'  
    [ , [ @subscriber_db= ] 'subscriber_db' ]  
    [ , [ @property= ] 'property' ]  
    [ , [ @value= ] 'value' ]  
```  
  
## <a name="arguments"></a>인수  
`[ @publication = ] 'publication'`변경할 게시의 이름입니다. *게시* 는 **sysname**이며 기본값은 NULL입니다. 게시는 이미 존재하고 있어야 하며 식별자에 적용되는 규칙을 준수해야 합니다.  
  
`[ @subscriber = ] 'subscriber'`구독자의 이름입니다. *구독자* 는 **sysname**이며 기본값은 NULL입니다.  
  
`[ @subscriber_db = ] 'subscriber_db'`구독 데이터베이스의 이름입니다. *subscriber_db*는 **sysname**이며 기본값은 NULL입니다.  
  
`[ @property = ] 'property'`지정 된 게시에 대해 변경할 속성입니다. *속성* 은 **sysname**이며 테이블의 값 중 하나일 수 있습니다.  
  
`[ @value = ] 'value'`지정 된 *속성*의 새 값입니다. *value* 는 **nvarchar (255)** 이며 테이블에 있는 값 중 하나일 수 있습니다.  
  
|속성|값|Description|  
|--------------|-----------|-----------------|  
|**한**||해당 병합 구독에 관한 설명입니다.|  
|**우선 순위**||구독 우선 순위입니다. 우선 순위는 기본 해결 프로그램이 충돌을 감지했을 때 먼저 적용할 항목을 선택하는 데 사용합니다.|  
|**merge_job_login**||에이전트가 실행되는 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 계정의 로그인입니다.|  
|**merge_job_password**||에이전트가 실행되는 Windows 계정의 암호입니다.|  
|**publisher_security_mode**|**1**|게시자에 연결할 때 Windows 인증을 사용합니다.|  
||**0**|게시자에 연결할 때 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인증을 사용합니다.|  
|**publisher_login**||게시자에서의 로그인 이름입니다.|  
|**publisher_password**||제공된 게시자 로그인에 대한 강력한 암호입니다.|  
|**subscriber_security_mode**|**1**|구독자에 연결할 때 Windows 인증을 사용합니다.|  
||**0**|구독자에 연결할 때 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인증을 사용합니다.|  
|**subscriber_login**||구독자에서의 로그인 이름입니다.|  
|**subscriber_password**||제공된 구독자 로그인에 대한 강력한 암호입니다.|  
|**sync_type**|**자동 번역**|게시된 테이블의 스키마 및 초기 데이터가 구독자에게 먼저 전송됩니다.|  
||**없음을**|구독자에 게시된 테이블에 대한 스키마 및 초기 데이터가 이미 있습니다. 시스템 테이블과 데이터는 항상 전송됩니다.|  
|**use_interactive_resolver**|**true**|대화형 해결을 허용하는 모든 아티클에 대해 충돌을 대화형으로 해결할 수 있도록 합니다.|  
||**허위**|기본 해결 프로그램이나 사용자 지정 해결 프로그램을 사용하여 충돌이 자동으로 해결됩니다.|  
|NULL(기본값)|NULL(기본값)||  
  
## <a name="return-code-values"></a>반환 코드 값  
 **0** (성공) 또는 **1** (실패)  
  
## <a name="remarks"></a>설명  
 **sp_changemergesubscription** 는 병합 복제에 사용 됩니다.  
  
 에이전트 로그인 또는 암호를 변경한 후 에이전트를 중지하고 다시 시작해야 변경 내용이 적용됩니다.  
  
## <a name="permissions"></a>사용 권한  
 **Sysadmin** 고정 서버 역할 또는 **db_owner** 고정 데이터베이스 역할의 멤버만 **sp_changemergesubscription**을 실행할 수 있습니다.  
  
## <a name="see-also"></a>참고 항목  
 [Transact-sql&#41;sp_addmergesubscription &#40;](../../relational-databases/system-stored-procedures/sp-addmergesubscription-transact-sql.md)   
 [Transact-sql&#41;sp_dropmergesubscription &#40;](../../relational-databases/system-stored-procedures/sp-dropmergesubscription-transact-sql.md)   
 [Transact-sql&#41;sp_helpmergesubscription &#40;](../../relational-databases/system-stored-procedures/sp-helpmergesubscription-transact-sql.md)   
 [시스템 저장 프로시저&#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
