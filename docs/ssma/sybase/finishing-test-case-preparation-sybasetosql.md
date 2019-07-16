---
title: 테스트 사례 준비 (SybaseToSQL) 완료 | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Tester Component,Test Case Settings
ms.assetid: 8b2a49b0-4296-4f3f-9e56-323aa6a6fa8e
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: c3085d17804866015a78e93556dd5373d3a1b8cd
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68029143"
---
# <a name="finishing-test-case-preparation-sybasetosql"></a>테스트 사례 준비 완료(SybaseToSQL)
마법사의 마지막 페이지를 테스트 사례 설명 및 테스트에 관련 된 개체에 대 한 정보를 표시합니다. 또한이 페이지에서 설정할 수 있습니다 테스트 실행 옵션.  
  
합니다 **테스트 사례 정보** 섹션에는 테스트 사례 이름 및 설명을 보여 줍니다.  
  
합니다 **테스트 개체** 섹션에 명명 된 개체 유형별로 그룹화 된 테스트 거친된 개체 목록이 포함 되어 있습니다.  
  
합니다 **분석할 영향을 받는 개체** 섹션에는 데이터 변경 내용을 테스트 개체 실행 후 비교 해야 하는 개체의 명명 된 목록이 표시 됩니다.  
  
## <a name="test-case-settings"></a>테스트 사례 설정  
에 **테스트 사례 설정** 섹션 다음 실행 테스트 옵션을 설정할 수 있습니다.  
  
### <a name="stop-test-execution-after-first-failure"></a>첫 번째 실패 후 테스트 실행을 중지  
테스트 실행 중에 오류가 발생 하는 경우 테스트를 중단 하도록 지정 합니다.  
  
-   선택 하면 **예**, 오류가 발생 하면 실행이 중단을 테스트 합니다.  
  
-   선택 하면 **No**, 오류가 발생 한 후 테스트 실행이 계속 됩니다.  
  
### <a name="perform-data-rollback"></a>데이터 롤백 수행  
테스트 실행 후 데이터 자동 롤백 기능을 활성화 합니다.  
  
-   선택 하면 **예**, 테스트 실행 후 데이터 변경 내용이 손실 됩니다.  
  
-   선택 하면 **No**, 모든 테스트 실행 데이터 변경 내용이 저장 됩니다.  
  
### <a name="auxiliary-tables-saving-mode"></a>보조 테이블 절약 모드  
테스트 실행 중 생성 된 보조 테이블에 대 한 저장 모드를 정의 합니다. 보조 테이블에 대 한 설명을 참조 합니다 [테스트 사례 실행 &#40;SybaseToSQL&#41; ](../../ssma/sybase/running-test-cases-sybasetosql.md) 항목입니다.  
  
-   선택 하는 경우 **항상 저장**, 나중에 사용할 항상 보조 테이블 데이터가 저장 됩니다.  
  
-   선택 하는 경우 **저장 테이블 비교에 실패 한 경우**, 오류가 발생 하는 경우에 보조 테이블 데이터가 저장 됩니다.  
  
-   선택 하는 경우 **언제 든 지 삭제할**, 항상 보조 테이블 테스트가 실행 된 후 삭제할 수 있습니다.  
  
-   선택 하는 경우 **테이블 비교에 실패 한 경우 사용자에 게**, 오류가 발생 하는 경우에 필요한 작업을 선택할 수 있습니다.  
  
클릭 합니다 **완료** 준비 테스트 사례를 저장 하려면 단추 [테스트 리포지토리를 사용 하 여 &#40;SybaseToSQL&#41;](../../ssma/sybase/using-test-repositories-sybasetosql.md).  
  
## <a name="see-also"></a>관련 항목  
[테스트 리포지토리를 사용 하 여 &#40;SybaseToSQL&#41;](../../ssma/sybase/using-test-repositories-sybasetosql.md)  
[테스트 사례 실행 &#40;SybaseToSQL&#41;](../../ssma/sybase/running-test-cases-sybasetosql.md)  
[마이그레이션된 데이터베이스 개체 테스트 &#40;SybaseToSQL&#41;](../../ssma/sybase/testing-migrated-database-objects-sybasetosql.md)  
  
