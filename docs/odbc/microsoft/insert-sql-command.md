---
title: INSERT-SQL 명령 | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- INSERT [ODBC]
ms.assetid: 9b648198-349f-46f6-b869-13d129945971
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 44e773248cd2d61e211f6de98d5a0f81acc78bd1
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62471178"
---
# <a name="insert---sql-command"></a>INSERT - SQL 명령
지정 된 필드 값이 포함 된 테이블의 끝에 레코드를 추가 합니다.  
  
 Visual FoxPro ODBC 드라이버는이 명령에 대 한 네이티브 Visual FoxPro 언어 구문을 지원합니다. 드라이버 관련 정보에 대 한 설명을 참조 하세요.  
  
## <a name="syntax"></a>구문  
  
```  
  
INSERT INTO dbf_name [(fname1 [, fname2, ...])]  
   VALUES (eExpression1 [, eExpression2, ...])  
```  
  
## <a name="arguments"></a>인수  
 INSERT INTO *dbf_name*  
 새 레코드가 추가 된 테이블의 이름을 지정 합니다. *dbf_name* 경로 포함할 수 있으며 이름은 식일 수 있습니다.  
  
 지정한 테이블에 열려 있지 않으면, 새 작업 영역에서 단독으로 열리는 및 새 레코드를 테이블에 추가 됩니다. 새 작업 영역 선택 되지 않은; 현재 작업 영역 선택 되어 있습니다.  
  
 지정한 테이블이 열려 있으면 INSERT 테이블에 새 레코드를 추가 합니다. 레코드 추가 된; 후 현재 작업 영역 이외의 테이블 작업 영역에 열려 있으면 선택 하지 않은 현재 작업 영역 선택 되어 있습니다.  
  
 [( *fname1*[, *fname2*[, ...]])]  
 새 레코드에서 필드의 이름을 지정 된 값이 삽입 되는에 있습니다.  
  
 VALUES ( *eExpression1*[, *eExpression2*[, ...]])  
 새 레코드를 삽입 하 여 필드 값을 지정 합니다. 필드 이름을 생략 하면 테이블 구조에 정의 된 순서 대로 필드 값을 지정 해야 합니다.  
  
## <a name="remarks"></a>Remarks  
 새 레코드를 VALUES 절에 나열 된 데이터를 포함 합니다.  
  
## <a name="driver-remarks"></a>드라이버 설명  
 응용 프로그램의 데이터 원본에는 ODBC SQL 문을 삽입 보내면 Visual FoxPro ODBC 드라이버는 명령을 변환 하지 않아도 Visual FoxProINSERT 명령으로 변환 합니다.  
  
## <a name="see-also"></a>관련 항목  
 [CREATE TABLE-SQL 명령](../../odbc/microsoft/create-table-sql-command.md)   
 [SELECT - SQL 명령](../../odbc/microsoft/select-sql-command.md)
