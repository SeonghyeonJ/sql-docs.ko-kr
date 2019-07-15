---
title: 여러 열에 대해 테이블 조인(Visual Database Tools) | Microsoft 문서
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- multiple column joins
- joins [SQL Server], multiple columns
ms.assetid: 56a158bc-a42a-4b78-baad-4721d2d22cd3
author: markingmyname
ms.author: maghan
manager: jroth
ms.openlocfilehash: f82acdab4dcab5644169852bdbba9dc326e03f26
ms.sourcegitcommit: 5d839dc63a5abb65508dc498d0a95027d530afb6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/09/2019
ms.locfileid: "67682110"
---
# <a name="join-tables-on-multiple-columns-visual-database-tools"></a>여러 열에 대해 테이블 조인(Visual Database Tools)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
테이블을 여러 열과 조인할 수 있습니다. 즉, 여러 조건을 만족하는 경우에만 두 테이블에서 행이 일치하는 쿼리를 만들 수 있습니다. 한 테이블에 있는 여러 외래 키 열이 다른 테이블에 있는 여러 기본 키 열과 일치하는 관계가 데이터베이스에 포함된 경우 이 관계를 사용하여 여러 열 조인을 만들 수 있습니다. 자세한 내용은 [테이블 자동 조인&#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/join-tables-automatically-visual-database-tools.md)을 참조하세요.  
  
데이터베이스에 여러 외래 키 열 관계가 포함되지 않은 경우에도 조인을 수동으로 만들 수 있습니다.  
  
### <a name="to-manually-create-a-multicolumn-join"></a>여러 열 조인을 수동으로 만들려면  
  
1.  조인할 테이블을 [다이어그램 창](../../ssms/visual-db-tools/diagram-pane-visual-database-tools.md) 에 추가합니다.  
  
2.  첫 번째 테이블 창의 첫 번째 조인 열 이름을 끌어서 두 번째 테이블 창의 관련 열 위에 놓습니다. 텍스트, ntext, 또는 이미지 열을 기반으로 할 수 없습니다.  
  
    > [!NOTE]  
    > 일반적으로 조인 열의 데이터 형식은 같거나 호환 가능해야 합니다. 예를 들어, 첫 번째 테이블의 조인 열이 날짜이면 이 열을 두 번째 테이블의 날짜 열과 관련시켜야 합니다. 반면에 첫 번째 조인 열이 정수이면 관련된 조인 열의 데이터 형식도 정수이어야 하지만 크기는 달라도 됩니다. 그러나 경우에 따라서는 암시적 데이터 형식 변환으로 외관상 호환되지 않는 열을 조인할 수도 있습니다.  
    >   
    > [쿼리 및 뷰 디자이너](../../ssms/visual-db-tools/query-and-view-designer-tools-visual-database-tools.md) 는 조인을 만드는 데 사용하는 열의 데이터 형식을 검사하지 않지만 데이터 형식이 호환되지 않으면 쿼리를 실행할 때 데이터베이스에 오류 메시지가 표시됩니다.  
  
3.  첫 번째 테이블 창의 두 번째 조인 열 이름을 끌어서 두 번째 테이블 창의 관련 열 위에 놓습니다.  
  
4.  두 테이블에 있는 각 추가 조인 열 쌍에 대해 3단계를 반복합니다.  
  
5.  쿼리를 실행합니다.  
  
## <a name="see-also"></a>참고 항목  
[조인을 사용한 쿼리&#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/query-with-joins-visual-database-tools.md)  
  
