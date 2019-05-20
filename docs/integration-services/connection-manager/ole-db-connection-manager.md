---
title: OLE DB 연결 관리자 | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql13.dts.designer.oledbconnection.f1
helpviewer_keywords:
- OLE DB connection manager
- data sources [Integration Services], connections
- connection managers [Integration Services], OLE DB
- connections [Integration Services], OLE DB
ms.assetid: 91e3622e-4b1a-439a-80c7-a00b90d66979
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: ee9368848e7c939bbc8d4bb14eb49014ef5efb48
ms.sourcegitcommit: fd71d04a9d30a9927cbfff645750ac9d5d5e5ee7
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/16/2019
ms.locfileid: "65728168"
---
# <a name="ole-db-connection-manager"></a>OLE DB 연결 관리자

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  OLE DB 연결 관리자를 사용하면 패키지에서 OLE DB Provider를 사용하여 데이터 원본에 연결할 수 있습니다. 예를 들어 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에 연결되는 OLE DB 연결 관리자에서는 [!INCLUDE[msCoName](../../includes/msconame-md.md)] OLE DB Provider for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]를 사용할 수 있습니다.    
    
> [!NOTE]
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 11.0 OLEDB 공급자는 다중 서브넷 장애 조치(Failover) 클러스터링에 대한 새 연결 문자열 키워드(MultiSubnetFailover=True)를 지원하지 않습니다. 자세한 내용은 [SQL Server 릴리스 정보](https://go.microsoft.com/fwlink/?LinkId=247824) 및 www.mattmasson.com의 블로그 게시물, [Always On 다중 서브넷 장애 조치(Failover) 및 SSIS](https://www.mattmasson.com/2012/03/alwayson-multi-subnet-failover-and-ssis/)를 참조하세요.    
> 
> [!NOTE]
>  데이터 원본이 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Office Excel 2007 또는 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Office Access 2007인 경우 이 데이터 원본에는 이전 버전의 Excel 또는 Access와 다른 데이터 공급자가 필요합니다. 자세한 내용은 [Excel 통합 문서에 연결](../../integration-services/connection-manager/connect-to-an-excel-workbook.md) 및 [Access 데이터베이스에 연결](../../integration-services/connection-manager/connect-to-an-access-database.md)을 참조하세요.    
    
 일부 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 태스크와 데이터 흐름 구성 요소에서는 OLE DB 연결 관리자가 사용됩니다. 예를 들어 OLE DB 원본과 OLE DB 대상에서는 이 연결 관리자를 사용하여 데이터를 추출 및 로드하고, SQL 실행 태스크에서는 이 연결 관리자를 사용하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터베이스에 연결하고 쿼리를 실행합니다.    
    
 OLE DB 연결 관리자는 또한 C++와 같은 언어를 사용하는 비관리 코드로 작성된 사용자 지정 태스크의 OLE DB 데이터 원본에 액세스하는 데에도 사용됩니다.    
    
 패키지에 OLE DB 연결 관리자를 추가하면 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 에서 런타임에 OLE DB 연결로 확인되는 연결 관리자를 만들고, 연결 관리자 속성을 설정하고, 연결 관리자를 패키지의 **Connections** 컬렉션에 추가합니다.    
    
 연결 관리자의 **ConnectionManagerType** 속성이 **OLEDB**로 설정됩니다.    
    
 다음과 같은 방법으로 OLE DB 연결 관리자를 구성할 수 있습니다.    
    
-   선택된 공급자에 대한 요구 사항을 만족하도록 구성된 특정 연결 문자열을 제공합니다.    
    
-   공급자에 따라 연결할 데이터 원본의 이름을 포함시킵니다.    
    
-   선택된 공급자에 적합한 보안 자격 증명을 제공합니다.    
    
-   연결 관리자에서 만든 연결이 런타임에 유지될지 여부를 나타냅니다.    
    
## <a name="logging"></a>로깅    
 OLE DB 연결 관리자가 외부 데이터 공급자에 대해 수행하는 호출을 로깅할 수 있습니다. 이 로깅 기능을 사용하여 OLE DB 연결 관리자가 수행하는 외부 데이터 원본에 대한 연결 문제를 해결할 수 있습니다. OLE DB 연결 관리자가 외부 데이터 공급자에 대해 수행하는 호출을 로깅하려면 패키지 로깅을 설정하고 패키지 수준에서 **Diagnostic** 이벤트를 선택합니다. 자세한 내용은 [패키지 실행 문제 해결 도구](../../integration-services/troubleshooting/troubleshooting-tools-for-package-execution.md)를 참조하세요.    
    
## <a name="configuration-of-the-oledb-connection-manager"></a>OLEDB 연결 관리자 구성    
 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 디자이너를 사용하거나 프로그래밍 방식으로 속성을 설정할 수 있습니다. [!INCLUDE[ssIS](../../includes/ssis-md.md)] 디자이너에서 설정할 수 있는 속성에 대한 자세한 내용은 [OLE DB 연결 관리자 구성](../../integration-services/connection-manager/configure-ole-db-connection-manager.md)을 참조하세요. 프로그래밍 방식으로 연결 관리자를 구성하는 방법은 개발자 가이드에서 **T:Microsoft.SqlServer.Dts.Runtime.ConnectionManager** 클래스에 대한 설명서를 참조하십시오.    
    
## <a name="related-content"></a>관련 내용    
    
-   social.technet.microsoft.com의 Wiki 문서 - [Oracle 커넥터가 있는 SSIS](https://go.microsoft.com/fwlink/?LinkId=220670)    
    
-   carlprothman.net의 기술 문서 [OLE DB 공급자에 대한 연결 문자열](https://go.microsoft.com/fwlink/?LinkId=220744)    
    
## <a name="configure-ole-db-connection-manager"></a>OLE DB 연결 관리자 구성
  **OLE DB 연결 관리자 구성** 대화 상자를 사용하면 새 연결을 만들거나 기존 연결을 복사하여 데이터 원본에 대한 연결을 추가할 수 있습니다.  
  
> [!NOTE]  
>  데이터 원본이 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Office Excel 2007인 경우 이 데이터 원본에는 이전 버전의 Excel과 다른 연결 관리자가 필요합니다. 자세한 내용은 [Excel 통합 문서에 연결](../../integration-services/connection-manager/connect-to-an-excel-workbook.md)을 참조하세요.  
>   
>  데이터 원본이 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Office Access 2007인 경우 이 데이터 원본에는 이전 버전의 Access와 다른 OLE DB 공급자가 필요합니다. 자세한 내용은 [Access 데이터베이스에 연결](../../integration-services/connection-manager/connect-to-an-access-database.md)을 참조하세요.  
  
 OLE DB 연결 관리자에 대한 자세한 내용은 [OLE DB Connection Manager](../../integration-services/connection-manager/ole-db-connection-manager.md)를 참조하십시오.  
  
### <a name="options"></a>옵션  
 **데이터 연결**  
 목록에서 기존 OLE DB 데이터 연결을 선택합니다.  
  
 **데이터 연결 속성**  
 선택한 OLE DB 데이터 연결의 속성과 값을 표시합니다.  
  
 **새로 만들기**  
 **연결 관리자** 대화 상자를 사용하여 OLE DB 데이터 연결을 만듭니다.  
  
 **Delete**  
 데이터 연결을 선택한 다음 **삭제** 단추를 사용하여 삭제합니다.  
  
## <a name="see-also"></a>참고 항목    
 [OLE DB 원본](../../integration-services/data-flow/ole-db-source.md)     
 [OLE DB 대상](../../integration-services/data-flow/ole-db-destination.md)     
 [SQL 실행 태스크](../../integration-services/control-flow/execute-sql-task.md)     
 [Integration Services&#40;SSIS&#41; 연결](../../integration-services/connection-manager/integration-services-ssis-connections.md)    
    
  
