---
title: 어셈블리 만들기 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- creating assemblies
- UNSAFE assemblies
- CREATE ASSEMBLY statement
- SAFE assemblies
- EXTERNAL_ACCESS assemblies
- assemblies [CLR integration], creating
ms.assetid: a2bc503d-b6b2-4963-8beb-c11c323f18e0
author: rothja
ms.author: jroth
ms.openlocfilehash: 995c3a621e6de5d1b878f28c7c0fffaae3311bd2
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84953884"
---
# <a name="creating-an-assembly"></a>어셈블리 만들기
  저장 프로시저나 트리거 같은 관리되는 데이터베이스 개체는 컴파일한 다음 어셈블리라는 단위로 배포합니다. 관리되는 DLL 어셈블리의 경우 어셈블리에서 제공하는 기능을 사용하려면 먼저 어셈블리를 [!INCLUDE[msCoName](../../../includes/ssnoversion-md.md)] 에 등록해야 합니다. CREATE ASSEMBLY 문을 사용하여 어셈블리를 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 데이터베이스에 등록할 수 있습니다. 이 항목에서는 CREATE ASSEMBLY 문을 사용하여 어셈블리를 데이터베이스에 등록하는 방법과 어셈블리에 대한 보안 설정을 지정하는 방법에 대해 설명합니다.  
  
## <a name="the-create-assembly-statement"></a>CREATE ASSEMBLY 문  
 CREATE ASSEMBLY 문은 데이터베이스에 어셈블리를 만드는 데 사용합니다. 다음은 예제입니다.  
  
```  
CREATE ASSEMBLY SQLCLRTest  
FROM 'C:\MyDBApp\SQLCLRTest.dll';  
```  
  
 FROM 절은 만들려는 어셈블리의 경로 이름을 지정합니다. 이 경로는 UNC(Universal Naming Convention) 경로나 시스템에 대해 로컬인 물리적 파일 경로일 수 있습니다.  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]에서는 이름, culture 및 공개 키가 동일한 서로 다른 버전의 어셈블리를 등록할 수 없습니다.  
  
 다른 어셈블리를 참조하는 어셈블리는 만들 수 있습니다. 에서 어셈블리를 만들면 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 루트 수준 어셈블리에서 참조 하는 어셈블리도 생성 됩니다 (참조 된 어셈블리가 데이터베이스에 아직 만들어지지 않은 경우).  
  
 데이터베이스 사용자나 사용자 역할에는 데이터베이스에 어셈블리를 만들고 이를 소유할 수 있는 권한이 부여됩니다. 어셈블리를 만들려면 데이터베이스 사용자나 역할에 CREATE ASSEMBLY 권한이 있어야 합니다.  
  
 어셈블리가 다른 어셈블리를 참조하려면 다음 조건을 만족해야 합니다.  
  
-   호출되거나 참조되는 어셈블리를 동일한 사용자나 역할이 소유하고 있습니다.  
  
-   호출되거나 참조되는 어셈블리가 동일한 데이터베이스에 만들어졌습니다.  
  
## <a name="specifying-security-when-creating-assemblies"></a>어셈블리 생성 시 보안 지정  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 데이터베이스에 어셈블리를 만들 때 코드가 실행될 수 있는 세 가지 보안 수준인 `SAFE`, `EXTERNAL_ACCESS` 또는 `UNSAFE` 중 하나를 지정할 수 있습니다. `CREATE ASSEMBLY` 문이 실행될 때 코드 어셈블리에 대해 특정 검사가 수행되어 어셈블리가 서버에 등록되지 않을 수 있습니다. 자세한 내용은 [CodePlex](https://msftengprodsamples.codeplex.com/)의 가장 예제를 참조하십시오.  
  
 `SAFE`는 기본 권한 집합이며 대부분의 시나리오에서 작동합니다. 이 보안 수준을 지정하려면 다음과 같이 CREATE ASSEMBLY 문의 구문을 수정합니다.  
  
```  
CREATE ASSEMBLY SQLCLRTest  
FROM 'C:\MyDBApp\SQLCLRTest.dll'  
WITH PERMISSION_SET = SAFE;  
```  
  
 `SAFE` 권한 집합으로 어셈블리를 만드는 데 위의 코드에서 세 번째 줄을 생략해도 됩니다.  
  
```  
CREATE ASSEMBLY SQLCLRTest  
FROM 'C:\MyDBApp\SQLCLRTest.dll';  
```  
  
 어셈블리의 코드를 `SAFE` 권한 집합으로 실행할 경우 코드는 in-process 관리 공급자를 통해 서버 내에서 계산 및 데이터 액세스만 수행할 수 있습니다.  
  
### <a name="creating-external_access-and-unsafe-assemblies"></a>EXTERNAL_ACCESS 및 UNSAFE 어셈블리 만들기  
 `EXTERNAL_ACCESS`는 코드에서 파일, 네트워크, 레지스트리, 환경 변수 등 서버 외부의 리소스에 액세스해야 하는 시나리오를 해결합니다. 서버에서 외부 리소스에 액세스할 때마다 서버는 관리 코드를 호출하는 사용자의 보안 컨텍스트를 가장합니다.  
  
 `UNSAFE` 코드 권한은 어셈블리가 안전한지 확인할 수 없거나 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Win32 API 같은 제한된 리소스에 대한 추가 액세스가 필요한 경우에 사용합니다.  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]에 `EXTERNAL_ACCESS` 또는 `UNSAFE` 어셈블리를 만들려면 다음 두 조건 중 하나를 만족해야 합니다.  
  
