---
description: getAsciiStream 메서드(java.lang.String)
title: getAsciiStream 메서드(java.lang.String) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.getAsciiStream (java.lang.String)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: b2d24a6b-f029-4691-981b-125c690b8ba5
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 3bea88a4c4ebab5845358b827a077a6915311cda
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88437415"
---
# <a name="getasciistream-method-javalangstring"></a>getAsciiStream 메서드(java.lang.String)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  이 [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) 개체의 현재 행에서 지정된 열 이름의 값을 ASCII 문자의 스트림으로 검색합니다.  
  
## <a name="syntax"></a>구문  
  
```  
  
public java.io.InputStream getAsciiStream(java.lang.String columnName)  
```  
  
#### <a name="parameters"></a>매개 변수  
 *columnName*  
  
 열 이름이 포함된 **문자열**입니다.  
  
## <a name="return-value"></a>반환 값  
 InputStream 개체입니다.  
  
## <a name="exceptions"></a>예외  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>설명  
 이 getAsciiStream 메서드는 java.sql.ResultSet 인터페이스의 getAsciiStream 메서드에 의해 지정됩니다.  
  
## <a name="see-also"></a>참고 항목  
 [getAsciiStream 메서드&#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/getasciistream-method-sqlserverresultset.md)   
 [SQLServerResultSet 멤버](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet 클래스](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
