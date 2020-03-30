---
title: 경량 풀링 해제 | Microsoft 문서
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 481bb43d-6fe5-497c-9096-971fb6bf733b
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 155426b05311354153e03994f854f3860afad9c5
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/30/2020
ms.locfileid: "67940448"
---
# <a name="disable-lightweight-pooling"></a>경량 풀링 해제
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  이 규칙은 서버에 경량 풀링이 해제되어 있는지 검사합니다. lightweightpooling을 1로 설정하면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 가 파이버 모드 일정으로 전환됩니다. 파이버 모드는 UMS 작업자의 컨텍스트 전환으로 인해 중대한 성능 병목 상태가 발생하는 특정한 상황을 위한 것입니다. 이런 경우는 드물기 때문에 파이버 모드가 일반 시스템의 성능이나 확장성을 향상시키는 경우는 거의 없습니다.  
  
## <a name="best-practices-recommendations"></a>최선의 구현 방법 권장 사항  
 lightweightpooling 옵션은 철저한 테스트를 수행하고 다른 모든 성능 튜닝 방법을 평가한 후에, 현재 환경에서 컨텍스트 전환이 알려진 문제인 경우에만 설정해야 합니다.  
  
 파이버 모드를 사용하면 컨텍스트 전환을 활용하지 못해 성능이 저하될 수 있고, TLS(스레드 로컬 스토리지) 또는 스레드 소유 개체(예: 뮤텍스 - Win32 커널 개체 유형)를 사용하는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 의 일부 구성 요소가 파이버 모드에서 제대로 작동하지 않으므로 일상적인 작업에는 파이버 모드 일정을 사용하지 않는 것이 좋습니다.  
  
 경량 풀링을 제거하려면 다음 문을 실행한 다음 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]을 다시 시작합니다.  
  
```sql  
sp_configure 'show advanced options', 1;  
GO  
sp_configure 'lightweight pooling', 0;  
GO  
RECONFIGURE;  
GO  
```  
  
## <a name="for-more-information"></a>참조 항목  
 [경량 풀링 서버 구성 옵션](../../database-engine/configure-windows/lightweight-pooling-server-configuration-option.md)  
  
## <a name="see-also"></a>참고 항목  
 [정책 기반 관리를 사용하여 최선의 방법 모니터링 및 적용](../../relational-databases/policy-based-management/monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
