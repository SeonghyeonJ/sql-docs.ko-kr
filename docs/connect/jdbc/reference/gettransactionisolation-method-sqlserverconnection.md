---
title: getTransactionIsolation 메서드(SQLServerConnection) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerConnection.getTransactionIsolation
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 179772e9-6572-4ce5-83c5-ab2b196cee67
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 078cf2cefbf57e07d50329767b2a3bc1f55b8aab
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66786255"
---
# <a name="gettransactionisolation-method-sqlserverconnection"></a>getTransactionIsolation 메서드(SQLServerConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  이 [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) 개체의 현재 트랜잭션 격리 수준을 검색합니다.  
  
## <a name="syntax"></a>구문  
  
```  
  
public int getTransactionIsolation()  
```  
  
## <a name="return-value"></a>반환 값  
 다음 격리 수준 중 하나가 포함된 **int** 값입니다.  
  
 TRANSACTION_NONE  
  
 TRANSACTION_READ_UNCOMMITTED  
  
 TRANSACTION_READ_COMMITTED  
  
 TRANSACTION_REPEATABLE_READ  
  
 TRANSACTION_SERIALIZABLE  
  
 TRANSACTION_SNAPSHOT = 0x1000  
  
## <a name="exceptions"></a>예외  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 이 getTransactionIsolation 메서드는 java.sql.Connection 인터페이스의 getTransactionIsolation 메서드에 의해 지정됩니다.  
  
## <a name="see-also"></a>참고 항목  
 [SQLServerConnection 멤버](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [SQLServerConnection 클래스](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
