---
description: 사용자 데이터베이스의 대칭 키
title: 사용자 데이터베이스의 대칭 키 | Microsoft 문서
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 3333ab5b-2518-4753-a0a8-57df5e5af74f
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: c7882b4f3f425b600e3ef57fa836ffffd6756289
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88380969"
---
# <a name="symmetric-keys-on-user-databases"></a>사용자 데이터베이스의 대칭 키
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  이 규칙은 길이가 128바이트 미만인 키에 RC2 또는 RC4 암호화 알고리즘이 사용되지 않는지 검사합니다.  
  
## <a name="best-practices-recommendations"></a>최선의 구현 방법 권장 사항  
 AES 128비트 이상을 사용하여 데이터 암호화를 위한 대칭 키를 만듭니다. 운영 체제에서 AES를 지원하지 않을 경우 3DES를 사용합니다.  
  
## <a name="for-more-information"></a>참조 항목  
 [암호화 알고리즘 선택](../../relational-databases/security/encryption/choose-an-encryption-algorithm.md)  
  
## <a name="see-also"></a>참고 항목  
 [정책 기반 관리를 사용하여 최선의 방법 모니터링 및 적용](../../relational-databases/policy-based-management/monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
