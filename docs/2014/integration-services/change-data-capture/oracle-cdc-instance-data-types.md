---
title: Oracle CDC 인스턴스 데이터 형식 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: eec13d8d-c15a-4542-bfc4-da66b1a6bfe0
author: janinezhang
ms.author: janinez
ms.openlocfilehash: b622fe35bd4b349057168464f8d42fa3f1160f52
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84922731"
---
# <a name="oracle-cdc-instance-data-types"></a>Oracle CDC 인스턴스 데이터 형식
  Oracle CDC 인스턴스는 대부분의 Oracle 데이터 형식을 지원합니다. 다음 섹션에서는 지원되는 데이터 형식과 지원되지 않는 데이터 형식에 대해 설명합니다.  
  
## <a name="supported-data-types"></a>지원되는 데이터 형식  
 다음 표에서는 캡처할 수 있는 Oracle 데이터 형식과 변경 테이블의 SQL Server 데이터 형식에 대한 기본 매핑에 대해 설명합니다. 원본 Oracle 테이블에 대한 캡처 인스턴스를 추가할 때 이러한 매핑 중 일부를 재정의할 수 있습니다.  
  
|Oracle 데이터베이스 데이터 형식|SQL Server 데이터 형식|  
|-------------------------------|--------------------------|  
|BINARY_FLOAT|real|  
|BINARY_DOUBLE|FLOAT|  
|CHAR|NVARCHAR|  
|DATE|DATETIME|  
|FLOAT|FLOAT|  
|INT|NUMERIC(38)|  
|INTERVAL|DATETIME|  
|NCHAR|NVARCHAR|  
|NUMBER|FLOAT|  
|NAVARCHAR2|NVARCHAR|  
|RAW|VARBINARY|  
|real|FLOAT|  
|timestamp|DATETIME2|  
|TIMESTAMP WITH TIME ZONE|VARCHAR(37)|  
|TIMESTAMP WITH LOCAL TIME ZONE|VARCHAR(37)|  
|VARCHAR2|VARCHAR|  
|XMLTYPE|NVARCHAR(MAX)|  
  
## <a name="non-supported-data-types"></a>지원되지 않는 데이터 형식  
 다음 Oracle 데이터 형식 열이 있는 원본 Oracle 테이블은 캡처할 수 없습니다. 이러한 데이터 형식을 가진 캡처된 열은 null로 표시되지만, 값 변경은 캡처된 테이블의 변경 마스크에 표시됩니다.  
  
-   LONG  
  
-   XMLTYPE  
  
-   BLOB  
  
-   CLOB  
  
 다음 Oracle 데이터 형식 열이 있는 원본 Oracle 테이블은 캡처할 수 없습니다.  
  
-   BFILE  
  
-   ROWID  
  
-   REF  
  
-   UROWID  
  
-   중첩 테이블  
  
 다음 데이터 형식이 테이블에 있는 경우 LogMinder가 테이블 열에 대한 데이터를 가져오지 않습니다.  
  
-   사용자 정의 데이터 형식  
  
-   VARRAY  
  
## <a name="see-also"></a>참고 항목  
 [Change Data Capture Designer for Oracle by Attunity](change-data-capture-designer-for-oracle-by-attunity.md)   
 [Oracle CDC 인스턴스](the-oracle-cdc-instance.md)  
  
  
