---
title: 저장 프로시저 실행(OLE DB) | Microsoft Docs
description: 데이터 원본에서 저장 프로시저를 호출하는 이점 및 OLE DB Driver for SQL Server가 제공하는 데이터 반환 메커니즘에 대해 알아봅니다.
ms.custom: ''
ms.date: 06/12/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- stored procedures [OLE DB], executing
- OLE DB, stored procedures
- OLE DB Driver for SQL Server, stored procedures
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 244a5719285589b182b14e5214fd0b27050db2a0
ms.sourcegitcommit: c95f3ef5734dec753de09e07752a5d15884125e2
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88858832"
---
# <a name="stored-procedures---running"></a>저장 프로시저 - 실행
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  문을 실행할 때 클라이언트 애플리케이션에서 직접 문을 실행하거나 준비하는 대신 데이터 원본의 저장 프로시저를 호출하면 다음과 같은 장점이 있습니다.  
  
-   성능 향상  
  
-   네트워크 오버헤드 감소  
  
-   일관성 향상  
  
-   정확성 향상  
  
-   기능 추가  
  
 OLE DB Driver for SQL Server는 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 저장 프로시저가 데이터를 반환하는 데 사용하는 세 가지 메커니즘을 지원합니다.  
  
-   프로시저의 모든 SELECT 문은 결과 집합을 생성합니다.  
  
-   프로시저는 출력 매개 변수를 통해 데이터를 반환할 수 있습니다.  
  
-   프로시저에는 정수 반환 코드가 있을 수 있습니다.  
  
 애플리케이션은 저장 프로시저의 이러한 모든 출력을 처리할 수 있어야 합니다.  
  
 OLE DB 공급자는 결과를 처리하는 동안 각각 다른 시기에 출력 매개 변수와 반환 값을 반환합니다. SQL Server용 OLE DB 드라이버의 경우 저장 프로시저에서 반환되는 결과 집합을 소비자가 검색 또는 취소하기 전에는 출력 매개 변수와 반환 코드를 제공하지 않습니다. 반환 코드와 출력 매개 변수는 서버에서 보내는 마지막 TDS 패킷에서 반환됩니다.  
  
 공급자는 출력 매개 변수와 반환 값을 반환할 때 DBPROP_OUTPUTPARAMETERAVAILABILITY 속성을 사용하여 보고합니다. 이 속성은 DBPROPSET_DATASOURCEINFO 속성 집합에 들어 있습니다.  
  
 SQL Server용 OLE DB 드라이버는 DBPROP_OUTPUTPARAMETERAVAILABILITY 속성을 DBPROPVAL_OA_ATROWRELEASE로 설정하여 결과 집합이 처리 또는 해제되기 전에는 반환 코드와 출력 매개 변수가 반환되지 않도록 지정합니다.  
  
## <a name="see-also"></a>참고 항목  
 [저장 프로시저](../../oledb/ole-db/stored-procedures.md)  
  
  
