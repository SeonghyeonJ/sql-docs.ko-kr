---
title: 테이블 별칭 만들기(Visual Database Tools) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- table aliases [SQL Server]
- aliases [SQL Server], tables
ms.assetid: 49e61e85-8abf-4ca7-8c70-7e9f8f1078bd
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 7e7172a7b9b17dfa4553d3179d8cc1a880040f13
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63306526"
---
# <a name="create-table-aliases-visual-database-tools"></a>테이블 별칭 만들기(Visual Database Tools)
  별칭을 사용하면 테이블 이름이 필요한 작업을 더 쉽게 수행할 수 있습니다. 별칭은 다음과 같은 경우에 유용하게 사용할 수 있습니다.  
  
-   [SQL 창](visual-database-tools.md) 에서 문을 더 간결하고 읽기 쉽게 만들려는 경우  
  
-   열 이름을 한정하는 경우 등과 같이 쿼리에서 테이블 이름을 자주 참조하고 쿼리에 대해 특정한 문자 길이 제한을 반드시 준수하려고 합니다. 일부 데이터베이스에서는 쿼리의 최대 길이가 제한됩니다.  
  
-   자체 조인 등과 같이 동일한 테이블의 여러 인스턴스를 사용하여 작업할 때 특정 인스턴스를 지정해야 하는 경우  
  
 예를 들어, 테이블 이름 `"e"` _ `employee`에 대한 별칭`information`를 만든 다음 쿼리의 나머지 부분 전반에 걸쳐 테이블을 `"e"` 로 지칭할 수 있습니다.  
  
### <a name="to-create-an-alias-for-a-table-or-table-valued-object"></a>테이블이나 테이블 반환 개체에 대한 별칭을 만들려면  
  
1.  테이블이나 테이블 반환 개체를 쿼리에 추가합니다.  
  
2.  **다이어그램 창**에서 별칭을 만들려는 개체를 마우스 오른쪽 단추로 클릭한 다음 바로 가기 메뉴에서 **속성** 을 선택합니다.  
  
3.  **속성** 창의 **별칭** 필드에 별칭을 입력합니다.  
  
## <a name="see-also"></a>관련 항목  
 [쿼리에 테이블 추가 &#40;Visual Database Tools&#41;](add-tables-to-queries-visual-database-tools.md)   
 [쿼리 결과 정렬 및 그룹화 &#40;Visual Database Tools&#41;](sort-and-group-query-results-visual-database-tools.md)   
 [쿼리 결과 요약 &#40;Visual Database Tools&#41;](summarize-query-results-visual-database-tools.md)   
 [쿼리 관련 기본 작업 수행&#40;Visual Database Tools&#41;](perform-basic-operations-with-queries-visual-database-tools.md)  
  
  
