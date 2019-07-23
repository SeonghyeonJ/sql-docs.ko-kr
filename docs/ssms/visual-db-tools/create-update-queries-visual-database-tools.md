---
title: 업데이트 쿼리 만들기(Visual Database Tools) | Microsoft 문서
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- tables [SQL Server], updating
- queries [SQL Server], types
- Update query
- updating tables
ms.assetid: 178b7b75-8078-4e61-b2a8-4719b9d8033d
author: markingmyname
ms.author: maghan
ms.openlocfilehash: e6f2f2102008976bd997ffae729907fb0d0e0f58
ms.sourcegitcommit: e7d921828e9eeac78e7ab96eb90996990c2405e9
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/16/2019
ms.locfileid: "68266917"
---
# <a name="create-update-queries-visual-database-tools"></a>업데이트 쿼리 만들기(Visual Database Tools)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
업데이트 쿼리를 사용하면 한 번의 작업으로 여러 행의 내용을 변경할 수 있습니다. 예를 들어 `titles` 테이블에서 업데이트 쿼리를 사용하여 특정 출판사의 모든 책 가격에 10%를 추가할 수 있습니다.  
  
업데이트 쿼리를 만들려면 다음 항목을 지정합니다.  
  
-   업데이트할 테이블  
  
-   내용을 업데이트하려는 열  
  
-   개별 열을 업데이트하는 데 사용할 값이나 식  
  
-   업데이트할 행을 정의하는 검색 조건  
  
예를 들어 다음 쿼리는 한 출판사의 모든 책 가격에 10%를 추가하여 `titles` 테이블을 업데이트합니다.  
  
```  
UPDATE titles  
SET price = price * 1.1  
WHERE (pub_id = '0766')  
```  
  
> [!CAUTION]  
> 업데이트 쿼리의 실행 동작을 취소할 수는 없습니다. 문제가 발생할 경우에 대비하여 쿼리를 실행하기 전에 데이터를 백업하는 것이 좋습니다.  
  
### <a name="to-create-an-update-query"></a>업데이트 쿼리를 만들려면  
  
1.  업데이트하려는 테이블을 다이어그램 창에 추가합니다.  
  
2.  **쿼리 디자이너** 메뉴에서 **형식 변경**을 가리킨 다음 **업데이트**를 클릭합니다.  
  
    > [!NOTE]  
    > 업데이트 쿼리를 시작할 때 다이어그램 창에 두 개 이상의 테이블이 표시되어 있으면 쿼리 및 뷰 디자이너에서 [값 삽입의 대상 테이블 선택 대화 상자](../../ssms/visual-db-tools/choose-target-table-for-insert-values-dialog-box-visual-database-tools.md) 에 업데이트할 테이블의 이름을 지정하라는 메시지가 표시됩니다.  
  
3.  다이어그램 창에서 새 값을 입력하려는 각 열의 확인란을 클릭합니다. 선택한 열이 조건 창에 표시됩니다. 열을 쿼리에 추가한 경우에만 열이 업데이트됩니다.  
  
4.  조건 창의 **새 값** 열에 열의 업데이트 값을 입력합니다. 리터럴 값, 열 이름 또는 식을 입력할 수 있습니다. 이 값은 업데이트하려는 열의 데이터 형식과 일치하거나 호환되어야 합니다.  
  
    > [!CAUTION]  
    > 쿼리 및 뷰 디자이너에서는 사용자가 입력한 값이 업데이트하려는 열의 길이에 맞는지 여부를 확인할 수 없습니다. 입력한 값이 너무 길면 아무런 경고 메시지 없이 값이 잘릴 수 있습니다. 예를 들어 20자까지 허용되는 `name` 열에 길이가 25자인 업데이트 값을 지정하면 마지막 5자가 잘릴 수 있습니다.  
  
5.  **필터** 열에 검색 조건을 입력하여 업데이트할 행을 정의합니다. 자세한 내용은 [검색 조건 지정&#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/specify-search-criteria-visual-database-tools.md)을 참조하세요.  
  
    검색 조건을 지정하지 않으면 지정된 테이블의 행 전체가 업데이트됩니다.  
  
    > [!NOTE]  
    > 검색 조건에 사용할 열을 조건 창에 추가하면 쿼리 및 뷰 디자이너의 업데이트할 열 목록에도 이 열이 추가됩니다. 열을 검색 조건에만 사용하고 업데이트는 하지 않으려면 테이블 또는 테이블 반환 개체를 나타내는 사각형에서 열 이름 옆에 있는 확인란의 선택을 해제합니다.  
  
업데이트 쿼리를 실행해도 [결과 창](../../ssms/visual-db-tools/results-pane-visual-database-tools.md)에는 결과가 보고되지 않습니다. 대신, 변경된 행의 수를 나타내는 메시지가 표시됩니다.  
  
## <a name="see-also"></a>참고 항목  
[지원되는 쿼리 형식&#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/supported-query-types-visual-database-tools.md)  
[쿼리 및 뷰 디자인 방법 도움말 항목&#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/design-queries-and-views-how-to-topics-visual-database-tools.md)  
[쿼리 관련 기본 작업 수행&#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/perform-basic-operations-with-queries-visual-database-tools.md)  
  
