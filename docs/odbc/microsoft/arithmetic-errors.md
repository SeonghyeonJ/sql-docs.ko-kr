---
title: 산술 오류 | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- arithmetic errors [ODBC]
- desktop database drivers [ODBC], arithmetic errors
ms.assetid: 1c47bfac-7455-4487-b673-6b47d2a2d756
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 2e0880e1746b4b65070fb28bf8d83aadec301aa4
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68138175"
---
# <a name="arithmetic-errors"></a>산술 오류
ODBC 드라이버는 각 행을 인출 하는 대로 SELECT 문에서 WHERE 절을 평가 합니다. 행 오버플로, 0으로 나누기 또는 숫자와 같은 산술 오류가 발생 하는 값을 포함 하는 경우 드라이버는 모든 행을 반환 했지만 산술 오류를 사용 하 여 열에 대 한 오류를 반환 합니다. 그러나 삽입 또는 업데이트 ODBC 드라이버를 중지 삽입 하거나 첫 번째 산술 오류가 발생 하는 경우 데이터를 업데이트 합니다.
