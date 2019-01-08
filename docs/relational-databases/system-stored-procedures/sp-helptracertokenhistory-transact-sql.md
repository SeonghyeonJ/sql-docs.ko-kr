---
title: sp_helptracertokenhistory (TRANSACT-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_helptracertokenhistory_TSQL
- sp_helptracertokenhistory
helpviewer_keywords:
- sp_helptracertokenhistory
ms.assetid: 96910d1c-be76-43eb-9c93-4477e6761749
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 04bd9a7d072f31fd6791e8cea7b17e14650e63c7
ms.sourcegitcommit: 6443f9a281904af93f0f5b78760b1c68901b7b8d
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53215409"
---
# <a name="sphelptracertokenhistory-transact-sql"></a>sp_helptracertokenhistory(Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  추적 프로그램 토큰에 대한 자세한 대기 시간 정보를 각 구독자당 한 개의 행과 함께 반환합니다. 이 저장 프로시저는 게시 데이터베이스의 게시자 또는 배포 데이터베이스의 배포자에서 실행됩니다.  
  
 ![항목 링크 아이콘](../../database-engine/configure-windows/media/topic-link.gif "항목 링크 아이콘") [Transact-SQL 구문 규칙](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>구문  
  
```  
  
sp_helptracertokenhistory [ @publication = ] 'publication'   
        , [ @tracer_id = ] tracer_id  
    [ , [ @publisher = ] 'publisher' ]  
    [ , [ @publisher_db = ] 'publisher_db' ]  
```  
  
## <a name="arguments"></a>인수  
 [  **@publication=** ] **'***게시***'**  
 추적 프로그램 토큰이 삽입된 게시의 이름입니다. *게시* 됩니다 **sysname**, 기본값은 없습니다.  
  
 [  **@tracer_id=** ] *tracer_id*  
 추적 프로그램 토큰의 id를 [MStracer_tokens &#40;TRANSACT-SQL&#41; ](../../relational-databases/system-tables/mstracer-tokens-transact-sql.md) 테이블 기록에 대 한 정보가 반환 됩니다. *tracer_id* 됩니다 **int**, 기본값은 없습니다.  
  
 [  **@publisher=** ] **'***게시자***'**  
 게시자의 이름입니다. *게시자* 됩니다 **sysname**, 기본값은 NULL입니다.  
  
> [!NOTE]
>  에 대 한에이 매개 변수를 지정 해야 이외 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 게시자입니다.  
  
 [  **@publisher_db=** ] **'***publisher_db***'**  
 게시 데이터베이스의 이름입니다. *publisher_db* 됩니다 **sysname**, 기본값은 NULL입니다. 이 매개 변수는 게시자에서 저장 프로시저가 실행될 경우 무시됩니다.  
  
## <a name="result-set"></a>결과 집합  
  
|열 이름|데이터 형식|Description|  
|-----------------|---------------|-----------------|  
|**distributor_latency**|**bigint**|게시자에서 커밋되는 추적 프로그램 토큰 레코드와 배포자에서 커밋되는 레코드 간의 시간 간격(초)입니다.|  
|**subscriber**|**sysname**|추적 프로그램 토큰을 받은 구독자의 이름입니다.|  
|**subscriber_db**|**sysname**|추적 프로그램 토큰 레코드가 삽입된 구독 데이터베이스의 이름입니다.|  
|**subscriber_latency**|**bigint**|배포자에서 커밋되는 추적 프로그램 토큰 레코드와 구독자에서 커밋되는 레코드 간의 시간 간격(초)입니다.|  
|**overall_latency**|**bigint**|게시자에서 커밋되는 추적 프로그램 토큰 레코드와 구독자에서 커밋되는 레코드 간의 시간 간격(초)입니다.|  
  
## <a name="return-code-values"></a>반환 코드 값  
 **0** (성공) 또는 **1** (실패)  
  
## <a name="remarks"></a>Remarks  
 **sp_helptracertokenhistory** 트랜잭션 복제에 사용 됩니다.  
  
 실행할 [sp_helptracertokens &#40;TRANSACT-SQL&#41; ](../../relational-databases/system-stored-procedures/sp-helptracertokens-transact-sql.md) 게시에 대 한 추적 프로그램 토큰의 목록을 가져올 수 있습니다.  
  
 결과 집합의 NULL 값은 대기 시간 통계를 계산할 수 없음을 나타냅니다. 이것은 배포자 또는 구독자 중 하나에서 추적 프로그램 토큰을 받지 못했기 때문입니다.  
  
## <a name="example"></a>예제  
 [!code-sql[HowTo#sp_tracertokens](../../relational-databases/replication/codesnippet/tsql/sp-helptracertokenhistor_1.sql)]  
  
## <a name="permissions"></a>사용 권한  
 멤버만 합니다 **sysadmin** 고정 서버 역할을 합니다 **db_owner** 게시 데이터베이스의 고정 데이터베이스 역할 또는 **db_owner** 고정된 데이터베이스 또는  **replmonitor** 배포 데이터베이스의 역할을 실행할 수 있습니다 **sp_helptracertokenhistory**합니다.  
  
## <a name="see-also"></a>관련 항목  
 [트랜잭션 복제에 대한 대기 시간 측정 및 연결 유효성 검사](../../relational-databases/replication/monitor/measure-latency-and-validate-connections-for-transactional-replication.md)   
 [sp_deletetracertokenhistory &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-deletetracertokenhistory-transact-sql.md)  
  
  
