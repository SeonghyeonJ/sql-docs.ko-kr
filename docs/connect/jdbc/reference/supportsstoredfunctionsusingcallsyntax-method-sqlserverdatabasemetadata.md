---
title: supportsStoredFunctionsUsingCallSyntax 메서드 | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 0e5c0579-84b5-4717-b128-0bcd512f6022
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 053dab7055969b502a79e2e2d0250cdd98749fbe
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 06/07/2019
ms.locfileid: "66797299"
---
# <a name="supportsstoredfunctionsusingcallsyntax-method-sqlserverdatabasemetadata"></a>supportsStoredFunctionsUsingCallSyntax 메서드(SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  현재 데이터베이스에서 저장 프로시저 이스케이프 구문을 사용하여 사용자 정의 또는 공급업체 정의 함수를 호출할 수 있는지 여부를 나타냅니다.  
  
## <a name="syntax"></a>구문  
  
```  
  
public boolean supportsStoredFunctionsUsingCallSyntax()  
```  
  
## <a name="return-value"></a>반환 값  
 **true** 지원 되는 경우. 그렇지 않으면 **false**입니다.  
  
## <a name="exceptions"></a>예외  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 이 supportsStoredFunctionsUsingCallSyntax 메서드는 java.sql.DatabaseMetaData 인터페이스의 supportsStoredFunctionsUsingCallSyntax 메서드에 의해 지정 됩니다.  
  
## <a name="see-also"></a>참고 항목  
 [SQLServerDatabaseMetaData 메서드](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData 멤버](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData 클래스](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
