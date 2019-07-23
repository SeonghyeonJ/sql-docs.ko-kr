---
title: SSTRANSTIGHTLYCPLD 필드 (SQLServerXAResource) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SSTRANSTIGHTLYCPLD Field (SQLServerXAResource)
apilocation:
- SSTRANSTIGHTLYCPLD Field (SQLServerXAResource)
apitype: Assembly
ms.assetid: 379857c3-9de1-4964-8782-32df317cbfbb
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 36563b76c4207b5924bb32f5c8e99cca575c9d72
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67970048"
---
# <a name="sstranstightlycpld-field-sqlserverxaresource"></a>SSTRANSTIGHTLYCPLD 필드(SQLServerXAResource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  XID(XA 분기 트랜잭션 ID)가 다르지만 GTRID(전역 트랜잭션 ID)는 동일한 밀접하게 결합된 XA 트랜잭션을 허용하는 데 사용됩니다.  
  
## <a name="syntax"></a>구문  
  
```  
  
public static final int SSTRANSTIGHTLYCPLD  
```  
  
## <a name="field-value"></a>필드 값  
 **int** 값 32768입니다.  
  
## <a name="remarks"></a>Remarks  
 각 트랜잭션은 XID(XA 분기 트랜잭션 ID)와 GTRID(전역 트랜잭션 ID)로 식별됩니다. 애플리케이션에서 XID가 다르지만 GTRID는 동일한 밀접하게 결합된 XA 트랜잭션을 사용할 수 있도록 하려면 XAResource.start 메서드의 flags 매개 변수에서 [SSTRANSTIGHTLYCPLD](../../../connect/jdbc/reference/sstranstightlycpld-field-sqlserverxaresource.md)를 설정해야 합니다. 이 플래그를 사용 하는 방법에 대 한 자세한 내용은 [XA 트랜잭션 이해](../../../connect/jdbc/understanding-xa-transactions.md)를 참조 하세요.  
  
## <a name="see-also"></a>참고 항목  
 [SQLServerXAResource 필드](../../../connect/jdbc/reference/sqlserverxaresource-fields.md)   
 [SQLServerXAResource 멤버](../../../connect/jdbc/reference/sqlserverxaresource-members.md)   
 [SQLServerXAResource 클래스](../../../connect/jdbc/reference/sqlserverxaresource-class.md)  
  
  
