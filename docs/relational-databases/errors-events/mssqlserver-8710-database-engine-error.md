---
title: MSSQLSERVER_8710 | Microsoft 문서
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 8710 (Database Engine error)
ms.assetid: 78b9f9da-5489-4be0-94df-f065d86ed18c
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 33bdc74ffee071d8a5f9e7d10543bad133066b32
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85637070"
---
# <a name="mssqlserver_8710"></a>MSSQLSERVER_8710
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>세부 정보  
  
| attribute | 값 |  
| :-------- | :---- |  
|제품 이름|MSSQLSERVER|  
|이벤트 ID|8710|  
|이벤트 원본|MSSQLSERVER|  
|구성 요소|SQLEngine|  
|심볼 이름|QUERY2_CUBE_ILLEGAL_AGG_FUNC|  
|메시지 텍스트|CUBE, ROLLUP 또는 GROUPING SET 쿼리에 사용되는 집계 함수는 하위 집계 병합을 지원해야 합니다. 이 문제를 해결하려면 집계 함수를 제거하거나 GROUP BY 절 대신 UNION ALL을 사용하여 쿼리를 작성하십시오.|  
  
## <a name="explanation"></a>설명  
하위 집계 병합 방법을 제공하지 않는 CUBE, ROLLUP 또는 GROUPING SETS에 집계 함수가 사용되었습니다.  
  
## <a name="user-action"></a>사용자 동작  
이 문제를 해결하려면 집계 함수를 제거하거나 GROUP BY 절 대신 UNION ALL을 사용하여 쿼리를 작성하십시오.  
  
