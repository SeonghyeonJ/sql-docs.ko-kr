---
title: MSSQLSERVER_617 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 617 (Database Engine error)
ms.assetid: 213545d9-08a7-4427-bfd1-8b7e16644281
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: f63983243d0859fcb7ebaaf1ac5d184757d1f274
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62867203"
---
# <a name="mssqlserver617"></a>MSSQLSERVER_617
    
## <a name="details"></a>설명  
  
|||  
|-|-|  
|제품 이름|SQL Server|  
|이벤트 ID|617|  
|이벤트 원본|MSSQLSERVER|  
|구성 요소|SQLEngine|  
|심볼 이름|NODESHASH|  
|메시지 텍스트|테이블의 해시를 취소하는 동안 해시 테이블에서 데이터베이스 ID %d의 개체 ID %ld에 대한 설명자를 찾을 수 없습니다. 작업 테이블에 항목이 없습니다. 쿼리를 다시 실행하십시오. 커서를 사용하는 경우에는 커서를 닫은 다음 다시 여십시오.|  
  
## <a name="explanation"></a>설명  
 SQL Server에서 특정 항목에 대한 작업 테이블을 찾을 수 없습니다.  
  
## <a name="user-action"></a>사용자 동작  
  
1.  커서를 사용하는 경우 커서를 닫은 다음 다시 엽니다.  
  
2.  쿼리를 다시 실행합니다.  
  
  
