---
title: isSameRM 메서드 (SQLServerXAResource) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerXAResource.isSameRM
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: bfa24c46-b7cf-470a-afa1-52301847a448
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 6cdfd42d0670d8d536e0a9bf40f2a6981ef5b937
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66796363"
---
# <a name="issamerm-method-sqlserverxaresource"></a>isSameRM 메서드(SQLServerXAResource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  대상 개체가 나타내는 리소스 관리자 인스턴스가 지정된 XAResource 개체가 나타내는 리소스 관리자 인스턴스와 동일한지 확인합니다.  
  
## <a name="syntax"></a>구문  
  
```  
  
public boolean isSameRM(javax.transaction.xa.XAResource xares)  
```  
  
#### <a name="parameters"></a>매개 변수  
 *xares*  
  
 XAResource 개체입니다.  
  
## <a name="return-value"></a>반환 값  
 인스턴스가 동일하면 **true**이고, 그렇지 않으면 **false**입니다.  
  
## <a name="exceptions"></a>예외  
 javax.transaction.xa.XAException  
  
## <a name="remarks"></a>Remarks  
 이 commit 메서드는 javax.transaction.xa.XAResource 인터페이스의 commit 메서드에 의해 지정됩니다.  
  
## <a name="see-also"></a>참고 항목  
 [SQLServerXAResource 메서드](../../../connect/jdbc/reference/sqlserverxaresource-methods.md)   
 [SQLServerXAResource 멤버](../../../connect/jdbc/reference/sqlserverxaresource-members.md)   
 [SQLServerXAResource 클래스](../../../connect/jdbc/reference/sqlserverxaresource-class.md)  
  
  
