---
title: sp_setsubscriptionxactseqno (TRANSACT-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_setsubscriptionxactseqno
- sp_setsubscriptionxactseqno_TSQL
helpviewer_keywords:
- sp_setsubscriptionxactseqno
ms.assetid: cdb4e0ba-5370-4905-b03f-0b0c6f080ca6
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 409f79007479fabe82b1c904f3bc0db943e3c116
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/03/2018
ms.locfileid: "52817865"
---
# <a name="spsetsubscriptionxactseqno-transact-sql"></a>sp_setsubscriptionxactseqno(Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  문제 해결 도중 구독자의 배포 에이전트에 의해 적용될 다음 트랜잭션의 LSN(로그 시퀀스 번호)을 지정하는 데 사용되며 에이전트에서 실패한 트랜잭션을 건너뛸 수 있게 해줍니다. 이 저장 프로시저는 구독 데이터베이스의 구독자에서 실행됩니다. SQL Server 이외 게시자에 대해서는 지원되지 않습니다.  
  
> [!CAUTION]  
>  이 저장 프로시저를 잘못 사용하거나 잘못된 LSN 값을 지정하면 배포 에이전트에서 구독자에 이미 적용된 변경 사항이 취소되거나 나머지 모든 변경 사항을 건너뛸 수 있습니다.  
  
 ![항목 링크 아이콘](../../database-engine/configure-windows/media/topic-link.gif "항목 링크 아이콘") [Transact-SQL 구문 규칙](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>구문  
  
```  
  
sp_setsubscriptionxactseqno [ @publisher = ] 'publisher'  
        , [ @publisher_db = ] 'publisher_db'  
        , [ @publication = ] 'publication'  
        , [ @xact_seqno = ] xact_seqno   
```  
  
## <a name="arguments"></a>인수  
 [  **@publisher=** ] **'***게시자***'**  
 게시자의 이름입니다. *게시자* 됩니다 **sysname**, 기본값은 없습니다.  
  
 [  **@publisher_db=** ] **'***publisher_db***'**  
 게시 데이터베이스의 이름입니다. *publisher_db* 됩니다 **sysname**, 기본값은 없습니다. 에 SQL Server 이외 게시자를 *publisher_db* 배포 데이터베이스의 이름입니다.  
  
 [  **@publication=** ] **'***게시***'**  
 게시의 이름입니다. *게시* 됩니다 **sysname**, 기본값은 없습니다. 둘 이상의 게시에서 배포 에이전트를 공유 하는 경우에에 대 한 모든 값을 지정 해야 *게시*합니다.  
  
 [  **@xact_seqno=** ] *xact_seqno*  
 배포자에서 구독자에 적용될 다음 트랜잭션의 LSN입니다. *xact_seqno* 됩니다 **varbinary(16)**, 기본값은 없습니다.  
  
## <a name="result-set"></a>결과 집합  
  
|열 이름|데이터 형식|Description|  
|-----------------|---------------|-----------------|  
|**원래 XACT_SEQNO**|**varbinary(16)**|구독자에 적용될 다음 트랜잭션의 원래 LSN입니다.|  
|**업데이트 된 XACT_SEQNO**|**varbinary(16)**|구독자에 적용될 다음 트랜잭션의 업데이트된 LSN입니다.|  
|**구독 스트림 수**|**int**|마지막 동기화 중에 사용된 구독 스트림의 수입니다.|  
  
## <a name="return-code-values"></a>반환 코드 값  
 **0** (성공) 또는 **1** (실패)  
  
## <a name="remarks"></a>Remarks  
 **sp_setsubscriptionxactseqno** 트랜잭션 복제에 사용 됩니다.  
  
 **sp_setsubscriptionxactseqno** 피어 투 피어 트랜잭션 복제 토폴로지를 사용할 수 없습니다.  
  
 **sp_setsubscriptionxactseqno** 에서 오류가 발생 하는 특정 트랜잭션을 건너뛸 수 때 구독자에서 적용 됩니다. 오류가 발생 하는 경우 배포 에이전트를 중지 한 후를 호출 [sp_helpsubscriptionerrors &#40;TRANSACT-SQL&#41; ](../../relational-databases/system-stored-procedures/sp-helpsubscriptionerrors-transact-sql.md) 실패 한 트랜잭션의 xact_seqno 값을 검색 하 고 를호출하는배포자에서**sp_setsubscriptionxactseqno**에 대 한이 값을 전달 *xact_seqno*합니다. 그러면 이 LSN 이후의 명령만 처리됩니다.  
  
 값을 지정 **0** 에 대 한 *xact_seqno* 배포 데이터베이스의 모든 보류 중인 명령을 구독자에 게 전달할 합니다.  
  
 **sp_setsubscriptionxactseqno** 배포 에이전트에서 복수 구독 스트림을 사용 하는 경우 실패할 수 있습니다.  
  
 이 오류가 발생하면 단일 구독 스트림으로 배포 에이전트를 실행해야 합니다. 자세한 내용은 [Replication Distribution Agent](../../relational-databases/replication/agents/replication-distribution-agent.md)을 참조하세요.  
  
## <a name="permissions"></a>사용 권한  
 멤버는 **sysadmin** 고정된 서버 역할 또는 **db_owner** 고정된 데이터베이스 역할을 실행할 수 있습니다 **sp_setsubscriptionxactseqno**합니다.  
  
  
