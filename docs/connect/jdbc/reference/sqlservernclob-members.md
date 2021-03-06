---
description: SQLServerNClob 멤버
title: SQLServerNClob 멤버 | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: b063f191-175e-4430-aab7-d88907f4ebec
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 3e23a4a5e9a4cb2d2c2a7ecd93db8615e814652c
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88354459"
---
# <a name="sqlservernclob-members"></a>SQLServerNClob 멤버
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  다음 표에는 [SQLServerNClob](../../../connect/jdbc/reference/sqlservernclob-class.md) 클래스에 의해 노출되는 멤버가 나와 있습니다.  
  
## <a name="constructors"></a>생성자  
 없음  
  
## <a name="fields"></a>필드  
 없음  
  
## <a name="inherited-fields"></a>상속된 필드  
 없음  
  
## <a name="methods"></a>메서드  
  
|속성|설명|  
|----------|-----------------|  
|[free](../../../connect/jdbc/reference/free-method-sqlservernclob.md)|이 메서드는 **NCLOB** 개체 및 이 개체가 보유한 리소스를 해제합니다.|  
|[getAsciiStream](../../../connect/jdbc/reference/getasciistream-method-sqlservernclob.md)|**java.sql.NClob** 개체에 의해 ASCII 스트림으로 지정된 **NCLOB** 값을 검색합니다.|  
|[getCharacterStream](../../../connect/jdbc/reference/getcharacterstream-method-sqlservernclob.md)|**java.sql.NClob** 개체에 의해 지정된 **NCLOB** 값을 검색합니다.|  
|[getSubString](../../../connect/jdbc/reference/getsubstring-method-sqlservernclob.md)|**java.sql.NClob** 개체에 의해 지정된 **NCLOB** 값에서 지정된 부분 문자열의 복사본을 검색합니다.|  
|[length](../../../connect/jdbc/reference/length-method-sqlservernclob.md)|**java.sql.NClob** 개체에 의해 지정된 **NCLOB** 값에서 문자의 수를 검색합니다.|  
|[position](../../../connect/jdbc/reference/position-method-sqlservernclob.md)|지정된 시작 위치에 따라 지정된 **java.sql.NClob** 개체 또는 해당 **java.sql.NClob**에 있는 부분 문자열의 문자 위치를 검색합니다.|  
|[setAsciiStream](../../../connect/jdbc/reference/setasciistream-method-sqlservernclob.md)|지정된 위치에서부터 ASCII 문자를 이 **java.sql.NClob** 개체가 나타내는 **NCLOB** 값에 쓰는 데 사용할 스트림을 검색합니다.|  
|[setCharacterStream](../../../connect/jdbc/reference/setcharacterstream-method-sqlservernclob.md)|지정된 위치에서부터 유니코드 문자의 스트림을 이 **java.sql.NClob** 개체가 나타내는 **NCLOB** 값에 쓰는 데 사용할 스트림을 검색합니다.|  
|[setString](../../../connect/jdbc/reference/setstring-method-sqlservernclob.md)|지정된 **문자열**을 **NCLOB**의 지정된 위치에서부터 씁니다.|  
|[truncate](../../../connect/jdbc/reference/truncate-method-sqlservernclob.md)|**NCLOB**값을 지정된 길이로 자릅니다.|  
  
## <a name="inherited-methods"></a>상속된 메서드  
  
|상속하는 원본 클래스|메서드|  
|--------------------------|-------------|  
|java.lang.Object|clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait|  
|java.sql.Clob|free, getAsciiStream, getCharacterStream, getSubString, length, position, setAsciiStream, setCharacterStream, setString, truncate|  
  
## <a name="see-also"></a>참고 항목  
 [SQLServerClob 클래스](../../../connect/jdbc/reference/sqlserverclob-class.md)  
  
  
