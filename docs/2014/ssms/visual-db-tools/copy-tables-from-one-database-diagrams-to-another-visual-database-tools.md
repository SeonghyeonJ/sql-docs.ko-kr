---
title: 한 데이터베이스 다이어그램에서 다른 다이어그램으로 테이블 복사 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- copying tables
- duplicating tables
ms.assetid: 155a4f09-9321-4887-a7d4-aa2ce6b51277
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: d1b0d70a5d8121963d424f25eef517af7cde4ba7
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2020
ms.locfileid: "62720067"
---
# <a name="copy-tables-from-one-database-diagrams-to-another-visual-database-tools"></a>한 데이터베이스 다이어그램에서 다른 다이어그램으로 테이블 복사(Visual Database Tools)
  같은 데이터베이스의 한 데이터베이스 다이어그램에서 다른 데이터베이스 다이어그램으로 테이블을 복사할 수 있습니다.  
  
 한 데이터베이스 다이어그램에서 다른 다이어그램으로 테이블을 복사하면 다른 다이어그램에는 그 테이블에 대한 참조만 추가되며 데이터베이스에 테이블이 복제되는 것은 아닙니다. 예를 들어 한 데이터베이스 다이어그램에서 다른 다이어그램으로 `authors` 테이블을 복사하면 각 다이어그램은 데이터베이스에 있는 같은 `authors` 테이블을 참조하게 됩니다.  
  
### <a name="to-copy-a-table-from-another-database-diagram"></a>다른 데이터베이스 다이어그램으로부터 테이블을 복사하려면  
  
1.  복사할 테이블이 있는 데이터베이스에 연결되어 있는지 확인합니다.  
  
2.  원본 및 대상 데이터베이스 다이어그램을 열고 원본 다이어그램에서 대상 다이어그램으로 복사할 테이블을 선택합니다.  
  
3.  도구 모음의 **복사** 단추를 클릭합니다. 이 단추를 클릭하면 선택한 테이블 정의가 클립보드에 복사됩니다.  
  
4.  대상 다이어그램으로 전환합니다. 이 다이어그램은 원본 다이어그램과 같은 데이터베이스에 있어야 합니다.  
  
5.  도구 모음에 있는 **붙여넣기** 단추를 클릭합니다. 클립보드 내용이 새 위치에 나타나고 다른 위치를 클릭할 때까지 강조 표시됩니다. 대상 다이어그램에서 선택한 테이블과 다른 테이블 사이에 관계가 있으면 관계 선이 자동으로 그려집니다.  
  
 어느 한 쪽 다이어그램에서 테이블을 편집하면 변경 내용은 두 다이어그램에 모두 반영됩니다. 마찬가지로 어느 한 쪽 다이어그램에서 테이블을 저장하면 해당 테이블은 더 이상 두 다이어그램 모두에서 "수정"된 것으로 간주되지 않습니다.  
  
## <a name="see-also"></a>참고 항목  
 [Visual Database Tools를 &#40;데이터베이스 다이어그램 작업&#41;](visual-database-tools.md)   
 [다이어그램에 테이블 추가&#40;Visual Database Tools&#41;](add-tables-to-diagrams-visual-database-tools.md)  
  
  
