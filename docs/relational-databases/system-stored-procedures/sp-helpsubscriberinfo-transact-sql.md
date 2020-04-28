---
title: sp_helpsubscriberinfo (Transact-sql) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_helpsubscriberinfo
- sp_helpsubscriberinfo_TSQL
helpviewer_keywords:
- sp_helpsubscriberinfo
ms.assetid: fbabe1ec-57cf-425c-bae7-af7f5d3198fd
author: stevestein
ms.author: sstein
ms.openlocfilehash: 38b653dcb51f428692401fb87609187a82449393
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/27/2020
ms.locfileid: "68771495"
---
# <a name="sp_helpsubscriberinfo-transact-sql"></a>sp_helpsubscriberinfo(Transact-SQL)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

  구독자에 관한 정보를 표시합니다. 이 저장 프로시저는 모든 데이터베이스의 게시자에서 실행됩니다.  
  
 ![항목 링크 아이콘](../../database-engine/configure-windows/media/topic-link.gif "항목 링크 아이콘") [Transact-SQL 구문 표기 규칙](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>구문  
  
```  
  
sp_helpsubscriberinfo [ [ @subscriber =] 'subscriber']  
    [ , [ @publisher = ] 'publisher' ]  
```  
  
## <a name="arguments"></a>인수  
`[ @subscriber = ] 'subscriber'`구독자의 이름입니다. *구독자* 는 **sysname**이며 기본값은 모든 정보 **%** 를 반환 하는입니다.  
  
`[ @publisher = ] 'publisher'`게시자의 이름입니다. *publisher* 는 **sysname**이며 기본값은 현재 서버의 이름입니다.  
  
> [!NOTE]  
>  Oracle 게시자 인 경우를 제외 하 고는 *게시자* 를 지정 하면 안 됩니다.  
  
## <a name="result-sets"></a>결과 집합  
  
|열 이름|데이터 형식|Description|  
|-----------------|---------------|-----------------|  
|**발행자**|**sysname**|게시자의 이름입니다.|  
|**구독자**|**sysname**|구독자의 이름입니다.|  
|**type**|**tinyint**|구독자의 유형입니다.<br /><br /> **0** =  0[!INCLUDE[msCoName](../../includes/msconame-md.md)] 데이터베이스 1 = ODBC 데이터 원본 **1** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|**로그인**|**sysname**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인증에 대한 로그인 ID입니다.|  
|**password**|**sysname**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인증에 대한 암호입니다.|  
|**commit_batch_size**|**int**|지원되지 않습니다.|  
|**status_batch_size**|**int**|지원되지 않습니다.|  
|**flush_frequency**|**int**|지원되지 않습니다.|  
|**frequency_type**|**int**|배포 에이전트가 실행되는 빈도입니다.<br /><br /> **1** = 한 번<br /><br /> **2** = 요청 시<br /><br /> **4** = 매일<br /><br /> **8** = 매주<br /><br /> **16** = 매월<br /><br /> **32** = 매월 상대적<br /><br /> **64** = 자동 시작<br /><br /> **128** = 되풀이|  
|**frequency_interval**|**int**|*Frequency_type*에 의해 설정 된 빈도에 적용 되는 값입니다.|  
|**frequency_relative_interval**|**int**|*Frequency_type* 가 **32** (매월 상대적)로 설정 된 경우 사용 되는 배포 에이전트의 날짜입니다.<br /><br /> **1** = 첫 번째<br /><br /> **2** = 초<br /><br /> **4** = 세 번째<br /><br /> **8** = 네 번째<br /><br /> **16** = 마지막|  
|**frequency_recurrence_factor**|**int**|*Frequency_type*에서 사용 하는 되풀이 비율입니다.|  
|**frequency_subday**|**int**|정의된 기간 동안 일정을 변경하는 빈도입니다.<br /><br /> **1** = 한 번<br /><br /> **2** = 초<br /><br /> **4** = 분<br /><br /> **8** = 시간|  
|**frequency_subday_interval**|**int**|*Frequency_subday*에 대 한 간격입니다.|  
|**active_start_time_of_day**|**int**|배포 에이전트가 처음으로 실행되도록 예약된 시간이며 HHMMSS 형식으로 표시됩니다.|  
|**active_end_time_of_day**|**int**|배포 에이전트가 마지막으로 실행되도록 예약된 시간이며 HHMMSS 형식으로 표시됩니다.|  
|**active_start_date**|**int**|배포 에이전트가 처음으로 실행되도록 예약된 날짜이며 YYYYMMDD 형식으로 표시됩니다.|  
|**active_end_date**|**int**|배포 에이전트가 마지막으로 실행되도록 예약된 날짜이며 YYYYMMDD 형식으로 표시됩니다.|  
|**retryattempt**|**int**|지원되지 않습니다.|  
|**retrydelay**|**int**|지원되지 않습니다.|  
|**한**|**nvarchar(255)**|구독자에 관한 텍스트 설명입니다.|  
|**security_mode**|**int**|구현된 보안 모드입니다.<br /><br /> **0** =  0[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인증<br /><br /> **1** =  1[!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 인증|  
|**frequency_type2**|**int**|병합 에이전트가 실행되는 빈도입니다.<br /><br /> **1** = 한 번<br /><br /> **2** = 요청 시<br /><br /> **4** = 매일<br /><br /> **8** = 매주<br /><br /> **16** = 매월<br /><br /> **32** = 매월 상대적<br /><br /> **64** = 자동 시작<br /><br /> **128** = 되풀이|  
|**frequency_interval2**|**int**|*Frequency_type*에 의해 설정 된 빈도에 적용 되는 값입니다.|  
|**frequency_relative_interval2**|**int**|*Frequency_type* 32 (매월 상대)로 설정 된 경우 사용 되는 병합 에이전트 날짜:<br /><br /> **1** = 첫 번째<br /><br /> **2** = 초<br /><br /> **4** = 세 번째<br /><br /> **8** = 네 번째<br /><br /> **16** = 마지막|  
|**frequency_recurrence_factor2**|**int**|*Frequency_type * ** 에서 사용 되는 되풀이 비율입니다.|  
|**frequency_subday2**|**int**|정의된 기간 동안 일정을 변경하는 빈도입니다.<br /><br /> **1** = 한 번<br /><br /> **2** = 초<br /><br /> **4** = 분<br /><br /> **8** = 시간|  
|**frequency_subday_interval2**|**int**|*Frequency_subday*에 대 한 간격입니다.|  
|**active_start_time_of_day2**|**int**|병합 에이전트가 처음으로 실행되도록 예약된 시간이며 HHMMSS 형식으로 표시됩니다.|  
|**active_end_time_of_day2**|**int**|병합 에이전트가 마지막으로 실행되도록 예약된 시간이며 HHMMSS 형식으로 표시됩니다.|  
|**active_start_date2**|**int**|병합 에이전트가 처음으로 실행되도록 예약된 날짜이며 YYYYMMDD 형식으로 표시됩니다.|  
|**active_end_date2**|**int**|병합 에이전트가 마지막으로 실행되도록 예약된 날짜이며 YYYYMMDD 형식으로 표시됩니다.|  
  
## <a name="return-code-values"></a>반환 코드 값  
 **0** (성공) 또는 **1** (실패)  
  
## <a name="remarks"></a>설명  
 **sp_helpsubscriberinfo** 는 스냅숏 복제, 트랜잭션 복제 및 병합 복제에 사용 됩니다.  
  
## <a name="permissions"></a>사용 권한  
 **Sysadmin** 고정 서버 역할, **db_owner** 고정 데이터베이스 역할의 멤버 또는 게시에 대 한 게시 액세스 목록의 멤버만 **sp_helpsubscriberinfo**을 실행할 수 있습니다.  
  
## <a name="see-also"></a>참고 항목  
 [Transact-sql&#41;sp_adddistpublisher &#40;](../../relational-databases/system-stored-procedures/sp-adddistpublisher-transact-sql.md)   
 [Transact-sql&#41;sp_addpullsubscription &#40;](../../relational-databases/system-stored-procedures/sp-addpullsubscription-transact-sql.md)   
 [Transact-sql&#41;sp_changesubscriber &#40;](../../relational-databases/system-stored-procedures/sp-changesubscriber-transact-sql.md)   
 [Transact-sql&#41;sp_dropsubscriber &#40;](../../relational-databases/system-stored-procedures/sp-dropsubscriber-transact-sql.md)   
 [Transact-sql&#41;sp_helpdistributor &#40;](../../relational-databases/system-stored-procedures/sp-helpdistributor-transact-sql.md)   
 [Transact-sql&#41;sp_helpserver &#40;](../../relational-databases/system-stored-procedures/sp-helpserver-transact-sql.md)   
 [시스템 저장 프로시저&#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
