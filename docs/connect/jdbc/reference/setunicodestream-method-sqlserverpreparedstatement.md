---
description: setUnicodeStream 메서드(SQLServerPreparedStatement)
title: setUnicodeStream 메서드(SQLServerPreparedStatement) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerPreparedStatement.setUnicodeStream
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 0a413e83-e0a4-41f8-9fe0-33ce4d368ee4
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: abcc41af7eedf01670aaaf439619e3fb199461c0
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88467156"
---
# <a name="setunicodestream-method-sqlserverpreparedstatement"></a>setUnicodeStream 메서드(SQLServerPreparedStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  지정된 매개 변수 번호를 지정된 바이트 수를 포함하는 지정된 입력 스트림으로 설정합니다.  
  
> [!NOTE]  
>  이 메서드는 JDBC 사양에서 더 이상 사용되지 않으며 이 메서드를 호출하면 "구현되지 않음" 예외가 발생합니다.  
  
## <a name="syntax"></a>구문  
  
```  
  
public final void setUnicodeStream(int n,  
                                   java.io.InputStream x,  
                                   int length)  
```  
  
#### <a name="parameters"></a>매개 변수  
 *n*  
  
 매개 변수 번호를 나타내는 **int**입니다.  
  
 *x*  
  
 InputStream 개체입니다.  
  
 *length*  
  
 바이트 수입니다.  
  
## <a name="exceptions"></a>예외  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>설명  
 이 setUnicodeStream 메서드는 java.sql.PreparedStatement 인터페이스의 setUnicodeStream 메서드에 의해 지정됩니다.  
  
## <a name="see-also"></a>참고 항목  
 [SQLServerPreparedStatement 멤버](../../../connect/jdbc/reference/sqlserverpreparedstatement-members.md)   
 [SQLServerPreparedStatement 클래스](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md)  
  
  
