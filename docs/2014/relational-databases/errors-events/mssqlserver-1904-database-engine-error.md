---
title: MSSQLSERVER_1904 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 1904 (Database Engine error)
ms.assetid: 2a35d57d-74e2-45a2-8f67-3f2e51d69712
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 568cfe7499c041c2ee6a8ac3698b31698171bece
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/18/2020
ms.locfileid: "85034804"
---
# <a name="mssqlserver_1904"></a>MSSQLSERVER_1904
    
## <a name="details"></a>세부 정보  
  
|||  
|-|-|  
|제품 이름|SQL Server|  
|이벤트 ID|1904|  
|이벤트 원본|MSSQLSERVER|  
|구성 요소|SQLEngine|  
|심볼 이름|KEYCOUNT|  
|메시지 텍스트|테이블 '%.\*ls'의 %S_MSG '%.*ls'에 있는 %S_MSG 키 목록에 %d개의 열 이름이 있습니다. 인덱스 또는 통계 키 열 목록의 최대 한계는 %d개입니다.|  
  
## <a name="explanation"></a>설명  
 지정된 인덱스 또는 통계의 키 열 목록이 허용되는 최대 열 개수를 초과했습니다.  
  
## <a name="user-action"></a>사용자 동작  
 지정된 최대 열 개수를 초과하지 않도록 키 열 목록을 수정하십시오.  
  
 비클러스터형 인덱스의 경우 CREATE INDEX 문에 INCLUDE 절을 사용하여 인덱스에 열을 키가 아닌 열로 추가하는 것을 고려해 보십시오. 이 방법을 사용하면 키 열 개수가 현재 인덱스 크기 제한인 최대 16개를 초과하는 것을 피할 수 있습니다. 자세한 내용은 [Create Indexes with Included Columns](../indexes/create-indexes-with-included-columns.md)을 참조하세요.  
  
## <a name="see-also"></a>참고 항목  
 [CREATE INDEX&#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql)   
 [CREATE STATISTICS&#40;Transact-SQL&#41;](/sql/t-sql/statements/create-statistics-transact-sql)  
  
  
