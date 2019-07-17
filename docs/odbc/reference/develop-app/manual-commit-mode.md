---
title: 수동 커밋 모드 | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- rolling back transactions [ODBC]
- manual-commit mode [ODBC]
- transactions [ODBC], commit modes
- committing transactions [ODBC]
- commit modes [ODBC]
- transactions [ODBC], rolling back
ms.assetid: 9c4b3931-e48b-4960-89a2-5697537e9f51
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 7189a0586ba4f62091d5eb209a56931627bc6f7f
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68036404"
---
# <a name="manual-commit-mode"></a>수동 커밋 모드
*수동 커밋 모드로* 응용 프로그램에 명시적으로 호출 하 여 트랜잭션을 완료 해야 합니다 **SQLEndTran** 커밋하거나 롤백할 합니다. 대부분의 관계형 데이터베이스에 대 한 기본 트랜잭션 모드입니다.  
  
 ODBC의 트랜잭션을 명시적으로 시작할 수 없습니다. 대신 트랜잭션 데이터베이스에서 응용 프로그램이 시작 될 때마다 암시적으로 시작 합니다. 데이터 원본에서 명시적 트랜잭션을 시작에 필요한 경우 드라이버를 제공 해야 응용 프로그램 트랜잭션이 필요한 문을 실행할 때마다 현재 트랜잭션이 없습니다.
