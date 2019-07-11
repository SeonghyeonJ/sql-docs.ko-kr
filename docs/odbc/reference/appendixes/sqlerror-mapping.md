---
title: SQLError 매핑 | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- mapping deprecated functions [ODBC], SQLError
- SQLError function [ODBC], mapping
ms.assetid: 802ac711-7e5d-4152-9698-db0cafcf6047
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 452ee7b5e2c9e38aaf0fb81969228f5c5e7b5559
ms.sourcegitcommit: 56b963446965f3a4bb0fa1446f49578dbff382e0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67793069"
---
# <a name="sqlerror-mapping"></a>SQLError 매핑
응용 프로그램을 호출할 때 **SQLError** 는 ODBC를 통한 *3.x* 드라이버에 대 한 호출  
  
```  
SQLError(henv, hdbc, hstmt, szSqlState, pfNativeError, szErrorMsg, cbErrorMsgMax, pcbErrorMsg)   
```  
  
 매핑되는  
  
```  
SQLGetDiagRec(HandleType, Handle, RecNumber, szSqlstate, pfNativeErrorPtr, szErrorMsg, cbErrorMsgMax, pcbErrorMsg)  
```  
  
 사용 하 여는 *HandleType* 인수를 적절 하 게 SQL_HANDLE_ENV, SQL_HANDLE_DBC를 호출 하 여, 값으로 설정 하며 *처리* 인수 값으로 설정 *henv*하십시오 *hdbc*, 또는 *hstmt*를 적절 하 게 합니다. 합니다 *RecNumber* 인수 드라이버 관리자에 의해 결정 됩니다.
