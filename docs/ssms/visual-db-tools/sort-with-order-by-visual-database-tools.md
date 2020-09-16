---
description: ORDER BY를 사용하여 정렬(Visual Database Tools)
title: ORDER BY로 정렬
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- ORDER BY clause [Visual Database Tools]
ms.assetid: 459f5640-8058-4c24-97e7-7bbd6168bc39
author: markingmyname
ms.author: maghan
ms.reviewer: ''
ms.openlocfilehash: 0b356e2fd46ac86b3b4a8060a18e5cc54c10128f
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88491576"
---
# <a name="sort-with-order-by-visual-database-tools"></a>ORDER BY를 사용하여 정렬(Visual Database Tools)
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]
ORDER BY 절을 사용하면 반환된 행에 있는 하나 이상의 열을 기준으로 쿼리 결과를 정렬할 수 있습니다. 조건 정보 창에서 옵션을 선택하여 ORDER BY 절을 정의할 수 있습니다.  
  
### <a name="to-sort-a-query-using-an-order-by-clause"></a>ORDER BY 절을 사용하여 쿼리를 정렬하려면  
  
1.  쿼리를 열거나 새 쿼리를 만듭니다.  
  
2.  [조건 창](../../ssms/visual-db-tools/criteria-pane-visual-database-tools.md)에서 쿼리 결과를 정렬하는 데 사용하려는 열에 상응하는 행의 **정렬 형식** 열을 클릭합니다.  
  
3.  드롭다운 목록에서 *오름차순* 또는 *내림차순* 을 선택합니다.  
  
> [!NOTE]  
> 열의 **정렬 형식** 항목을 지우면 ORDER BY 절에서 해당 열이 제거됩니다.  
  
조건 창에서 작업하는 경우 가장 최근의 동작에 일치하도록 쿼리의 UNION 절이 변경됩니다.  
  
> [!NOTE]  
> 여러 열을 기준으로 결과를 정렬하는 경우 **정렬 순서** 열을 사용하여 각 열에 대해 서로를 기준으로 열이 검색되는 순서를 지정합니다. 자세한 내용은 **방법: 쿼리에서 여러 열 정렬**을 참조하세요.  
  
## <a name="see-also"></a>참고 항목  
[쿼리 결과 정렬 및 그룹화&#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/sort-and-group-query-results-visual-database-tools.md)  
[쿼리 결과 요약&#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/summarize-query-results-visual-database-tools.md)  
[쿼리 및 뷰 디자인 방법 도움말 항목&#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/design-queries-and-views-how-to-topics-visual-database-tools.md)  
  
