---
title: SQLDriverConnect를 사용 하 여 연결 | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data sources [ODBC], connection functions
- functions [ODBC], data source or driver connections
- connecting to data source [ODBC], SQLDriverConnect
- connecting to driver [ODBC], SQLDriverConnect
- connecting to data source [ODBC], functions
- connecting to driver [ODBC], functions
- SQLDriverConnect function [ODBC], connecting
- connection functions [ODBC]
- ODBC drivers [ODBC], connection functions
ms.assetid: e46e959f-d3c5-4ddb-810a-107bfcb83fd2
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 6cd95364d8a5316a50d9f55616236a8677bf99e4
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81299073"
---
# <a name="connecting-with-sqldriverconnect"></a>SQLDriverConnect로 연결
**SQLDriverConnect** 는 연결 문자열을 사용 하 여 데이터 원본에 연결 하는 데 사용 됩니다. **SQLDriverConnect** 는 다음과 같은 이유로 **SQLConnect** 대신 사용 됩니다.  
  
-   응용 프로그램에서 드라이버별 연결 정보를 사용할 수 있도록 합니다.  
  
-   드라이버가 연결 정보를 묻는 메시지를 사용자에게 표시하도록 하려는 경우  
  
-   데이터 원본을 지정 하지 않고 연결 하려면입니다.  
  
 이 섹션에서는 다음 항목을 다룹니다.  
  
-   [드라이버별 연결 정보](../../../odbc/reference/develop-app/driver-specific-connection-information.md)  
  
-   [사용자에게 연결 정보 요청](../../../odbc/reference/develop-app/prompting-the-user-for-connection-information.md)  
  
-   [파일 데이터 원본을 사용하여 연결](../../../odbc/reference/develop-app/connecting-using-file-data-sources.md)  
  
-   [드라이버에 직접 연결](../../../odbc/reference/develop-app/connecting-directly-to-drivers.md)
