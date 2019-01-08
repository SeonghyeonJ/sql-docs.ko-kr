---
title: CDC Service에서 작업하는 방법 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: db5c718a-6e7f-48ec-82a3-9d5b131716e5
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 2cab5b109a8f9181235fa1b61d18a2f7a5976c80
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/03/2018
ms.locfileid: "52796045"
---
# <a name="how-to-work-with-cdc-services"></a>CDC Service에서 작업하는 방법
  이 절차에서는 CDC Service 구성 콘솔을 사용하여 Oracle CDC Service에서 작업하기 위해 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스를 준비하고 새 CDC Service를 만드는 방법에 대해 설명합니다.  
  
### <a name="to-work-with-cdc-services"></a>CDC Service에서 작업하려면  
  
1.  **시작** 메뉴에서 **Oracle CDC Service 구성**을 선택합니다.  
  
2.  왼쪽 창에서 **로컬 CDC Service** (루트 수준)를 선택합니다.  
  
3.  다음 태스크 중 하나 또는 모두 수행합니다.  
  
    -   **SQL Server 준비**  
  
         CDC Service 구성 콘솔 오른쪽의 **작업** 창에서 이 옵션을 선택합니다.  
  
         **로컬 CDC Service** 를 마우스 오른쪽 단추로 클릭하고 **SQL Server 준비**를 선택할 수도 있습니다.  
  
         Oracle CDC를 위한 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스 준비 대화 상자가 열립니다.  
  
         Oracle CDC Service를 위해 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스를 준비하려면 로그인은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 고정 서버 역할이 있는 `dbcreator` 로그인이 있어야 합니다. 이 로그인은 Oracle CDC Service 및 이후 Oracle CDC 인스턴스 추가에 필요한 MSXDBCDC 데이터베이스를 만드는 데 사용됩니다.  
  
         이 대화 상자를 사용하는 방법은 [Prepare SQL Server for CDC](prepare-sql-server-for-cdc.md)를 참조하십시오. CDC를 위한 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스 설정 방법에 대한 자세한 내용은 [CDC를 위해 SQL Server를 준비하는 방법](how-to-prepare-sql-server-for-cdc.md)을 참조하세요.  
  
    -   **새 CDC Service 만들기**  
  
         CDC Service 구성 콘솔 오른쪽의 **작업** 창에서 **새 서비스** 를 선택합니다.  
  
         **로컬 CDC Service** 를 마우스 오른쪽 단추로 클릭하고 **새 서비스**를 선택할 수도 있습니다.  
  
         새 Oracle CDC Service 대화 상자가 열립니다.  
  
         이 대화 상자를 사용하는 방법은 [Create and Edit an Oracle CDC Service](create-and-edit-an-oracle-cdc-service.md)를 참조하십시오. CDC Service를 만들거나 편집하는 방법은 [CDC Service를 만들고 편집하는 방법](how-to-create-and-edit-a-cdc-service.md)를 참조하십시오.  
  
         Oracle CDC Service에서 사용되는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 로그인은 `public` 고정 서버 역할의 구성원이면 가능하며 다른 권한은 필요 없습니다. 하지만 Oracle CDC Service를 만들려면 로그인은 MSXDBCDC 데이터베이스에 대해 쓰기 권한이 있어야 합니다. 예를 들어 **db_owner** 데이터베이스 역할을 로그인에 할당해야 합니다. MSXDBCDC 데이터베이스에 대해 쓰기 권한이 없는 로그인이 새 Oracle CDC 인스턴스를 만들려고 시도하면 오류 메시지가 표시됩니다. 해당 대화 상자에서 **확인** 을 클릭하여 SQL Server에 연결 대화 상자를 표시합니다.  
  
         **db_owner** 데이터베이스 역할과 같이 MSXDBCDC 데이터베이스에 대해 쓰기 권한이 있는 로그인의 자격 증명을 입력하는 방법은 [Oracle CDC Service 만들기 및 편집](create-and-edit-an-oracle-cdc-service.md) 및 [SQL Server에 연결](connection-to-sql-server.md)을 참조하세요.  
  
## <a name="see-also"></a>관련 항목  
 [CDC Service 작업](work-with-cdc-services.md)  
  
  
