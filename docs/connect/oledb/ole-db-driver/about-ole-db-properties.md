---
title: OLE DB 연결 속성 정보 | Microsoft Docs
description: OLE DB 속성 정보
ms.custom: ''
ms.date: 05/20/2020
ms.prod: sql
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- OLE DB, properties
- OLE DB Driver for SQL Server, properties
- properties [OLE DB]
- property values [OLE DB Driver for SQL Server]
author: pmasl
ms.author: pelopes
ms.openlocfilehash: fa2fbb56d9d8926c45970ecddfabd226c87d26e2
ms.sourcegitcommit: f3321ed29d6d8725ba6378d207277a57cb5fe8c2
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/06/2020
ms.locfileid: "86004454"
---
# <a name="about-ole-db-properties"></a>OLE DB 속성 정보
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

<!--
NOTE , GeneMi , 2020/May/20:
    This SQL 2016+ article is a nearly exact duplicate of another SQL 2016+ article.
    This article resides under docs/connect/oledb/ole-db-driver/.

    The other article resides under docs/relational-databases/native-client-ole-db-provider/.
    And, the other article has a SQL 2014 counterpart having its same GitHub directory path and filename, to support SQL 2014 OPS Versioning with SQL 2016+.

    This path-file name is:
'\sql-docs-pr\docs\connect\oledb\ole-db-driver\about-ole-db-properties.md'.

    The other path-file is named:
'\sql-docs-pr\docs\relational-databases\native-client-ole-db-provider\about-ole-db-properties.md'.

    Therefore, maybe this docs/connect/oledb/... file should be deleted?

1611957:  This NOTE relates to SEO content bug 1611957 about metadata 'title:' value duplication:
    https://mseng.visualstudio.com/TechnicalContent/_workitems/edit/1611957

PR 15068:  This HTML comment is being added by PR...
    https://github.com/MicrosoftDocs/sql-docs-pr/pull/15068
-->

  소비자는 속성 값을 설정하여 특정 개체 동작을 요청합니다. 예를 들어 소비자는 속성을 사용하여 행 집합에서 노출할 인터페이스를 지정합니다. 소비자는 속성 값을 가져와서 행 집합, 세션 또는 데이터 원본 개체와 같은 개체의 기능을 확인합니다.  
  
 각 속성에는 값, 유형, 설명 및 읽기/쓰기 특성이 있고 행 집합 속성의 경우 열 단위로 지정할 수 있는지 여부는 나타내는 표시도 있습니다.  
  
 속성은 GUID와 속성 ID를 나타내는 정수로 식별됩니다. 속성 집합은 동일한 GUID를 공유하는 모든 속성의 집합입니다. SQL Server용 OLE DB 드라이버에서는 미리 정의된 OLE DB 속성 집합 외에도 공급자별 속성 집합과 해당 집합 내의 속성을 구현합니다. 각 속성은 하나 이상의 속성 그룹에 속합니다. 속성 그룹은 특정 개체에 적용되는 모든 속성의 그룹입니다. 예를 들어 초기화 속성 그룹, 데이터 원본 속성 그룹, 세션 속성 그룹, 행 집합 속성 그룹, 테이블 속성 그룹, 열 속성 그룹 등이 있습니다. 이러한 각 속성 그룹에는 속성들이 있습니다.  
  
 속성 값을 설정하는 과정은 다음과 같습니다.  
  
1.  값을 설정할 속성을 결정합니다.  
  
2.  식별된 속성을 포함하는 속성 집합을 결정합니다.  
  
3.  식별한 각 속성 집합에 대해 하나씩 DBPROPSET 구조 배열을 할당합니다.  
  
4.  각 속성 집합에 대해 DBPROP 구조 배열을 할당합니다. 각 배열의 요소 수는 1단계에서 식별한 해당 속성 집합에 속한 속성의 수입니다.  
  
5.  각 속성의 DBPROP 구조를 채웁니다.  
  
6.  각 속성 집합의 DBPROPSET 구조에 정보(속성 집합 GUID, 요소 수 및 해당 DBPROP 배열에 대한 포인터)를 채웁니다.  
  
7.  속성을 설정할 메서드를 호출하고 DBPROPSET 구조의 수 및 배열을 전달합니다.  
  
## <a name="see-also"></a>참고 항목  
 [SQL Server 애플리케이션용 OLE DB 드라이버 만들기](../../oledb/ole-db-driver/creating-a-oledb-driver-for-sql-server-application.md)   
 [속성(OLE DB)](https://go.microsoft.com/fwlink/?LinkId=112207)  
  
  
