---
title: ISQLServerConnection 인터페이스 | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 031c01e2-2c65-4fe4-9700-fdbcc7a39f30
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 0f979ef1a15a07866e5331849130a7089acb1cea
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 06/07/2019
ms.locfileid: "66796428"
---
# <a name="isqlserverconnection-interface"></a>ISQLServerConnection 인터페이스
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  [!INCLUDE[msCoName](../../../includes/msconame_md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 데이터베이스에 대한 JDBC 연결을 나타냅니다. 이 인터페이스는 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] JDBC 드라이버 3.0에서 추가되었습니다.  
  
 **패키지:** com.microsoft.sqlserver.jdbc  
  
 **확장:** : java.sql.Connection  
  
## <a name="syntax"></a>구문  
  
```  
  
public interface ISQLServerConnection  
```  
  
## <a name="remarks"></a>Remarks  
 이 인터페이스는 구현한 [SQLServerConnection 클래스](../../../connect/jdbc/reference/sqlserverconnection-class.md)합니다.  
  
 이 인터페이스는 다음 [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] 관련 필드를 노출합니다.  
  
|필드|자세한 내용은 다음을 참조하세요.|  
|-----------|-------------------------------|  
|public final static int TRANSACTION_SNAPSHOT|[TRANSACTION_SNAPSHOT](../../../connect/jdbc/reference/transaction-snapshot-field-sqlserverconnection.md)|  
|public UUID getClientConnectionId()|[getClientConnectionID()](../../../connect/jdbc/reference/getclientconnectionid-method-sqlserverconnection.md)|  
  
## <a name="see-also"></a>참고 항목  
 [JDBC 드라이버 API 참조](../../../connect/jdbc/reference/jdbc-driver-api-reference.md)  
  
  
