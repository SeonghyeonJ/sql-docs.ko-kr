---
title: '&amp;= (비트 AND 대입)(Transact-SQL) | Microsoft Docs'
ms.custom: ''
ms.date: 01/10/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- '&='
- '&=_TSQL'
dev_langs:
- TSQL
helpviewer_keywords:
- compound operators, &=
- assignment operators, &=
- augmented operators, &=
- '&= (bitwise AND equals)'
ms.assetid: f374c885-3fee-434a-93fb-dfe6e0bcd100
author: rothja
ms.author: jroth
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 3ff077ff7e2b9dff766734b4d6023a97bba9438f
ms.sourcegitcommit: 5ed48c7dc6bed153079bc2b23a1e0506841310d1
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/21/2019
ms.locfileid: "65981377"
---
# <a name="amp-bitwise-and-assignment-transact-sql"></a>&amp;= (비트 AND 대입)(Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]


  두 개의 정수 값 간에 비트 논리적 OR 연산을 수행하고 값을 연산 결과로 설정합니다.  
  
 ![항목 링크 아이콘](../../database-engine/configure-windows/media/topic-link.gif "항목 링크 아이콘") [Transact-SQL 구문 규칙](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>구문  
  
```  
expression &= expression  
```  
  
## <a name="arguments"></a>인수  
 *expression*  
 숫자 범주에서 **bit** 데이터 형식을 제외한 모든 데이터 형식 중 하나에 대한 올바른 [식](../../t-sql/language-elements/expressions-transact-sql.md)입니다.  
  
## <a name="result-types"></a>결과 형식  
 우선 순위가 높은 인수의 데이터 형식을 반환합니다. 자세한 내용은 [데이터 형식 우선 순위&#40;Transact-SQL&#41;](../../t-sql/data-types/data-type-precedence-transact-sql.md)를 참조하세요.  
  
## <a name="remarks"></a>Remarks  
 자세한 내용은 [&&#40;비트 AND&#41;&#40;Transact-SQL&#41;](../../t-sql/language-elements/bitwise-and-transact-sql.md)를 참조하세요.  
  
## <a name="see-also"></a>참고 항목  
 [복합 연산자&#40;Transact-SQL&#41;](../../t-sql/language-elements/compound-operators-transact-sql.md)   
 [식&#40;Transact-SQL&#41;](../../t-sql/language-elements/expressions-transact-sql.md)   
 [연산자&#40;Transact-SQL&#41;](../../t-sql/language-elements/operators-transact-sql.md)   
 [비트 연산자&#40;Transact-SQL&#41;](../../t-sql/language-elements/bitwise-operators-transact-sql.md)  
  
  
