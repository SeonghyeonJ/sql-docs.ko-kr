---
description: sys.database_event_session_targets(Azure SQL Database)
title: database_event_session_targets (Azure SQL Database) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
ms.assetid: 38d775ee-1fe1-4820-88c6-02b2f875a66b
author: markingmyname
ms.author: maghan
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 680cac9474fd63806c046ffeede22e83c04773c5
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89537399"
---
# <a name="sysdatabase_event_session_targets-azure-sql-database"></a>sys.database_event_session_targets(Azure SQL Database)

[!INCLUDE [sqlserver2016-asdb-asdbmi](../../includes/applies-to-version/sqlserver2016-asdb-asdbmi.md)]

  이벤트 세션의 각 이벤트 대상에 대해 한 행을 반환합니다.  
  
||  
|-|  
|**적용**대상: [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] V12 이상 버전.|  
  
|열 이름|데이터 형식|Description|  
|-----------------|---------------|-----------------|  
|event_session_id|**int**|이벤트 세션의 ID입니다. Null을 허용하지 않습니다.|  
|target_id|**int**|대상의 ID입니다. ID는 이벤트 세션 개체 내에서 고유합니다. Null을 허용하지 않습니다.|  
|name|**sysname**|이벤트 대상의 이름입니다. Null을 허용하지 않습니다.|  
|패키지|**sysname**|이벤트 대상이 포함된 이벤트 패키지의 이름입니다. Null을 허용하지 않습니다.|  
|모듈(module)|**sysname**|이벤트 대상이 포함된 모듈의 이름입니다. Null을 허용하지 않습니다.|  
  
## <a name="permissions"></a>사용 권한  
 서버에 대한 VIEW DATABASE STATE 권한이 필요합니다.  
  
## <a name="remarks"></a>설명  
 이 뷰는 다음과 같은 관계 카디널리티를 가집니다.  
  
|시작|대상|관계|  
|-|-|-|  
|database_event_session_targets. event_session_id|database_event_sessions. event_session_id|다 대 일|  
  
## <a name="see-also"></a>참고 항목  
 [확장 이벤트](../../relational-databases/extended-events/extended-events.md)  
  
  
