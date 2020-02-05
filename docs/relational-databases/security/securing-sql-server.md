---
title: SQL Server 보안 설정 | Microsoft 문서
ms.custom: ''
ms.date: 06/21/2019
ms.prod: sql
ms.prod_service: security
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
f1_keywords:
- Security [SQL Server]
helpviewer_keywords:
- database objects [SQL Server], security
- SQL Server, security
- operating systems [SQL Server], security
- security [SQL Server], planning
- applications [SQL Server], security
ms.assetid: 4d93489e-e9bb-45b3-8354-21f58209965d
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 473c12211ada579c3ceb441792788a1e975a85e0
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/01/2020
ms.locfileid: "68892490"
---
# <a name="securing-sql-server"></a>SQL Server 보안 설정

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 보안은 플랫폼, 인증, 개체(데이터 포함) 및 시스템에 액세스하는 애플리케이션의 네 가지 영역과 관련된 일련의 단계로 볼 수 있습니다. 다음 항목에서는 효과적인 보안 계획을 만들고 구현하는 방법을 설명합니다.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SQL Server [웹 사이트에서](https://go.microsoft.com/fwlink/?LinkID=31629) 보안에 대한 자세한 정보를 확인할 수 있습니다. 여기에는 최선의 구현 방법 안내와 보안 검사 목록도 포함되어 있습니다. 이 사이트에는 최신 서비스 팩 정보 및 다운로드도 포함되어 있습니다.  
  
## <a name="platform-and-network-security"></a>플랫폼 및 네트워크 보안  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에 대한 플랫폼에는 클라이언트를 데이터베이스 서버에 연결하는 물리적 하드웨어와 네트워킹 시스템 및 데이터베이스 요청을 처리하는 데 사용되는 이진 파일이 포함되어 있습니다.  
  
### <a name="physical-security"></a>물리적 보안  
 최상의 물리적 보안 방법은 물리적 서버 및 하드웨어 구성 요소에 대한 접근을 엄격하게 제한하는 것입니다. 예를 들어 데이터베이스 서버 하드웨어 및 네트워킹 디바이스가 있는 방에는 자물쇠를 달고 접근을 제한합니다. 또한 별도의 안전한 장소에 백업 미디어를 보관하여 접근을 제한합니다.  
  
 물리적 네트워크 보안의 구현은 권한이 없는 사용자가 네트워크에 접근하지 못하게 방지하는 것으로부터 시작됩니다. 다음 표에서는 네트워킹 보안에 대한 자세한 정보를 제공합니다.  
  
|원하는 정보|참조 항목|  
|---------------------------|---------|  
|[!INCLUDE[ssEW](../../includes/ssew-md.md)] 및 다른 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 버전에 대한 네트워크 액세스|[!INCLUDE[ssEW](../../includes/ssew-md.md)] 온라인 설명서의 "서버 환경 구성 및 보안 설정"|  
| &nbsp; | &nbsp; |
  
### <a name="operating-system-security"></a>운영 체제 보안  
 운영 체제 서비스 팩 및 업그레이드에는 중요한 보안 향상 기능이 포함되어 있습니다. 모든 업데이트와 업그레이드를 데이터베이스 애플리케이션을 사용하여 테스트한 후 운영 체제에 적용합니다.  
  
 방화벽을 사용하는 것도 효과적인 보안 구현 방법입니다. 논리적으로 방화벽은 네트워크 트래픽을 분리 또는 제한하므로 방화벽을 구성하여 조직의 데이터 보안 정책을 강화할 수 있습니다. 방화벽을 사용하면 보안 조치를 중점적으로 취할 수 있는 검사점이 제공되어 운영 체제 수준의 보안이 향상됩니다. 다음 표에서는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]의 방화벽 사용 방법에 대한 자세한 정보를 제공합니다.  
  
