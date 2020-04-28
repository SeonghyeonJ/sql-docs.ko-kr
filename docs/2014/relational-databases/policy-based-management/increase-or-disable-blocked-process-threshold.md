---
title: 차단된 프로세스 임계값 늘리기 또는 해제 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 71db8ef6-341b-4465-99db-5c63e48d4c7d
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 694c5676a5d55fe4fca227d9042ff4f1a9e9d618
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/26/2020
ms.locfileid: "62704971"
---
# <a name="increase-or-disable-blocked-process-threshold"></a>차단된 프로세스 임계값 늘리기 또는 해제
  이 규칙은 blocked process threshold 옵션이 0(해제)으로 설정되거나 5 이상의 값(초)으로 설정되어 있는지 검사합니다. blocked process threshold 옵션을 1에서 4 사이의 값으로 설정하면 교착 상태 모니터가 계속해서 실행될 수 있습니다. 1에서 4 사이의 값은 문제 해결 용도로만 사용해야 하며 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 고객 서비스 지원 센터의 도움 없이 장기적으로 사용하거나 프로덕션 환경에서 사용하면 안 됩니다.  
  
## <a name="best-practices-recommendations"></a>최선의 구현 방법 권장 사항  
 이 문제를 해결하려면 blocked process threshold 옵션의 값을 5(초) 이상으로 설정하거나 값을 0으로 설정하여 blocked process threshold를 해제합니다. blocked process threshold를 `5` 초로 설정하려면 다음 문을 실행합니다.  
  
```  
sp_configure 'show advanced options', 1 ;  
GO  
RECONFIGURE ;  
GO  
sp_configure 'blocked process threshold', 5 ;  
GO  
RECONFIGURE ;  
GO  
```  
  
## <a name="for-more-information"></a>참조 항목  
 [blocked process threshold 서버 구성 옵션](../../database-engine/configure-windows/blocked-process-threshold-server-configuration-option.md)  
  
## <a name="see-also"></a>참고 항목  
 [정책 기반 관리를 사용하여 최선의 방법 모니터링 및 적용](monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
