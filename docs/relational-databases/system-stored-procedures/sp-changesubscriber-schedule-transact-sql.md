---
title: sp_changesubscriber_schedule (TRANSACT-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_changesubscriber_schedule
- sp_changesubscriber_schedule_TSQL
helpviewer_keywords:
- sp_changesubscriber_schedule
ms.assetid: ff84e8e2-d496-482c-b23e-38a6626596e6
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 83edeb0c94276e10528b05bc5a1cd8d9474d07aa
ms.sourcegitcommit: 7aa6beaaf64daf01b0e98e6c63cc22906a77ed04
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54127913"
---
# <a name="spchangesubscriberschedule-transact-sql"></a>sp_changesubscriber_schedule(Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  구독자에 대해 배포 에이전트 또는 병합 에이전트 일정을 변경합니다. 이 저장 프로시저는 모든 데이터베이스의 게시자에서 실행됩니다.  
  
 ![항목 링크 아이콘](../../database-engine/configure-windows/media/topic-link.gif "항목 링크 아이콘") [Transact-SQL 구문 규칙](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>구문  
  
```  
  
sp_changesubscriber_schedule [ @subscriber = ] 'subscriber', [ @agent_type = ] type  
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
    [ , [ @publisher = ] 'publisher' ]  
```  
  
## <a name="arguments"></a>인수  
 [  **@subscriber=**] **'**_구독자_**'**  
 구독자의 이름입니다. *구독자* 됩니다 **sysname**합니다. 구독자의 이름은 데이터베이스에서 고유해야 하고 이미 존재해서는 안 되며 NULL일 수 없습니다.  
  
 [  **@agent_type=**] *형식*  
 에이전트의 유형입니다. *형식* 됩니다 **smallint**, 기본값은 **0**합니다. **0** 은 배포 에이전트를 나타냅니다. **1** 병합 에이전트를 나타냅니다.  
  
 [  **@frequency_type=**] *frequency_type*  
 배포 태스크를 예약하는 빈도입니다. *frequency_type* 됩니다 **int**, 기본값은 **64**합니다. 10개의 일정 열이 있습니다.  
  
 [  **@frequency_interval=**] *frequency_interval*  
 설정 된 빈도에 적용 된 값인 *frequency_type*합니다. *frequency_interval* 됩니다 **int**, 기본값은 **1**합니다.  
  
 [  **@frequency_relative_interval=**] *frequency_relative_interval*  
 배포 태스크 날짜입니다. *frequency_relative_interval* 됩니다 **int**, 기본값은 **1**합니다.  
  
 [  **@frequency_recurrence_factor=**] *frequency_recurrence_factor*  
 사용 하는 되풀이 비율 *frequency_type*합니다. *frequency_recurrence_factor* 됩니다 **int**, 기본값은 **0**합니다.  
  
 [  **@frequency_subday=**] *frequency_subday*  
 정의된 기간 동안 다시 예약하는 빈도(분)입니다. *frequency_subday* 됩니다 **int**, 기본값은 **4**합니다.  
  
 [  **@frequency_subday_interval=**] *frequency_subday_interval*  
 에 대 한 간격인 *frequency_subday*합니다. *frequency_subday_interval* 됩니다 **int**, 기본값은 **5**합니다.  
  
 [  **@active_start_time_of_day=**] *active_start_time_of_day*  
 하루 중에서 배포 태스크가 처음으로 실행되도록 예약된 시간입니다. *active_start_time_of_day* 됩니다 **int**, 기본값은 **0**합니다.  
  
 [  **@active_end_time_of_day=**] *active_end_time_of_day*  
 하루 중에서 배포 태스크가 마지막으로 실행되도록 예약된 시간입니다. *active_end_time_of_day* 됩니다 **int**, 기본값은 **235959**, 즉 오후 11시 59분: 59 24시간제를 기준으로 오후 11:59:59를 나타냅니다.  
  
 [  **@active_start_date=**] *active_start_date*  
 배포 태스크가 처음으로 실행되도록 예약된 날짜이며 YYYYMMDD 형식으로 표시됩니다. *active_start_date* 됩니다 **int**, 기본값은 **0**합니다.  
  
 [  **@active_end_date=**] *active_end_date*  
 배포 태스크가 마지막으로 실행되도록 예약된 날짜이며 YYYYMMDD 형식으로 표시됩니다. *active_end_date* 됩니다 **int**, 기본값은 **99991231**, 9999 의미 하는 12 월 31 일입니다.  
  
 [ **@publisher**=] **'**_게시자_**'**  
 이외 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 게시자입니다. *게시자* 됩니다 **sysname**, 기본값은 NULL입니다.  
  
> [!NOTE]  
>  *게시자* 해서는 안에서 아티클 속성을 변경 하는 경우는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 게시자입니다.  
  
## <a name="return-code-values"></a>반환 코드 값  
 **0** (성공) 또는 **1** (실패)  
  
## <a name="remarks"></a>Remarks  
 **sp_changesubscriber_schedule** 모든 유형의 복제에 사용 됩니다.  
  
## <a name="permissions"></a>사용 권한  
 멤버는 **sysadmin** 고정된 서버 역할을 실행할 수 있습니다 **sp_changesubscriber_schedule**합니다.  
  
## <a name="see-also"></a>관련 항목  
 [sp_addsubscriber_schedule &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addsubscriber-schedule-transact-sql.md)   
 [시스템 저장 프로시저&#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
