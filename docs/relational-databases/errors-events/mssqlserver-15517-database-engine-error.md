---
title: MSSQLSERVER_15517 | Microsoft 문서
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 15517 (Database Engine error)
ms.assetid: f94287f5-129f-4c52-9d34-62b996088001
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c4b1ec66d80f04d15f9671baa79ee55e3b6a2736
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85780966"
---
# <a name="mssqlserver_15517"></a>MSSQLSERVER_15517
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>세부 정보  
  
| attribute | 값 |  
| :-------- | :---- |  
|제품 이름|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|이벤트 ID|15517|  
|이벤트 원본|MSSQLSERVER|  
|구성 요소|SQLEngine|  
|심볼 이름|SEC_CANNOTEXECUTEASUSER|  
|메시지 텍스트|보안 주체 "*principal*"이(가) 없거나 이 유형의 보안 주체를 가장할 수 없거나 사용 권한이 없기 때문에 데이터베이스 보안 주체로 실행할 수 없습니다.|  
  
## <a name="user-action"></a>사용자 동작  
기존 보안 주체의 이름을 사용하거나 해당 보안 주체에 대한 IMPERSONATE 권한을 가져옵니다.  
  
15517은 원래 데이터베이스 소유자 이외의 다른 사용자가 데이터베이스 연결 및 복원을 수행한 후에 발생할 수 있습니다. 이 오류를 해결하려면 다음 명령을 실행해서 db_owner를 서버의 로그인 계정으로 변경합니다.  
  
```  
ALTER AUTHORIZATION ON DATABASE:: DBName TO [NewLogin]  
```  
  
## <a name="see-also"></a>참고 항목  
[메모리 내 OLTP&#40;메모리 내 최적화&#41;](~/relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
