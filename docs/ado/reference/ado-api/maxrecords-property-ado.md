---
description: MaxRecords 속성(ADO)
title: MaxRecords 속성 (ADO) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset15::MaxRecords
helpviewer_keywords:
- MaxRecords property [ADO]
ms.assetid: 20c76571-8c9a-482c-a99e-726ab1d93f8b
author: rothja
ms.author: jroth
ms.openlocfilehash: 4431d9a8af8623150717474cd5429a772f86be8c
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/24/2020
ms.locfileid: "88774452"
---
# <a name="maxrecords-property-ado"></a>MaxRecords 속성(ADO)
쿼리에서 [레코드 집합](./recordset-object-ado.md) 으로 반환할 최대 레코드 수를 나타냅니다.  
  
## <a name="settings-and-return-values"></a>설정 및 반환 값  
 반환할 최대 레코드 수를 나타내는 **Long** 값을 설정 하거나 반환 합니다. 기본값은 영 (**0**)으로, 제한이 없음을 의미 합니다.  
  
## <a name="remarks"></a>설명  
 **MaxRecords** 속성을 사용 하 여 공급자가 데이터 원본에서 반환 하는 레코드 수를 제한할 수 있습니다. 이 속성의 기본 설정은 0 이며,이는 공급자가 요청 된 모든 레코드를 반환 함을 의미 합니다.  
  
 **MaxRecords** 속성은 **레코드 집합이** 닫혀 있을 때 읽기/쓰기이 고, 열려 있으면 읽기 전용입니다.  
  
## <a name="applies-to"></a>적용 대상  
 [레코드 집합 개체(ADO)](./recordset-object-ado.md)  
  
## <a name="see-also"></a>참고 항목  
 [MaxRecords 속성 예제 (VB)](./maxrecords-property-example-vb.md)   
 [MaxRecords 속성 예제(VC++)](./maxrecords-property-example-vc.md)