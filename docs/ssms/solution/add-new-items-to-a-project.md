---
title: 프로젝트에 새 항목 추가
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- projects [SQL Server Management Studio], item additions
- adding project items
ms.assetid: 76af8692-324f-4f5e-b1a0-d72ca8a107e3
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 0440f720923ebfa6378766372e4bcdb48a2a166d
ms.sourcegitcommit: f3321ed29d6d8725ba6378d207277a57cb5fe8c2
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/06/2020
ms.locfileid: "86003308"
---
# <a name="add-new-items-to-a-project"></a>프로젝트에 새 항목 추가
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]
프로젝트에 새 항목을 추가하여 애플리케이션 기능을 확장할 수 있습니다. 새 항목은 쿼리나 연결이 될 수 있습니다. [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 스크립트 프로젝트 및 Analysis Services 스크립트 프로젝트의 두 가지 프로젝트 형식이 있습니다. 프로젝트 형식에 따라 프로젝트에 추가할 수 있는 항목이 결정됩니다. 예를 들어 [!INCLUDE[tsql](../../includes/tsql-md.md)] 스크립트 프로젝트에는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 쿼리(확장명이 .sql인 파일)를 추가할 수 있지만 Analysis Services 스크립트 프로젝트에는 추가할 수 없습니다.  
  
[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 프로젝트 내에서 폴더를 만드는 것이 허용되지 않습니다. 작업을 구성하려면 솔루션 내에서 여러 프로젝트를 만듭니다.  
  
### <a name="to-add-a-new-query-to-an-existing-project"></a>기존 프로젝트에 새 쿼리를 추가하려면  
  
1.  솔루션 탐색기에서 대상 프로젝트를 선택합니다.  
  
2.  **프로젝트** 메뉴에서 **새 항목 추가**를 클릭합니다.  
  
3.  **새 항목 추가** 대화 상자에서 왼쪽 창의 범주를 선택합니다.  
  
4.  오른쪽 창에서 쿼리 템플릿을 선택한 다음 **추가**를 클릭합니다. 프로젝트의 **쿼리** 폴더에 새 쿼리가 추가됩니다.  
  
5.  **데이터베이스 엔진에 연결** 대화 상자에서 새 쿼리에 대한 연결을 지정한 다음 **연결**을 클릭합니다. 연결을 새 쿼리에 연결하지 않으려는 경우 연결 대화 상자에서 **취소** 를 클릭합니다.  
  
6.  원할 경우 솔루션 탐색기에서 쿼리의 이름을 바꿉니다.  
  
### <a name="to-add-a-new-connection-to-an-existing-project"></a>기존 프로젝트에 새 연결을 추가하려면  
  
1.  솔루션 탐색기에서 대상 프로젝트를 선택합니다.  
  
2.  **프로젝트** 메뉴에서 **새 항목 추가**를 클릭합니다.  
  
3.  왼쪽 창에서 **연결** 을 선택합니다.  
  
4.  오른쪽 창에서 **새 연결** 을 선택한 다음 **추가**를 클릭합니다.  
  
5.  **데이터베이스 엔진에 연결** 대화 상자에서 새 쿼리에 대한 연결을 지정한 다음 **연결**을 클릭합니다. 프로젝트의 **연결** 폴더에 새 연결이 추가됩니다.  
  
## <a name="see-also"></a>참고 항목  
[솔루션 탐색기](../../ssms/solution/solution-explorer.md)  
[파일 확장명을 코드 편집기에 연결](../../relational-databases/scripting/associate-file-extensions-to-a-code-editor.md)  
[프로젝트에 기존 항목 추가](../../ssms/solution/add-existing-items-to-a-project.md)  
[항목이나 프로젝트 제거 또는 삭제](../../ssms/solution/remove-or-delete-an-item-or-project.md)  
  
