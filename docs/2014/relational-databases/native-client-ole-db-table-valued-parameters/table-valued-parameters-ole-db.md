---
title: 테이블 반환 매개 변수(OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- OLE DB, table-valued parameters
- table-valued parameters (OLE DB)
ms.assetid: 4298b73d-615b-4d28-9843-03b4d5fc489e
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e9c58b1837eb017a3cc51652ff404b37690b3849
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/26/2020
ms.locfileid: "63046435"
---
# <a name="table-valued-parameters-ole-db"></a>테이블 반환 매개 변수(OLE DB)
  이 섹션에서는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 공급자의 테이블 반환 매개 변수 지원에 대해 설명합니다. 추가 개요 정보는 [SQL Server Native Client&#41;&#40;테이블 반환 매개 변수 ](../native-client/features/table-valued-parameters-sql-server-native-client.md)를 참조 하세요. 샘플은 [테이블 반환 매개 변수 사용&#40;OLE DB&#41;](../native-client-ole-db-how-to/use-table-valued-parameters-ole-db.md)을 참조하세요.  
  
## <a name="remarks"></a>설명  
 현재 매개 변수 집합(`ICommand::Execute`의 DBPARAMS 매개 변수)을 사용하여 다중 행 데이터를 프로시저에 대한 매개 변수로 서버에 보낼 수 있습니다. 매개 변수 집합을 사용할 경우 해당 집합의 모든 요소가 서버에 개별 RPC(원격 프로시저 호출) 요청으로 서버에 전송되어야 합니다. 테이블 반환 매개 변수는 유사한 기능을 제공하지만 서버와 더 밀접하게 통합됩니다. 따라서 RPC 요청 수가 감소하며 서버에서 집합 기반 작업을 사용할 수 있습니다.  
  
 테이블 반환 매개 변수는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 공급자에서 OLE DB `Rowset` 개체로 지원됩니다. 소비자(즉, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 공급자를 사용하는 클라이언트 애플리케이션)는 모든 `Rowset` 개체를 테이블 반환 매개 변수의 자리 표시자로 제공할 수 있습니다. 테이블 반환 매개 변수는 다른 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 매개 변수 유형과 마찬가지로 처리됩니다. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 공급자는 생성, 검색, 지정, 바인딩 및 스키마 인터페이스를 제공합니다.  
  
## <a name="in-this-section"></a>섹션 내용  
  
-   [테이블 반환 매개 변수 행 집합 만들기](table-valued-parameter-rowset-creation.md)  
  
-   [테이블 반환 매개 변수 형식 검색](../../database-engine/dev-guide/table-valued-parameter-type-discovery.md)  
  
-   [테이블 반환 매개 변수가 포함된 명령 실행](executing-commands-containing-table-valued-parameters.md)  
  
-   [테이블 반환 매개 변수에 데이터 삽입](inserting-data-into-table-valued-parameters.md)  
  
-   [OLE DB 테이블 반환 매개 변수에 대해 변경된 스키마 행 집합](schema-rowsets-changed-for-ole-db-table-valued-parameters.md)  
  
-   [OLE DB 테이블 반환 매개 변수 형식 지원](ole-db-table-valued-parameter-type-support.md)  
  
-   [OLE DB 테이블 반환 매개 변수 형식 지원&#40;Methods&#41;](ole-db-table-valued-parameter-type-support-methods.md)  
  
-   [OLE DB 테이블 반환 매개 변수 형식 지원&#40;Properties&#41;](ole-db-table-valued-parameter-type-support-properties.md)  
  
## <a name="see-also"></a>참고 항목  
 [SQL Server Native Client &#40;OLE DB&#41;](../native-client/ole-db/sql-server-native-client-ole-db.md)   
 [테이블 반환 매개 변수&#40;OLE DB&#41; 사용](../native-client-ole-db-how-to/use-table-valued-parameters-ole-db.md)  
  
  
