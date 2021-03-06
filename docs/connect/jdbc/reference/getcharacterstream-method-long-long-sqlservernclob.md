---
description: getCharacterStream 메서드(long, long)(SQLServerNClob)
title: getCharacterStream 메서드(long, long)(SQLServerNClob) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 5a8028bc-c877-4668-b662-0746d462040e
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: d66d64ff62bad45d454a535b78a01e666835126a
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88436805"
---
# <a name="getcharacterstream-method-long-long-sqlservernclob"></a>getCharacterStream 메서드(long, long)(SQLServerNClob)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  **NCLOB** 데이터를 지정된 위치 및 길이의 문자 스트림 또는 **Reader** 개체로 검색합니다.  
  
## <a name="syntax"></a>구문  
  
```  
  
public java.io.Reader getCharacterStream(long pos,  
                                  long length)  
```  
  
#### <a name="parameters"></a>매개 변수  
 *pos*  
  
 검색할 부분 값의 첫 번째 문자에 대한 오프셋을 나타내는 **long**입니다.  
  
 *length*  
  
 검색할 부분 값의 문자 길이를 나타내는 **long**입니다.  
  
## <a name="return-value"></a>반환 값  
 **NCLOB** 데이터가 들어 있는 Reader 개체입니다.  
  
## <a name="exceptions"></a>예외  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>설명  
 이 getCharacterStream 메서드는 java.sql.NClob 인터페이스의 getCharacterStream 메서드에 의해 지정됩니다.  
  
## <a name="see-also"></a>참고 항목  
 [getCharacterStream 메서드&#40;SQLServerNClob&#41;](../../../connect/jdbc/reference/getcharacterstream-method-sqlservernclob.md)   
 [SQLServerNClob 메서드](../../../connect/jdbc/reference/sqlservernclob-methods.md)   
 [SQLServerNClob 멤버](../../../connect/jdbc/reference/sqlservernclob-members.md)   
 [SQLServerNClob 클래스](../../../connect/jdbc/reference/sqlservernclob-class.md)  
  
  
