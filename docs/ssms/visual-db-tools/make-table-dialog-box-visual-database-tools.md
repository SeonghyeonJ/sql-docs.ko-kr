---
description: 테이블 만들기 대화 상자(Visual Database Tools)
title: 테이블 만들기 대화 상자
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- vdtsql.chm:69650
- vdt.dlgbox.maketable
ms.assetid: 5eb28dc3-828e-486c-9348-596bb5a04c85
author: markingmyname
ms.author: maghan
ms.reviewer: ''
ms.openlocfilehash: 1f0df6edfdb553f85065c0e6a9f8748b52a0f2c0
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88485028"
---
# <a name="make-table-dialog-box-visual-database-tools"></a>테이블 만들기 대화 상자(Visual Database Tools)
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]
이 대화 상자를 사용하면 행을 복사하려는 대상 테이블을 만들고 이름을 지정할 수 있습니다. 이 대화 상자는 쿼리 형식을 MAKE TABLE 쿼리로 변경하면 나타납니다. 쿼리 형식을 변경하려면 **쿼리 디자이너** 메뉴에서 **형식 변경**을 가리킨 다음 **테이블 만들기**를 클릭합니다.  
  
## <a name="options"></a>옵션  
**Table Name**  
만들 테이블의 이름을 입력합니다. 쿼리 및 뷰 디자이너는 이 이름이 이미 사용되고 있는지 또는 사용자에게 테이블을 만들 수 있는 권한이 있는지를 확인하지 않습니다.  
  
다른 데이터베이스에 대상 테이블을 만들려면 대상 데이터베이스의 이름, 소유자(필요한 경우) 및 테이블의 이름을 포함하는 정규화된 테이블 이름을 지정하십시오.  
  
> [!NOTE]  
> 만들 테이블의 속성을 변경하려는 경우 쿼리를 실행하기 전에 **속성** 창에서 이러한 테이블의 속성을 변경할 수 있습니다. 자세한 내용은 [쿼리 속성&#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/query-properties-visual-database-tools.md)을 참조하세요.  
  
## <a name="see-also"></a>참고 항목  
[테이블 만들기 쿼리 만들기&#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/create-make-table-queries-visual-database-tools.md)  
[쿼리 형식&#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/types-of-queries-visual-database-tools.md)  
  
