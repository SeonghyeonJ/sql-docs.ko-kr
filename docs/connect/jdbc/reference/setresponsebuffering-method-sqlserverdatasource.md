---
description: setResponseBuffering 메서드(SQLServerDataSource)
title: setResponseBuffering 메서드(SQLServerDataSource) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDataSource.setResponseBuffering(String responseBufferingValue)
apilocation:
- SQLServerDataSource.setResponseBuffering(String responseBufferingValue)
apitype: Assembly
ms.assetid: c9e43ff2-8117-4dca-982d-83c863d0c8e1
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 90f66ec23ebd40296e5dee45bb3c663688551cc1
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88458422"
---
# <a name="setresponsebuffering-method-sqlserverdatasource"></a>setResponseBuffering 메서드(SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  이 [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md) 개체를 사용하여 만들어진 연결에 대한 응답 버퍼링 모드를 설정합니다.  
  
## <a name="syntax"></a>구문  
  
```  
  
public void setResponseBuffering(java.lang.String value)  
```  
  
#### <a name="parameters"></a>매개 변수  
 *value*  
  
 버퍼링 및 스트리밍 모드가 들어 있는 **String**입니다. 유효한 모드는 대/소문자를 구분하지 않는 문자열 **full** 또는 **adaptive**일 수 있습니다.  
  
## <a name="remarks"></a>설명  
 **full** 값은 런타임에 서버의 전체 결과를 읽도록 지정합니다.  
  
 **adaptive** 값은 필요할 때 가능한 최소한의 데이터를 버퍼링하도록 지정합니다. **adaptive** 값은 기본 버퍼링 모드입니다.  
  
 응답 버퍼링 모드 사용에 대한 자세한 내용은 [적응 버퍼링 사용](../../../connect/jdbc/using-adaptive-buffering.md)을 참조하세요.  
  
## <a name="see-also"></a>참고 항목  
 [SQLServerDataSource 멤버](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource 클래스](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
