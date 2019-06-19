---
title: 그룹 조건 지정(Visual Database Tools) | Microsoft 문서
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- HAVING clause, query groups
- group query conditions [SQL Server]
ms.assetid: 269ad9c5-3261-4526-badf-7be3c869f229
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 8fbf1ea1a9793ae8d0aad56ee6f524e2e225d26a
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/15/2019
ms.locfileid: "65098962"
---
# <a name="specify-conditions-for-groups-visual-database-tools"></a>그룹 조건 지정(Visual Database Tools)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
HAVING 절에서 그룹 전체에 적용되는 조건을 지정하여 쿼리에 표시되는 그룹을 제한할 수 있습니다. 데이터를 그룹화하고 집계한 후에 HAVING 절의 조건이 적용됩니다. 쿼리에는 이 조건에 맞는 그룹만 표시됩니다.  
  
예를 들어, `titles` 테이블의 각 출판사에서 발행한 모든 도서의 평균 가격 중에서 $10.00를 초과하는 평균 가격만 표시할 수 있습니다. 이 경우, `AVG(price) > 10`과 같은 조건을 사용하여 HAVING 절을 지정합니다.  
  
> [!NOTE]  
> 경우에 따라서는 그룹 전체에 조건을 적용하기 전에 특정 개별 행을 그룹에서 제외할 수도 있습니다. 자세한 내용은 [동일한 쿼리에서 HAVING 및 WHERE 절 사용&#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/use-having-and-where-clauses-in-the-same-query-visual-database-tools.md)을 참조하세요.  
  
AND 및 OR을 사용하여 조건을 연결하면 HAVING 절에 대한 복잡한 조건을 만들 수 있습니다. 검색 조건에 AND 및 OR을 사용하는 방법에 대한 자세한 내용은 [한 열에 여러 검색 조건 지정&#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/specify-multiple-search-conditions-for-one-column-visual-database-tools.md)을 참조하세요.  
  
### <a name="to-specify-a-condition-for-a-group"></a>그룹에 대한 조건을 지정하려면  
  
1.  쿼리의 그룹을 지정합니다. 자세한 내용은 [쿼리 결과 행 그룹화&#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/group-rows-in-query-results-visual-database-tools.md)를 참조하세요.  
  
2.  조건의 기반으로 삼을 열이 [조건 창](../../ssms/visual-db-tools/criteria-pane-visual-database-tools.md)에 아직 없으면 이 열을 추가합니다. 조건에 사용되는 열은 대부분 이미 그룹 열이거나 요약 열인 경우가 많습니다. 집계 함수나 GROUP BY 절의 일부가 아닌 열은 사용할 수 없습니다.  
  
3.  **필터** 열에서 그룹에 적용할 조건을 지정합니다.  
  
    [쿼리 및 뷰 디자이너](../../ssms/visual-db-tools/query-and-view-designer-tools-visual-database-tools.md) 에서 [SQL 창](../../ssms/visual-db-tools/sql-pane-visual-database-tools.md)의 문에 HAVING 절이 자동으로 작성됩니다. 예를 들면 다음과 같습니다.  
  
    ```  
    SELECT pub_id, AVG(price)  
    FROM titles  
    GROUP BY pub_id  
    HAVING (AVG(price) > 10)  
    ```  
  
4.  추가로 지정할 각 조건에 대하여 2단계와 3단계를 반복합니다.  
  
## <a name="see-also"></a>참고 항목  
[쿼리 결과 정렬 및 그룹화&#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/sort-and-group-query-results-visual-database-tools.md)  
  
