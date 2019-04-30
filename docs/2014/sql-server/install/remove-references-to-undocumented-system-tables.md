---
title: 문서화 되지 않은 시스템 테이블에 대 한 참조를 제거 합니다. | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- undocumented system tables [SQL Server]
- system tables [SQL Server]
ms.assetid: 010b1236-2219-4bf4-a6db-e3fc3abfa37a
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 0c2c25120191b88abcf177723749aa5c46ba44ff
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63294815"
---
# <a name="remove-references-to-undocumented-system-tables"></a>문서화되지 않은 시스템 테이블에 대한 참조를 제거합니다.
  이전 릴리스에서 문서화되지 않은 많은 시스템 테이블이 변경되었거나 더 이상 존재하지 않기 때문에 업그레이드한 후 이러한 테이블을 사용하면 오류가 발생할 수 있습니다. 업그레이드 관리자는 시스템 테이블 이름에 대한 참조를 찾기 때문에 시스템 테이블과 동일한 이름을 갖는 모든 사용자 테이블에 대한 참조를 보고합니다.  
  
## <a name="component"></a>구성 요소  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>Description  
 다음과 같은 문서화되지 않은 시스템 테이블이 제거되었습니다.  
  
-   **spt_datatype_info**  
  
-   **spt_datatype_info_ext**  
  
-   **spt_provider_types**  
  
-   **spt_server_info**  
  
-   **spt_values**  
  
-   **sysfulltextnotify**  
  
-   **syslocks**  
  
-   **sysproperties**  
  
-   **sysprotects_aux**  
  
-   **sysprotects_view**  
  
-   **SYSREMOTE_CATALOGS**  
  
-   **SYSREMOTE_COLUMN_PRIVILEGES**  
  
-   **SYSREMOTE_COLUMNS**  
  
-   **SYSREMOTE_FOREIGN_KEYS**  
  
-   **SYSREMOTE_INDEXES**  
  
-   **SYSREMOTE_PRIMARY_KEYS**  
  
-   **SYSREMOTE_PROVIDER_TYPES**  
  
-   **SYSREMOTE_SCHEMATA**  
  
-   **SYSREMOTE_STATISTICS**  
  
-   **SYSREMOTE_TABLE_PRIVILEGES**  
  
-   **SYSREMOTE_TABLES**  
  
-   **SYSREMOTE_VIEWS**  
  
-   **syssegments**  
  
-   **sysxlogins**  
  
## <a name="corrective-action"></a>수정 동작  
 다음 표에 따라 애플리케이션을 수정합니다.  
  
|이전|이후|  
|----------------|---------|  
|**sysfulltextnotify**|OBJECTPROPERTYEX 함수의**TableFulltextPendingChanges** 속성|  
|**syslocks**|**sys.dm_tran_locks** 동적 관리 뷰, sp_lock 또는 **sys.syslockinfo** 호환성 뷰|  
|**sysproperties**|**sys.extended_properties** 카탈로그 뷰 또는 **fn_listextendedproperty** 함수|  
|**sysxlogins**|**sys.server_principals** 카탈로그 뷰 또는 **syslogins** 호환성 뷰|  
|모든 **spt_** 테이블|사용 가능한 대체 항목 없음|  
  
## <a name="see-also"></a>관련 항목  
 [데이터베이스 엔진 업그레이드 문제](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [SQL Server 2014 업그레이드 관리자 &#91;새로 만들기&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
