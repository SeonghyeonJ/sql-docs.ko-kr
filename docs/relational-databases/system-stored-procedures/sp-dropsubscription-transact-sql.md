---
title: sp_dropsubscription (TRANSACT-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_dropsubscription
- sp_dropsubscription_TSQL
helpviewer_keywords:
- sp_dropsubscription
ms.assetid: 7551f345-5510-4684-ab53-f9057249d13a
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 08e25ee6f2de589c3d7367c140bd0ea63d4cec1e
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/03/2018
ms.locfileid: "52812973"
---
# <a name="spdropsubscription-transact-sql"></a>sp_dropsubscription(Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  게시자에서 특정 아티클에 대한 구독, 게시 또는 구독 집합을 삭제합니다. 이 저장 프로시저는 게시 데이터베이스의 게시자에서 실행됩니다.  
  
 ![항목 링크 아이콘](../../database-engine/configure-windows/media/topic-link.gif "항목 링크 아이콘") [Transact-SQL 구문 규칙](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>구문  
  
```  
  
sp_dropsubscription [ [ @publication= ] 'publication' ]  
    [ , [ @article= ] 'article' ]  
        , [ @subscriber= ] 'subscriber'  
    [ , [ @destination_db= ] 'destination_db' ]  
    [ , [ @ignore_distributor = ] ignore_distributor ]  
    [ , [ @reserved= ] 'reserved' ]  
```  
  
## <a name="arguments"></a>인수  
 [  **@publication=** ] **'**_게시_**'**  
 연결된 게시의 이름입니다. *게시* 됩니다 **sysname**, 기본값은 NULL입니다. 하는 경우 **모든**, 지정 된 구독자의 모든 게시에 대 한 모든 구독이 취소 됩니다. *게시* 필수 매개 변수입니다.  
  
 [  **@article=** ] **'**_문서_**'**  
 아티클의 이름입니다. *문서* 됩니다 **sysname**, 기본값은 NULL입니다. 하는 경우 **모든**, 각각에 대 한 모든 아티클을 구독 지정 게시 및 구독자에서 삭제 됩니다. 사용 하 여 **모든** 즉시 허용 하는 게시에 대 한 업데이트 합니다.  
  
 [  **@subscriber=** ] **'**_subscribe_r **'**  
 삭제할 구독이 속해 있는 구독자의 이름입니다. *구독자* 됩니다 **sysname**, 기본값은 없습니다. 하는 경우 **모든**를 모든 구독자에 대 한 모든 구독이 삭제 됩니다.  
  
 [  **@destination_db=** ] **'**_destination_db_**'**  
 대상 데이터베이스의 이름입니다. *destination_db* 됩니다 **sysname**, 기본값은 NULL입니다. NULL인 경우 해당 구독자에서 모든 구독이 삭제됩니다.  
  
 [  **@ignore_distributor =** ] *ignore_distributor*  
 [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
 [  **@reserved=** ] **'**_예약_**'**  
 [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
## <a name="return-code-values"></a>반환 코드 값  
 **0** (성공) 또는 **1** (실패)  
  
## <a name="remarks"></a>Remarks  
 **sp_dropsubscription** 스냅숏 및 트랜잭션 복제에 사용 됩니다.  
  
 즉시 동기화 게시에서 아티클에 관한 구독을 삭제한 경우에는 게시에서 모든 아티클에 대한 구독을 삭제한 다음, 모두 한꺼번에 다시 추가하지 않는 한 다시 추가할 수 없습니다.  
  
## <a name="example"></a>예제  
 [!code-sql[HowTo#sp_droptransubscription](../../relational-databases/replication/codesnippet/tsql/sp-dropsubscription-tran_1.sql)]  
  
## <a name="permissions"></a>사용 권한  
 멤버만 합니다 **sysadmin** 고정 서버 역할을 **db_owner** 고정된 데이터베이스 역할 또는 사용자 구독을 만든 실행할 수 있습니다 **sp_dropsubscription**합니다.  
  
## <a name="see-also"></a>관련 항목  
 [밀어넣기 구독 삭제](../../relational-databases/replication/delete-a-push-subscription.md)   
 [sp_addsubscription &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md)   
 [sp_changesubstatus &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changesubstatus-transact-sql.md)   
 [sp_helpsubscription &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpsubscription-transact-sql.md)  
  
  
