---
title: MSsubscriptions (TRANSACT-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSsubscriptions_TSQL
- MSsubscriptions
dev_langs:
- TSQL
helpviewer_keywords:
- MSsubscriptions system table
ms.assetid: b7e8301d-d115-41f6-8d4f-e0d25f453b25
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 4b0c5d53519b09c9f30ccdf7e973e25e5a06a6a3
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/03/2018
ms.locfileid: "52823598"
---
# <a name="mssubscriptions-transact-sql"></a>MSsubscriptions(Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  합니다 **MSsubscriptions** 로컬 배포자 구독에 문서를 게시 된 각 테이블 하나의 행을 포함 합니다. 이 테이블은 배포 데이터베이스에 저장됩니다.  
  
|열 이름|데이터 형식|Description|  
|-----------------|---------------|-----------------|  
|**publisher_database_id**|**int**|게시자 데이터베이스의 ID입니다.|  
|**publisher_id**|**smallint**|게시자의 ID입니다.|  
|**publisher_db**|**sysname**|게시자 데이터베이스의 이름입니다.|  
|**publication_id**|**int**|게시의 ID입니다.|  
|**article_id**|**int**|아티클의 ID입니다.|  
|**subscriber_id**|**smallint**|구독자의 ID입니다.|  
|**subscriber_db**|**sysname**|구독 데이터베이스의 이름입니다.|  
|**subscription_type**|**int**|구독 유형은 다음과 같습니다.<br /><br /> **0** = 밀어넣기 합니다.<br /><br /> **1** = 끌어오기.<br /><br /> **2** = 익명입니다.|  
|**sync_type**|**tinyint**|동기화 유형입니다.<br /><br /> **1** = automatic.<br /><br /> **2** = 동기화 없음.|  
|**상태**|**tinyint**|구독 상태입니다.<br /><br /> **0** = 비활성입니다.<br /><br /> **1** = 구독 합니다.<br /><br /> **2** = 활성입니다.|  
|**subscription_seqno**|**varbinary(16)**|스냅숏 트랜잭션 시퀀스 번호입니다.|  
|**snapshot_seqno_flag**|**bit**|스냅숏 트랜잭션 시퀀스 번호의 소스를 나타냅니다. 여기서 값 **1** 즉 **subscription_seqno** 스냅숏 시퀀스 번호입니다.|  
|**independent_agent**|**bit**|이 게시에 대한 독립 실행형 배포 에이전트가 있는지 여부를 나타냅니다.|  
|**subscription_time**|**datetime**|내부적으로만 사용됩니다.|  
|**loopback_detection**|**bit**|양방향 트랜잭션 복제 토폴로지에 속한 구독에 적용됩니다. 루프백 검색은 배포 에이전트가 구독자에서 발생한 트랜잭션을 다시 구독자에게 보낼지 여부를 결정합니다.<br /><br /> **1** 않습니다 = 다시 보내지 않습니다.<br /><br /> **0** = 다시 보냅니다.<br /><br /> 참고: 이 열은 [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]의 양방향 복제 기능에 대한 이전 버전과의 호환성을 위해서만 지원됩니다. 최신 버전의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서는 피어 투 피어 복제를 대신 사용해야 합니다. 자세한 내용은 [Peer-to-Peer Transactional Replication](../../relational-databases/replication/transactional/peer-to-peer-transactional-replication.md)을 참조하세요.|  
|**agent_id**|**int**|에이전트의 ID입니다.|  
|**update_mode**|**tinyint**|업데이트의 유형입니다.|  
|**publisher_seqno**|**varbinary(16)**|이 구독에 대한 게시자에서의 트랜잭션 시퀀스 번호입니다.|  
|**ss_cplt_seqno**|**varbinary(16)**|동시 스냅숏 처리의 완료를 표시하는 데 사용되는 시퀀스 번호입니다.|  
  
## <a name="see-also"></a>관련 항목:  
 [복제 테이블](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [복제 뷰](../../relational-databases/system-views/replication-views-transact-sql.md)   
 [sp_helpsubscription &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpsubscription-transact-sql.md)  
  
  
