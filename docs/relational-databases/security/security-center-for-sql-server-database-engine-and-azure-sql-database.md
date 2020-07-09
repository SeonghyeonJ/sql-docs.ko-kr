---
title: SQL Server 및 Azure SQL Database의 보안 문서
description: SQL Server 및 Azure SQL Database의 보안 및 보호 관련 콘텐츠 참조입니다.
ms.custom: seo-lt-2019
ms.date: 09/27/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
f1_keywords:
- Security [SQL Server]
helpviewer_keywords:
- SQL Server, security
- security [SQL Server]
- database security [SQL Server]
- databases [SQL Server], security
ms.assetid: dfb39d16-722a-4734-94bb-98e61e014ee7
author: VanMSFT
ms.author: vanto
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 00e99fc389780939e277039c637e48a5c8065c28
ms.sourcegitcommit: f3321ed29d6d8725ba6378d207277a57cb5fe8c2
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/06/2020
ms.locfileid: "86001074"
---
# <a name="security-center-for-sql-server-database-engine-and-azure-sql-database"></a>SQL Server 데이터베이스 엔진 및 Azure SQL 데이터베이스에 대한 보안 센터
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  이 페이지에서는 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 및 [!INCLUDE[ssSDSFull](../../includes/sssdsfull-md.md)]의 보안 및 보호에 대해 필요한 정보를 찾는 데 도움이 되는 링크를 제공합니다.  
  
 **범례**  
  
 ![security-center-legend](../performance/media/security-center-legend.PNG "security-center-legend")  
  
##  <a name="authentication-who-are-you"></a><a name="Who"></a> 인증: 귀하는 누구인가요?  
  
