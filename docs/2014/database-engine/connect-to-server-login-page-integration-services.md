---
title: 서버에 연결(로그인 페이지) Integration Services | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.connecttodtsserver.login.f1
- sql12.swb.connecttodts.login.f1
ms.assetid: 402c2de4-f4ea-40b0-909f-3ddf3bd59950
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 53a9793fc2a8770c8d926c945ba31a335bdfed3f
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/26/2020
ms.locfileid: "62808734"
---
# <a name="connect-to-server-login-page-integration-services"></a>서버에 연결(로그인 페이지) Integration Services
  에 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]연결할 때이 탭을 사용 하 여 다음 옵션을 확인 하거나 지정할 수 있습니다.  
  
## <a name="options"></a>옵션  
 **서버 유형**  
 개체 탐색기에서 서버를 등록할 때 연결할 서버 유형을 [!INCLUDE[ssDE](../includes/ssde-md.md)], Analysis Services, Reporting Services 또는 Integration Services 중에서 선택합니다. 대화 상자의 나머지 부분에는 선택한 서버 유형에 적용되는 옵션만 표시됩니다. 등록된 서버에서 서버를 등록하는 경우 **서버 유형** 상자는 읽기 전용이며 등록된 서버 구성 요소에 표시된 서버 유형과 일치합니다. 다른 유형의 서버를 등록하려면 새 서버를 등록하기 전에 등록된 서버 도구 모음에서 [!INCLUDE[ssDE](../includes/ssde-md.md)], Analysis Services, Reporting Services 또는 Integration Services를 선택합니다.  
  
 **서버 이름**  
 연결할 서버를 선택합니다. 마지막으로 연결한 서버 인스턴스가 기본적으로 표시됩니다.  
  
> [!NOTE]  
>  는 컴퓨터에서 여러 인스턴스를 지원 하지 않으므로 * \<servername>* \\ * \<instancename>* 를 사용 하지 마십시오. [!INCLUDE[ssIS](../includes/ssis-md.md)]  
  
 **인증**  
 [!INCLUDE[msCoName](../includes/msconame-md.md)] 에는 [!INCLUDE[ssIS](../includes/ssis-md.md)]Windows 인증만 사용할 수 있습니다. Windows 인증 모드에서는 사용자가 Windows 사용자 계정을 통해 연결할 수 있습니다.  
  
 **사용자 이름**  
 [!INCLUDE[ssIS](../includes/ssis-md.md)]에는 Windows 인증만 사용 가능하므로 이 옵션은 사용할 수 없습니다.  
  
 **암호**  
 [!INCLUDE[ssIS](../includes/ssis-md.md)]에는 Windows 인증만 사용 가능하므로 이 옵션은 사용할 수 없습니다.  
  
 **암호 기억**  
 [!INCLUDE[ssIS](../includes/ssis-md.md)]에는 Windows 인증만 사용 가능하므로 이 옵션은 사용할 수 없습니다.  
  
 **연결**  
 위에서 선택한 서버에 연결합니다.  
  
 **옵션**  
 대화 상자를 변경하고 암호 저장과 같은 추가 서버 연결 옵션을 숨기려면 클릭합니다.  
  
  
