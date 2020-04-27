---
title: sys. fn_MSxe_read_event_stream (Transact-sql) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- fn_MSxe_read_event_stream_TSQL
- sys.fn_MSxe_read_event_stream_TSQL
- sys.fn_MSxe_read_event_stream
- fn_MSxe_read_event_stream
dev_langs:
- TSQL
helpviewer_keywords:
- sys.fn_MSxe_read_event_stream
- fn_MSxe_read_event_stream
ms.assetid: 5edb1162-625a-41e0-8ec9-1edc8ab9a74a
author: rothja
ms.author: jroth
ms.openlocfilehash: 886b874aeee47f71eb8b50dba27fdfdf8ea45c62
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/26/2020
ms.locfileid: "68082687"
---
# <a name="sysfn_msxe_read_event_stream-transact-sql"></a>sys.fn_MSxe_read_event_stream(Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  확장 이벤트는 확장 이벤트 UI(사용자 인터페이스)에서 내부용으로 사용하는 TVF(테이블 반환 함수)를 제공합니다. 테이블에 고객이 사용 가능한 데이터는 제공되지 않습니다.  
  
 이벤트 데이터를 보려면 다음 중 하나를 사용합니다.  
  
-   확장 이벤트의 새 세션 UI.  
  
-   fn_xe_file_target_read_file TVF. 자세한 내용은 [sys.fn_xe_file_target_read_file&#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-xe-file-target-read-file-transact-sql.md)을 참조하세요.  
  
  
 ![항목 링크 아이콘](../../database-engine/configure-windows/media/topic-link.gif "항목 링크 아이콘") [Transact-SQL 구문 표기 규칙](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>구문  
  
```  
  
sys.fn_MSxe_read_event_stream ( session_name)  
```  
  
## <a name="arguments"></a>인수  
 *Session_name*  
 서버에서 실행 중인 세션의 이름입니다.  
  
## <a name="table-returned"></a>반환된 테이블  
  
|열 이름|데이터 형식|Description|  
|-----------------|---------------|-----------------|  
|type|**Integer(4)**|이벤트 유형입니다. Null을 허용하지 않습니다.|  
|데이터|**Image(16)**|이벤트 이미지 데이터로, Null을 허용합니다.|  
  
## <a name="see-also"></a>참고 항목  
 [확장 이벤트 동적 관리 뷰](../../relational-databases/system-dynamic-management-views/extended-events-dynamic-management-views.md)   
 [Transact-sql&#41;&#40;확장 이벤트 카탈로그 뷰](../../relational-databases/system-catalog-views/extended-events-catalog-views-transact-sql.md)   
 [확장 이벤트](../../relational-databases/extended-events/extended-events.md)  
  
  
