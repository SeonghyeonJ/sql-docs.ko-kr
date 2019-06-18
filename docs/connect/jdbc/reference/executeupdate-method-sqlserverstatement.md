---
title: executeUpdate 메서드(SQLServerStatement) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerStatement.executeUpdate
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 10ae662a-ce3c-4b24-875c-5c2df319d93b
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 9052e28e66e6767a64b392978c6c52a42c24eaec
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66804128"
---
# <a name="executeupdate-method-sqlserverstatement"></a>executeUpdate 메서드(SQLServerStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  INSERT, UPDATE 또는 DELETE 문과 같은 지정된 SQL 문이나 SQL DDL 문 같이 아무 것도 반환하지 않는 SQL 문을 실행합니다. [!INCLUDE[msCoName](../../../includes/msconame_md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] JDBC 드라이버 3.0부터 executeUpdate는 MERGE 작업에서 업데이트되는 정확한 행 수를 반환합니다.  
  
## <a name="overload-list"></a>오버로드 목록  
  
|속성|설명|  
|----------|-----------------|  
|[executeUpdate(java.lang.String)](../../../connect/jdbc/reference/executeupdate-method-java-lang-string-sqlserverstatement.md)|INSERT, UPDATE, DELETE 또는 MERGE 문과 같은 지정된 SQL 문이나 SQL DDL 문 같이 아무 것도 반환하지 않는 SQL 문을 실행합니다.|  
|[executeUpdate(java.lang.String, int)](../../../connect/jdbc/reference/executeupdate-method-java-lang-string-int.md)|지정된 SQL 문을 실행하고 이 [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) 개체에서 생성된 자동 생성 키를 검색에 사용할 수 있도록 해야 하는지 여부를 지정된 플래그로 [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)]에 알립니다.|  
|[executeUpdate(java.lang.String, int&#91;&#93;)](../../../connect/jdbc/reference/executeupdate-method-java-lang-string.md)|지정된 SQL 문을 실행하고, 지정된 배열에 표시된 자동 생성 키를 검색에 사용할 수 있도록 해야 할지 여부를 JDBC 드라이버에 알립니다.|  
|[executeUpdate(java.lang.String, java.lang.String&#91;&#93;)](../../../connect/jdbc/reference/executeupdate-method-java-lang-string-java-lang-string.md)|지정된 SQL 문을 실행하고, 지정된 배열에 표시된 자동 생성 키를 검색에 사용할 수 있도록 해야 할지 여부를 JDBC 드라이버에 알립니다.|  
  
## <a name="see-also"></a>참고 항목  
 [SQLServerStatement 멤버](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [SQLServerStatement 클래스](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
