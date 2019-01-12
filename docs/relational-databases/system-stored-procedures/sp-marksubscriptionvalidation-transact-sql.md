---
title: sp_marksubscriptionvalidation (TRANSACT-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_marksubscriptionvalidation
- sp_marksubscriptionvalidation_TSQL
helpviewer_keywords:
- sp_marksubscriptionvalidation
ms.assetid: e68fe0b9-5993-4880-917a-b0f661f8459b
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: e49099c2bf0ecd7974531c9f1b840e77805cf218
ms.sourcegitcommit: 7aa6beaaf64daf01b0e98e6c63cc22906a77ed04
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54131353"
---
# <a name="spmarksubscriptionvalidation-transact-sql"></a>sp_marksubscriptionvalidation(Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  현재 열려 있는 트랜잭션을 지정된 구독자에 대한 구독 수준 유효성 검사 트랜잭션으로 표시합니다. 이 저장 프로시저는 게시 데이터베이스의 게시자에서 실행됩니다.  
  
 ![항목 링크 아이콘](../../database-engine/configure-windows/media/topic-link.gif "항목 링크 아이콘") [Transact-SQL 구문 규칙](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>구문  
  
```  
  
sp_marksubscriptionvalidation [ @publication = ] 'publication'  
        , [ @subscriber = ] 'subscriber'  
        , [ @destination_db = ] 'destination_db'  
    [ , [ @publisher = ] 'publisher' ]  
```  
  
## <a name="arguments"></a>인수  
 [ **@publication**=] **'***게시***'**  
 게시의 이름입니다. *게시* 됩니다 **sysname**, 기본값은 없습니다.  
  
 [ **@subscriber**=] **'***구독자***'**  
 구독자의 이름입니다. *구독자* 는 sysname 이며 기본값은 없습니다.  
  
 [  **@destination_db=**] **'***destination_db***'**  
 대상 데이터베이스의 이름입니다. *destination_db* 됩니다 **sysname**, 기본값은 없습니다.  
  
 [  **@publisher=** ] **'***게시자***'**  
 이외 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 게시자입니다. *게시자* 됩니다 **sysname**, 기본값은 NULL입니다.  
  
> [!NOTE]  
>  *게시자* 에 속하는 게시에 대 한 쓰일 수 없습니다는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 게시자입니다.  
  
## <a name="return-code-values"></a>반환 코드 값  
 **0** (성공) 또는 **1** (실패)  
  
## <a name="remarks"></a>Remarks  
 **sp_marksubscriptionvalidation** 트랜잭션 복제에 사용 됩니다.  
  
 **sp_marksubscriptionvalidation** 지원 하지 않습니다 이외 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 구독자입니다.  
  
 에 대 한 비 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 실행할 수 없습니다. 게시자 **sp_marksubscriptionvalidation** 에서 명시적 트랜잭션 내에서. 이는 게시자에 액세스하는 데 사용되는 연결된 서버 연결을 통해서는 명시적 트랜잭션이 지원되지 않기 때문입니다.  
  
 **sp_marksubscriptionvalidation** 와 함께 사용 해야 합니다 [sp_article_validation &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-article-validation-transact-sql.md)에 값을 지정 하면 **1** 에 대 한  *subscription_level*, 다른 호출과 함께 사용할 수 있습니다 **sp_marksubscriptionvalidation** 다른 구독자에 대 한 현재 열려 있는 트랜잭션을 표시 합니다.  
  
## <a name="permissions"></a>사용 권한  
 멤버는 **sysadmin** 고정된 서버 역할 또는 **db_owner** 고정된 데이터베이스 역할을 실행할 수 있습니다 **sp_marksubscriptionvalidation**합니다.  
  
## <a name="example"></a>예제  
 다음 쿼리는 게시 데이터베이스가 구독 수준 유효성 검사 명령을 게시하는 데 적용할 수 있습니다. 다음 명령은 지정한 구독자의 배포 에이전트에 의해 적용됩니다. 첫 번째 트랜잭션의 문서의 유효성을 검사 하는 참고 '**art1**', 트랜잭션 유효성을 검사 하는 동안 두 번째'**art2**'. 또한에 대 한 호출 **sp_marksubscriptionvalidation** 하 고 [sp_article_validation &#40;TRANSACT-SQL&#41; ](../../relational-databases/system-stored-procedures/sp-article-validation-transact-sql.md) 트랜잭션에서 캡슐화 되었습니다. 한 번만 호출 것이 좋습니다 [sp_article_validation &#40;TRANSACT-SQL&#41; ](../../relational-databases/system-stored-procedures/sp-article-validation-transact-sql.md) 트랜잭션당 합니다. 왜냐하면 [sp_article_validation &#40;TRANSACT-SQL&#41; ](../../relational-databases/system-stored-procedures/sp-article-validation-transact-sql.md) 트랜잭션 기간에 대 한 원본 테이블에 공유 테이블 잠금을 보유 합니다. 반드시 트랜잭션 길이를 짧게 유지하여 동시성을 최대화해야 합니다.  
  
```  
begin tran  
  
exec sp_marksubscriptionvalidation @publication = 'pub1',  
 @subscriber = 'Sub', @destination_db = 'SubDB'  
  
exec sp_marksubscriptionvalidation @publication = 'pub1',  
 @subscriber = 'Sub2', @destination_db = 'SubDB'  
  
exec sp_article_validation @publication = 'pub1', @article = 'art1',  
 @rowcount_only = 0, @full_or_fast = 0, @shutdown_agent = 0,  
 @subscription_level = 1  
  
commit tran  
  
begin tran  
  
exec sp_marksubscriptionvalidation @publication = 'pub1',  
 @subscriber = 'Sub', @destination_db = 'SubDB'  
  
exec sp_marksubscriptionvalidation @publication = 'pub1',  
 @subscriber = 'Sub2', @destination_db = 'SubDB'  
  
exec sp_article_validation @publication = 'pub1', @article = 'art2',  
 @rowcount_only = 0, @full_or_fast = 0, @shutdown_agent = 0,  
 @subscription_level = 1  
  
commit tran  
```  
  
## <a name="see-also"></a>관련 항목  
 [시스템 저장 프로시저&#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [복제된 데이터의 유효성 검사](../../relational-databases/replication/validate-data-at-the-subscriber.md)  
  
  
