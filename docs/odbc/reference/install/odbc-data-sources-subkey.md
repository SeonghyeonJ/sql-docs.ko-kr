---
title: ODBC 데이터 원본 하위 키 | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- subkeys [ODBC], for data sources
- data sources [ODBC], subkeys
- registry entries for data sources [ODBC], subkeys
ms.assetid: 0a8ccb80-c573-4418-84e5-f04a2b0e2ac1
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 2a1d0c506c4a4b33d7138378032947821d4e9f3e
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68093989"
---
# <a name="odbc-data-sources-subkey"></a>ODBC 데이터 원본 하위 키
ODBC 데이터 원본 하위 키 아래의 값에 데이터 원본을 나열합니다. 이러한 값의 형식은 다음 표와에서 같이 합니다.  
  
|이름|데이터 형식|data|  
|----------|---------------|----------|  
|*data-source-name*|REG_SZ|*driver-description*|  
  
 *데이터 원본 이름* 값 (일반적으로 묻는 메시지에 대 한)는 관리 프로그램에 의해 정의 됩니다 및 *드라이버 설명* 드라이버 개발자가 정의한 (의 이름입니다 일반적으로 DBMS 드라이버를 사용 하 여 연결 된)입니다.  
  
 예를 들어 3 개의 데이터 원본 정의 되었습니다. SQL Server에는 인벤토리 DBASE;를 사용 하는 급여 및 담당자를 사용 하는 형식이 지정 된 텍스트 파일입니다. ODBC 데이터 원본 하위 키 아래의 값은 다음과 같을 수 있습니다.  
  
```  
Inventory : REG_SZ : SQL Server  
Payroll : REG_SZ : dBASE  
Personnel : REG_SZ : Text  
```
