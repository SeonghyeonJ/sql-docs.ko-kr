---
description: SkipLine 메서드
title: SkipLine 메서드 | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Stream::raw_SkipLine
- _Stream::SkipLine
helpviewer_keywords:
- Skipline method [ADO]
ms.assetid: 0abc00fe-ee09-4c8e-b1f2-48ee9c5f3329
author: rothja
ms.author: jroth
ms.openlocfilehash: 840c0111aca8b202fd081d3f0250d17fd43e5bbb
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/27/2020
ms.locfileid: "88989054"
---
# <a name="skipline-method"></a>SkipLine 메서드
텍스트 [스트림을](./stream-object-ado.md)읽을 때 한 줄 전체를 건너뜁니다.  
  
## <a name="syntax"></a>구문  
  
```  
  
Stream.SkipLine  
```  
  
## <a name="remarks"></a>설명  
 다음 줄 구분 기호를 포함 하 여 모든 문자를 건너뜁니다. 기본적으로 [LineSeparator](./lineseparator-property-ado.md) 는 **adcrlf**입니다. [Eos](./eos-property.md)를 지나서 건너뛰려면 현재 위치가 **eos**에 유지 됩니다.  
  
 **SkipLine** 메서드는 텍스트 스트림과 함께 사용 됩니다 ([Type](./type-property-ado-stream.md) is **adTypeText**).  
  
## <a name="applies-to"></a>적용 대상  
 [스트림 개체(ADO)](./stream-object-ado.md)