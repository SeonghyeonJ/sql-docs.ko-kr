---
title: 테이블 및 열 대화 상자(Visual Database Tools) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- vdt.dlgbox.tablesandcolumns
ms.assetid: 8cf27be1-e66d-4735-a428-9ab4b33af4f5
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 056c200ec6b73cb7cf11ee4b3acf35bc331110b3
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/26/2020
ms.locfileid: "63204674"
---
# <a name="tables-and-columns-dialog-box-visual-database-tools"></a>테이블 및 열 대화 상자(Visual Database Tools)
  이 대화 상자를 사용하면 한 테이블의 기본 키를 다른 테이블의 외래 키에 매핑할 수 있습니다. 이 대화 상자를 열려면 **테이블 디자이너** 메뉴에서 **관계**를 클릭합니다. **외래 키 관계** 대화 상자에서 **테이블 및 열 사양** 필드를 클릭한 다음, 속성의 오른쪽에 있는 줄임표 **(...)** 를 클릭합니다.  
  
> [!NOTE]  
>  테이블이 복제용으로 게시된 경우 Transact-SQL 문 [ALTER TABLE](/sql/t-sql/statements/alter-table-transact-sql) 또는 SMO(SQL Server 관리 개체)를 사용하여 스키마를 변경해야 합니다. 테이블 디자이너 또는 데이터베이스 다이어그램 디자이너를 사용하여 스키마를 변경하면 테이블 삭제 및 재생성이 시도됩니다. 게시된 개체를 삭제할 수 없으므로 스키마가 변경되지 않습니다.  
  
## <a name="options"></a>옵션  
 **관계 이름**  
 관계의 이름을 표시합니다.  
  
 **기본 키 테이블**  
 데이터베이스의 테이블 목록이 표시됩니다. 관계의 기본 키 쪽에 사용할 테이블을 선택할 수 있습니다.  
  
 **외래 키 테이블**  
 관계의 외래 키 쪽 테이블을 표시합니다. 이 테이블은 테이블 디자이너에 현재 선택되어 있는 테이블입니다.  
  
 **기본 키 테이블 아래의 표**  
 **기본 키 테이블** 목록에서 선택한 테이블의 열이 나열됩니다. 해당 테이블의 기본 키로 사용되는 열을 입력할 수 있습니다.  
  
 **외래 키 테이블 아래의 표**  
 **외래 키 테이블** 목록에서 선택한 테이블의 열이 나열됩니다. 기본 키 열에 상응하는 외래 키 테이블의 외래 키 열을 입력할 수 있습니다.  
  
> [!NOTE]  
>  외래 키로 선택한 열의 데이터 형식은 상응하는 기본 키 열의 데이터 형식과 동일해야 합니다. 각 키 열의 수는 동일해야 합니다. 예를 들어 관계의 기본 키 쪽에 있는 테이블의 기본 키가 두 개의 열로 구성되어 있는 경우 이러한 열을 각각 관계의 외래 키 쪽에 있는 테이블의 열에 일치시켜야 합니다.  
  
## <a name="see-also"></a>참고 항목  
 [외래 키 관계 만들기](../../relational-databases/tables/create-foreign-key-relationships.md)  
  
  
