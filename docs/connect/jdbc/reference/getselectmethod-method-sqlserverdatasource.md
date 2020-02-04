---
title: getSelectMethod 메서드(SQLServerDataSource) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDataSource.getSelectMethod
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: b6255d2e-0028-474a-afa8-553ef092243e
author: MightyPen
ms.author: genemi
ms.openlocfilehash: d0919590ec727068b97ef66d3d0f6824aefcbe03
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/31/2020
ms.locfileid: "67980033"
---
# <a name="getselectmethod-method-sqlserverdatasource"></a>getSelectMethod 메서드(SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  이 [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md) 개체를 사용하여 만들어진 모든 결과 집합에 사용되는 기본 커서 형식을 반환합니다.  
  
## <a name="syntax"></a>구문  
  
```  
  
public java.lang.String getSelectMethod()  
```  
  
## <a name="return-value"></a>Return Value  
 기본 커서 형식이 포함된 **문자열** 값입니다.  
  
## <a name="remarks"></a>설명  
 selectMethod 속성은 결과 집합에 사용되는 기본 커서 유형을 지정합니다. 이 속성은 큰 결과 집합을 처리하면서 클라이언트측 메모리에 전체 결과 집합을 저장하지 않으려는 경우에 유용합니다. 이 속성을 "cursor"로 설정하면 보다 작은 여러 개의 데이터 청크를 한 번에 인출할 수 있는 서버측 커서를 만들 수 있습니다. selectMethod 속성이 설정되어 있지 않으면 getSelectMethod는 기본값인 "direct"를 반환합니다.  
  
## <a name="see-also"></a>참고 항목  
 [SQLServerDataSource 멤버](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource 클래스](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
