---
title: 다른 컴퓨터에 연결(SQL Server 구성 관리자) | Microsoft Docs
description: 원격 컴퓨터의 서비스를 관리하는 방법을 알아봅니다. 이 태스크에 SQL Server 구성 관리자 또는 SQL Server Management Studio를 사용하는 방법을 알아봅니다.
ms.custom: ''
ms.date: 11/19/2019
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- connections [SQL Server], other computers
ms.assetid: c4c1e94f-4f5f-431e-8b5b-d5ff97baf723
author: markingmyname
ms.author: maghan
ms.openlocfilehash: e4a2ca1eea0ec4b42bba65b62525bb6d86e52c88
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85651343"
---
# <a name="scm-services---connect-to-another-computer"></a>SCM 서비스 - 다른 컴퓨터에 연결

 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

이 문서에서는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]에서 다른 컴퓨터에 연결하는 방법에 대해 설명합니다. 첫 번째 절차에 따라 Windows 컴퓨터 관리 MMC( [!INCLUDE[msCoName](../../includes/msconame-md.md)] Management Console)를 열고 해당 컴퓨터에 연결한 다음 서비스 및 애플리케이션 트리를 확장합니다. 두 번째 절차에 따라 원격 컴퓨터의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 구성 관리자에 대한 링크가 있는 파일을 만듭니다.

> [!NOTE]
> 일부 작업은 원격으로 연결할 때 구성 관리를 통해 수행할 수 없습니다.

다른 컴퓨터의 서비스를 시작, 중지, 일시 중지 또는 재개하기 위해 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]를 사용하여 서버에 연결하고 해당 서버 또는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트를 마우스 오른쪽 단추로 클릭한 다음 원하는 동작을 클릭할 수도 있습니다.

## <a name="SSMSProcedure"></a>

### <a name="to-connect-to-another-computer-with-windows-computer-management"></a>Windows 컴퓨터 관리에서 다른 컴퓨터에 연결하려면

1. **시작** 메뉴 단추를 마우스 오른쪽 단추로 클릭한 다음에 **컴퓨터 관리(로컬)** 를 클릭합니다.
2. **작업** 메뉴에서 **다른 컴퓨터에 연결**을 클릭합니다.
3. **컴퓨터 선택** 대화 상자의 **다른 컴퓨터** 입력란에 관리할 컴퓨터의 이름을 입력하고 **확인**을 클릭합니다.

   원격 컴퓨터에서 실행 중인 서비스가 컴퓨터 관리에 표시됩니다. 최상위 노드가 **컴퓨터 관리** \<*remotecomputer*>로 변경됩니다.

4. 콘솔 트리에서 **서비스 및 애플리케이션**을 확장한 다음 **SQL Server 구성 관리자** 를 확장하여 원격 컴퓨터의 서비스를 관리합니다.

### <a name="to-save-a-link-to-sql-server-configuration-manager-for-another-computer"></a>다른 컴퓨터의 SQL Server 구성 관리자에 대한 링크를 저장하려면

1. **시작** 메뉴에서 **실행**을 클릭합니다.

2. **열기** 상자에 **mmc -a**(64비트 컴퓨터의 경우 **mmc /32 -a**)를 입력하여 작성자 모드에서 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 관리 콘솔을 엽니다.
3. **파일** 메뉴에서 **스냅인 추가/제거**를 클릭합니다.
4. **스냅인 추가/제거** 창에서 **추가**를 클릭합니다.
5. **독립 실행형 스냅인 추가** 창에서 **컴퓨터 관리** 를 클릭한 다음 **추가**를 클릭합니다.
6. **컴퓨터 관리** 창에서 **다른 컴퓨터**를 클릭하고 관리할 원격 컴퓨터의 이름을 입력한 다음 **마침**을 클릭합니다.
7. **독립 실행형 스냅인 추가** 창에서 **닫기**를 클릭합니다.
8. **스냅인 추가/제거** 창에서 **확인**을 클릭합니다.
9. **컴퓨터 관리**( _\<computer name>_ **)** 와 **서비스 및 애플리케이션**을 확장합니다.
10. **SQL Server 구성 관리자**를 마우스 오른쪽 단추로 클릭한 다음 **여기에서 창 새로 만들기**를 클릭합니다.
11. **창** 메뉴에서 **콘솔 루트**를 클릭하여 첫 번째 창으로 전환한 다음, 창을 삭제합니다.
12. **파일** 메뉴에서 **다른 이름으로 저장**을 클릭한 다음 **.msc** 파일 확장명을 가진 적절한 이름을 지정하여 파일을 원하는 폴더에 저장합니다. [!INCLUDE[msCoName](../../includes/msconame-md.md)] Management Console을 닫습니다.
13. 대상 컴퓨터에서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 구성 관리자를 열려면 파일을 두 번 클릭합니다. 필요한 경우 파일에 대한 링크를 바탕 화면이나 **시작** 메뉴에 저장합니다.

> [!CAUTION]
> 원격 컴퓨터의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 구성 관리자를 사용하는 경우 컴퓨터 이름이 명확하지 않아 실수로 다른 컴퓨터를 중지하거나 구성할 수 있습니다. **서비스** 탭에서 **호스트 이름** 상자를 선택하여 서비스를 수정하기 전에 컴퓨터 이름을 확인합니다.

## <a name="see-also"></a>참고 항목

- [WMI를 구성하여 SQL Server 도구에 서버 상태 표시](../../ssms/configure-wmi-to-show-server-status-in-sql-server-tools.md)
