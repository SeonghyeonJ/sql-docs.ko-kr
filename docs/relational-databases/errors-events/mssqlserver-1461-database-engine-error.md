---
title: MSSQLSERVER_1461 | Microsoft 문서
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 1461 (Database Engine error)
ms.assetid: fce10907-4753-441b-b624-f28e00ed7520
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 6411b8eaf64daf16bc42636950f43fd37104629a
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/01/2020
ms.locfileid: "68033455"
---
# <a name="mssqlserver_1461"></a>MSSQLSERVER_1461
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>세부 정보  
  
|||  
|-|-|  
|제품 이름|SQL Server|  
|이벤트 ID|1461|  
|이벤트 원본|MSSQLSERVER|  
|구성 요소|SQLEngine|  
|심볼 이름|DBM_SAFETY_MISMATCH|  
|메시지 텍스트|데이터베이스 "%.*ls"에 대한 데이터베이스 미러링 보안 수준이 서버마다 다릅니다. FULL 보안 수준이 사용됩니다.|  
  
## <a name="explanation"></a>설명  
트랜잭션 보안 설정이 주 데이터베이스 및 미러 데이터베이스에서 일관성이 없어 트랜잭션 보안 수준이 수정되는 동안 미러링 연결이 끊어졌습니다. 전체 트랜잭션 보안의 기본 보안 설정을 사용합니다. 세션은 보호 우선 모드에서 실행됩니다.  
  
## <a name="user-action"></a>사용자 동작  
트랜잭션 보안 해제를 설정하려면 ALTER DATABASE *database_name* SET PARTNER SAFETY OFF 문을 주 데이터베이스에서 다시 실행하세요.  
  
