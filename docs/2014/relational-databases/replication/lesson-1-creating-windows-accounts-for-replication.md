---
title: '1단원: 복제용 Windows 계정 만들기 | Microsoft 문서'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- replication [SQL Server], tutorials
- replication [SQL Server], administering
ms.assetid: 65c3816b-47f0-448c-a4a4-ebd3e2a58820
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: f11321b20c4238fdf9b3376d79edcb12c0e9204b
ms.sourcegitcommit: 4b5919e3ae5e252f8d6422e8e6fddac1319075a1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/09/2020
ms.locfileid: "83000473"
---
# <a name="lesson-1-creating-windows-accounts-for-replication"></a>1단원: 복제용 Windows 계정 만들기
  이 단원에서는 복제 에이전트를 실행할 Windows 계정을 만들며 다음 에이전트에 대해 로컬 서버에 별도의 Windows 계정을 만듭니다.  
  
|에이전트|위치|계정 이름|  
|-----------|--------------|------------------|  
|스냅샷 에이전트|Publisher|\<*machine_name*> \ repl_snapshot|  
|로그 판독기 에이전트|Publisher|\<*machine_name*> \ repl_logreader|  
|배포 에이전트|게시자 및 구독자|\<*machine_name*> \ repl_distribution|  
|병합 에이전트|게시자 및 구독자|\<*machine_name*> \ repl_merge|  
  
> [!NOTE]  
>  복제 자습서에서는 게시자 및 배포자가 같은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]인스턴스를 공유합니다. 게시자와 구독자는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]의 같은 인스턴스를 공유할 수 있지만 반드시 이렇게 해야 하는 것은 아닙니다. 게시자와 구독자가 같은 인스턴스를 공유하는 경우 구독자에서는 계정을 만드는 단계를 수행하지 않아도 됩니다.  
  
### <a name="to-create-local-windows-accounts-for-replication-agents-at-the-publisher"></a>게시자에서 복제 에이전트에 대한 로컬 Windows 계정을 만들려면  
  
1.  게시자에서 제어판의 **관리 도구**에 있는 **컴퓨터 관리**를 엽니다.  
  
2.  **시스템 도구**에서 **로컬 사용자 및 그룹**을 확장합니다.  
  
3.  **사용자** 를 마우스 오른쪽 단추로 클릭 한 다음 **새 사용자**를 클릭 합니다.  
  
4.  `repl_snapshot` **사용자 이름** 상자에를 입력 하 고 암호 및 기타 관련 정보를 입력 한 다음 **만들기** 를 클릭 하 여 repl_snapshot 계정을 만듭니다.  
  
5.  이전 단계를 반복하여 repl_logreader, repl_distribution 및 repl_merge 계정을 만듭니다.  
  
6.  **닫기**를 클릭합니다.  
  
### <a name="to-create-local-windows-accounts-for-replication-agents-at-the-subscriber"></a>구독자에서 복제 에이전트에 대한 로컬 Windows 계정을 만들려면  
  
1.  구독자에서 제어판의 **관리 도구**에 있는 **컴퓨터 관리**를 엽니다.  
  
2.  **시스템 도구**에서 **로컬 사용자 및 그룹**을 확장합니다.  
  
3.  **사용자** 를 마우스 오른쪽 단추로 클릭 한 다음 **새 사용자**를 클릭 합니다.  
  
4.  `repl_distribution` **사용자 이름** 상자에를 입력 하 고 암호 및 기타 관련 정보를 입력 한 다음 **만들기** 를 클릭 하 여 repl_distribution 계정을 만듭니다.  
  
5.  이전 단계를 반복하여 repl_merge 계정을 만듭니다.  
  
6.  **닫기**를 클릭합니다.  
  
## <a name="next-steps"></a>다음 단계  
 복제 에이전트에 대한 Windows 계정을 성공적으로 만들었습니다. 다음 단원에서는 스냅샷 폴더를 구성합니다. [2단원: 스냅샷 폴더 준비](lesson-2-preparing-the-snapshot-folder.md)를 참조하세요.  
  
## <a name="see-also"></a>참고 항목  
 [복제 에이전트 개요](agents/replication-agents-overview.md)  
  
  
