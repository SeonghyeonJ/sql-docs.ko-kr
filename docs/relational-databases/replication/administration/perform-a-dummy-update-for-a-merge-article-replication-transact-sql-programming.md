---
title: 병합 아티클에 대해 더미 업데이트 수행(복제 T-SQL 프로그래밍) | Microsoft 문서
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- sp_mergedummyupdate
- dummy updates [SQL Server replication]
ms.assetid: 2f339210-4d85-4843-bd94-e86f7100d3ef
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 38076ebad44e59d6004ac852486788a4b22c32f3
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67939086"
---
# <a name="perform-a-dummy-update-for-a-merge-article-replication-transact-sql-programming"></a>병합 아티클에 대해 더미 업데이트 수행(복제 Transact-SQL 프로그래밍)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  병합 복제에서는 복제 프로세스의 일부로 트리거가 사용됩니다. 게시된 테이블이 업데이트될 경우 업데이트 트리거가 발생합니다. WRITETEXT 및 UPDATETEXT 작업을 수행할 때와 같은 일부 경우에는 트리거를 발생시키지 않고 데이터를 업데이트할 수 있습니다. 이러한 경우 변경 내용을 명시적으로 복제하려면 더미 UPDATE 문을 추가해야 합니다. 복제 저장 프로시저를 사용하여 더미 UPDATE 문을 추가할 수 있습니다.  
  
### <a name="to-add-a-dummy-update-statement"></a>더미 UPDATE 문을 추가하려면  
  
1.  더미 업데이트가 필요한 병합 게시된 테이블의 행에 대해 UPDATETEXT와 같은 작업을 실행합니다.  
  
2.  변경된 데이터베이스의 서버(게시자 또는 구독자)에서 [sp_mergedummyupdate&#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-mergedummyupdate-transact-sql.md)를 실행합니다. **@source_object** 에 변경된 테이블을 지정하고 **@rowguid** 에 변경된 행의 고유 식별자를 지정합니다.  
  
3.  구독을 동기화하여 변경된 행을 복제합니다.  
  
  
