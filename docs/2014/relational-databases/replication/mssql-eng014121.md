---
title: MSSQL_ENG014121 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG014121 error
ms.assetid: c8595854-cce1-4566-ad64-d565555caded
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 996b93f04d9e9fc063bbacbb5f4a7588794ad208
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/03/2018
ms.locfileid: "52804325"
---
# <a name="mssqleng014121"></a>MSSQL_ENG014121
    
## <a name="message-details"></a>메시지 정보  
  
|||  
|-|-|  
|제품 이름|SQL Server|  
|이벤트 ID|14121|  
|이벤트 원본|MSSQLSERVER|  
|구성 요소|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|심볼 이름||  
|메시지 텍스트|배포자 '%s'을(를) 삭제할 수 없습니다. 이 배포자가 배포 데이터베이스와 연관되어 있습니다.|  
  
## <a name="explanation"></a>설명  
 배포자로 구성된 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스와 연결된 배포 데이터베이스가 있으므로 해당 인스턴스를 배포자 역할에서 제거할 수 없습니다. 이 오류는 하나 이상의 게시자와 연결된 배포 데이터베이스를 삭제하려고 할 때 발생합니다.  
  
## <a name="user-action"></a>사용자 동작  
 이 배포자와 연결된 게시자 및 배포 데이터베이스의 이름을 찾으려면 배포자의 데이터베이스에서 [sp_helpdistpublisher&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helpdistpublisher-transact-sql)를 실행합니다.  
  
 이 배포자와 연결된 배포 데이터베이스에 대해 [sp_dropdistributiondb&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dropdistributiondb-transact-sql)를 실행합니다. 모든 배포 데이터베이스 연결을 제거한 다음 배포를 해제할 수 있습니다.  
  
## <a name="see-also"></a>관련 항목  
 [오류 및 이벤트 참조&#40;복제&#41;](errors-and-events-reference-replication.md)   
 [배포 구성](configure-distribution.md)  
  
  
