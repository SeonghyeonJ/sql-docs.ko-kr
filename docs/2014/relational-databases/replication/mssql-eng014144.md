---
title: MSSQL_ENG014144 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG014144 error
ms.assetid: fdc744d5-530e-48c4-9420-cca032fd482b
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: f85903658025f3ea1e5df805bb0593da9d840f25
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63192432"
---
# <a name="mssqleng014144"></a>MSSQL_ENG014144
    
## <a name="message-details"></a>메시지 정보  
  
|||  
|-|-|  
|제품 이름|SQL Server|  
|이벤트 ID|14144|  
|이벤트 원본|MSSQLSERVER|  
|구성 요소|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|심볼 이름||  
|메시지 텍스트|구독자 '%s'을(를) 삭제할 수 없습니다. 게시 데이터베이스 '%s'에 이 구독자에 대한 구독이 있습니다.|  
  
## <a name="explanation"></a>설명  
 구독자로 구성된 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스에 대해 구성된 활성 구독이 있으면 해당 인스턴스를 구독자 역할에서 제거할 수 없습니다.  
  
## <a name="user-action"></a>사용자 동작  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스의 구독자 상태를 변경하기 전에 연결된 구독을 모두 삭제합니다.  
  
1.  게시자의 게시 데이터베이스에서 [sp_helpsubscription&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helpsubscription-transact-sql)을 실행하여 구독을 찾습니다.  
  
2.  게시 데이터베이스에서 [sp_dropsubscription&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dropsubscription-transact-sql)을 실행하여 구독을 삭제합니다.  
  
## <a name="see-also"></a>관련 항목  
 [오류 및 이벤트 참조&#40;복제&#41;](errors-and-events-reference-replication.md)   
 [게시 구독](subscribe-to-publications.md)  
  
  
