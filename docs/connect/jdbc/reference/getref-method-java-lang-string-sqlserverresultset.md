---
title: getRef 메서드(java.lang.String) (SQLServerResultSet) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.getRef (java.lang.String)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 83c60c5d-7a69-498b-be9c-bbdbfafec157
author: MightyPen
ms.author: genemi
ms.openlocfilehash: fbb9a65610730ba23e157aabf81c04c1f4af8eec
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67980578"
---
# <a name="getref-method-javalangstring-sqlserverresultset"></a>getRef 메서드(java.lang.String)(SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  이 [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) 개체의 현재 행에서 지정된 열 이름의 값을 Java 프로그래밍 언어의 Ref 개체로 검색합니다.  
  
## <a name="syntax"></a>구문  
  
```  
  
public java.sql.Ref getRef(java.lang.String colName)  
```  
  
#### <a name="parameters"></a>매개 변수  
 *colName*  
  
 열 이름이 포함된 **문자열**입니다.  
  
## <a name="return-value"></a>반환 값  
 Ref 개체입니다.  
  
## <a name="exceptions"></a>예외  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 이 getRef 메서드는 java.sql.ResultSet 인터페이스의 getRef 메서드에 의해 지정됩니다.  
  
## <a name="see-also"></a>참고 항목  
 [getRef 메서드 &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/getref-method-sqlserverresultset.md)   
 [SQLServerResultSet 멤버](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet 클래스](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
