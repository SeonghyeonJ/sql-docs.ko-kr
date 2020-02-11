---
title: 도메인 컨트롤러에서 SQL Server 2008로 업그레이드 하기 위한 서비스 계정 요구 사항 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- domain controllers
- service accounts
- network service accounts
- local service accounts
ms.assetid: 574245b6-11e2-4849-b0ca-836d673ecd0d
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: bb703e42edcbf128ff78ca294e08fc487f06d8f8
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66092263"
---
# <a name="service-account-requirements-for-upgrading-to-sql-server-2008-on-a-domain-controller"></a>도메인 컨트롤러에서 SQL Server 2008로 업그레이드하기 위한 서비스 계정 요구 사항
  업그레이드 관리자가 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)] 도메인 컨트롤러의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 네트워크 서비스 또는 로컬 서비스 계정에서 실행 중인 인스턴스를 검색 했습니다. 
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 도메인 컨트롤러에 [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)]가 설치되어 있으면 로컬 서비스 계정 또는 네트워크 서비스 계정 권한으로 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 서비스를 실행할 수 없습니다.  
  
## <a name="component"></a>구성 요소  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a>수정 동작  
 모든 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 서비스 계정을 도메인 계정이나 로컬 시스템 계정에 할당합니다. 업그레이드하기 전에 이러한 변경 작업을 수행하지 못하면 설치가 차단됩니다. 서비스 계정 SQL 기록기 및 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Active Directory Helper Service는 네트워크 서비스 계정으로 하드 코딩되어 변경할 수 없으므로 예외입니다.  
  
## <a name="see-also"></a>참고 항목  
 [업그레이드 문제 데이터베이스 엔진](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [SQL Server 2014 업그레이드 관리자 &#91;새&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
