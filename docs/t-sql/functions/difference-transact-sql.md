---
title: DIFFERENCE(Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- DIFFERENCE
- DIFFERENCE_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- DIFFERENCE function
- comparing SOUNDEX values
- SOUNDEX values
ms.assetid: c58ca25d-d6ea-48fa-93bb-c9374b0b2a2b
author: julieMSFT
ms.author: jrasnick
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 310428540e390261840d438506e17da84390aa0c
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/05/2020
ms.locfileid: "82827047"
---
# <a name="difference-transact-sql"></a>DIFFERENCE(Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

이 함수는 두 문자 식의 [SOUNDEX()](./soundex-transact-sql.md) 값의 차이를 측정하는 정수 값을 반환합니다.  
  
 ![항목 링크 아이콘](../../database-engine/configure-windows/media/topic-link.gif "항목 링크 아이콘") [Transact-SQL 구문 표기 규칙](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>구문  
  
```syntaxsql
DIFFERENCE ( character_expression , character_expression )  
```  
  
## <a name="arguments"></a>인수  
*character_expression*  
문자 데이터의 영숫자 [식](../../t-sql/language-elements/expressions-transact-sql.md)입니다. *character_expression*은 상수, 변수 또는 열일 수 있습니다.  
  
## <a name="return-types"></a>반환 형식  
**int**  
 
## <a name="remarks"></a>설명  
`DIFFERENCE`는 서로 다른 두 `SOUNDEX` 값을 비교하고 정수 값을 반환합니다. 이 값은 0에서 4의 척도로 `SOUNDEX` 값이 일치하는 정도를 측정합니다. 0의 값은 SOUNDEX 값 간에 유사성이 없거나 약하다는 것을 나타내며, 4는 강력한 유사성이 있거나 동일하게 일치하는 SOUNDEX 값을 나타냅니다.  
  
`DIFFERENCE` 및 `SOUNDEX`에는 데이터 정렬 구분이 있습니다.  
  
## <a name="examples"></a>예  
이 예의 첫 번째 부분에서 매우 유사한 두 개의 문자열에 대한 `SOUNDEX` 값을 비교합니다. Latin1_General 데이터 정렬에 대해 `DIFFERENCE`는 `4` 값을 반환합니다. 예의 두 번째 부분에서 매우 다른 두 개의 문자열에 대한 `SOUNDEX` 값을 비교하고, Latin1_General 데이터 정렬에 대해 `DIFFERENCE`는 `0` 값을 반환합니다.  
  
```  
-- Returns a DIFFERENCE value of 4, the least possible difference.  
SELECT SOUNDEX('Green'), SOUNDEX('Greene'), DIFFERENCE('Green','Greene');  
GO  
-- Returns a DIFFERENCE value of 0, the highest possible difference.  
SELECT SOUNDEX('Blotchet-Halls'), SOUNDEX('Greene'), DIFFERENCE('Blotchet-Halls', 'Greene');  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
----- ----- -----------   
G650  G650  4             
  
(1 row(s) affected)  
  
----- ----- -----------   
B432  G650  0             
  
(1 row(s) affected)  
```  
  
## <a name="see-also"></a>참고 항목  
 [SOUNDEX&#40;Transact-SQL&#41;](../../t-sql/functions/soundex-transact-sql.md)   
 [문자열 함수&#40;Transact-SQL&#41;](../../t-sql/functions/string-functions-transact-sql.md)  
  
  

