---
description: setCharacterStream 메서드(SQLServerClob)
title: setCharacterStream 메서드(SQLServerClob) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerClob.setCharacterStream
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: c02778f2-6681-4a84-a58b-2bcfac4233e4
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: f79891e2a2492a225896495651f8f0746353e6a5
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88432235"
---
# <a name="setcharacterstream-method-sqlserverclob"></a>setCharacterStream 메서드(SQLServerClob)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  CLOB의 지정된 위치부터 유니코드 문자 스트림을 쓰는 데 사용할 스트림을 반환합니다.  
  
## <a name="syntax"></a>구문  
  
```  
  
public java.io.Writer setCharacterStream(long pos)  
```  
  
#### <a name="parameters"></a>매개 변수  
 *pos*  
  
 CLOB 개체에 쓰기 시작할 위치입니다.  
  
## <a name="return-value"></a>반환 값  
 유니코드 인코딩 문자를 쓸 수 있는 스트림입니다.  
  
## <a name="exceptions"></a>예외  
 java.sql.SQLException  
  
## <a name="remarks"></a>설명  
 이 setCharacterStream 메서드는 java.sql.Clob 인터페이스의 setCharacterStream 메서드에 의해 지정됩니다.  
  
 CLOB의 문자 데이터는 기록기에 의해 지정된 위치부터 덮어쓰여지며 CLOB의 초기 길이를 초과할 수 있습니다. 위치+1 값을 지정하면 문자가 추가되고, 위치+2 이상(또는 0 이하)의 값을 지정하면 위치 오류가 발생합니다.  
  
## <a name="see-also"></a>참고 항목  
 [SQLServerClob 메서드](../../../connect/jdbc/reference/sqlserverclob-methods.md)   
 [SQLServerClob 멤버](../../../connect/jdbc/reference/sqlserverclob-members.md)   
 [SQLServerClob 클래스](../../../connect/jdbc/reference/sqlserverclob-class.md)  
  
  
