---
title: MSSQLSERVER_107 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 107 (Database Engine error)
ms.assetid: f33f514c-56aa-42e2-841b-e91244da90e2
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: bea6901e999f1bb236e94e220c3cfeac53119e16
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2020
ms.locfileid: "62870559"
---
# <a name="mssqlserver_107"></a>MSSQLSERVER_107
    
## <a name="details"></a>세부 정보  
  
|||  
|-|-|  
|제품 이름|SQL Server|  
|이벤트 ID|107|  
|이벤트 원본|MSSQLSERVER|  
|구성 요소|SQLEngine|  
|심볼 이름|P_NOCORRMATCH|  
|메시지 텍스트|열 접두사 '%.*ls'이(가) 쿼리에 사용된 테이블 이름 또는 별칭과 일치하지 않습니다.|  
  
## <a name="explanation"></a>설명  
 쿼리의 SELECT 목록에 열 접두사로 잘못 한정된 별표(*)가 포함되어 있습니다. 이 오류는 다음과 같은 경우에 반환될 수 있습니다.  
  
-   열 접두사가 쿼리에 사용된 테이블 또는 별칭 이름과 일치하지 않습니다. 예를 들어 다음 문에서는 별칭 이름(`T1`)을 열 접두사로 사용하고 있지만 FROM 절에는 별칭이 정의되지 않았습니다.  
  
    ```  
    SELECT T1.* FROM dbo.ErrorLog;  
    ```  
  
-   FROM 절에 테이블에 대한 별칭 이름을 제공하면 테이블 이름이 열 접두사로 지정됩니다. 예를 들어 다음 문에서는 테이블 이름 `ErrorLog`를 열 접두사로 사용하지만 테이블에는 FROM 절에 정의된 별칭(`T1`)이 있습니다.  
  
    ```  
    SELECT ErrorLog.* FROM dbo.ErrorLog AS T1;  
    ```  
  
     FROM 절에 테이블 이름에 대한 별칭을 제공한 경우 테이블에서 해당 별칭만 열 접두사로 사용할 수 있습니다.  
  
## <a name="user-action"></a>사용자 동작  
 쿼리의 FROM 절에 지정된 테이블 이름 또는 별칭 이름과 열 접두사가 일치하도록 수정하십시오. 예를 들어 위의 문은 다음과 같이 수정할 수 있습니다.  
  
```  
SELECT T1.* FROM dbo.ErrorLog AS T1;  
```  
  
 또는  
  
```  
SELECT ErrorLog.* FROM dbo.ErrorLog;  
```  
  
## <a name="see-also"></a>참고 항목  
 [MSSQLSERVER_4104](mssqlserver-4104-database-engine-error.md)  
  
  
