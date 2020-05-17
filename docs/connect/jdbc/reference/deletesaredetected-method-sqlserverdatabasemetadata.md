---
title: deletesAreDetected 메서드(SQLServerDatabaseMetaData) | Microsoft Docs
ms.custom: ''
ms.date: 01/20/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.deletesAreDetected
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 73f3d994-bbd7-43d2-8b64-50057e278983
author: MightyPen
ms.author: genemi
ms.openlocfilehash: aef2ebd78b1aed2d03ba56ef3371d7f0dbfade31
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/29/2020
ms.locfileid: "67955128"
---
# <a name="deletesaredetected-method-sqlserverdatabasemetadata"></a>deletesAreDetected 메서드(SQLServerDatabaseMetaData)

[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  [SQLServerResultSet](../../../connect/jdbc/reference/rowdeleted-method-sqlserverresultset.md) 클래스의 [rowDeleted](../../../connect/jdbc/reference/sqlserverresultset-class.md) 메서드를 호출하여 표시된 행 삭제를 검색할 수 있는지 여부를 검색합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
public boolean deletesAreDetected(int type)  
```  
  
#### <a name="parameters"></a>매개 변수  
 *type*  
  
 결과 집합 유형을 나타내는 **int**이며, java.sql.ResultSet 또는 SQLServerResultSet에 정의된 다음 값 중 하나일 수 있습니다.  
  
## <a name="javasqlresultset-types"></a>java.sql.ResultSet 형식  
 TYPE_FORWARD_ONLY  
  
 TYPE_SCROLL_SENSITIVE  
  
 TYPE_SCROLL_INSENSITIVE  
  
## <a name="sqlserverresultset-types"></a>SQLServerResultSet 형식  
 TYPE_SS_SCROLL_STATIC  
  
 TYPE_SS_SCROLL_KEYSET  
  
 TYPE_SS_DIRECT_FORWARD_ONLY  
  
 TYPE_SS_SERVER_CURSOR_FORWARD_ONLY  
  
 TYPE_SS_SCROLL_DYNAMIC  
  
## <a name="return-value"></a>Return Value  
 간격이 삭제된 행을 대체하면 **true**입니다. 삭제된 행이 제거되면 **false**입니다.  
  
 [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] 데이터베이스와 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]를 함께 사용할 경우 이 메서드는 TYPE_SS_SCROLL_KEYSET 커서에 대해 **true**를 반환하고 다른 모든 결과 집합 유형에 대해서는 **false**를 반환합니다.  
  
## <a name="exceptions"></a>예외  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>설명  
 이 deletesAreDetected 메서드는 java.sql.DatabaseMetaData 인터페이스의 deletesAreDetected 메서드에 의해 지정됩니다.  
  
> [!NOTE]  
>  검색이 정방향 및 동적 커서에 대해 일시적이기는 하지만 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]에서는 업데이트 가능한 모든 커서 유형에 대해 삭제된 행을 검색합니다.  
  
## <a name="see-also"></a>참고 항목  
 [SQLServerDatabaseMetaData 메서드](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData 멤버](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData 클래스](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
