---
title: Visual FoxPro 필드 데이터 형식 | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- field data types [ODBC]
- Visual FoxPro ODBC driver [ODBC], data types
ms.assetid: 50b733dc-679a-4b10-bc5d-98bb474dead2
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 217058bf328677bf375d346ae7201c6eb81efa4e
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68087950"
---
# <a name="visual-foxpro-field-data-types"></a>Visual FoxPro 필드 데이터 형식
다음 표에서 대 한 값을 *FieldType* ALTER TABLE 및 CREATE TABLE에서 인수를 나타내고 있는지 여부를 *nFieldWidth* 및 *nPrecision* 인수는 필수.  
  
|*FieldType*|*NFieldWidth*|*nPrecision*|설명|  
|-----------------|-------------------|------------------|-----------------|  
|B|-|d|Double|  
|C|N|-|너비의 문자 필드 *n*|  
|D|-|-|Date|  
|F|N|d|숫자 필드 너비의 부동 *n* 사용 하 여 *d* 소수 자릿수|  
|G|-|-|일반|  
|I|-|-|정수|  
|L|-|-|논리|  
|M|-|-|Memo|  
|N|N|d|숫자 필드 너비 *n* 사용 하 여 *d* 소수 자릿수|  
|T|-|-|Datetime|  
|Y|-|-|Currency|
