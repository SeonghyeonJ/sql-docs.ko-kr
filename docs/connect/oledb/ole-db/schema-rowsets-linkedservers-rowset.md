---
title: LINKEDSERVERS 행 집합(OLE DB) | Microsoft Docs
description: OLE DB Driver for SQL Server에서 LINKEDSERVERS 행 집합은 분산 쿼리에 참여할 수 있는 조직 데이터 원본을 열거합니다.
ms.custom: ''
ms.date: 06/12/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- LINKEDSERVERS rowset
- enumerating data sources [OLE DB]
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 1639463992bfffe7ea86a97c43564214a92b2cdb
ms.sourcegitcommit: c95f3ef5734dec753de09e07752a5d15884125e2
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88861557"
---
# <a name="schema-rowsets---linkedservers-rowset"></a>스키마 행 집합 - LINKEDSERVERS 행 집합
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  **LINKEDSERVERS** 행 집합은 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 분산 쿼리에 참여할 수 있는 조직 데이터 원본을 열거합니다.  
  
 **LINKEDSERVERS** 행 집합에는 다음 열이 포함되어 있습니다.  
  
|열 이름|유형 표시기|Description|  
|-----------------|--------------------|-----------------|  
|SVR_NAME|DBTYPE_WSTR|연결된 서버의 이름입니다.|  
|SVR_PRODUCT|DBTYPE_WSTR|연결된 서버 이름이 나타내는 데이터 저장소 유형을 식별하는 제조업체 또는 기타 이름입니다.|  
|SVR_PROVIDERNAME|DBTYPE_WSTR|서버 데이터를 이용할 때 사용되는 OLE DB 공급자의 이름입니다.|  
|SVR_DATASOURCE|DBTYPE_WSTR|공급자의 데이터 원본을 가져올 때 사용되는 OLE DB DBPROP_INIT_DATASOURCE 문자열입니다.|  
|SVR_PROVIDERSTRING|DBTYPE_WSTR|공급자의 데이터 원본을 가져올 때 사용되는 OLE DB DBPROP_INIT_PROVIDERSTRING 값입니다.|  
|SVR_LOCATION|DBTYPE_WSTR|공급자의 데이터 원본을 가져올 때 사용되는 OLE DB DBPROP_INIT_LOCATION 문자열입니다.|  
  
 행 집합은 SRV_NAME을 기준으로 정렬되며 SRV_NAME에서 하나의 제한이 지원됩니다.  
  
## <a name="see-also"></a>참고 항목  
 [스키마 행 집합 지원&#40;OLE DB&#41;](../../oledb/ole-db/schema-rowset-support-ole-db.md)  
  
  
