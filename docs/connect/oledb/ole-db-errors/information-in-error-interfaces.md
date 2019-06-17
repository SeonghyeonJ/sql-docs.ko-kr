---
title: 오류 인터페이스의 정보 | Microsoft Docs
description: 오류 인터페이스의 정보
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- OLE DB Driver for SQL Server, errors
- IErrorRecords interface
- IErrorInfo interface
- OLE DB error handling, error interfaces
- ISQLErrorInfo interface
- errors [OLE DB], error interfaces
author: pmasl
ms.author: pelopes
manager: jroth
ms.openlocfilehash: 7b87011fc8d95d617562bb72ce6a3a6ee49ae0c5
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 06/07/2019
ms.locfileid: "66798126"
---
# <a name="information-in-error-interfaces"></a>오류 인터페이스의 정보
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  SQL Server용 OLE DB 드라이버는 OLE DB에서 정의된 오류 인터페이스 **IErrorInfo**, **IErrorRecords** 및 **ISQLErrorInfo**의 몇 가지 오류 및 상태 정보를 보고합니다.  
  
 OLE DB Driver for SQL Server 지원 **IErrorInfo** 멤버 함수를 다음과 같이 합니다.  
  
|멤버 함수|설명|  
|---------------------|-----------------|  
|**GetDescription**|설명적인 오류 메시지 문자열입니다.|  
|**GetGUID**|오류를 정의한 인터페이스의 GUID입니다.|  
|**GetHelpContext**|지원되지 않습니다. 항상 0을 반환합니다.|  
|**GetHelpFile**|지원되지 않습니다. 항상 NULL을 반환합니다.|  
|**GetSource**|“SQL Server용 Microsoft OLE DB 드라이버” 문자열입니다.|  
  
 OLE DB Driver for SQL Server 소비자가 사용할 수 있는 지원 **IErrorRecords** 멤버 함수를 다음과 같이 합니다.  
  
|멤버 함수|설명|  
|---------------------|-----------------|  
|**GetBasicErrorInfo**|ERRORINFO 구조에 오류에 대한 기본 정보를 채웁니다. ERRORINFO 구조에는 오류에 대한 HRESULT 반환 값을 식별하는 멤버와 오류가 적용되는 공급자 및 인터페이스가 포함됩니다.|  
|**GetCustomErrorObject**|**ISQLErrorInfo** 및 [ISQLServerErrorInfo](https://msdn.microsoft.com/library/a8323b5c-686a-4235-a8d2-bda43617b3a1) 인터페이스에 대한 참조를 반환합니다.|  
|**GetErrorInfo**|**IErrorInfo** 인터페이스에 대한 참조를 반환합니다.|  
|**GetErrorParameters**|OLE DB Driver for SQL Server를 통해 소비자에 게 매개 변수를 반환 하지 않는 **GetErrorParameters**합니다.|  
|**GetRecordCount**|사용할 수 있는 오류 레코드 수입니다.|  
  
 OLE DB Driver for SQL Server 지원 **isqlerrorinfo:: Getsqlinfo** 다음과 같은 매개 변수입니다.  
  
|매개 변수|설명|  
|---------------|-----------------|  
|*pbstrSQLState*|오류의 SQLSTATE 값을 반환합니다. SQLSTATE 값은 SQL-92, ODBC 및 ISO SQL, API 사양에서 정의됩니다. 모두 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 나는 OLE DB Driver for SQL Server 구현 별 SQLSTATE 값을 정의 합니다.|  
|*plNativeError*|사용 가능한 경우 **master.dbo.sysmessages**의 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 오류 번호를 반환합니다. 원시 오류를 성공적으로는 OLE DB Driver for SQL Server 데이터 원본 초기화 후 사용할 수 있습니다. 전에 OLE DB Driver for SQL Server 항상 0을 반환 합니다.|  
  
## <a name="see-also"></a>참고 항목  
 [오류](../../oledb/ole-db-errors/errors.md)  
  
  
