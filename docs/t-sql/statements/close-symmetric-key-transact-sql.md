---
title: CLOSE SYMMETRIC KEY(Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 05/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- CLOSE SYMMETRIC KEY
- CLOSE_SYMMETRIC_KEY_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- closing symmetric keys
- encryption [SQL Server], symmetric keys
- symmetric keys [SQL Server], closing
- CLOSE SYMMETRIC KEY statement
- cryptography [SQL Server], symmetric keys
ms.assetid: 3b083cbb-3c6a-4f59-8d34-601db1efcc83
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: 999e8cc5e66e8e809b2c716c77b0c0fba8ae95ba
ms.sourcegitcommit: 9c99f992abd5f1c174b3d1e978774dffb99ff218
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/17/2019
ms.locfileid: "54361363"
---
# <a name="close-symmetric-key-transact-sql"></a>CLOSE SYMMETRIC KEY(Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  하나의 대칭 키를 닫거나 현재 세션에서 열려 있는 모든 대칭 키를 닫습니다.  
  
  
 ![항목 링크 아이콘](../../database-engine/configure-windows/media/topic-link.gif "항목 링크 아이콘") [Transact-SQL 구문 규칙](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>구문  
  
```  
CLOSE { SYMMETRIC KEY key_name | ALL SYMMETRIC KEYS }  
```  
  
## <a name="arguments"></a>인수  
 *Key_name*  
 닫을 대칭 키의 이름입니다.  
  
## <a name="remarks"></a>Remarks  
 열린 대칭 키는 보안 컨텍스트가 아니라 세션에 바인딩됩니다. 열린 키는 명시적으로 닫히거나 세션이 종료될 때까지 계속 사용할 수 있습니다. CLOSE ALL SYMMETRIC KEYS는 [OPEN MASTER KEY](../../t-sql/statements/open-master-key-transact-sql.md) 문을 사용하여 현재 세션에서 열려 있는 모든 데이터베이스 마스터 키를 닫습니다.  열린 키에 대한 정보는 [sys.openkeys &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-openkeys-transact-sql.md) 카탈로그 뷰에 표시됩니다.  
  
## <a name="permissions"></a>Permissions  
 대칭 키를 닫는 데 필요한 명시적 사용 권한이 없습니다.  
  
## <a name="examples"></a>예  
  
### <a name="a-closing-a-symmetric-key"></a>1. 하나의 대칭 키 닫기  
 다음 예에서는 대칭 키 `ShippingSymKey04`를 닫습니다.  
  
```  
CLOSE SYMMETRIC KEY ShippingSymKey04;  
GO  
```  
  
### <a name="b-closing-all-symmetric-keys"></a>2. 모든 대칭 키 닫기  
 다음 예에서는 현재 세션에서 열려 있는 모든 대칭 키를 닫고 명시적으로 연 데이터베이스 마스터 키도 닫습니다.  
  
```  
CLOSE ALL SYMMETRIC KEYS;  
GO  
```  
  
## <a name="see-also"></a>참고 항목  
 [CREATE SYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/create-symmetric-key-transact-sql.md)   
 [ALTER SYMMETRIC KEY&#40;Transact-SQL&#41;](../../t-sql/statements/alter-symmetric-key-transact-sql.md)   
 [OPEN SYMMETRIC KEY&#40;Transact-SQL&#41;](../../t-sql/statements/open-symmetric-key-transact-sql.md)   
 [DROP SYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/drop-symmetric-key-transact-sql.md)  
  
  
