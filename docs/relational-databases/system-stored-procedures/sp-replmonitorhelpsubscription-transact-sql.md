---
description: sp_replmonitorhelpsubscription(Transact-SQL)
title: sp_replmonitorhelpsubscription (Transact-sql) | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_replmonitorhelpsubscription_TSQL
- sp_replmonitorhelpsubscription
helpviewer_keywords:
- sp_replmonitorhelpsubscription
ms.assetid: a681b2db-c82d-4624-a10c-396afb0ac42f
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: b9597e7a3512307367568ee14800fcbf69a3045f
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88485689"
---
# <a name="sp_replmonitorhelpsubscription-transact-sql"></a>sp_replmonitorhelpsubscription(Transact-SQL)
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]

  게시자에 있는 하나 이상의 게시에 속한 구독의 현재 상태 정보를 반환하고 반환된 각 구독당 한 개의 행을 반환합니다. 복제 모니터링에 사용되는 이 저장 프로시저는 배포 데이터베이스의 배포자에서 실행됩니다.  
  
 ![항목 링크 아이콘](../../database-engine/configure-windows/media/topic-link.gif "항목 링크 아이콘") [Transact-SQL 구문 표기 규칙](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>구문  
  
```  
  
sp_replmonitorhelpsubscription [ @publisher = ] 'publisher'  
    [ , [ @publisher_db = ] 'publisher_db' ]  
    [ , [ @publication = ] 'publication' ]  
    [ , [ @publication_type = ] publication_type ]   
    [ , [ @mode = ] mode ]  
    [ , [ @topnum = ] topnum ]   
    [ , [ @exclude_anonymous = ] exclude_anonymous ]   
    [ , [ @refreshpolicy = ] refreshpolicy ]  
```  
  
## <a name="arguments"></a>인수  
`[ @publisher = ] 'publisher'` 상태를 모니터링 하는 게시자의 이름입니다. *publisher* 는 **sysname**이며 기본값은 NULL입니다. **Null**인 경우 배포자를 사용 하는 모든 게시자에 대해 정보가 반환 됩니다.  
  
`[ @publisher_db = ] 'publisher_db'` 게시 된 데이터베이스의 이름입니다. *publisher_db* 는 **sysname**이며 기본값은 NULL입니다. NULL인 경우 게시자에 게시된 모든 데이터베이스에 대한 정보가 반환됩니다.  
  
`[ @publication = ] 'publication'` 모니터링 되는 게시의 이름입니다. *게시* 는 **sysname**이며 기본값은 NULL입니다.  
  
`[ @publication_type = ] publication_type` 게시의 유형입니다. *publication_type* 은 **int**이며 다음 값 중 하나일 수 있습니다.  
  
|값|설명|  
|-----------|-----------------|  
|**0**|트랜잭션 게시|  
|**1**|스냅샷 게시|  
|**2**|병합 게시|  
|NULL(기본값)|복제가 게시 유형을 확인하려고 합니다.|  
  
`[ @mode = ] mode` 구독 모니터링 정보를 반환할 때 사용 하는 필터링 모드입니다. *모드* 는 **int**이며 다음 값 중 하나일 수 있습니다.  
  
|값|Description|  
|-----------|-----------------|  
|**0** (기본값)|모든 구독을 반환합니다.|  
|**1**|오류가 있는 구독만 반환합니다.|  
|**2**|생성된 임계값 메트릭 경고가 있는 구독만 반환합니다.|  
|**3**|오류 또는 생성된 임계값 메트릭 경고가 있는 구독만 반환합니다.|  
|**4**|가장 많이 수행 되는 25 개의 가장 낮은 구독을 반환 합니다.|  
|**5**|성능이 가장 낮은 50개의 구독을 반환합니다.|  
|**6**|현재 동기화 중인 구독만 반환합니다.|  
|**7**|현재 동기화 중이 아닌 구독만 반환합니다.|  
  
`[ @topnum = ] topnum` 반환 된 데이터의 맨 위에 있는 지정 된 수의 구독으로 결과 집합을 제한 합니다. *topnum* 은 **int**이며 기본값은 없습니다.  
  
`[ @exclude_anonymous = ] exclude_anonymous` 결과 집합에서 익명 끌어오기 구독을 제외할지 여부입니다. *exclude_anonymous* 은 **bit**이며 기본값은 **0**입니다. 값 **1** 은 익명 구독을 제외 하 고 값이 **0** 이면 포함 됨을 의미 합니다.  
  
`[ @refreshpolicy = ] refreshpolicy` 내부용 으로만 사용 됩니다.  
  
## <a name="result-sets"></a>결과 집합  
  
|열 이름|데이터 형식|Description|  
|-----------------|---------------|-----------------|  
|**status**|**int**|게시와 연결된 모든 복제 에이전트의 상태를 검사하고 다음 순서로 발견된 가장 높은 상태를 반환합니다.<br /><br /> **6** = 실패<br /><br /> **5** = 다시 시도 중<br /><br /> **2** = 중지 됨<br /><br /> **4** = 유휴 상태<br /><br /> **3** = 진행 중<br /><br /> **1** = 시작 됨|  
|**warning**|**int**|게시에 속한 구독에서 생성한 최대 임계값 경고로 다음 값 중 하나 이상의 논리 OR 결과일 수 있습니다.<br /><br /> **1** = 만료-트랜잭션 게시에 대 한 구독이 보존 기간 임계값 내에서 동기화 되지 않았습니다.<br /><br /> **2** = latency-트랜잭션 게시자에서 구독자로 데이터를 복제 하는 데 소요 된 시간이 임계값 (초)을 초과 합니다.<br /><br /> **4** = mergeexpiration-병합 게시에 대 한 구독이 보존 기간 임계값 내에서 동기화 되지 않았습니다.<br /><br /> **8** = mergefastrunduration-고속 네트워크 연결을 통해 병합 구독의 동기화를 완료 하는 데 소요 된 시간이 임계값 (초)을 초과 합니다.<br /><br /> **16** = mergeslowrunduration-저속 또는 전화 접속 네트워크 연결을 통해 병합 구독의 동기화를 완료 하는 데 소요 된 시간이 임계값 (초)을 초과 합니다.<br /><br /> **32** = mergefastrunspeed-고속 네트워크 연결을 통해 병합 구독을 동기화 하는 동안 행의 배달 속도가 임계값 속도 (초당 행 수)를 유지 하지 못했습니다.<br /><br /> **64** = mergeslowrunspeed-저속 또는 전화 접속 네트워크 연결을 통해 병합 구독을 동기화 하는 동안 행의 배달 속도가 임계값 속도 (초당 행 수)를 유지 하지 못했습니다.|  
|**구독자**|**sysname**|구독자의 이름입니다.|  
|**subscriber_db**|**sysname**|구독에 사용되는 데이터베이스의 이름입니다.|  
|**publisher_db**|**sysname**|게시 데이터베이스의 이름입니다.|  
|**게시물**|**sysname**|게시의 이름입니다.|  
|**publication_type**|**int**|게시 유형이며 다음 값 중 하나일 수 있습니다.<br /><br /> **0** = 트랜잭션 게시<br /><br /> **1** = 스냅숏 게시<br /><br /> **2** = 병합 게시|  
|**하위 형식**|**int**|구독 유형이며 다음 값 중 하나일 수 있습니다.<br /><br /> **0** = 푸시<br /><br /> **1** = 끌어오기<br /><br /> **2** = 익명|  
|**대기가**|**int**|트랜잭션 게시에 대해 로그 판독기 또는 배포 에이전트가 전파하는 데이터 변경에 대한 최대 대기 시간(초)입니다.|  
|**latencythreshold**|**int**|경고 발생의 기준이 되는 트랜잭션 게시에 대한 최대 대기 시간입니다.|  
|**agentnotrunning**|**int**|에이전트가 실행되지 않은 시간(시간)입니다.|  
|**agentnotrunningthreshold**|**int**|경고가 발생하기 전까지 에이전트가 실행되지 않은 시간(시간)입니다.|  
|**timetoexpiration**|**int**|구독이 동기화되지 않은 경우 만료되기 전까지의 시간(시간)입니다.|  
|**expirationthreshold**|**int**|경고가 발생한 구독이 만료되기 전까지의 시간(시간)입니다.|  
|**last_distsync**|**datetime**|배포 에이전트가 마지막으로 실행된 날짜/시간입니다.|  
|**distribution_agentname**|**sysname**|트랜잭션 게시 구독에 대한 배포 에이전트 작업의 이름입니다.|  
|**mergeagentname**|**sysname**|병합 게시 구독에 대한 병합 에이전트 작업의 이름입니다.|  
|**mergesubscriptionfriendlyname**|**sysname**|구독에 지정된 이름입니다.|  
|**mergeagentlocation**|**sysname**|병합 에이전트가 실행되는 서버의 이름입니다.|  
|**mergeconnectiontype**|**int**|구독과 병합 게시를 동기화할 때 사용하는 연결이며 다음 값 중 하나일 수 있습니다.<br /><br /> **1** = lan (local area network)<br /><br /> **2** = 전화 접속 네트워크 연결<br /><br /> **3** = 웹 동기화.|  
|**mergePerformance**|**int**|구독에 대한 모든 동기화 성능과 비교한 최근 동기화의 성능입니다. 최근 동기화의 배달 속도를 이전의 모든 배달 속도 평균으로 나눈 값을 기반으로 합니다.|  
|**mergerunspeed**|**float**|구독에 대한 최근 동기화의 배달 속도입니다.|  
|**mergerunduration**|**int**|구독의 최근 동기화를 완료하는 데 걸린 시간입니다.|  
|**monitorranking**|**int**|결과 집합에서 구독을 정렬하는 데 사용하는 순위 값이며 다음 값 중 하나일 수 있습니다.<br /><br /> 트랜잭션 게시인 경우<br /><br /> **60** = 오류<br /><br /> **56** = 경고: 성능 심각<br /><br /> **52** = 경고: 곧 만료 됨 또는 만료 됨<br /><br /> **50** = 경고: 구독이 초기화 되지 않음<br /><br /> **40** = 실패 한 명령 다시 시도 중<br /><br /> **30** = 실행 중이 아님 (성공)<br /><br /> **20** = 실행 중 (시작 중, 실행 중 또는 유휴 상태)<br /><br /> 병합 게시인 경우<br /><br /> **60** = 오류<br /><br /> **56** = 경고: 성능 심각<br /><br /> **54** = 경고: 장기 실행 병합<br /><br /> **52** = 경고: 곧 만료 됨<br /><br /> **50** = 경고: 구독이 초기화 되지 않음<br /><br /> **40** = 실패 한 명령 다시 시도 중<br /><br /> **30** = 실행 중 (시작 중, 실행 중 또는 유휴 상태)<br /><br /> **20** = 실행 중이 아님 (성공)|  
|**distributionagentjobid**|**binary(16)**|트랜잭션 게시 구독에 대한 배포 에이전트 작업의 ID입니다.|  
|**mergeagentjobid**|**binary(16)**|병합 게시 구독에 대한 병합 에이전트 작업의 ID입니다.|  
|**distributionagentid**|**int**|구독에 대한 배포 에이전트 작업의 ID입니다.|  
|**distributionagentprofileid**|**int**|배포 에이전트에서 사용하는 에이전트 프로필의 ID입니다.|  
|**mergeagentid**|**int**|구독에 대한 병합 에이전트 작업의 ID입니다.|  
|**mergeagentprofileid**|**int**|병합 에이전트에서 사용하는 에이전트 프로필의 ID입니다.|  
  
## <a name="return-code-values"></a>반환 코드 값  
 **0** (성공) 또는 **1** (실패)  
  
## <a name="remarks"></a>설명  
 **sp_replmonitorhelpsubscription** 은 모든 유형의 복제에 사용 됩니다.  
  
 **sp_replmonitorhelpsubscription** 는 *monitorranking*값에 따라 결정 되는 구독 상태의 심각도에 따라 결과 집합을 정렬 합니다. 예를 들어 오류 상태에 있는 모든 구독에 대한 행은 경고 상태에 있는 구독에 대한 행보다 위에 정렬됩니다.  
  
## <a name="permissions"></a>사용 권한  
 배포 데이터베이스에서 **db_owner** 또는 **replmonitor** 고정 데이터베이스 역할의 멤버만 **sp_replmonitorhelpsubscription**을 실행할 수 있습니다.  
  
## <a name="see-also"></a>참고 항목  
 [프로그래밍 방식으로 복제 모니터링](../../relational-databases/replication/monitor/programmatically-monitor-replication.md)  
  
  