|원하는 정보|참조 항목|  
|---------------------------|---------|  
|사용할 방화벽 구성: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|[데이터베이스 엔진 액세스에 대한 Windows 방화벽 구성](../../database-engine/configure-windows/configure-a-windows-firewall-for-database-engine-access.md)|  
|사용할 방화벽 구성: [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]|[Integration Services 서비스&#40;SSIS 서비스&#41;](../../integration-services/service/integration-services-service-ssis-service.md)|  
|사용할 방화벽 구성: [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]|[Analysis Services 액세스를 허용하도록 Windows 방화벽 구성](https://docs.microsoft.com/analysis-services/instances/configure-the-windows-firewall-to-allow-analysis-services-access)|  
|다음에 액세스할 수 있도록 방화벽의 특정 포트 열기: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|[SQL Server 액세스를 허용하도록 Windows 방화벽 구성](../../sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access.md)|  
|채널 바인딩 및 서비스 바인딩을 사용하여 인증에 대한 확장된 보호 지원 구성|[확장된 보호를 사용하여 데이터베이스 엔진에 연결](../../database-engine/configure-windows/connect-to-the-database-engine-using-extended-protection.md)|  
| &nbsp; | &nbsp; |
  
 노출 영역 축소는 사용하지 않는 구성 요소를 중지하거나 비활성화하는 보안 조치입니다. 노출 영역 축소는 시스템에 대한 공격 가능성을 낮춤으로써 보안 향상에 도움이 됩니다. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 의 노출 영역을 제한할 때의 핵심은 서비스와 사용자에게 적절한 권한만 부여하여 "최소한의 권한"으로 필요한 서비스를 실행하는 것입니다. 다음 표에서는 서비스 및 시스템 액세스에 대한 자세한 정보를 제공합니다.  
  
|원하는 정보|참조 항목|  
|---------------------------|---------|  
|다음을 위해 필요한 서비스: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|[Windows 서비스 계정 및 권한 구성](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md)|  
| &nbsp; | &nbsp; |
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 시스템에서 인터넷 정보 서비스(IIS)를 사용하는 경우 추가 단계를 수행해야 플랫폼의 노출 영역에 대한 보안을 설정할 수 있습니다. 다음 표에서는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 및 인터넷 정보 서비스에 대한 자세한 정보를 제공합니다.  
  
|원하는 정보|참조 항목|  
|---------------------------|---------|  
|다음 IIS 보안: [!INCLUDE[ssEW](../../includes/ssew-md.md)]|[!INCLUDE[ssEW](../../includes/ssew-md.md)] 온라인 설명서의 "IIS 보안"|  
|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 인증|[Reporting Services의 인증](../../reporting-services/extensions/security-extension/authentication-in-reporting-services.md)|  
|[!INCLUDE[ssEW](../../includes/ssew-md.md)] 및 IIS 액세스|[!INCLUDE[ssEW](../../includes/ssew-md.md)] 온라인 설명서의 "인터넷 정보 서비스 보안 순서도"|  
| &nbsp; | &nbsp; |
  
### <a name="sql-server-operating-system-files-security"></a>SQL Server 운영 체제 파일 보안  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 는 작업 및 데이터 스토리지를 위해 운영 체제 파일을 사용합니다. 최상의 파일 보안 방법은 이러한 파일에 대한 액세스를 제한하는 것입니다. 다음 표에서는 이러한 파일에 대해 설명합니다.  
  
|원하는 정보|참조 항목|  
|---------------------------|---------|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 프로그램 파일|[SQL Server 기본 인스턴스 및 명명된 인스턴스의 파일 위치](../../sql-server/install/file-locations-for-default-and-named-instances-of-sql-server.md)|  
| &nbsp; | &nbsp; |
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 서비스 팩 및 업그레이드는 향상된 보안 기능을 제공합니다. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에 사용할 수 있는 최신 서비스 팩을 확인하려면 [SQL Server](https://go.microsoft.com/fwlink/?LinkID=31629) 웹 사이트를 참조하십시오.  
  
 다음 스크립트를 사용하여 시스템에 설치된 서비스 팩을 확인할 수 있습니다.  
  
```sql
SELECT CONVERT(char(20), SERVERPROPERTY('productlevel'));  
```  
  
## <a name="principals-and-database-object-security"></a>보안 주체 및 데이터베이스 개체 보안  
 보안 주체는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에 대한 액세스 권한을 부여 받은 개인, 그룹 및 프로세스입니다. "보안 개체"는 서버, 데이터베이스 및 데이터베이스에 포함된 개체입니다. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 노출 영역이 감소되도록 각 보안 개체의 사용 권한 집합을 구성할 수 있습니다. 다음 표에서는 보안 주체 및 보안 개체에 대한 자세한 정보를 제공합니다.  
  
|원하는 정보|참조 항목|  
|---------------------------|---------|  
|서버와 데이터베이스 사용자, 역할 및 프로세스|[보안 주체&#40;데이터베이스 엔진&#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)|  
|서버 및 데이터베이스 개체 보안|[보안 개체](../../relational-databases/security/securables.md)|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 보안 계층|[사용 권한 계층&#40;데이터베이스 엔진&#41;](../../relational-databases/security/permissions-hierarchy-database-engine.md)|  
| &nbsp; | &nbsp; |
  
### <a name="encryption-and-certificates"></a>암호화 및 인증서  
 암호화를 통해 액세스 제어 문제를 해결할 수는 없습니다. 그러나 암호화를 사용하면 드물게 발생하긴 하지만 액세스 제어가 무시되는 경우에도 데이터 손실을 제한하여 보안이 향상됩니다. 예를 들어 데이터베이스 호스트 컴퓨터가 잘못 구성되어 악의적인 사용자가 신용 카드 번호와 같은 중요한 데이터를 얻는 경우 해당 정보가 암호화되어 있으면 도난 당한 정보를 사용할 수 없을 수도 있습니다. 다음 표에서는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]의 암호화에 대한 자세한 정보를 제공합니다.  
  
|원하는 정보|참조 항목|  
|---------------------------|---------|  
|다음 암호화 계층 구조: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|[암호화 계층](../../relational-databases/security/encryption/encryption-hierarchy.md)|  
|안전한 연결 구현|[데이터베이스 엔진에 암호화 연결 사용&#40;SQL Server 구성 관리자&#41;](../../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md)|  
|암호화 함수|[암호화 함수&#40;Transact-SQL&#41;](../../t-sql/functions/cryptographic-functions-transact-sql.md)|  
  
 인증서는 강력한 인증을 통해 안전한 통신을 수행할 수 있도록 두 서버 간에 공유되는 소프트웨어 "키"입니다. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서 인증서를 만들고 사용하여 개체 및 연결 보안을 향상시킬 수 있습니다. 다음 표에서는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]의 인증서 사용 방법에 대한 자세한 정보를 제공합니다.  
  
|원하는 정보|참조 항목|  
|---------------------------|---------|  
|다음에서 사용할 인증서 만들기 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|[CREATE CERTIFICATE&#40;Transact-SQL&#41;](../../t-sql/statements/create-certificate-transact-sql.md)|  
|데이터베이스 미러링에 인증서 사용|[데이터베이스 미러링 엔드포인트에 대한 인증서 사용&#40;Transact-SQL&#41;](../../database-engine/database-mirroring/use-certificates-for-a-database-mirroring-endpoint-transact-sql.md)|  
| &nbsp; | &nbsp; |

## <a name="application-security"></a>애플리케이션 보안

### <a name="client-programs"></a>클라이언트 프로그램

[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 보안 방법에는 보안 클라이언트 애플리케이션 작성이 포함됩니다. 네트워킹 계층에서 클라이언트 애플리케이션의 보안을 설정하는 방법은 [Client Network Configuration](../../database-engine/configure-windows/client-network-configuration.md)을 참조하십시오.

### <a name="windows-defender-application-control-wdac"></a>WDAC(Windows Defender 애플리케이션 컨트롤)

<!--
This next live paragraph, about Windows Defender Application Control (WDAC), was requested by Bella Brahm, 2019/06/20. (GeneMi)

WDAC can also prevent the kind of highly sophisticated 'Nansh0u' attacks described in 'https://www.guardicore.com/2019/05/nansh0u-campaign-hackers-arsenal-grows-stronger/'. That webpage recommends this present article.
-->

WDAC(Windows Defender 애플리케이션 컨트롤)는 권한이 없는 코드 실행을 방지합니다. WDAC는 실행 파일 기반 맬웨어의 위협을 완화하는 효과적인 방법입니다. 자세한 내용은 [Windows Defender 애플리케이션 컨트롤](/windows/security/threat-protection/windows-defender-application-control/windows-defender-application-control) 설명서를 참조하세요.

## <a name="sql-server-security-tools-utilities-views-and-functions"></a>SQL Server 보안 도구, 유틸리티, 뷰 및 함수  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 는 보안을 구성하고 관리하는 데 사용할 수 있는 도구, 유틸리티, 뷰 및 함수를 제공합니다.  
  
### <a name="sql-server-security-tools-and-utilities"></a>SQL Server 보안 도구 및 유틸리티  
 다음 표에서는 보안을 구성하고 관리하는 데 사용할 수 있는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 도구 및 유틸리티에 대한 자세한 정보를 제공합니다.  
  
|원하는 정보|참조 항목|  
|---------------------------|---------|  
|다음 연결, 구성 및 제어: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|[SQL Server Management Studio 사용](https://msdn.microsoft.com/library/f289e978-14ca-46ef-9e61-e1fe5fd593be)|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 연결 및 명령 프롬프트에서 쿼리 실행|[sqlcmd 유틸리티](../../tools/sqlcmd-utility.md)|  
|다음 네트워크 구성 및 제어: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|[SQL Server 구성 관리자](../../relational-databases/sql-server-configuration-manager.md)|  
|정책 기반 관리를 사용하여 기능 설정 및 해제|[정책 기반 관리를 사용하여 서버 관리](../../relational-databases/policy-based-management/administer-servers-by-using-policy-based-management.md)|  
|보고서 서버에 대한 대칭 키 조작|[rskeymgmt 유틸리티&#40;SSRS&#41;](../../reporting-services/tools/rskeymgmt-utility-ssrs.md)|  
| &nbsp; | &nbsp; |

### <a name="sql-server-security-catalog-views-and-functions"></a>SQL Server 보안 카탈로그 뷰 및 함수  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 은 성능과 유틸리티에 맞게 최적화된 다양한 뷰 및 함수를 통해 보안 정보를 표시합니다. 다음 표에서는 보안 뷰 및 함수에 대한 자세한 정보를 제공합니다.  
  
|원하는 정보|참조 항목|  
|---------------------------|---------|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 보안 카탈로그 뷰(데이터베이스 수준 및 서버 수준의 사용 권한, 보안 주체, 역할 등에 대한 정보 반환) 암호화 키, 인증서 및 자격 증명에 대한 정보를 제공하는 카탈로그 뷰도 있습니다.|[보안 카탈로그 뷰&#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 보안 함수|[보안 함수&#40;Transact-SQL&#41;](../../t-sql/functions/security-functions-transact-sql.md)|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 보안 동적 관리 뷰|[보안 관련 동적 관리 뷰 및 함수&#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/security-related-dynamic-management-views-and-functions-transact-sql.md)|  
| &nbsp; | &nbsp; |

## <a name="related-content"></a>관련 내용  
 [SQL Server 설치에 대한 보안 고려 사항](../../sql-server/install/security-considerations-for-a-sql-server-installation.md)  
 [SQL Server 데이터베이스 엔진 및 Azure SQL Database 보안 센터](../../relational-databases/security/security-center-for-sql-server-database-engine-and-azure-sql-database.md)  
[SQL Server 2012 보안 모범 사례 - 운영 및 관리 태스크](https://download.microsoft.com/download/8/F/A/8FABACD7-803E-40FC-ADF8-355E7D218F4C/SQL_Server_2012_Security_Best_Practice_Whitepaper_Apr2012.docx)   
[SQL Server 보안 블로그](https://blogs.msdn.microsoft.com/sqlsecurity/)  
[보안 모범 사례 및 레이블 보안 백서](https://blogs.msdn.microsoft.com/sqlsecurity/2012/03/06/security-best-practice-and-label-security-whitepapers/)  
[행 수준 보안](../../relational-databases/security/row-level-security.md)   
[SQL Server 지적 재산 보호](../../relational-databases/security/protecting-your-sql-server-intellectual-property.md)   
  
