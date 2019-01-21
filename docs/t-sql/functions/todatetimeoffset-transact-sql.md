---
title: TODATETIMEOFFSET(Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/13/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- TO_DATETIMEOFFSET_TSQL
- SWITCH_TZ_TSQL
- SWITCH_TZ
- TO_DATETIMEOFFSET
dev_langs:
- TSQL
helpviewer_keywords:
- date and time [SQL Server], TODATETIMEOFFSET
- TODATETIMEOFFSET function
- functions [SQL Server], time
- functions [SQL Server], date and time
- time [SQL Server], functions
ms.assetid: b5fafc08-efd4-4a3b-a0b3-068981a0a685
author: MashaMSFT
ms.author: mathoma
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 4d2234f6f8d9fa54ccbbae35e1e1dfc7568cc8ff
ms.sourcegitcommit: 1f53b6a536ccffd701fc87e658ddac714f6da7a2
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/10/2019
ms.locfileid: "54206229"
---
# <a name="todatetimeoffset-transact-sql"></a>TODATETIMEOFFSET(Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  **datetime2** 표현식에서 변환된 **datetimeoffset** 값을 반환합니다.  
  
 ![항목 링크 아이콘](../../database-engine/configure-windows/media/topic-link.gif "항목 링크 아이콘") [Transact-SQL 구문 규칙](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>구문  
  
```  
TODATETIMEOFFSET ( expression , time_zone )  
```  
  
## <a name="arguments"></a>인수  
 *expression*  
 [datetime2](../../t-sql/language-elements/expressions-transact-sql.md) 값으로 확인되는 [식](../../t-sql/data-types/datetime2-transact-sql.md)입니다.  
  
> [!NOTE]  
>  **varchar** 또는 **nvarchar**로 암시적으로 변환할 수 없는 **text**, **ntext** 또는 **image** 형식의 식을 사용할 수 없습니다.  
  
 *time_zone*  
 분(-120과 같은 정수인 경우) 단위나 시간 및 분('+13:00'과 같은 문자열인 경우) 단위의 표준 시간대 오프셋을 나타내는 식입니다. 범위는 +14에서 -14(시간) 사이입니다. 이 식은 지정된 time_zone의 현지 시간으로 해석됩니다.  
  
> [!NOTE]  
>  식이 문자열인 경우 {+|-}TZH:THM 형식이어야 합니다.  
  
## <a name="return-type"></a>반환 형식  
 **datetimeoffset**. 소수 자릿수는 *datetime* 인수와 같습니다.  
  
## <a name="examples"></a>예  
  
### <a name="a-changing-the-time-zone-offset-of-the-current-date-and-time"></a>1. 현재 날짜 및 시간의 표준 시간대 오프셋 변경  
 다음 예에서는 현재 날짜 및 시간의 표준 시간대 오프셋을 표준 시간대 `-07:00`으로 변경합니다.  
  
```  
DECLARE @todaysDateTime datetime2;  
SET @todaysDateTime = GETDATE();  
SELECT TODATETIMEOFFSET (@todaysDateTime, '-07:00');  
-- RETURNS 2007-08-30 15:51:34.7030000 -07:00  
```  
  
### <a name="b-changing-the-time-zone-offset-in-minutes"></a>2. 표준 시간대 오프셋(분) 변경  
 다음 예에서는 현재 표준 시간대를 `-120`분으로 변경합니다.  
  
```  
DECLARE @todaysDate datetime2;  
SET @todaysDate = GETDATE();  
SELECT TODATETIMEOFFSET (@todaysDate, -120);  
-- RETURNS 2007-08-30 15:52:37.8770000 -02:00  
```  
  
### <a name="c-adding-a-13-hour-time-zone-offset"></a>3. 13시간 표준 시간대 오프셋 추가  
 다음 예에서는 날짜 및 시간에 13시간 표준 시간대 오프셋을 추가합니다.  
  
```  
DECLARE @dateTime datetimeoffset(7)= '2007-08-28 18:00:30';  
SELECT TODATETIMEOFFSET (@dateTime, '+13:00');  
-- RETURNS 2007-08-28 18:00:30.0000000 +13:00  
```  
  
## <a name="see-also"></a>참고 항목  
 [CAST 및 CONVERT&#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)   
 [날짜 및 시간 데이터 형식 및 함수&#40;Transact-SQL&#41;](../../t-sql/functions/date-and-time-data-types-and-functions-transact-sql.md)   
 [AT TIME ZONE &#40;Transact-SQL&#41;](../../t-sql/queries/at-time-zone-transact-sql.md)  
  
  

