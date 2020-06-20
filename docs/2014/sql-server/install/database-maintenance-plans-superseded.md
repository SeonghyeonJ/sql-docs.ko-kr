---
title: 데이터베이스 유지 관리 계획 대체 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- suspended database maintenance plans
- database maintenance plans [SQL Server Agent]
- maintenance plans [SQL Server Agent]
ms.assetid: efac127c-6c81-4c7a-a6c4-9aae5d15545d
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 3aea75cc4ecc94ccbaeb1f35cecd0b18ff3a65ff
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/18/2020
ms.locfileid: "85054927"
---
# <a name="database-maintenance-plans-superseded"></a>데이터베이스 유지 관리 계획이 대체됩니다.
    
## <a name="component"></a>구성 요소  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에이전트  
  
## <a name="description"></a>Description  
 기존 데이터베이스 유지 관리 계획이 업그레이드되고 계속 작동하지만 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]를 사용하여 새 데이터베이스 유지 관리 계획을 만들 수 없습니다. 개체 탐색기에서 유지 관리 계획을 보려면 관리, 레거시를 차례로 확장합니다. 데이터베이스 유지 관리 계획에 대 한 상황에 맞는 메뉴에서 **마이그레이션** 을 선택 하 여 기존 데이터베이스 유지 관리 계획을 새 형식으로 마이그레이션할 수 있습니다. 새 유지 관리 계획 기능은 데이터베이스 유지 관리 계획을 완전히 대체하지는 않으므로 마이그레이션 후에 일부 기능이 손실될 수도 있습니다. 데이터베이스 유지 관리 계획을 마이그레이션해도 이전 계획은 삭제되지 않으므로 이전 계획을 제거하기 전에 해당 기능을 유지 관리 계획으로 테스트할 수 있습니다.  
  
 다음 기능은 데이터베이스 유지 관리 계획에서 더 이상 지원되지 않습니다.  
  
-   로그 전달  
  
-   **데이터베이스 무결성 검사** 태스크의 **사소한 문제를 복구 하려고** 합니다. 옵션  
  
## <a name="corrective-action"></a>수정 동작  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 로그 전달이 데이터베이스 유지 관리 계획에 포함되지 않도록 방지됩니다. 자세한 내용은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 온라인 설명서에서 "로그 전달"을 참조하십시오.  
  
  
