---
title: 버전 간 호환성 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- table-valued parameters (ODBC), cross-version compatibility
ms.assetid: 5f14850b-b85c-41e2-8116-6f5b3f5e0856
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f23b0f43b32d737f03cb7c9b00368558e89e9288
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63199999"
---
# <a name="cross-version-compatibility"></a>버전 간 호환성
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]보다 이전 버전인 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]의 클라이언트 또는 서버 인스턴스에서 테이블 반환 매개 변수를 처리하는 경우 버전 간 충돌이 발생할 수 있습니다.  
  
 일반적으로 테이블 반환 매개 변수 기능은 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 이상 버전의 서버에 연결된 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 이상 버전의 클라이언트(SQL Server Native Client 10.0 사용)에서만 사용할 수 있습니다. 카탈로그 함수 결과 집합에 새 열만 연결할 때 표시 됩니다는 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] (또는 이상) 서버.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client의 이전 버전으로 컴파일된 클라이언트 응용 프로그램이 테이블 반환 매개 변수가 필요한 문을 실행하면 서버에서 데이터 변환 오류를 통해 이 상태를 검색하며, ODBC에서 SQLSTATE 07006 및 "제한된 데이터 형식 특성을 위반했습니다"라는 메시지를 반환합니다.  
  
 으로 컴파일된 클라이언트 응용 프로그램이 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 10.0 또는 서버 인스턴스에 연결 하는 경우 테이블 반환 매개 변수를 사용 하는 이후 하려고 이전의 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client에서이 감지 및 SQLBindCol, SQLBindParameter, SQLSetDescFields, 및 SQLSetDescRec 호출 "제한 된 데이터 형식 특성 위반 (이 연결에 대 한 SQL Server의 버전 테이블 반환 매개 변수를 지원 하지 않습니다)" SQLSTATE 07006 및 메시지 실패 합니다.  
  
## <a name="see-also"></a>관련 항목  
 [테이블 반환 매개 변수 &#40;ODBC&#41;](table-valued-parameters-odbc.md)  
  
  
