---
title: JDBC 드라이버 애플리케이션 보안 | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 90724ec6-a9cb-43ef-903e-793f89410bc0
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 3a7a8079f60336bbdfe7b837afa2313f5fda2691
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 06/07/2019
ms.locfileid: "66797839"
---
# <a name="securing-jdbc-driver-applications"></a>JDBC 드라이버 응용 프로그램 보안

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

[!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] 애플리케이션의 보안을 강화하려면 일반적인 코딩 문제를 방지하는 것 이상의 조치를 취해야 합니다. 데이터에 액세스하는 응용 프로그램에는 공격자가 주요한 데이터를 검색, 조작 또는 파괴하는 데 사용할 수 있는 수많은 잠재적인 오류 지점이 있습니다. 응용 프로그램의 디자인 단계 동안 위협 모델링 프로세스에서 결과 배포에 이르기까지, 그리고 진행 중인 유지 관리에서 지속적으로 모든 보안 측면을 이해하고 있어야 합니다.  
  
이 섹션의 항목에서는 연결 문자열, 사용자 입력의 유효성 검사 및 일반 응용 프로그램 보안을 포함한 일반적인 보안 문제에 대해 설명해야 합니다.  
  
## <a name="in-this-section"></a>섹션 내용  
  
| 항목                                                                            | 설명                                                                                                                                                           |
| -------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [연결 문자열 보안](../../connect/jdbc/securing-connection-strings.md) | 데이터 원본에 연결하는 데 사용되는 정보를 보호하는 기술에 대해 설명합니다.                                                                                    |
| [사용자 입력 유효성 검사](../../connect/jdbc/validating-user-input.md)             | 사용자 입력의 유효성을 검사하는 기술에 대해 설명합니다.                                                                                                                          |
| [애플리케이션 보안](../../connect/jdbc/application-security.md)               | Java 정책 권한을 사용하여 JDBC 드라이버 응용 프로그램의 보안을 유지하는 방법에 대해 설명합니다.                                                                                |
| [SSL 암호화 사용](../../connect/jdbc/using-ssl-encryption.md)               | SSL(Secure Sockets Layer)을 사용하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터베이스로 보안 통신 채널을 설정하는 방법에 대해 설명합니다. |
| [FIPS 모드](../../connect/jdbc/fips-mode.md)                                     | FIPS 규격 모드에서 JDBC 드라이버를 사용 하는 방법을 설명 합니다.                                                                                                              |
  
## <a name="see-also"></a>참고 항목  

 [JDBC 드라이버 개요](../../connect/jdbc/overview-of-the-jdbc-driver.md)  
