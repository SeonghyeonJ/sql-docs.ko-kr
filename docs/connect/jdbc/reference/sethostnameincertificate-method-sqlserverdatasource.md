---
title: setHostNameInCertificate 메서드 (SQLServerDataSource) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- setHostNameInCertificate Method (SQLServerDataSource)
apilocation:
- setHostNameInCertificate Method (SQLServerDataSource)
apitype: Assembly
ms.assetid: 2bcf4f2e-a103-4374-abc4-ffad4ce8e3c0
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: cde4c07a6a611fd6cd97324c46eae1e2ddc379ce
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 06/07/2019
ms.locfileid: "66764366"
---
# <a name="sethostnameincertificate-method-sqlserverdatasource"></a>setHostNameInCertificate 메서드(SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] SSL(Secure Sockets Layer) 인증서의 유효성을 검사하는 데 사용할 호스트 이름을 설정합니다.  
  
## <a name="syntax"></a>구문  
  
```  
  
public void setHostNameInCertificate(java.lang.String hostNameInCertificate)  
```  
  
#### <a name="parameters"></a>매개 변수  
 *hostNameInCertificate*  
  
 호스트 이름이 들어 있는 **문자열**입니다.  
  
## <a name="remarks"></a>Remarks  
 hostNameInCertificate 값은 통신 계층이 SSL을 사용하여 암호화된 경우 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] SSL 인증서의 유효성을 검사하는 데 사용됩니다. 기본값은 null입니다.  
  
 hostNameInCertificate 속성이 null로 설정되었거나 지정되지 않은 경우 [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)]에서는 serverName 속성 값을 사용하여 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] SSL 인증서에 대해 유효성을 검사합니다. hostNameInCertificate 속성이 문자열이나 빈 문자열 ""로 설정된 경우 드라이버에서는 해당 값을 사용하여 서버 SSL 인증서의 유효성을 검사합니다.  
  
## <a name="see-also"></a>참고 항목  
 [SQLServerDataSource 멤버](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource 클래스](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
