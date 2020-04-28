---
title: 구현 참고 사항 | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 7ec14b9c-69b8-4c6e-838a-88d1ebdc8725
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 970188a2fca45706405e398cece0f04d38dfdc68
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81284314"
---
# <a name="implementation-notes"></a>구현 참고 사항
> [!IMPORTANT]  
>  이 기능은 이후 버전의 Windows에서 제거 될 예정입니다. 새 개발 작업에서는이 기능을 사용 하지 않도록 하 고 현재이 기능을 사용 하는 응용 프로그램은 수정 하십시오. 드라이버의 커서 기능을 사용 하는 것이 좋습니다.  
  
 이 섹션에서는 ODBC 커서 라이브러리를 구현 하는 방법에 대해 설명 합니다. 커서 라이브러리가 캐시를 유지 관리 하 고, SQL 문을 실행 하 고, ODBC 함수를 구현 하는 방법을 설명 합니다.  
  
 이 섹션에서는 다음 항목을 다룹니다.  
  
-   [커서 라이브러리 캐시](../../../odbc/reference/appendixes/cursor-library-cache.md)  
  
-   [SQL 문 처리](../../../odbc/reference/appendixes/processing-sql-statements.md)  
  
-   [ODBC 함수 및 커서 라이브러리](../../../odbc/reference/appendixes/odbc-functions-and-the-cursor-library.md)
