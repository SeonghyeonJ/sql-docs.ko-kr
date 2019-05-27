---
title: TEXTVALID(Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- TEXTVALID_TSQL
- TEXTVALID
dev_langs:
- TSQL
helpviewer_keywords:
- invalid text pointers [SQL Server]
- valid text pointers [SQL Server]
- TEXTVALID function
- checking text pointers
- text-pointer values
- verifying text pointers
ms.assetid: 9411c349-b59b-4740-a270-92f91d81ad23
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 1ad4bc199c923c488e968740324c5f4d47766b96
ms.sourcegitcommit: 83f061304fedbc2801d8d6a44094ccda97fdb576
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/20/2019
ms.locfileid: "65948438"
---
# <a name="text-and-image-functions---textvalid-transact-sql"></a>텍스트 및 이미지 함수 - TEXTVALID (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  특정 텍스트 포인터가 유효한지 여부를 확인하는 **text**, **ntext** 또는 **image** 함수입니다.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] 대체 기능을 사용할 수 없습니다.  
  
 ![항목 링크 아이콘](../../database-engine/configure-windows/media/topic-link.gif "항목 링크 아이콘") [Transact-SQL 구문 규칙](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>구문  
  
```  
  
TEXTVALID ( 'table.column' ,text_ ptr )  
```  
  
## <a name="arguments"></a>인수  
 *table*  
 사용할 테이블의 이름입니다.  
  
 *column*  
 사용할 열의 이름입니다.  
  
 *text_ptr*  
 확인할 텍스트 포인터입니다.  
  
## <a name="return-types"></a>반환 형식  
 **ssNoversion**  
  
## <a name="remarks"></a>Remarks  
 포인터가 유효하면 1, 유효하지 않으면 0을 반환합니다. **text** 열에 대한 식별자에는 테이블 이름이 포함되어야 합니다. 유효한 텍스트 포인터가 없으면 UPDATETEXT, WRITETEXT 또는 READTEXT를 사용할 수 없습니다.  
  
 이러한 함수와 문은 **text**, **ntext** 및 **image** 데이터를 사용하는 작업에도 유용합니다.  
  
|함수 또는 문|설명|  
|---------------------------|-----------------|  
|PATINDEX **(** ' _%pattern%_ ' **,** _expression_ **)**|**text** 및 **ntext** 열에서 지정된 문자열의 문자 위치를 반환합니다.|  
|DATALENGTH **(** _expression_ **)**|**text**, **ntext** 및 **image** 열의 데이터 길이를 반환합니다.|  
|SET TEXTSIZE|SELECT 문으로 반환할 **text**, **ntext** 또는 **image** 데이터의 크기 제한(바이트)을 반환합니다.|  
  
## <a name="examples"></a>예  
 다음 예에서는 `logo` 테이블의 `pub_info` 열에 있는 각 값에 대해 유효한 텍스트 포인터가 있는지 여부를 보고합니다.  
  
> [!NOTE]  
>  이 예를 실행하려면 **pubs** 데이터베이스를 설치해야 합니다.  
  
```  
USE pubs;  
GO  
SELECT pub_id, 'Valid (if 1) Text data'   
   = TEXTVALID ('pub_info.logo', TEXTPTR(logo))   
FROM pub_info  
ORDER BY pub_id;  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
pub_id Valid (if 1) Text data   
------ ----------------------   
0736   1                        
0877   1                        
1389   1                        
1622   1                        
1756   1                        
9901   1                        
9952   1                        
9999   1                        
  
(8 row(s) affected)  
```  
  
## <a name="see-also"></a>참고 항목  
 [DATALENGTH&#40;Transact-SQL&#41;](../../t-sql/functions/datalength-transact-sql.md)   
 [PATINDEX&#40;Transact-SQL&#41;](../../t-sql/functions/patindex-transact-sql.md)   
 [SET TEXTSIZE&#40;Transact-SQL&#41;](../../t-sql/statements/set-textsize-transact-sql.md)   
 [텍스트 및 이미지 함수&#40;Transact-SQL&#41;](https://msdn.microsoft.com/library/b9c70488-1bf5-4068-a003-e548ccbc5199)   
 [TEXTPTR&#40;Transact-SQL&#41;](../../t-sql/functions/text-and-image-functions-textptr-transact-sql.md)  
  
  
