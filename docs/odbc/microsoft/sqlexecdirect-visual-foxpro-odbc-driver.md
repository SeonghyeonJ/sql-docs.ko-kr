---
description: SQLExecDirect(Visual FoxPro ODBC 드라이버)
title: SQLExecDirect (Visual FoxPro ODBC 드라이버) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLExecDirect function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: 5004060f-8510-4018-87a4-d41789e69d3e
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: d12218097caf6d4a2c4a0375f1a8e9542b2ccf59
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88449185"
---
# <a name="sqlexecdirect-visual-foxpro-odbc-driver"></a>SQLExecDirect(Visual FoxPro ODBC 드라이버)
> [!NOTE]  
>  이 항목에는 Visual FoxPro ODBC 드라이버 관련 정보가 포함 되어 있습니다. 이 함수에 대 한 일반 정보는 [ODBC API 참조](../../odbc/reference/syntax/odbc-api-reference.md)에서 적절 한 항목을 참조 하세요.  
  
 지원: 전체  
  
 ODBC API 규칙: 코어 수준  
  
 새 [PREPARABLE SQL 문을](../../odbc/microsoft/visual-foxpro-terminology.md)실행 합니다. 문에 매개 변수가 있는 경우 Visual FoxPro ODBC 드라이버는 매개 변수 표식 변수의 현재 값을 사용 합니다.  
  
 한 번에 둘 이상의 SQL 문을 전송 하는 일괄 처리 명령을 만들려면 세미콜론 (;)을 사용 합니다. 일괄 처리의 각 SQL 문을 구분 합니다.  
  
 테이블, 뷰 또는 필드 이름에 공백이 포함 된 경우에는 따옴표 안에 이름을 묶습니다. 예를 들어 데이터베이스에 내 테이블 이라는 테이블과 My Field 필드가 있는 경우 식별자의 각 요소를 다음과 같이 묶습니다.  
  
```  
SELECT `My Table`.`Field1`, `My Table`.`Field2` FROM `My Table`  
```  
  
 자세한 내용은 *ODBC 프로그래머 참조*에서 [sqlexecdirect](../../odbc/reference/syntax/sqlexecdirect-function.md) 를 참조 하세요.
