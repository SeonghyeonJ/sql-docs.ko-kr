---
title: sys.sp_rda_reconcile_columns (TRANSACT-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: language-reference
f1_keywords:
- sys.sp_rda_reconcile_columns
- sys.sp_rda_reconcile_columns_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sp_rda_reconcile_columns stored procedure
ms.assetid: 60d9cc4e-1828-450b-9d88-5b8485800d73
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 83ac2322d39fba05ce75f50fcd9cf9e5005b72b4
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/15/2019
ms.locfileid: "65982984"
---
# <a name="syssprdareconcilecolumns-transact-sql"></a>sys.sp_rda_reconcile_columns (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  SQL Server 스트레치 사용 테이블의 열에는 원격 Azure 테이블의 열을 조정합니다.  
    
  **sp_rda_reconcile_columns** 원격 테이블에 없는 SQL Server 스트레치 사용 테이블에 있는 원격 테이블에 열을 추가 합니다. 이러한 열에는 원격 테이블에서 실수로 삭제 하는 열 수 있습니다. 그러나 **sp_rda_reconcile_columns** SQL Server 테이블에 없는 원격 테이블에 있는 원격 테이블에서 열을 삭제 하지 않습니다.
  
  > [!IMPORTANT]
  > **sp_rda_reconcile_columns** 가 원격 테이블에서 실수로 삭제한 열을 다시 만드는 경우 이전에 삭제된 열에 있었던 데이터를 복원하지 않습니다.
  
 ![항목 링크 아이콘](../../database-engine/configure-windows/media/topic-link.gif "항목 링크 아이콘") [Transact-SQL 구문 규칙](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
   
## <a name="syntax"></a>구문  
  
```  
  
sp_rda_reconcile_columns @objname = '@objname'  
  
```  
  
## <a name="arguments"></a>인수  
 \@objname = ' *\@objname*'  
 스트레치 사용 SQL Server 테이블의 이름입니다.  
  
## <a name="return-code-values"></a>반환 코드 값  
 0 (성공) 또는 > 0 (실패)  
  
## <a name="permissions"></a>사용 권한  
 Db_owner 권한이 필요합니다.  
   
## <a name="remarks"></a>Remarks  
 원격 Azure 테이블의 열이 스트레치가 활성화된 SQL Server 테이블에 더 이상 존재하지 않는 경우 이러한 추가 열이 있어도 스트레치 데이터베이스가 정상적으로 작동합니다. 필요에 따라 추가 열을 수동으로 제거할 수 있습니다.  
  
## <a name="example"></a>예제  
 원격 Azure 테이블의 열을 조정 하려면 다음 문을 실행 합니다.  
  
```sql  
EXEC sp_rda_reconcile_columns @objname = N'StretchEnabledTableName';  
```  
  
  