|||  
|-|-|  
|**누가 인증했습니까?**<br /><br /> ![security-center-sqlserver](../performance/media/security-center-sqlserver.png "security-center-sqlserver") Windows 인증<br /><br /> ![security-center-both](../performance/media/security-center-both.png "security-center-both") [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인증<br /><br /> ![security-center-sqldb](../../relational-databases/security/media/security-center-sqldb.png "security-center-sqldb") Azure Active Directory|누가 인증했습니까? (Windows 또는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)])<br /><br /> [인증 모드 선택](../../relational-databases/security/choose-an-authentication-mode.md)<br /><br /> [Azure Active Directory 인증을 사용하여 SQL Database에 연결](https://azure.microsoft.com/documentation/articles/sql-database-aad-authentication/)|  
|**어디서 인증했습니까?**<br /><br /> ![security-center-both](../performance/media/security-center-both.png "security-center-both") master 데이터베이스: 로그인 및 DB 사용자<br /><br /> ![security-center-both](../performance/media/security-center-both.png "security-center-both") 사용자 데이터베이스: 포함된 DB 사용자|master 데이터베이스에서 인증(로그인 및 데이터베이스 사용자)<br /><br /> [SQL Server 로그인 만들기](../../relational-databases/security/authentication-access/create-a-login.md)<br /><br /> [Azure SQL Database에서 데이터베이스 및 로그인 관리](https://msdn.microsoft.com/library/ee336235.aspx)<br /><br /> [데이터베이스 사용자 만들기](../../relational-databases/security/authentication-access/create-a-database-user.md)<br /><br /> <br /><br /> 사용자 데이터베이스에서 인증<br /><br /> [포함된 데이터베이스 사용자 - 휴대용 데이터베이스 만들기](../../relational-databases/security/contained-database-users-making-your-database-portable.md)|  
|**다른 ID 사용**<br /><br /> ![security-center-both](../performance/media/security-center-both.png "security-center-both") 자격 증명<br /><br /> ![security-center-sqlserver](../performance/media/security-center-sqlserver.png "security-center-sqlserver") 다른 로그인으로 실행<br /><br /> ![security-center-both](../performance/media/security-center-both.png "security-center-both") 다른 데이터베이스 사용자로 실행|[자격 증명&#40;데이터베이스 엔진&#41;](../../relational-databases/security/authentication-access/credentials-database-engine.md)<br /><br /> [다른 로그인으로 실행합니다.](../../t-sql/statements/execute-as-transact-sql.md)<br /><br /> [다른 데이터베이스 사용자로 실행](../../t-sql/statements/execute-as-transact-sql.md)|  
  
##  <a name="authorization-what-can-you-do"></a><a name="What"></a> 권한 부여: 무엇을 할 수 있나요?  
  
|||  
|-|-|  
|**권한 부여, 취소 및 거부**<br /><br /> ![security-center-both](../performance/media/security-center-both.png "security-center-both") 보안 개체 클래스<br /><br /> ![security-center-sqlserver](../performance/media/security-center-sqlserver.png "security-center-sqlserver") 세분화된 서버 권한<br /><br /> ![security-center-both](../performance/media/security-center-both.png "security-center-both") 세분화된 데이터베이스 권한|[사용 권한 계층&#40;데이터베이스 엔진&#41;](../../relational-databases/security/permissions-hierarchy-database-engine.md)<br /><br /> [권한](../../relational-databases/security/permissions-database-engine.md)<br /><br /> [보안 개체](../../relational-databases/security/securables.md)<br /><br /> [데이터베이스 엔진 권한 시작](../../relational-databases/security/authentication-access/getting-started-with-database-engine-permissions.md)|  
|**역할별 보안**<br /><br /> ![security-center-sqlserver](../performance/media/security-center-sqlserver.png "security-center-sqlserver") 서버 수준 역할<br /><br /> ![security-center-both](../performance/media/security-center-both.png "security-center-both") 데이터베이스 수준 역할|[서버 수준 역할](../../relational-databases/security/authentication-access/server-level-roles.md)<br /><br /> [데이터베이스 수준 역할](../../relational-databases/security/authentication-access/database-level-roles.md)|  
|**선택한 데이터 요소에 대한 데이터 액세스 제한**<br /><br /> ![security-center-both](../performance/media/security-center-both.png "security-center-both") 뷰/프로시저를 사용한 데이터 액세스 제한<br /><br /> ![security-center-both](../performance/media/security-center-both.png "security-center-both") 행 수준 보안<br /><br /> ![security-center-both](../performance/media/security-center-both.png "security-center-both") 동적 데이터 마스킹<br /><br /> ![security-center-both](../performance/media/security-center-both.png "security-center-both") 서명된 개체|[뷰](../../relational-databases/views/views.md) 및 [프로시저](../../relational-databases/stored-procedures/stored-procedures-database-engine.md)를 사용한 데이터 액세스 제한<br /><br /> [행 수준 보안(SQL Server)](../../relational-databases/security/row-level-security.md)<br /><br /> [행 수준 보안(Azure SQL 데이터베이스)](https://msdn.microsoft.com/library/azure/dn765131.aspx)<br /><br /> [동적 데이터 마스킹(SQL Server)](../../relational-databases/security/dynamic-data-masking.md)<br /><br /> [동적 데이터 마스킹(Azure SQL 데이터베이스)](https://azure.microsoft.com/documentation/articles/sql-database-dynamic-data-masking-get-started/)<br /><br /> [서명된 개체](../../t-sql/statements/add-signature-transact-sql.md)|  
  
##  <a name="encryption-storing-secret-data"></a><a name="Encrypt"></a> 암호화: 비밀 데이터 저장  
  
|||  
|-|-|  
|**파일 암호화**<br /><br /> ![security-center-sqlserver](../performance/media/security-center-sqlserver.png "security-center-sqlserver") BitLocker 암호화(드라이브 수준)<br /><br /> ![security-center-sqlserver](../performance/media/security-center-sqlserver.png "security-center-sqlserver") NTFS 암호화(폴더 수준)<br /><br /> ![security-center-both](../performance/media/security-center-both.png "security-center-both") 투명한 데이터 암호화(파일 수준)<br /><br /> ![security-center-both](../performance/media/security-center-both.png "security-center-both") 백업 암호화(파일 수준)|[BitLocker(드라이브 수준)](https://support.microsoft.com/kb/2855131)<br /><br /> [NTFS 암호화(폴더 수준)](https://msdn.microsoft.com/library/dd163562.aspx)<br /><br /> [투명한 데이터 암호화(파일 수준)](../../relational-databases/security/encryption/transparent-data-encryption.md)<br /><br /> [백업 암호화(파일 수준)](../../relational-databases/backup-restore/backup-encryption.md)|  
|**소스 암호화**<br /><br /> ![security-center-sqlserver](../performance/media/security-center-sqlserver.png "security-center-sqlserver") 확장 가능 키 관리 모듈<br /><br /> ![security-center-sqlserver](../performance/media/security-center-sqlserver.png "security-center-sqlserver") Azure Key Vault에 저장된 키<br /><br /> ![security-center-both](../performance/media/security-center-both.png "security-center-both") Always Encrypted|[확장 가능 키 관리 모듈](../../relational-databases/security/encryption/extensible-key-management-ekm.md)<br /><br /> [Azure 키 자격 증명 모음에 저장된 키](../../relational-databases/security/encryption/extensible-key-management-using-azure-key-vault-sql-server.md)<br /><br /> [Always Encrypted](../../relational-databases/security/encryption/always-encrypted-database-engine.md)|  
|**열, 데이터 및 키 암호화**<br /><br /> ![security-center-both](../performance/media/security-center-both.png "security-center-both") 인증서로 암호화<br /><br /> ![security-center-both](../performance/media/security-center-both.png "security-center-both") 대칭 키로 암호화<br /><br /> ![security-center-both](../performance/media/security-center-both.png "security-center-both") 비대칭 키로 암호화<br /><br /> ![security-center-both](../performance/media/security-center-both.png "security-center-both") 암호로 암호화|[인증서로 암호화](../../t-sql/functions/encryptbycert-transact-sql.md)<br /><br /> [비대칭 키로 암호화](../../t-sql/functions/encryptbyasymkey-transact-sql.md)<br /><br /> [대칭 키로 암호화](../../t-sql/functions/encryptbykey-transact-sql.md)<br /><br /> [암호로 암호화](../../t-sql/functions/encryptbypassphrase-transact-sql.md)<br /><br /> [데이터 열 암호화](../../relational-databases/security/encryption/encrypt-a-column-of-data.md)|  
  
##  <a name="connection-security-restricting-and-securing"></a><a name="Connect"></a> 연결 보안: 제한 및 보안  
  
|||  
|-|-|  
|**방화벽 보호**<br /><br /> ![security-center-sqlserver](../performance/media/security-center-sqlserver.png "security-center-sqlserver") Windows 방화벽 설정<br /><br /> ![security-center-sqldb](../../relational-databases/security/media/security-center-sqldb.png "security-center-sqldb") Azure 서비스 방화벽 설정<br /><br /> ![security-center-sqldb](../../relational-databases/security/media/security-center-sqldb.png "security-center-sqldb") 데이터베이스 방화벽 설정|[데이터베이스 엔진 액세스에 대한 Windows 방화벽 구성](../../database-engine/configure-windows/configure-a-windows-firewall-for-database-engine-access.md)<br /><br /> [Azure SQL 데이터베이스 방화벽 설정](../../relational-databases/system-stored-procedures/sp-set-database-firewall-rule-azure-sql-database.md)<br /><br /> [Azure 서비스 방화벽 설정](../../relational-databases/system-stored-procedures/sp-set-firewall-rule-azure-sql-database.md)|  
|**전송 중인 데이터 암호화**<br /><br /> ![security-center-both](../performance/media/security-center-both.png "security-center-both") 강제 SSL 연결<br /><br /> ![security-center-sqlserver](../performance/media/security-center-sqlserver.png "security-center-sqlserver") 선택적 SSL 연결|[데이터베이스 엔진에 암호화된 연결 사용](../../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md)<br /><br /> [데이터베이스 엔진](../../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md), [네트워크 보안에 암호화된 연결 사용](/azure/sql-database/sql-database-security-best-practice#network-security) <br /><br /> [Microsoft SQL Server에 대한 TLS 1.2 지원](https://support.microsoft.com/kb/3135244)|  
  
##  <a name="auditing-recording-access"></a><a name="Audit"></a> 감사: 액세스 기록  
  
|||  
|-|-|  
|**감사 자동화**<br /><br /> ![security-center-sqlserver](../../relational-databases/performance/media/security-center-sqlserver.png "security-center-sqlserver") [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 감사(서버 및 DB 수준)<br /><br /> ![security-center-sqldb](../../relational-databases/security/media/security-center-sqldb.png "security-center-sqldb") [!INCLUDE[ssSDS](../../includes/sssds-md.md)] 감사(데이터베이스 수준)<br /><br /> ![security-center-sqldb](../../relational-databases/security/media/security-center-sqldb.png "security-center-sqldb") 위협 탐지| <br /><br /> [SQL Server Audit&#40;데이터베이스 엔진&#41;](../../relational-databases/security/auditing/sql-server-audit-database-engine.md)<br /><br /> [SQL 데이터베이스 감사](https://azure.microsoft.com/documentation/articles/sql-database-auditing-get-started/)<br /><br /> [SQL Database Advanced Threat Protection 시작](https://azure.microsoft.com/documentation/articles/sql-database-threat-detection-get-started/) <br /><br /> [SQL Database 취약성 평가](https://docs.microsoft.com/azure/sql-database/sql-vulnerability-assessment) |  
|**사용자 지정 감사**<br /><br /> ![security-center-both](../../relational-databases/performance/media/security-center-both.png "security-center-both") 트리거|사용자 지정 감사 구현: 만들기 [DDL Triggers](../../relational-databases/triggers/ddl-triggers.md) 및 [DML Triggers](../../relational-databases/triggers/dml-triggers.md)|  
|**호환성**<br /><br /> ![security-center-both](../../relational-databases/performance/media/security-center-both.png "security-center-both") 호환성|SQL Server:<br />                        [Common Criteria](https://go.microsoft.com/fwlink/?LinkId=616319)<br /><br /> SQL 데이터베이스:<br />                        [Microsoft Azure 보안 센터: 기능별 준수](https://azure.microsoft.com/support/trust-center/services/)|  
  
##  <a name="sql-injection"></a><a name="SQLInjection"></a> SQL 인젝션  
 SQL 삽입은 문자열에 삽입된 악성 코드가 나중에 구문 분석 및 실행용으로 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 에 전달되는 방식의 공격입니다. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 는 구문상 유효한 모든 수신 쿼리를 실행하므로 SQL 문을 생성하는 모든 프로시저에 삽입과 관련한 보안 위험이 있는지 확인해야 합니다. 모든 데이터베이스 시스템에는 어느 정도 SQL 삽입 공격을 받을 위험이 있으며, 대부분의 취약성은 [!INCLUDE[ssDE](../../includes/ssde-md.md)]을 쿼리하는 애플리케이션에서 발생합니다. 저장 프로시저 및 매개 변수화된 명령을 사용하면 SQL 삽입 공격을 차단하여 동적 SQL을 방지하고 모든 사용자에 대해 권한을 제한할 수 있습니다.  자세한 내용은 [SQL Injection](../../relational-databases/security/sql-injection.md)을 참조하세요.  
  
 애플리케이션 프로그래머를 위한 추가 링크:  
  
-   [SQL Server의 애플리케이션 보안 시나리오](/dotnet/framework/data/adonet/sql/application-security-scenarios-in-sql-server)  
  
-   [SQL Server에서 보안 동적 SQL 작성](/dotnet/framework/data/adonet/sql/writing-secure-dynamic-sql-in-sql-server)  
  
-   [방법: ASP.NET에서 SQL 삽입으로부터 보호](https://msdn.microsoft.com/library/ff648339.aspx)  
  
## <a name="see-also"></a>참고 항목  
 [데이터베이스 엔진 권한 시작](../../relational-databases/security/authentication-access/getting-started-with-database-engine-permissions.md)   
 [SQL Server 보안 설정](../../relational-databases/security/securing-sql-server.md)   
 [보안 주체&#40;데이터베이스 엔진&#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)   
 [SQL Server 인증서 및 비대칭 키](../../relational-databases/security/sql-server-certificates-and-asymmetric-keys.md)   
 [SQL Server 암호화](../../relational-databases/security/encryption/sql-server-encryption.md)   
 [노출 영역 구성](../../relational-databases/security/surface-area-configuration.md)   
 [강력한 암호](../../relational-databases/security/strong-passwords.md)   
 [TRUSTWORTHY 데이터베이스 속성](../../relational-databases/security/trustworthy-database-property.md)   
 [데이터베이스 엔진 기능 및 태스크](https://msdn.microsoft.com/library/d9efe145-3306-4d61-bd77-e2af43e19c34)  
 [SQL Server 지적 재산 보호](../../relational-databases/security/protecting-your-sql-server-intellectual-property.md)   
  
[!INCLUDE[get-help-security](../../includes/get-help-security.md)]
