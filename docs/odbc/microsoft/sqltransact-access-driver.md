---
title: SQLTransact (Access 드라이버) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Access driver [ODBC], SQLTransact
- SQLTransact function [ODBC], Access Driver
ms.assetid: 892b79c7-9e20-4d1f-bc60-d4b25694ca25
author: MightyPen
ms.author: genemi
ms.openlocfilehash: f4d4b3d8d417591bd72dde22240c81a91d80f990
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67948978"
---
# <a name="sqltransact-access-driver"></a>SQLTransact(Access 드라이버)
> [!NOTE]  
>  이 항목에서는 액세스 드라이버 관련 정보를 제공 합니다. 이 함수에 대 한 일반 정보에서 해당 항목을 참조 하세요 [ODBC API 참조](../../odbc/reference/syntax/odbc-api-reference.md)합니다.  
  
 Microsoft Access 드라이버를 사용 하는 경우 SQL_COMMIT 및 SQL_ROLLBACK는 지원 합니다 *fType* 호출에서 인수 **SQLTransact**.  
  
 커밋 프로세스 중에 오류가 발생할 경우의 영향을 받는 데이터베이스를 복구할 수 또는 REPAIR_DB 키워드를 사용 하 여 Microsoft Access 드라이버 설치에서 데이터베이스 복구 옵션을 사용 하 여 **SQLConfigDataSource** 함수입니다.
