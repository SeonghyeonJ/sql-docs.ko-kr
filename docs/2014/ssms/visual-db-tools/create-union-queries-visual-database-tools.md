---
title: 통합 쿼리 만들기(Visual Database Tools) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- queries [SQL Server], types
- UNION queries
- Select query
- combining query results
- merged SELECT query [SQL Server]
ms.assetid: b5aafb1d-e4ed-4922-b790-56abc5ec551a
author: stevestein
ms.author: sstein
ms.openlocfilehash: 3c10f39c3e44844c4ec8a6a2328c41ea2de350d2
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/18/2020
ms.locfileid: "85058099"
---
# <a name="create-union-queries-visual-database-tools"></a>통합 쿼리 만들기(Visual Database Tools)
  UNION 키워드를 사용하면 두 SELECT 문의 결과를 하나의 결과 테이블에 포함할 수 있습니다. 각 SELECT 문에서 반환된 모든 행이 UNION 식의 결과로 결합됩니다. 예제는 [transact-sql&#41;&#40;SELECT 예 ](/sql/t-sql/queries/select-examples-transact-sql)를 참조 하세요.  
  
> [!NOTE]  
>  다이어그램 창에는 SELECT 절을 하나만 표시할 수 있습니다. 따라서 통합 쿼리 작업을 진행할 때는 쿼리 디자이너에서 테이블 작업 창이 숨겨집니다.  
  
### <a name="to-create-a-merged-select-query"></a>병합된 선택 쿼리를 만들려면  
  
1.  쿼리를 열거나 새 쿼리를 만듭니다.  
  
2.  SQL 창에서 유효한 UNION 식을 입력합니다.  
  
     다음 예에서는 UNION 식이 유효합니다.  
  
    ```  
    SELECT ProductModelID, Name  
    FROM Production.ProductModel  
    UNION  
    SELECT ProductModelID, Name   
    FROM dbo.Gloves;  
    ```  
  
3.  **쿼리 디자이너** 메뉴에서 **SQL 실행** 을 클릭하여 쿼리를 실행합니다.  
  
     쿼리 디자이너에서 통합 쿼리의 서식이 지정됩니다.  
  
## <a name="see-also"></a>참고 항목  
 [Visual Database Tools를 &#40;지원 되는 쿼리 유형&#41;](visual-database-tools.md)   
 [쿼리 및 뷰 디자인 방법 도움말 항목 &#40;Visual Database Tools&#41;](design-queries-and-views-how-to-topics-visual-database-tools.md)   
 [Visual Database Tools를 &#40;쿼리를 사용 하 여 기본 작업을 수행&#41;](perform-basic-operations-with-queries-visual-database-tools.md)   
 [UNION&#40;Transact-SQL&#41;](/sql/t-sql/language-elements/set-operators-union-transact-sql)  
  
  
