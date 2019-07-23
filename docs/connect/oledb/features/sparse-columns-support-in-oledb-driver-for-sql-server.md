---
title: SQL Server용 OLE DB 드라이버에서 스파스 열 지원 | Microsoft Docs
description: SQL Server용 OLE DB 드라이버에서 스파스 열 지원
ms.custom: ''
ms.date: 06/12/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- sparse columns, OLE DB Driver for SQL Server
- sparse columns, OLE DB
author: pmasl
ms.author: pelopes
ms.openlocfilehash: 7b617ecdbf2977372dbb006baaec4c791b988ef8
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67988908"
---
# <a name="sparse-columns-support-in-ole-db-driver-for-sql-server"></a>SQL Server용 OLE DB 드라이버에서 스파스 열 지원
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  SQL Server에 대 한 OLE DB 드라이버는 스파스 열을 지원 합니다. 의 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]스파스 열에 대 한 자세한 내용은 [스파스 열 사용](../../../relational-databases/tables/use-sparse-columns.md) 및 [열 집합 사용](../../../relational-databases/tables/use-column-sets.md)을 참조 하세요.  
  
 SQL Server용 OLE DB 드라이버에서 스파스 열 지원에 대한 자세한 내용은 [스파스 열 지원(OLE DB)](../../oledb/ole-db/sparse-columns-support-ole-db.md)을 참조하세요.  
  
 이 기능을 보여 주는 예제 애플리케이션에 대한 자세한 내용은 [SQL Server 데이터 프로그래밍 예제](https://msftdpprodsamples.codeplex.com/)를 참조하십시오.  
  
## <a name="user-scenarios-for-sparse-columns-and-ole-db-driver-for-sql-server"></a>스파스 열에 대 한 사용자 시나리오 및 SQL Server에 대 한 OLE DB 드라이버  
 다음 표에는 스파스 열을 사용 하는 SQL Server 사용자의 OLE DB 드라이버에 대 한 일반적인 사용자 시나리오가 요약 되어 있습니다.  
  
|시나리오|동작|  
|--------------|--------------|  
|**select\* from table** 또는 iopenrowset:: OpenRowset.|스파스 **column_set**의 멤버가 아닌 모든 열과 스파스 **column_set**의 null이 아닌 모든 열의 값이 포함된 XML 열을 반환합니다.|  
|이름으로 열 참조|열이 스파스 열인지 또는 **column_set**의 멤버인지 여부에 관계없이 열을 참조할 수 있습니다.|  
|XML 계산 열을 통해 **column_set** 멤버 열에 액세스합니다.|이름으로 **column_set**을 선택하여 스파스 **column_set**의 멤버인 열에 액세스할 수 있고 **column_set** 열의 XML을 업데이트하여 값을 삽입하고 업데이트할 수 있습니다.<br /><br /> 값은 **column_set** 열에 대한 스키마를 따라야 합니다.|  
|열 제한이 없는 DBSCHEMA_COLUMNS 스키마 행 집합을 통해 테이블의 모든 열에 대 한 메타 데이터를 검색 합니다 (OLE DB).|**column_set**의 멤버가 아닌 모든 열에 대해 한 개의 행을 반환합니다. 테이블에 스파스 **column_set**이 있으면 이에 대해 한 개의 행이 반환됩니다.<br /><br /> **column_set**의 멤버인 열에 대해서는 메타데이터를 반환하지 않습니다.|  
|열이 스파스 열인지 또는 **column_set**의 멤버인지 여부에 관계없이 모든 열의 메타데이터 검색. 이 경우 많은 수의 행이 반환될 수 있습니다.|DBSCHEMA_COLUMNS_EXTENDED 스키마 행 집합에 대해 IDBSchemaRowset:: GetRowset을 호출 합니다.|  
|**column_set**의 멤버인 열에 대해서만 메타데이터 검색. 이 경우 많은 수의 행이 반환될 수 있습니다.|DBSCHEMA_SPARSE_COLUMN_SET 스키마 행 집합에 대해 IDBSchemaRowset:: GetRowset을 호출 합니다.|  
|열이 스파스 열인지 여부 확인|DBSCHEMA_COLUMNS 스키마 행 집합의 SS_IS_SPARSE 열을 확인합니다(OLE DB).|  
|열이 **column_set**인지 여부를 확인 합니다.|DBSCHEMA_COLUMNS 스키마 행 집합의 SS_IS_COLUMN_SET 열을 확인합니다. 또는 IColumnsRowset:: GetColumnsRowset에서 반환 된 행 집합의 IColumnsinfo:: GetColumnInfo 또는 DBCOLUMNFLAGS에서 반환 된 *dwFlags* 를 참조 하세요. **column_set** 열의 경우 DBCOLUMNFLAGS_SS_ISCOLUMNSET이 설정됩니다.|  
|**column_set**이 없는 테이블에 대해 BCP를 사용하여 스파스 열 가져오기 및 내보내기.|SQL Server에 대 한 OLE DB 드라이버의 이전 버전에서의 동작이 변경 되지 않았습니다.|  
|**column_set**이 있는 테이블에 대해 BCP를 사용하여 스파스 열 가져오기 및 내보내기.|**Column_set** 은 XML과 같은 방식으로 가져오고 내보냅니다. 즉, 이진 형식으로 바인딩된 경우 **varbinary (max)** 로, **char** 또는 **wchar** 형식으로 바인딩되는 경우 **nvarchar (max)** 로 계산 합니다.<br /><br /> 스파스 **column_set**의 멤버인 열은 별개의 열로 내보내지 않습니다. 이러한 열은 **column_set**의 값으로만 내보냅니다.|  
|BCP에 대 한 **queryout** 동작입니다.|SQL Server에 대 한 OLE DB 드라이버의 이전 버전에서 명시적으로 명명 된 열의 처리는 변경 되지 않습니다.<br /><br /> 스키마가 서로 다른 테이블 간의 가져오기 및 내보내기가 포함된 시나리오의 경우 특수 처리가 필요할 수도 있습니다.<br /><br /> BCP에 대한 자세한 내용은 이 항목의 뒤에 나오는 스파스 열에 대한 BCP(대량 복사) 지원을 참조하십시오.|  
  
## <a name="down-level-client-behavior"></a>하위 수준 클라이언트 동작  
 하위 수준 클라이언트는 SQLColumns 및 DBSCHMA_COLUMNS에 대해 스파스 **column_set**의 멤버가 아닌 열에 대해서만 메타데이터를 반환합니다.
  
 하위 수준 클라이언트는 스파스 **column_set**의 멤버인 열에 이름으로 액세스할 수 있습니다. **column_set** 열은 XML 열로 [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] 클라이언트에 액세스할 수 있습니다.  
  
## <a name="bulk-copy-bcp-support-for-sparse-columns"></a>스파스 열에 대한 BCP(대량 복사) 지원  
 스파스 열이나 **column_set** 기능과 관련해서는 OLE DB의 BCP API에 변경된 사항이 없습니다.  
  
 테이블에 **column_set**이 있으면 스파스 열이 별개의 열로 처리되지 않습니다. 모든 스파스 열의 값은 XML 열과 동일한 방식으로 내보내지는 **column_set**의 값에 포함 됩니다. 즉, 이진 형식으로 바인딩된 경우 **varbinary (max)** 로, **char** 또는 **wchar** 형식으로 바인딩되는 경우 **nvarchar (max)** 로 계산 합니다. 가져올 때 **column_set** 값은 **column_set**의 스키마를 준수 해야 합니다.  
  
 **queryout** 작업의 경우 명시적으로 참조된 열의 처리 방법에는 변경된 사항이 없습니다. **column_set** 열은 XML 열과 동작이 같고 스파스 열인지 여부는 명명된 스파스 열의 처리에 어떠한 영향도 주지 않습니다.  
  
 그러나 내보내기 작업에 **queryout**을 사용하고 스파스 열 집합의 멤버인 스파스 열을 이름으로 참조하는 경우 구조가 비슷한 테이블에는 직접 내보낼 수 없습니다. 이는 BCP가 가져오기 작업에서 **select \*** 작업과 일치하는 메타데이터를 사용하는데 **column_set** 멤버 열을 이 메타데이터와 일치시킬 수 없기 때문입니다. **column_set** 멤버 열을 개별적으로 가져오려면 원하는 **column_set** 열을 참조하는 뷰를 테이블에서 정의한 다음, 이 뷰를 사용해 가져오기 작업을 수행해야 합니다.  
  
## <a name="see-also"></a>참고 항목  
 [SQL Server용 OLE DB 드라이버](../../oledb/oledb-driver-for-sql-server.md)  
  
  
