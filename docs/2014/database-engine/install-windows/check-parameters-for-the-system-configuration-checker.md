---
title: 시스템 구성 검사기의 검사 매개 변수 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
helpviewer_keywords:
- installing SQL Server, system configuration checks
- failed system configuration checks [SQL Server]
- verifying configuration before installation
- SCC [SQL Server]
- system configuration checker
- scanning computer before installation [SQL Server]
- checking configuration before installation
- status information [SQL Server], system configuration checker
- parameters [SQL Server], system configuration checker
- configuration checkers [SQL Server]
- Setup [SQL Server], system configuration checker
ms.assetid: 8e712c15-6bfa-4d71-b303-9526101e5594
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 2a1d08730c8fd4ec5a750c0cf2c70e0498be602e
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/26/2020
ms.locfileid: "62779446"
---
# <a name="check-parameters-for-the-system-configuration-checker"></a>시스템 구성 검사기의 검사 매개 변수
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 설치 중에 SCC(시스템 구성 검사기)는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 를 설치할 컴퓨터를 검색합니다. SCC는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 의 성공적인 설치를 방해하는 조건이 있는지 확인합니다. 설치 프로그램이 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 설치 마법사를 시작하기 전에 SCC는 각 항목의 상태를 검색합니다. 그런 다음 검색 결과를 필수 조건과 비교하고 차단 문제 해결을 위한 지침을 제공합니다.  
  
 시스템 구성 검사기에서는 각 실행 규칙에 대한 간단한 설명과 실행 상태를 포함하는 보고서를 생성합니다. 시스템 구성 검사 보고서 는%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]programfiles% \120\Setup Bootstrap\Log\\<YYYYMMDD_HHMM>\\에 있습니다.  
  
## <a name="see-also"></a>참고 항목  
 [SQL Server 2014를 설치 하기 위한 하드웨어 및 소프트웨어 요구 사항](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md)   
 [SQL Server 설치에 대 한 보안 고려 사항](../../sql-server/install/security-considerations-for-a-sql-server-installation.md)   
 [지원되는 버전 및 에디션 업그레이드](supported-version-and-edition-upgrades.md)  
  
  
