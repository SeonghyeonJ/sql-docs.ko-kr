---
description: getNClob 메서드(int)
title: getNClob 메서드(int) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 10dfa251-9408-469e-ae2a-1acf3917cf47
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 154d86c586449c3b5db57c02ca0e5d8d95f07392
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88435295"
---
# <a name="getnclob-method-int"></a>getNClob 메서드(int)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  지정된 JDBC **NCLOB** 매개 변수의 값을 Java 프로그래밍 언어의 NClob 개체로 검색합니다.  
  
## <a name="syntax"></a>구문  
  
```  
  
public java.sql.NClob getNClob(int parameterIndex)  
```  
  
#### <a name="parameters"></a>매개 변수  
 *parameterIndex*  
  
 매개 변수 인덱스를 나타내는 **int**입니다.  
  
## <a name="return-value"></a>반환 값  
 NClob 개체입니다.  
  
## <a name="exceptions"></a>예외  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>설명  
 이 getNClob 메서드는 java.sql.CallableStatement 인터페이스의 getNClob 메서드에 의해 지정됩니다.  
  
 이 메서드는 **NCHAR**, **NVARCHAR**, **NTEXT** 및 **XML** 매개 변수 검색만 지원합니다. 다른 데이터 형식 매개 변수에서 이러한 메서드를 호출하면 예외가 발생합니다.  
  
## <a name="see-also"></a>참고 항목  
 [getNClob 메서드 &#40;SQLServerCallableStatement&#41;](../../../connect/jdbc/reference/getnclob-method-sqlservercallablestatement.md)   
 [SQLServerCallableStatement 멤버](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)  
  
  
