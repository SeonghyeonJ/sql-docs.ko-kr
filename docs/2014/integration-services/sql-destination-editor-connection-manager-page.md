---
title: SQL 대상 편집기 (연결 관리자 페이지) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.sqlserverdestadapter.connection.f1
helpviewer_keywords:
- SQL Server Destination Editor
ms.assetid: 423e1654-54af-47c6-ab6f-98670534557d
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: d3bffc98a14c1a8bc672e9f15a4bad8b6f5a7dbe
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/26/2020
ms.locfileid: "66055404"
---
# <a name="sql-destination-editor-connection-manager-page"></a>SQL 대상 편집기(연결 관리자 페이지)
  **SQL 대상 편집기** 대화 상자의 **연결 관리자** 페이지를 사용하여 데이터 원본 정보를 지정하고 결과를 미리 볼 수 있습니다. [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[msCoName](../includes/msconame-md.md)] 대상은 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 데이터베이스의 테이블 또는 뷰로 데이터를 로드 합니다.  
  
 SQL Server 대상에 대한 자세한 내용은 [SQL Server Destination](data-flow/sql-server-destination.md)을 참조하십시오.  
  
## <a name="options"></a>옵션  
 **OLE DB 연결 관리자**  
 목록에서 기존 연결을 선택하거나 **새로 만들기**를 클릭하여 새 연결을 만듭니다.  
  
 **신규**  
 **OLE DB 연결 관리자 구성** 대화 상자를 사용하여 새 연결을 만듭니다.  
  
 **테이블 또는 뷰 사용**  
 목록에서 기존 테이블 또는 뷰를 선택하거나 **새로 만들기**를 클릭하여 새 연결을 만듭니다.  
  
 **신규**  
 **테이블 만들기** 대화 상자를 사용하여 새 테이블을 만듭니다.  
  
> [!NOTE]  
>  **새로 만들기**를 클릭 하면 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 에서 연결 된 데이터 원본을 기반으로 기본 CREATE TABLE 문을 생성 합니다. 원본 테이블에 선언된 FILESTREAM 특성이 포함된 열이 있어도 기본 CREATE TABLE 문은 FILESTREAM 특성을 포함하지 않습니다. FILESTREAM 특성이 포함된 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 구성 요소를 실행하려면 먼저 대상 데이터베이스에서 FILESTREAM 스토리지를 구현하십시오. 그런 다음 **테이블 만들기** 대화 상자에서 FILESTREAM 특성을 CREATE TABLE 문에 추가하십시오. 자세한 내용은 [Blob&#40;Binary Large Object&#41; 데이터&#40;SQL Server&#41;](../relational-databases/blob/binary-large-object-blob-data-sql-server.md)를 참조하세요.  
  
 **미리 보기**  
 **쿼리 결과 미리 보기** 대화 상자를 사용하여 결과를 미리 봅니다. 미리 보기에는 최대 200개의 행이 표시될 수 있습니다.  
  
## <a name="see-also"></a>참고 항목  
 [Integration Services 오류 및 메시지 참조](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [SQL 대상 편집기 &#40;매핑 페이지&#41;](../../2014/integration-services/sql-destination-editor-mappings-page.md)   
 [SQL 대상 편집기 &#40;고급 페이지&#41;](../../2014/integration-services/sql-destination-editor-advanced-page.md)   
 [SQL Server 대상을 사용하여 데이터 대량 로드](data-flow/bulk-load-data-by-using-the-sql-server-destination.md)  
  
  
