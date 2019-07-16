---
title: 64 비트 정수 구조 | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- C data types [ODBC], 64-bit integer structures
- data types [ODBC], C data types
- 64-bit integer structures [ODBC]
ms.assetid: ac80c798-d9b2-4430-85ed-bd2461db0ac7
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 93d9e6fd01d6b9ef98ebb10f6728ec4ba205fbb5
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67996260"
---
# <a name="64-bit-integer-structures"></a>64비트 정수 구조
Microsoft C 컴파일러에서 SQL_C_SBIGINT 및 SQL_C_UBIGINT 데이터 형식 식별자에 대 한 C 형식은 _int64 표시 합니다. Microsoft® C 컴파일러가 보다 다른 컴파일러를 사용 하는 경우 C 형식 달라질 수 있습니다. 컴파일러가 64 비트 정수를 고유 하 게 지원, 드라이버 또는 응용 프로그램 ODBCINT64 네이티브 64 비트 정수 형식으로 정의 해야 합니다. 컴파일러가 64 비트 정수를 고유 하 게 지원 하지 않는 경우 응용 프로그램 또는 드라이버는이 데이터에 액세스할 수 있는지 확인 하는 다음 구조로 정의할 수 있습니다.  
  
```  
typedef struct{  
SQLUINTEGER dwLowWord;  
SQLUINTEGER dwHighWord;  
} SQLUBIGINT  
  
typedef struct{  
SQLUINTEGER dwLowWord;  
SQLINTEGER sdwHighWord;  
} SQLBIGINT  
```  
  
 64 비트 정수를 8 바이트 경계에 맞춥니다 때문에 이러한 구조는 8 바이트 경계에 맞춰야 합니다.
