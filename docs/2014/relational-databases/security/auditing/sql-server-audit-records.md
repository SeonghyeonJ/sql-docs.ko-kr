---
title: SQL Server Audit 레코드 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- audit records [SQL Server]
ms.assetid: 7a291015-df15-44fe-8d53-c6d90a157118
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: 3cc249ebfce796d7932e68d993ac98ede867845f
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/26/2020
ms.locfileid: "63238383"
---
# <a name="sql-server-audit-records"></a>SQL Server Audit 레코드
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Audit 기능을 통해 서버 수준 및 데이터베이스 수준의 이벤트와 이벤트 그룹을 감사할 수 있습니다. 자세한 내용은 [SQL Server Audit&#40;데이터베이스 엔진&#41;](sql-server-audit-database-engine.md)을 참조하세요. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]입니다.  
  
 감사는 0개 이상의 감사 동작 항목으로 구성되어 있으며 이들은 감사 *대상*에 기록됩니다. 이진 파일, Windows 애플리케이션 이벤트 로그 또는 Windows 보안 이벤트 로그가 감사 대상이 될 수 있습니다. 대상에 전달된 레코드에는 다음 표에 설명된 요소가 포함될 수 있습니다.  
  
|열 이름|Description|Type|항상 사용 가능 여부|  
|-----------------|-----------------|----------|----------------------|  
|**event_time**|감사 가능한 동작이 발생한 날짜/시간입니다.|`datetime2`|예|  
|**sequence_no**|너무 커서 감사에 대한 쓰기 버퍼에 맞지 않는 단일 감사 레코드 내의 레코드 시퀀스를 추적합니다.|`int`|예|  
|**action_id**|동작의 ID입니다.<br /><br /> 팁: **action_id** 를 조건자로 사용하려면 문자열에서 숫자 값으로 변환해야 합니다. 자세한 내용은 [action_id/class_type 조건자에서 SQL Server 감사 필터링](https://blogs.msdn.com/b/sqlsecurity/archive/2012/10/03/filter-sql-server-audit-on-action-id-class-type-predicate.aspx)을 참조하세요.|`varchar(4)`|예|  
|**열었습니다**|이벤트를 발생시킨 동작의 성공 여부를 나타냅니다.|`bit`-1 = 성공, 0 = 실패|예|  
|**permission_bitmask**|해당되는 경우 부여, 거부 또는 취소된 사용 권한을 표시합니다.|`bigint`|아니요|  
|**is_column_permission**|열 수준 사용 권한을 나타내는 플래그입니다.|`bit`-1 = True, 0 = False|아니요|  
|**session_id**|이벤트가 발생한 세션의 ID입니다.|`int`|예|  
|**server_principal_id**|동작을 수행한 로그인 컨텍스트의 ID입니다.|`int`|예|  
|**database_principal_id**|동작을 수행한 데이터베이스 사용자 컨텍스트의 ID입니다.|`int`|아니요|  
|**object_ id**|감사가 수행된 엔터티의 주 ID이며 여기에는 다음이 포함됩니다.<br /><br /> 서버 개체<br /><br /> 데이터베이스<br /><br /> 데이터베이스 개체<br /><br /> 스키마 개체|`int`|아니요|  
|**target_server_principal_id**|감사 가능한 동작이 적용되는 서버 보안 주체입니다.|`int`|예|  
|**target_database_principal_id**|감사 가능한 동작이 적용되는 데이터베이스 보안 주체입니다.|`int`|아니요|  
|**class_type**|감사가 수행되는 감사 가능한 엔터티의 형식입니다.|`varchar(2)`|예|  
|**session_server_principal_name**|세션의 서버 보안 주체입니다.|`sysname`|예|  
|**server_principal_name**|현재 로그인입니다.|`sysname`|예|  
|**server_principal_sid**|현재 로그인 SID입니다.|`varbinary`|예|  
|**database_principal_name**|현재 사용자입니다.|`sysname`|아니요|  
|**target_server_principal_name**|동작의 대상 로그인입니다.|`sysname`|아니요|  
|**target_server_principal_sid**|대상 로그인의 SID입니다.|`varbinary`|아니요|  
|**target_database_principal_name**|동작의 대상 사용자입니다.|`sysname`|아니요|  
|**server_instance_name**|감사가 수행된 서버 인스턴스의 이름입니다. 표준 machine\instance 형식을 사용합니다.|`nvarchar(120)`|예|  
|**database_name**|동작이 수행된 데이터베이스 컨텍스트입니다.|`sysname`|아니요|  
|**schema_name**|동작이 수행된 스키마 컨텍스트입니다.|`sysname`|예|  
|**object_name**|감사가 수행된 대상 엔터티의 이름입니다. 여기에는 다음이 포함됩니다.<br /><br /> 서버 개체<br /><br /> 데이터베이스<br /><br /> 데이터베이스 개체<br /><br /> 스키마 개체<br /><br /> TSQL 문(있는 경우)|`sysname`|아니요|  
|**선언문**|TSQL 문(있는 경우)|`nvarchar(4000)`|예|  
|**additional_information**|이벤트에 대한 추가 정보이며 XML로 저장됩니다.|`nvarchar(4000)`|아니요|  
  
## <a name="remarks"></a>설명  
 일부 동작은 적용되지 않을 수 있는 열 값을 채우지 않습니다.  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Audit는 감사 레코드의 문자 필드 하나당 4000자의 데이터를 저장합니다. 감사 가능한 동작에서 반환된 **additional_information** 및 **statement** 값이 4000자를 넘는 경우 **sequence_no** 열을 사용하여 단일 감사 동작에 대한 감사 보고서에 여러 레코드를 작성함으로써 이 데이터를 기록합니다. 프로세스는 다음과 같습니다.  
  
-   **statement** 열이 4000자씩 나누어집니다.  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Audit는 일부 데이터와 함께 감사 레코드에 대한 첫 번째 행으로 기록됩니다. 다른 모든 필드는 각 행에 복제됩니다.  
  
-   **sequence_no** 값이 증가합니다.  
  
-   모든 데이터가 기록될 때까지 이 프로세스가 반복됩니다.  
  
 **sequence_no** 값을 사용하여 행을 순서대로 읽고 **event_Time**, **action_id** 및 **session_id** 열을 사용하여 동작을 식별함으로써 데이터를 연결할 수 있습니다.  
  
## <a name="related-content"></a>관련 내용  
 [CREATE SERVER AUDIT&#40;Transact-SQL&#41;](/sql/t-sql/statements/create-server-audit-transact-sql)  
  
 [ALTER SERVER AUDIT  &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-server-audit-specification-transact-sql)  
  
 [DROP SERVER AUDIT  &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-server-audit-transact-sql)  
  
 [CREATE SERVER AUDIT SPECIFICATION &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-server-audit-specification-transact-sql)  
  
 [ALTER SERVER AUDIT SPECIFICATION &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-server-audit-transact-sql)  
  
 [DROP SERVER AUDIT SPECIFICATION &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-server-audit-specification-transact-sql)  
  
 [CREATE DATABASE AUDIT SPECIFICATION &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-database-audit-specification-transact-sql)  
  
 [ALTER DATABASE AUDIT SPECIFICATION &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-audit-specification-transact-sql)  
  
 [DROP DATABASE AUDIT SPECIFICATION &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-database-encryption-key-transact-sql)  
  
 [ALTER AUTHORIZATION &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-authorization-transact-sql)  
  
 [sys.fn_get_audit_file &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/sys-fn-get-audit-file-transact-sql)  
  
 [sys.server_audits &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-server-audits-transact-sql)  
  
 [sys.server_file_audits &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-server-file-audits-transact-sql)  
  
 [sys.server_audit_specifications &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-server-audit-specifications-transact-sql)  
  
 [sys.server_audit_specification_details &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-server-audit-specification-details-transact-sql)  
  
 [sys.database_audit_specifications &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-audit-specifications-transact-sql)  
  
 [sys.database_audit_specification_details &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-audit-specification-details-transact-sql)  
  
 [sys.dm_server_audit_status &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-server-audit-status-transact-sql)  
  
 [sys.dm_audit_actions &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-audit-actions-transact-sql)  
  
 [sys.dm_audit_class_type_map &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-audit-class-type-map-transact-sql)  
  
  
