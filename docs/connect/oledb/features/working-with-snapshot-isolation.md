---
title: Snapshot 격리 작업 | Microsoft Docs
description: SQL Server에 대 한 OLE DB 드라이버에서 스냅숏 격리 작업
ms.custom: ''
ms.date: 06/12/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- data access [OLE DB Driver for SQL Server], snapshot isolation
- MSOLEDBSQL, snapshot isolation
- isolation levels [SQL Server], snapshot
- DBPROPSET_SESSION property set
- DBDROPSET_DATASOURCEINFO property set
- snapshot isolation [OLE DB Driver for SQL Server]
- OLE DB Driver for SQL Server, snapshot isolation
- SQLGetInfo function
- concurrency [OLE DB Driver for SQL Server]
- SQLSetConnectAttr function
author: pmasl
ms.author: pelopes
ms.openlocfilehash: 25d3dbaf09e5cdd6dc6726402275376766cf0591
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67988692"
---
# <a name="working-with-snapshot-isolation"></a>스냅샷 격리 작업
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]에서는 OLTP(온라인 트랜잭션 처리) 응용 프로그램의 동시성을 향상시키기 위한 새로운 "스냅샷" 격리 수준이 도입되었습니다. 이전 버전의 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]에서는 동시성이 일부 애플리케이션에 대해 문제 차단 및 교착 상태를 발생시킬 수 있는 잠금 기능에만 의존했습니다. 스냅샷 격리는 향상된 행 버전 관리 기능을 사용하며 읽기/쓰기 차단 시나리오를 방지하여 성능을 향상시킵니다.  
  
 스냅샷 격리 하에 시작된 트랜잭션은 트랜잭션이 시작된 시간을 기준으로 데이터베이스 스냅샷을 읽습니다. 스냅샷 트랜잭션 컨텍스트 내에서 열린 키 집합, 동적 및 정적 서버 커서가 직렬화 가능 트랜잭션 내에서 열린 정적 커서처럼 동작합니다. 그러나 스냅숏 격리 수준에서 커서가 열려 있으면 잠금이 수행 되지 않습니다. 이 사실은 서버에서 차단을 줄일 수 있습니다.  
  
## <a name="ole-db-driver-for-sql-server"></a>SQL Server용 OLE DB 드라이버  
 SQL Server에 대 한 OLE DB 드라이버에는에 [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]도입 된 스냅숏 격리를 활용 하는 향상 된 기능이 있습니다. 이러한 향상된 기능에는 DATASOURCEINFO 및 DBPROPSET_SESSION 속성 집합의 변경 내용이 포함됩니다.  
  
### <a name="dbpropset_datasourceinfo"></a>DBPROPSET_DATASOURCEINFO  
 DBPROPSET_DATASOURCEINFO 속성 집합은 DBPROP_SUPPORTEDTXNISOLEVELS 속성에 사용되는 DBPROPVAL_TI_SNAPSHOT 값을 추가하여 스냅샷 격리 수준이 지원됨을 나타내도록 변경되었습니다. 이 새로운 값은 데이터베이스에 버전 관리가 설정되어 있는지 여부에 관계없이 스냅샷 격리 수준이 지원됨을 나타냅니다. 다음 표에서는 DBPROP_SUPPORTEDTXNISOLEVELS 값을 보여 줍니다.  
  
|속성 ID|설명|  
|-----------------|-----------------|  
|DBPROP_SUPPORTEDTXNISOLEVELS|형식: VT_I4<br /><br /> R/W: 읽기 전용<br /><br /> 설명: 지원되는 트랜잭션 격리 수준을 지정하는 비트 마스크입니다. 다음을 0개 이상 조합하여 지정합니다.<br /><br /> DBPROPVAL_TI_CHAOS<br /><br /> DBPROPVAL_TI_READUNCOMMITTED<br /><br /> DBPROPVAL_TI_BROWSE<br /><br /> DBPROPVAL_TI_CURSORSTABILITY<br /><br /> DBPROPVAL_TI_READCOMMITTED<br /><br /> DBPROPVAL_TI_REPEATABLEREAD<br /><br /> DBPROPVAL_TI_SERIALIZABLE<br /><br /> DBPROPVAL_TI_ISOLATED<br /><br /> DBPROPVAL_TI_SNAPSHOT|  
  
### <a name="dbpropset_session"></a>DBPROPSET_SESSION  
 DBPROPSET_SESSION 속성 집합은 DBPROP_SESS_AUTOCOMMITISOLEVELS 속성에 사용되는 DBPROPVAL_TI_SNAPSHOT 값을 추가하여 스냅샷 격리 수준이 지원됨을 나타내도록 변경되었습니다. 이 새로운 값은 데이터베이스에 버전 관리가 설정되어 있는지 여부에 관계없이 스냅샷 격리 수준이 지원됨을 나타냅니다. 다음 테이블은 DBPROP_SESS_AUTOCOMMITISOLEVELS 값을 나열합니다.
  
|속성 ID|설명|  
|-----------------|-----------------|  
|DBPROP_SESS_AUTOCOMMITISOLEVELS|형식: VT_I4<br /><br /> R/W: 읽기 전용<br /><br /> 설명: 자동 커밋 모드에서 트랜잭션 격리 수준을 나타내는 비트 마스크를 지정합니다. 이 비트 마스크에 설정할 수 있는 값은 DBPROP_SUPPORTEDTXNISOLEVELS에 설정할 수 있는 값과 같습니다.|  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]보다 이전 버전의 [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]를 사용할 때 DBPROPVAL_TI_SNAPSHOT을 설정하면 오류 DB_S_ERRORSOCCURRED 또는 DB_E_ERRORSOCCURRED가 발생합니다.  
  
 트랜잭션에서 스냅숏 격리가 지원 되는 방법에 대 한 자세한 내용은 [로컬 트랜잭션 지원](../../oledb/ole-db-transactions/supporting-local-transactions.md)을 참조 하세요.  

  
## <a name="see-also"></a>참고 항목  
 [SQL Server 기능용 OLE DB 드라이버](../../oledb/features/oledb-driver-for-sql-server-features.md)    
 [행 집합 속성 및 동작](../../oledb/ole-db-rowsets/rowset-properties-and-behaviors.md)  
  
  
