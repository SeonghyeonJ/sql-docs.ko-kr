---
title: sp_helpxactsetjob (TRANSACT-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_helpxactsetjob
- sp_helpxactsetjob_TSQL
helpviewer_keywords:
- sp_helpxactsetjob
ms.assetid: 242cea3e-e6ac-4f84-a072-b003b920eb33
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 7402fcc825e6f537703268c1fd3fead9c88b1f5e
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62959613"
---
# <a name="sphelpxactsetjob-transact-sql"></a>sp_helpxactsetjob(Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Oracle 게시자에 대한 Xactset 작업 정보를 표시합니다. 이 저장 프로시저는 모든 데이터베이스의 배포자에서 실행됩니다.  
  
 ![항목 링크 아이콘](../../database-engine/configure-windows/media/topic-link.gif "항목 링크 아이콘") [Transact-SQL 구문 규칙](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>구문  
  
```  
  
sp_helpxactsetjob [ @publisher = ] 'publisher'   
```  
  
## <a name="arguments"></a>인수  
 [ **@publisher** = ] **'***publisher***'**  
 비-의 이름인 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 작업이 속한 게시자입니다. *게시자* 됩니다 **sysname**, 기본값은 없습니다.  
  
## <a name="result-sets"></a>결과 집합  
  
|열 이름|데이터 형식|Description|  
|-----------------|---------------|-----------------|  
|**jobnumber**|**int**|Oracle 작업 번호입니다.|  
|**lastdate**|**varchar(22)**|작업을 실행한 최근 날짜입니다.|  
|**thisdate**|**varchar(22)**|변경 시간|  
|**nextdate**|**varchar(22)**|작업을 실행할 다음 날짜입니다.|  
|**broken**|**varchar(1)**|작업이 끊어지는지 여부를 나타내는 플래그입니다.|  
|**interval**|**varchar(200)**|작업 간격입니다.|  
|**failures**|**int**|해당 작업에 대한 실패 횟수입니다.|  
|**xactsetjobwhat**|**varchar(200)**|작업에 의해 실행된 프로시저 이름입니다.|  
|**xactsetjob**|**varchar(1)**|작업의 상태이며 다음 중 하나일 수 있습니다.<br /><br /> **1** -작업을 사용 하도록 설정 합니다.<br /><br /> **0** -작업이 해제 합니다.|  
|**xactsetlonginterval**|**int**|작업에 대한 긴 간격입니다.|  
|**xactsetlongthreshold**|**int**|작업에 대한 긴 임계값입니다.|  
|**xactsetshortinterval**|**int**|작업에 대한 짧은 간격입니다.|  
|**xactsetshortthreshold**|**int**|작업에 대한 짧은 임계값입니다.|  
  
## <a name="return-code-values"></a>반환 코드 값  
 **0** (성공) 또는 **1** (실패)  
  
## <a name="remarks"></a>Remarks  
 **sp_helpxactsetjob** 스냅숏 복제 및 Oracle 게시자에 대 한 트랜잭션 복제에 사용 됩니다.  
  
 **sp_helpxactsetjob** 항상 게시자에서 Xactset 작업 (HREPL_XactSetJob) 현재 설정을 반환 합니다. Xactset 작업이 현재 작업 큐에 있는 경우 Oracle 게시자의 관리자 계정에서 만든 USER_JOB 데이터 사전 뷰에서 작업의 특성을 추가로 반환합니다.  
  
## <a name="permissions"></a>사용 권한  
 구성원만 합니다 **sysadmin** 고정된 서버 역할을 실행할 수 있습니다 **sp_helpxactsetjob**합니다.  
  
## <a name="see-also"></a>관련 항목  
 [Oracle 게시자에 대한 트랜잭션 집합 작업 구성&#40;복제 Transact-SQL 프로그래밍&#41;](../../relational-databases/replication/administration/configure-the-transaction-set-job-for-an-oracle-publisher.md)   
 [sp_publisherproperty &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-publisherproperty-transact-sql.md)  
  
  
