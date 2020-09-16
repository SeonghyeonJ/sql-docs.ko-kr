---
description: SET OFFSETS(Transact-SQL)
title: SET OFFSETS(Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- SET_OFFSETS_TSQL
- OFFSETS_TSQL
- SET OFFSETS
- OFFSETS
dev_langs:
- TSQL
helpviewer_keywords:
- position relative to start of statement [SQL Server]
- OFFSETS option
- offsets [SQL Server]
- SET OFFSETS statement
ms.assetid: c7bcc697-0930-4630-acae-d8ccbfa4414c
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 8accd5a69be5182b0828eefcf8ac7f41e1ce0caf
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89544130"
---
# <a name="set-offsets-transact-sql"></a>SET OFFSETS(Transact-SQL)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

  [!INCLUDE[tsql](../../includes/tsql-md.md)] 문에서 지정한 키워드의 오프셋(문 시작에 대한 상대적 위치)을 반환합니다.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]  
 
 ![항목 링크 아이콘](../../database-engine/configure-windows/media/topic-link.gif "항목 링크 아이콘") [Transact-SQL 구문 표기 규칙](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>구문  
  
```syntaxsql
  
SET OFFSETS keyword_list { ON | OFF }  
```  
  
[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="arguments"></a>인수
 *keyword_list*  
 SELECT, FROM, ORDER, TABLE, PROCEDURE, STATEMENT, PARAM 및 EXECUTE를 포함한 [!INCLUDE[tsql](../../includes/tsql-md.md)] 구문을 쉼표로 구분한 목록입니다.  
  
## <a name="remarks"></a>설명  
 SET OFFSETS 옵션은 DB-Library 애플리케이션에서만 사용됩니다.  
  
 SET OFFSETS 옵션은 구문 분석 시 설정되며, 실행 시 또는 런타임에는 설정되지 않습니다. 구문 분석 시에 설정되면 코드 실행이 실제로 해당 지점에 이르렀는지에 관계없이 SET 문이 일괄 처리나 저장 프로시저에 있으면 이 설정이 적용되고 문이 실행되기 전에 SET 문이 적용됩니다. 예를 들어, 실행 중 도달한 적이 없는 IF...ELSE 문 블록에 SET 문이 있어도, IF...ELSE 문 블록이 구문 분석되기 때문에 SET 문이 적용됩니다.  
  
 SET OFFSETS 옵션을 저장 프로시저에 설정하면 저장 프로시저에서 컨트롤이 반환된 후 SET OFFSETS 값이 복원됩니다. 따라서 동적 SQL에 지정한 SET OFFSETS 문은 동적 SQL 문 다음에 오는 문에는 영향을 주지 않습니다.  
  
 OFFSETS 옵션이 ON으로 설정되어 있고 오류가 발생하지 않으면 SET PARSEONLY가 오프셋을 반환합니다.  
  
## <a name="permissions"></a>사용 권한  
 **public** 역할의 멤버 자격이 필요합니다.  
  
## <a name="see-also"></a>참고 항목  
 [SET 문&#40;Transact-SQL&#41;](../../t-sql/statements/set-statements-transact-sql.md)   
 [SET PARSEONLY &#40;Transact-SQL&#41;](../../t-sql/statements/set-parseonly-transact-sql.md)  
  
  
