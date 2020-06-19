---
title: 데이터베이스 변경 감지 대화 상자(Visual Database Tools) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- vdt.dlgbox.schema.databasechangesdetected
- vdtsql.chm:65543
- vdtsql.chm:65554
ms.assetid: 91f13086-371f-46a2-9f46-804c1415f3ed
author: stevestein
ms.author: sstein
ms.openlocfilehash: 01512949fae8e922c3f5d0056d4bc8d76f407cd6
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/18/2020
ms.locfileid: "85061803"
---
# <a name="database-changes-detected-dialog-box-visual-database-tools"></a>데이터베이스 변경 감지 대화 상자(Visual Database Tools)
  이 대화 상자는 데이터베이스 다이어그램이나 선택된 테이블을 저장하려 하지만 저장 동작이 적용되는 일부 데이터베이스 개체가 최신 상태가 아닌 경우에 나타납니다. 이 대화 상자에 표시되는 변경 내용을 적용하면 데이터베이스가 다이어그램과 일치하도록 업데이트되고 다른 사용자의 변경 내용을 덮어쓰게 됩니다.  
  
> [!NOTE]  
>  테이블이나 데이터베이스 다이어그램에 적용된 변경 내용을 실행 취소할 수는 없지만 테이블이나 다이어그램을 저장하기 전까지는 변경 내용이 데이터베이스에 저장되지 않습니다. **아니요** 를 선택하고 모든 열려 있는 다이어그램을 저장하지 않은 채 닫으면 저장되지 않은 변경 내용을 모두 취소할 수 있습니다.  
  
## <a name="options"></a>옵션  
 **차이점 발견 경고**  
 이후에 데이터베이스 다이어그램이나 선택된 테이블을 저장하려 할 때 이 대화 상자를 표시할지 여부를 지정합니다. 이 옵션을 선택하면 오래된 다이어그램이나 테이블을 데이터베이스와 함께 저장하려 할 때마다 이 대화 상자가 계속하여 나타납니다. 이 옵션을 해제하면 대화 상자가 나타나지 않습니다. 이 확인란은 기본적으로 선택되어 있습니다. 이 옵션이 해제되어 있는 경우 **옵션** 대화 상자에서 다시 선택할 수 있습니다.  
  
 **예**  
 목록에 표시된 모든 변경 내용으로 데이터베이스를 업데이트합니다.  
  
 **아니요**  
 저장 동작을 취소합니다.  
  
> [!NOTE]  
>  데이터베이스에 일치하도록 다이어그램을 새로 고치려면 변경 내용을 저장하지 않은 상태로 다이어그램을 닫고 서버 탐색기에서 다이어그램을 마우스 오른쪽 단추로 클릭한 다음 새로 고침을 클릭하고 다이어그램을 다시 엽니다.  
  
 **텍스트 파일 저장**  
 **다른 이름으로 저장** 대화 상자가 나타납니다. 이 대화 상자를 사용하면 데이터베이스 변경 내용 목록이 포함된 텍스트 파일의 위치를 지정할 수 있습니다.  
  
## <a name="see-also"></a>참고 항목  
 [Visual Database Tools를 사용 하 &#40;수정 된 데이터베이스를 사용 하 여 데이터베이스 다이어그램 조정&#41;](visual-database-tools.md)   
 [다중 사용자 환경&#40;Visual Database Tools&#41;](multiuser-environments-visual-database-tools.md)  
  
  