1.  어셈블리가 서명된 강력한 이름이거나 인증서로 서명된 Authenticode입니다. 이 강력한 이름(또는 인증서)이 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 내에서 비대칭 키(또는 인증서)로 생성되었고 `EXTERNAL ACCESS ASSEMBLY` 권한(외부 액세스 어셈블리의 경우) 또는 `UNSAFE ASSEMBLY` 권한(안전하지 않은 어셈블리의 경우)이 있는 해당 로그인을 가지고 있습니다.  
  
2.  DBO (데이터베이스 소유자)에는 `EXTERNAL ACCESS ASSEMBLY` (어셈블리의 경우) `EXTERNAL ACCESS` 또는 `UNSAFE ASSEMBLY` (어셈블리의 경우 `UNSAFE` ) 권한이 있고 데이터베이스에는 [신뢰할 수 있는 데이터베이스 속성이](../../security/trustworthy-database-property.md) 로 설정 되어 있습니다 `ON` .  
  
 위에 나열된 두 가지 조건은 어셈블리가 실행될 때는 물론 로드될 때에도 검사되며 두 가지 조건 중 적어도 하나는 만족해야 어셈블리가 로드됩니다.  
  
 서버 프로세스에서 CLR (공용 언어 런타임) 코드를 실행 하기 위해서만 데이터베이스의 신뢰할 수 있는 [데이터베이스 속성](../../security/trustworthy-database-property.md) 을로 설정 하는 것이 좋습니다 `ON` . 이 경우 대신 master 데이터베이스의 어셈블리 파일에서 비대칭 키를 만드는 것이 좋습니다. 그런 다음 이 비대칭 키에 매핑된 로그인을 만들고 로그인에 `EXTERNAL ACCESS ASSEMBLY` 또는 `UNSAFE ASSEMBLY` 권한을 부여해야 합니다.  
  
 [!INCLUDE[tsql](../../../includes/tsql-md.md)]CREATE ASSEMBLY 문을 실행 하기 전에 다음 문을 실행 합니다.  
  
```  
USE master;   
GO    
  
CREATE ASYMMETRIC KEY SQLCLRTestKey FROM EXECUTABLE FILE = 'C:\MyDBApp\SQLCLRTest.dll'     
CREATE LOGIN SQLCLRTestLogin FROM ASYMMETRIC KEY SQLCLRTestKey     
GRANT EXTERNAL ACCESS ASSEMBLY TO SQLCLRTestLogin;   
GO   
```  
  
> [!NOTE]  
>  비대칭 키와 연결할 새 로그인을 만들어야 합니다. 이 로그인은 사용 권한을 부여하기 위해서만 사용됩니다. 사용자에 연결하거나 애플리케이션 내에서 사용할 필요는 없습니다.  
  
 `EXTERNAL ACCESS` 어셈블리를 만들려면 `EXTERNAL ACCESS` 권한이 있어야 합니다. 이 권한은 어셈블리를 만들 때 지정합니다.  
  
```  
CREATE ASSEMBLY SQLCLRTest  
FROM 'C:\MyDBApp\SQLCLRTest.dll'  
WITH PERMISSION_SET = EXTERNAL_ACCESS;  
```  
  
 [!INCLUDE[tsql](../../../includes/tsql-md.md)]CREATE ASSEMBLY 문을 실행 하기 전에 다음 문을 실행 합니다.  
  
```  
USE master;   
GO    
  
CREATE ASYMMETRIC KEY SQLCLRTestKey FROM EXECUTABLE FILE = 'C:\MyDBApp\SQLCLRTest.dll';     
CREATE LOGIN SQLCLRTestLogin FROM ASYMMETRIC KEY SQLCLRTestKey ;    
GRANT UNSAFE ASSEMBLY TO SQLCLRTestLogin ;  
GO  
```  
  
 어셈블리가 `UNSAFE` 권한으로 로드되도록 지정하려면 어셈블리를 서버에 로드할 때 `UNSAFE` 권한 집합을 지정합니다.  
  
```  
CREATE ASSEMBLY SQLCLRTest  
FROM 'C:\MyDBApp\SQLCLRTest.dll'  
WITH PERMISSION_SET = UNSAFE;  
```  
  
 각 설정의 권한에 대한 자세한 내용은 [CLR Integration Security](../security/clr-integration-security.md)을 참조하십시오.  
  
## <a name="see-also"></a>참고 항목  
 [CLR 통합 어셈블리 관리](managing-clr-integration-assemblies.md)   
 [어셈블리 변경](altering-an-assembly.md)   
 [어셈블리 삭제](dropping-an-assembly.md)   
 [CLR 통합 코드 액세스 보안](../security/clr-integration-code-access-security.md)   
 [TRUSTWORTHY 데이터베이스 속성](../../security/trustworthy-database-property.md)   
 [부분적으로 신뢰할 수 있는 호출자 허용](../../../database-engine/dev-guide/allowing-partially-trusted-callers.md)  
  
