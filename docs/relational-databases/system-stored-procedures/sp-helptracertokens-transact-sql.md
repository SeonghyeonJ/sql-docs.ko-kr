---
title: sp_helptracertokens (Transact-sql) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_helptracertokens
- sp_helptracertokens_TSQL
helpviewer_keywords:
- sp_helptracertokens
ms.assetid: 61f27234-531d-4b37-8fa3-fe4c32e6f521
author: stevestein
ms.author: sstein
ms.openlocfilehash: 9b4df50d1cf43ba1b0f4eb8b8f313634b4d11d18
ms.sourcegitcommit: 728a4fa5a3022c237b68b31724fce441c4e4d0ab
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/03/2019
ms.locfileid: "68771544"
---
# <a name="sphelptracertokens-transact-sql"></a>sp_helptracertokens(Transact-SQL)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

  대기 시간을 확인할 수 있도록 게시에 삽입된 각 추적 프로그램 토큰당 하나의 행을 반환합니다. 이 저장 프로시저는 게시 데이터베이스의 게시자 또는 배포 데이터베이스의 배포자에서 실행됩니다.  
  
 ![항목 링크 아이콘](../../database-engine/configure-windows/media/topic-link.gif "항목 링크 아이콘") [Transact-SQL 구문 규칙](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>구문  
  
```  
  
sp_helptracertokens [ @publication = ] 'publication'   
    [ , [ @publisher = ] 'publisher' ]   
    [ , [ @publisher_db = ] 'publisher_db' ]  
```  
  
## <a name="arguments"></a>인수  
`[ @publication = ] 'publication'`추적 프로그램 토큰이 삽입 된 게시의 이름입니다. *게시* 는 **sysname**이며 기본값은 없습니다.  
  
`[ @publisher = ] 'publisher'`게시자의 이름입니다. *publisher* 는 **sysname**이며 기본값은 NULL입니다.  
  
> [!NOTE]
>  이 매개 변수는 이외 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 게시자에 대해서만 지정 해야 합니다.  
  
`[ @publisher_db = ] 'publisher_db'`게시 데이터베이스의 이름입니다. *publisher_db* 는 **sysname**이며 기본값은 NULL입니다. 이 매개 변수는 게시자에서 저장 프로시저가 실행될 경우 무시됩니다.  
  
## <a name="result-set"></a>결과 집합  
  
|열 이름|데이터 형식|설명|  
|-----------------|---------------|-----------------|  
|**tracer_id**|**int**|추적 프로그램 토큰 레코드를 식별합니다.|  
|**publisher_commit**|**datetime**|게시 데이터베이스의 게시자에서 토큰 레코드가 커밋된 날짜와 시간입니다.|  
  
## <a name="return-code-values"></a>반환 코드 값  
 **0** (성공) 또는 **1** (실패)  
  
## <a name="remarks"></a>설명  
 **sp_helptracertokens** 은 트랜잭션 복제에 사용 됩니다.  
  
 **sp_helptracertokens** 는 [sp_helptracertokenhistory &#40;transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-helptracertokenhistory-transact-sql.md)을 실행할 때 추적 프로그램 토큰 id를 가져오는 데 사용 됩니다.  
  
## <a name="example"></a>예제  
 [!code-sql[HowTo#sp_tracertokens](../../relational-databases/replication/codesnippet/tsql/sp-helptracertokens-tran_1.sql)]  
  
## <a name="permissions"></a>사용 권한  
 **Sysadmin** 고정 서버 역할의 멤버, 게시 데이터베이스의 **db_owner** 고정 데이터베이스 역할의 멤버 또는 배포 데이터베이스의 **db_owner** 고정 데이터베이스 역할 또는 **replmonitor** 역할의 멤버만 p _ i p _을 실행할 수 있습니다.  **helptracertokenhistory**.  
  
## <a name="see-also"></a>관련 항목  
 [트랜잭션 복제에 대한 대기 시간 측정 및 연결 유효성 검사](../../relational-databases/replication/monitor/measure-latency-and-validate-connections-for-transactional-replication.md)   
 [sp_deletetracertokenhistory &#40;transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-deletetracertokenhistory-transact-sql.md)  
  
  
