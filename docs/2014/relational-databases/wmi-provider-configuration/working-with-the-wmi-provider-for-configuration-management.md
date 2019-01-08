---
title: 구성 관리용 WMI 공급자를 사용 하 여 작업 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
helpviewer_keywords:
- permissions [WMI]
- connection strings [WMI]
- security [WMI]
- WMI Provider for Configuration Management, connection strings
- WMI Provider for Configuration Management, security
- late binding [WMI]
- WMI Provider for Configuration Management, late binding
- binding [WMI]
ms.assetid: 34daa922-7074-41d0-9077-042bb18c222a
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 9d9f3ab9f80c6f2c77153439cf554f0ae8598586
ms.sourcegitcommit: 334cae1925fa5ac6c140e0b2c38c844c477e3ffb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/13/2018
ms.locfileid: "53351790"
---
# <a name="working-with-the-wmi-provider-for-configuration-management"></a>구성 관리용 WMI 공급자 작업
  컴퓨터 관리용 WMI 공급자를 사용하여 프로그래밍하기 전에 다음을 고려합니다.  
  
## <a name="binding"></a>바인딩  
 구성 관리용 WMI 공급자는 COM 개체 모델이며 초기 바인딩과 런타임에 바인딩을 지원합니다. 런타임에 바인딩의 경우 VBScript와 같은 스크립트 언어를 사용하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 서비스, 네트워크 설정 및 별칭을 프로그래밍 방식으로 조작할 수 있습니다.  
  
 스크립팅 언어를 사용 하 여 WMI 공급자 구현을 프로그래밍 하는 방법에 대 한 자세한 내용은 참조는 [!INCLUDE[msCoName](../../includes/msconame-md.md)] MSDN [웹 사이트](https://go.microsoft.com/fwlink/?linkid=15426)합니다.  
  
## <a name="specifying-a-connection-string"></a>연결 문자열 지정  
 응용 프로그램은 공급자가 정의한 WMI 네임스페이스에 연결하여 구성 관리용 WMI 공급자를 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스로 보냅니다. Windows WMI 서비스는 이 네임스페이스를 공급자 DLL에 매핑하여 메모리에 로드합니다. 모든 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스는 단일 WMI 네임스페이스로 나타냅니다. 기본 네임스페이스는 다음과 같습니다.  
  
```  
\\.\root\Microsoft\SqlServer\ComputerManagement12\instance_name  
```  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 기본 설치에서 `instance_name`의 기본값은 `MSSQLSERVER`입니다.  
  
 **참고:** Windows 방화벽을 통해 연결하는 경우 컴퓨터가 올바르게 구성되었는지 확인해야 합니다. Windows Management Instrumentation 설명서에서 "Connecting Through Windows Firewall" 문서를 참조 하세요 [!INCLUDE[msCoName](../../includes/msconame-md.md)] MSDN [웹 사이트](https://go.microsoft.com/fwlink/?linkid=15426)합니다.  
  
## <a name="permissions-and-server-authentication"></a>권한과 서버 인증  
 구성 관리용 WMI 공급자에 액세스하려면 클라이언트 WMI 관리 스크립트가 대상 컴퓨터에서 관리자 컨텍스트로 실행되고 있어야 합니다. 관리할 컴퓨터에서 로컬 Windows Administrators 그룹의 멤버여야 합니다.  
  
 관리자는 그룹 정책을 설정하여 WMI 공급자에 대한 사용자 액세스를 제어할 수 있습니다. 그룹 정책 설정에 대한 자세한 내용은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 구성 관리자 도움말의 "그룹 정책 및 MMC"를 참조하십시오.  
  
 WMI 관리 스크립트를 사용하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 서비스가 실행되는 계정을 업데이트할 수 있습니다.  
  
 구성 관리용 WMI 공급자는 보안 인증서를 지원합니다. 인증서에 대 한 자세한 내용은 참조 하세요. [암호화 계층](../security/encryption/encryption-hierarchy.md)합니다.  
  
## <a name="see-also"></a>관련 항목  
 [SQL Server 구성 관리자](../sql-server-configuration-manager.md)  
  
  
