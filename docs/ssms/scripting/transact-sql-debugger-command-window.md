---
title: 명령 창 | Microsoft 문서
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.technology: scripting
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- Command Window [Transact-SQL]
ms.assetid: e567ebf9-0793-451b-92c7-26193a02d9da
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: f884fedf974e863636de39c126c583498564d79e
ms.sourcegitcommit: 40c3b86793d91531a919f598dd312f7e572171ec
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/13/2018
ms.locfileid: "53328503"
---
# <a name="transact-sql-debugger---command-window"></a>Transact-SQL 디버거 - 명령 창
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
  **명령 창** 을 사용하여 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 쿼리 편집기 창에서 현재 디버깅 중인 코드에 디버그 및 편집 명령과 같은 명령을 실행합니다. **명령 창**을 사용하려면 디버그 모드여야 합니다.  [!INCLUDE[tsql](../../includes/tsql-md.md)] 디버거는 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] **명령** 창에서도 지원되는 많은 명령을 지원합니다. 자세한 내용은 [Visual Studio 명령 창](https://go.microsoft.com/fwlink/?LinkId=112007)을 참조하십시오.  
  
## <a name="task-list"></a>작업 목록  
 **명령 창에 액세스하려면**  
  
-   **디버그** 메뉴에서 **디버깅 시작**을 클릭합니다.  
  
 **변수 값을 인쇄하려면**  
  
-   **명령 창**에서 **Debug.Print \<VariableName>** 을 입력하고 Enter 키를 누릅니다.  
  
 **현재 스레드에 대한 정보를 표시하려면**  
  
-   **명령 창**에서 **Debug.ListThread**를 입력하고 Enter 키를 누릅니다.  
  
 **간략한 조사식 창에 변수를 추가하려면**  
  
-   **명령 창**에서 **Debug.QuickWatch \<VariableName>** 을 입력하고 Enter 키를 누릅니다.  
  
## <a name="see-also"></a>참고 항목  
 [Transact-SQL 디버거](../../relational-databases/scripting/transact-sql-debugger.md)  
