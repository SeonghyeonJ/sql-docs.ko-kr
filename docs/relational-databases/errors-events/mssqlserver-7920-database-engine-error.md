---
title: MSSQLSERVER_7920 | Microsoft 문서
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 7920 (Database Engine error)
ms.assetid: d16290ea-3875-4148-8d53-057bfee00438
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b974fda9619cd3819e79dc608d671c58e95419aa
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85726388"
---
# <a name="mssqlserver_7920"></a>MSSQLSERVER_7920
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>세부 정보  
  
| attribute | 값 |  
| :-------- | :---- |  
|제품 이름|SQL Server|  
|이벤트 ID|7920|  
|이벤트 원본|MSSQLSERVER|  
|구성 요소|SQLEngine|  
|심볼 이름|DBCC2_SUMMARY_ENTRIES|  
|메시지 텍스트|데이터베이스 ID D_ID의 시스템 카탈로그에서 ENTRY_COUNT개 항목을 처리했습니다.|  
  
## <a name="explanation"></a>설명  
DBCC CHECKALLOC을 제외한 모든 DBCC CHECK 명령에서 반환하는 정보 메시지입니다. 반환되는 값은 검사 대상 행 집합의 총 개수입니다.  
  
## <a name="user-action"></a>사용자 동작  
None  
  
