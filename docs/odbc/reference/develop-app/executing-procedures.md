---
title: 프로시저 실행 | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQL statements [ODBC], procedures
- procedures [ODBC], executing
ms.assetid: a75e497a-4661-438a-a10e-f598c65f81be
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ff234d1d8e099611c8718eac5ae3b584e926a2bd
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63061971"
---
# <a name="executing-procedures"></a>프로시저 실행
ODBC에는 프로시저 실행에 대 한 표준 이스케이프 시퀀스를 정의 합니다. 이 시퀀스 및 사용 하는 코드 예제에서는 구문에 대 한 참조 [프로시저 호출](../../../odbc/reference/develop-app/procedure-calls.md)합니다.  
  
 프로시저를 실행 하려면 응용 프로그램에는 다음 작업을 수행 합니다.  
  
1.  매개 변수의 값을 설정합니다. 자세한 내용은 [문 매개 변수](../../../odbc/reference/develop-app/statement-parameters.md)이 섹션의 뒷부분에 나오는.  
  
2.  호출 **SQLExecDirect** 프로시저를 실행 하는 SQL 문을 포함 하는 문자열을 전달 합니다. 이 문은 ODBC 또는 DBMS 관련 구문;에 의해 정의 된 이스케이프 시퀀스를 사용할 수 있습니다. DBMS 관련 구문을 사용 하는 문을 상호 운용 되지는 않습니다.  
  
3.  때 **SQLExecDirect** 호출 되는 드라이버:  
  
    -   현재 매개 변수 값을 검색 하 고 필요에 따라 변환 합니다. 자세한 내용은 [문 매개 변수](../../../odbc/reference/develop-app/statement-parameters.md)이 섹션의 뒷부분에 나오는.  
  
    -   데이터 원본에서 프로시저를 호출 하 고 변환 된 매개 변수 값을 보냅니다. 드라이버별은 드라이버는 프로시저를 호출 하는 방법입니다. 예를 들어, 해당 데이터 원본의 SQL 문법을 사용 하 고이 문을 실행을 위해 제출 하는 SQL 문을 수정할 수 또는 DBMS의 데이터 스트림 프로토콜에 정의 된 원격 프로시저 호출 (RPC) 메커니즘을 사용 하 여 직접 프로시저를 호출할 수 있습니다.  
  
    -   모든 입/출력 또는 출력 매개 변수의 값 또는 프로시저에서 성공 하는 것으로 가정 하 여 프로시저 반환 값을 반환 합니다. 기타 모든 결과 (행 개수 및 결과 집합) 생성 프로시저에 의해 처리 된 후 이러한 값 수까지 사용할 수 없습니다. 프로시저가 실패 하면 드라이버는 모든 오류를 반환 합니다.
