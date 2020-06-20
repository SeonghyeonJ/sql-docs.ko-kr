---
title: CLR 통합 보안 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- security [CLR integration]
- authorization [CLR integration]
- common language runtime [SQL Server], security
- database objects [CLR integration], security
ms.assetid: 05d7a471-c5d5-4730-b903-e4edc8157bb4
author: rothja
ms.author: jroth
ms.openlocfilehash: aeec8c832061756a818c9d2438df3046a29c1160
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84970583"
---
# <a name="clr-integration-security"></a>CLR 통합 보안
  [!INCLUDE[ssNoVersion](../../../includes/dnprdnshort-md.md)]Clr (공용 언어 런타임)의 보안 모델은 다른 형식의 clr 및 [!INCLUDE[ssNoVersion](../../../includes/tsql-md.md)] 서버에서 실행 되는 다른 clr 개체 또는 문 내에서 실행 되는 clr이 아닌 개체 간 액세스를 관리 하 고 보호 합니다. 개체 간의 호출을 링크라고 합니다. 이러한 개체에 대해 수행되는 보안 검사의 유형은 관련된 링크의 유형에 따라 다릅니다.  
  
 CLR 통합 보안 모델의 목표는 다음과 같습니다.  
  
-   기본적으로에서 관리 되는 사용자 코드를 실행 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 합니다. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]의 견고성을 손상할 수 있는 작업을 수행하려면 높은 수준의 사용 권한으로 보호해야 합니다.  
  
-   관리되는 사용자 코드에서 데이터베이스의 사용자 데이터나 다른 사용자 코드에 무단으로 액세스하지 못하도록 해야 합니다. 사용자 정의 코드는 해당 코드를 호출한 사용자 세션의 보안 컨텍스트에서 해당 보안 컨텍스트에 대한 올바른 권한을 사용하여 실행해야 합니다.  
  
-   사용자 코드를 로컬 데이터 액세스 및 계산용으로만 사용하여 사용자 코드에서 서버 외부의 리소스에 액세스하지 못하도록 제어해야 합니다.  
  
-   사용자 정의 코드가 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 프로세스에서 실행된다는 것 때문에 시스템 리소스에 무단으로 액세스할 수 있게 되면 안 됩니다.  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]CLR의 코드 액세스 기반 보안 모델을 사용 합니다. 이러한 통합된 보안 방법의 일부 이점에 대해 이 섹션에서 설명합니다.  
  
 다음 표에서는 이 섹션에서 다루는 항목을 나열합니다.  
  
 [CLR 통합 코드 액세스 보안](clr-integration-code-access-security.md)  
 관리 코드에 대한 CAS(코드 액세스 보안) 모델을 설명합니다.  
  
 [호스트 보호 특성 및 CLR 통합 프로그래밍](../../clr-integration-security-host-protection-attributes/host-protection-attributes-and-clr-integration-programming.md)  
 SAFE 및 EXTERNAL_ACCESS 어셈블리에서 허용되지 않는 HPA(호스트 보호 특성)에 대한 정보를 제공합니다.  
  
 [CLR 통합 보안의 링크](../../../database-engine/dev-guide/links-in-clr-integration-security.md)  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]에서 사용자 코드 조각이 상호 호출하는 방법을 설명합니다.  
  
 [가장 및 CLR 통합 보안](../../../database-engine/dev-guide/impersonation-and-clr-integration-security.md)  
 관리 코드에서 가장을 사용하여 외부 리소스에 액세스하는 방법을 설명합니다.  
  
 [부분적으로 신뢰할 수 있는 호출자 허용](../../../database-engine/dev-guide/allowing-partially-trusted-callers.md)  
 관리되는 메서드에서 다른 어셈블리에 포함된 클래스의 메서드를 호출할 때 발생하는 문제를 설명합니다.  
  
 [애플리케이션 도메인 및 CLR 통합 보안](../../../database-engine/dev-guide/application-domains-and-clr-integration-security.md)  
 애플리케이션 도메인에 어셈블리를 로드하는 방법에 대해 설명합니다.  
  
## <a name="see-also"></a>참고 항목  
 [CLR 통합 어셈블리 관리](../assemblies/managing-clr-integration-assemblies.md)  
  
  
