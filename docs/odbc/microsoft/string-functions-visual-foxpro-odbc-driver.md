---
description: 문자열 함수(Visual FoxPro ODBC 드라이버)
title: 문자열 함수 (Visual FoxPro ODBC 드라이버) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC string functions [ODBC]
- string functions [ODBC]
- Visual FoxPro ODBC driver [ODBC], string functions
- FoxPro ODBC driver [ODBC], string functions
ms.assetid: 1974fd26-ef0d-45d5-860b-298917c8e9c3
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 4ab2ecefb604183b0387a561f72494028c62d15f
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88471545"
---
# <a name="string-functions-visual-foxpro-odbc-driver"></a>문자열 함수(Visual FoxPro ODBC 드라이버)
다음 표에서는 Visual FoxPro ODBC 드라이버에서 지 원하는 ODBC 문자열 조작 함수를 보여 줍니다. 동일한 함수에 대 한 Visual FoxPro 문법이 ODBC 구문과 다를 경우 Visual FoxPro와 동일한 항목이 나열 됩니다.  
  
|ODBC 문법|Visual FoxPro 문법|  
|------------------|---------------------------|  
|ASCII *(string_exp)*|ASC *(string_exp)*|  
|CHAR *(코드)*|CHR *(string_exp)*|  
|CONCAT *(string_exp1, string_exp2)*|*string_exp1 + string_exp2*|  
|차이 *(string_exp1, string_exp2)*||  
|삽입 *(string_exp1, 시작, 길이, string_exp2)*|사물 *(string_exp1, 시작, 길이, string_exp2)*|  
|LCASE *(string_exp)*|LOWER *(string_exp)*|  
|LEFT *(string_exp, count)*||  
|길이 *(string_exp)*|LEN *(string_exp)*|  
|LTRIM *(string_exp)*||  
|반복 *(string_exp, 개수)*|복제 *(string_exp, 개수)*|  
|REPLACE *(string_exp1, string_exp2, string_exp3)*|STRTRAN *(string_exp1, string_exp2, string_exp3)*|  
|RIGHT *(string_exp, count)*||  
|RTRIM *(string_exp)*||  
|SOUNDEX *(string_exp)*||  
|공간 *(개수)*||  
|부분 문자열 *(string_exp, 시작, 길이)*|SUBSTR *(string_exp, 시작, 길이)*|  
|UCASE *(string_exp)*|UPPER *(string_exp)*|
