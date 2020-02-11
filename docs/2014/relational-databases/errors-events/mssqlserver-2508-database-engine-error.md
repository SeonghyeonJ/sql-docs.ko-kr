---
title: MSSQLSERVER_2508 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 2508 (Database Engine error)
ms.assetid: c37d40e5-c665-4d66-a727-5cb845634fcc
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 7b09fcbc5e6e291ae87945d55bc534a0a63fb0c0
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2020
ms.locfileid: "62869160"
---
# <a name="mssqlserver_2508"></a>MSSQLSERVER_2508
    
## <a name="details"></a>세부 정보  
  
|||  
|-|-|  
|제품 이름|SQL Server|  
|이벤트 ID|2508|  
|이벤트 원본|MSSQLSERVER|  
|구성 요소|SQLEngine|  
|심볼 이름|DBCC_OUT_OF_DATE_PAGE_OR_ROW_COUNT|  
|메시지 텍스트|개체 "%.\*ls", 인덱스 ID %d, 파티션 ID %I64d, 할당 단위 ID %I64d(%.\*ls 유형)의 %.*ls 개수가 잘못되었습니다. DBCC UPDATEUSAGE를 실행하십시오.|  
  
## <a name="explanation"></a>설명  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 이전 버전의 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]에서는 테이블 및 인덱스의 행 및 페이지 개수의 값이 정확하지 않게 계산될 수 있습니다. [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 이전 버전에서 만든 데이터베이스에는 올바르지 않은 개수가 포함될 수 있습니다. 이러한 오류를 검색하고 오류가 발견되면 이 경고 메시지를 반환하도록 DBCC CHECKDB가 개선되었습니다.  
  
## <a name="user-action"></a>사용자 동작  
 지정된 개체나 인덱스 또는 개체가 포함된 데이터베이스를 대상으로 DBCC UPDATEUSAGE를 실행하여 잘못된 개수를 수정하십시오.  
  
  
