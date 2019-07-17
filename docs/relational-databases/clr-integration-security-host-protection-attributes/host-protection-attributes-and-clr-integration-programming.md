---
title: 호스트 보호 특성 및 CLR 통합 프로그래밍 | Microsoft Docs
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- host protection attributes [CLR integration]
- HostProtectionAttribute [CLR integration]
- common language runtime [SQL Server], host protection attributes
- disallowed types and members [CLR integration]
- common language runtime [SQL Server], disallowed types and members
- HPAs [CLR integration]
ms.assetid: 268078df-63ca-4c03-a8e7-7108bcea9697
author: rothja
ms.author: jroth
ms.openlocfilehash: 6e060411864c0f354ee9107216b86a47f738bf43
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68028057"
---
# <a name="host-protection-attributes-and-clr-integration-programming"></a>호스트 보호 특성 및 CLR 통합 프로그래밍
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  CLR(공용 언어 런타임)은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]부터 시작하여, [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]와 같은 CLR 호스트에 유용할 수 있는 특성으로 .NET Framework의 일부인 관리되는 API(응용 프로그래밍 인터페이스)에 주석을 추가하는 메커니즘을 제공합니다. 이러한 HPA(호스트 보호 특성)의 예는 다음과 같습니다.  
  
-   **Sharedstate:** , 공유 된 상태 (예: 정적 클래스 필드) API가 만들거나 관리 하는 기능을 노출 하는지 여부를 나타냅니다.  
  
-   **동기화**, API가 스레드 간 동기화를 수행 하는 기능을 노출 하는지 여부를 나타냅니다.  
  
-   **ExternalProcessMgmt**, API가 호스트 프로세스를 제어 하는 방법을 노출 하는지 여부를 나타냅니다.  
  
 이러한 특성을 사용하면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]는 CAS(코드 액세스 보안)를 통해 호스팅된 환경에서 허용하지 않는 HPA 목록을 지정합니다. CAS 요구 사항은 3 가지 된 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 권한 집합: **안전한**, **EXTERNAL_ACCESS**, 또는 **UNSAFE**합니다. 서버에서 어셈블리를 등록 하는 경우 이러한 세 보안 수준 중 하나가 지정 된 사용 하는 **CREATE ASSEMBLY** 문입니다. 코드 내에서 실행 되는 **안전한** 또는 **EXTERNAL_ACCESS** 권한 집합에는 특정 형식 또는 멤버를 되지 않도록 해야 합니다는 **System.Security.Permissions.HostProtectionAttribute** 특성을 적용 합니다. 자세한 내용은 [Creating an Assembly](../../relational-databases/clr-integration/assemblies/creating-an-assembly.md) 하 고 [CLR 통합 프로그래밍 모델 제한 사항](../../relational-databases/clr-integration/database-objects/clr-integration-programming-model-restrictions.md)합니다.  
  
 합니다 **HostProtectionAttribute** 아닙니다 보안 권한이 형식 또는 메서드를 특정 코드 식별 한다는 점에서 안정성 향상을 위해 생성 하는 만큼의 호스트는 허용 되지 않을 수 있습니다. 사용 된 **HostProtectionAttribute** 호스트의 안정성을 보호 하는 프로그래밍 모델을 적용 합니다.  
  
## <a name="host-protection-attributes"></a>호스트 보호 특성  
 HPA는 호스트 프로그래밍 모델에 맞지 않고 다음과 같이 안정성 위협의 증가 수준을 나타내는 형식이나 멤버를 식별합니다.  
  
-   달리 유해하지 않습니다.  
  
-   서버에서 관리하는 사용자 코드가 불안정해질 수 있습니다.  
  
-   서버 프로세스 자체가 불안정해질 수 있습니다.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 형식 또는 멤버에는 사용할 수 없게 하는 **HostProtectionAttribute** 를 지정 하는 **System.Security.Permissions.HostProtectionResource** 열거형의 값을 사용 하 여  **ExternalProcessMgmt**, **ExternalThreading**를 **MayLeakOnAbort**하십시오 **SecurityInfrastructure**,  **SelfAffectingProcessMgmnt**, **SelfAffectingThreading**를 **: SharedState**를 **동기화**, 또는 **UI**. 이로 인해 상태를 공유할 수 있게 하거나, 동기화를 수행하거나, 종료할 때 리소스 누출을 일으키거나 또는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 프로세스의 무결성에 영향을 주는 멤버를 어셈블리가 호출할 수 없습니다.  
  
### <a name="disallowed-types-and-members"></a>허용되지 않는 형식 및 멤버  
 형식 및 멤버를 식별 하는 다음 항목은 해당 **HostProtectionResource** 값에서 허용 되지 않는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]합니다.  
  
> [!NOTE]  
>  이러한 항목에 있는 목록은 지원되는 어셈블리에서 생성되었습니다.  자세한 내용은 [Supported .NET Framework Libraries](../../relational-databases/clr-integration/database-objects/supported-net-framework-libraries.md)을 참조하세요.  
  
## <a name="in-this-section"></a>섹션 내용  
 [Microsoft.VisualBasic.dll에 허용되지 않는 형식 및 멤버](../../relational-databases/clr-integration-security-host-protection-attributes/disallowed-types-and-members-in-microsoft-visualbasic-dll.md)  
 HPA 값이 허용되지 않는 Microsoft.VisualBasic.dll의 유형 및 멤버가 나열되어 있습니다.  
  
 [mscorlib.dll에 허용되지 않는 형식 및 멤버](../../relational-databases/clr-integration-security-host-protection-attributes/disallowed-types-and-members-in-mscorlib-dll.md)  
 HPA 값이 허용되지 않는 mscorlib.dll의 유형 및 멤버를 표시합니다.  
  
 [System.dll에 허용되지 않는 형식 및 멤버](../../relational-databases/clr-integration-security-host-protection-attributes/disallowed-types-and-members-in-system-dll.md)  
 HPA 값이 허용되지 않는 System.dll의 유형 및 멤버를 표시합니다.  
  
 [System.Data.dll에 허용되지 않는 형식 및 멤버](../../relational-databases/clr-integration-security-host-protection-attributes/disallowed-types-and-members-in-system-data-dll.md)  
 HPA 값이 허용되지 않는 System.Data.dll의 유형 및 멤버를 표시합니다.  
  
 [System.Core.dll에 허용되지 않는 형식 및 멤버](../../relational-databases/clr-integration-security-host-protection-attributes/disallowed-types-and-members-in-system-core-dll.md)  
 HPA 값이 허용되지 않는 System.Core.dll의 유형 및 멤버를 표시합니다.  
  
## <a name="see-also"></a>관련 항목  
 [CLR 통합 코드 액세스 보안](../../relational-databases/clr-integration/security/clr-integration-code-access-security.md)   
 [CLR 통합 프로그래밍 모델 제한 사항](../../relational-databases/clr-integration/database-objects/clr-integration-programming-model-restrictions.md)   
 [어셈블리 만들기](../../relational-databases/clr-integration/assemblies/creating-an-assembly.md)  
  
  
