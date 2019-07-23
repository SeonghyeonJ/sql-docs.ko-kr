---
title: MSSQLSERVER_2570 | Microsoft 문서
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 2570 (Database Engine error)
ms.assetid: 29800aa9-81aa-4371-992c-487dbb617f46
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 63adadd3dda40dc520e2152eab1a461dfe69958a
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68023031"
---
# <a name="mssqlserver2570"></a>MSSQLSERVER_2570
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>세부 정보  
  
|||  
|-|-|  
|제품 이름|SQL Server|  
|이벤트 ID|2570|  
|이벤트 원본|MSSQLSERVER|  
|구성 요소|SQLEngine|  
|심볼 이름|DBCC_COLUMN_VALUE_OUT_OF_RANGE|  
|메시지 텍스트|개체 ID O_ID, 인덱스 ID I_ID, 파티션 ID PN_ID, 할당 단위 ID A_ID(TYPE 유형)의 페이지 P_ID, 슬롯 S_ID. 열 COLUMN_NAME 값이 데이터 형식 "DATATYPE"의 범위를 벗어났습니다. 열을 유효한 값으로 업데이트하십시오.|  
  
## <a name="explanation"></a>설명  
지정한 열에 포함된 열 값이 열 데이터 형식에 대해 가능한 값의 범위를 벗어났습니다.  
  
## <a name="user-action"></a>사용자 동작  
복구할 수 없는 오류입니다. 열을 해당 열 데이터 형식 범위 내의 값으로 업데이트하고 명령을 다시 실행하십시오.  자세한 내용은 기술 자료 문서 [923247](https://support.microsoft.com/kb/923247)을 참조하세요.  
  
## <a name="see-also"></a>참고 항목  
[UPDATE&#40;Transact-SQL&#41;](~/t-sql/queries/update-transact-sql.md)  
[데이터 형식&#40;Transact-SQL&#41;](~/t-sql/data-types/data-types-transact-sql.md)  
  
