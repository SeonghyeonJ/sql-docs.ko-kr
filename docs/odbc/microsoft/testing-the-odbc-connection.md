---
description: ODBC 연결 테스트
title: ODBC 연결 테스트 | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- testing connections [ODBC]
- ODBC driver for Oracle [ODBC], testing connections
ms.assetid: 5e671665-2aba-49a7-8871-70784d8b3cc9
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 61a471af3c5681ca58ca3268ad4512ee80abb9cb
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88421547"
---
# <a name="testing-the-odbc-connection"></a>ODBC 연결 테스트
> [!IMPORTANT]  
>  이 기능은 이후 버전의 Windows에서 제거 될 예정입니다. 새 개발 작업에서는 이 기능을 사용하지 않도록 하고, 현재 이 기능을 사용하는 애플리케이션은 수정하세요. 대신 Oracle에서 제공 하는 ODBC 드라이버를 사용 합니다.  
  
 Oracle 4.x 및 Oracle8 RDBMS 서버에 대 한 ODBC 액세스 문제를 해결할 때 기본 SQL * Net 및 Oracle 프로토콜 어댑터가 올바르게 설치 되었는지 확인 해야 할 수 있습니다. 이렇게 하려면 Orawin\Bin 디렉터리에 Nettest.exe Oracle 제공 유틸리티를 사용 합니다.  
  
 Nettest는 Oracle 클라이언트의 일부인 설치 된 SQL * Net 소프트웨어만 사용 하 여 선택한 서버에 로그온을 시도 하는 간단한 유틸리티입니다. 이 유틸리티는 로그인 이름, 암호 및 TNS 연결 문자열을 요청 합니다. Oracle 클라이언트가 올바르게 설치 된 경우 유틸리티는 단순히 "Ping 성공"을 표시 합니다. 로그인이 실패 한 경우에는 데이터베이스 관리자에 게 문의 해야 합니다.
