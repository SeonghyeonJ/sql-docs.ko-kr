---
title: 웹 동기화를 위한 토폴로지 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- Web synchronization, topologies
- IIS server configuration [SQL Server replication]
ms.assetid: 59444faf-bcb6-4421-a3df-8715753e453b
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 62fd4cd78beaeff479fc7cc9ec3abbd79e227e04
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2020
ms.locfileid: "63273544"
---
# <a name="topologies-for-web-synchronization"></a>Topologies for Web Synchronization
  다양 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 한 웹 동기화 복제 토폴로지에서 선택할 수 있습니다. 웹 동기화를 구성하는 일반적인 방법은 다음과 같습니다.  
  
-   단일 서버  
  
-   두 대의 서버  
  
-   여러 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 인터넷 정보 서비스(IIS) 시스템 및 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 재게시  
  
 웹 동기화를 구성하는 방법은 [웹 동기화 구성](configure-web-synchronization.md)을 참조하세요.  
  
## <a name="single-server"></a>단일 서버  
 가장 간단한 토폴로지에서 IIS, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 게시자 및 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 배포자는 모두 단일 서버에 상주합니다. 구독자는 게시자의 IIS에 연결하여 동기화합니다. 게시자는 방화벽 뒤에 있습니다.  
  
> [!NOTE]  
>  이 구성은 인트라넷 시나리오에만 사용하는 것이 좋습니다. 다른 시나리오에서는 IIS 서버와 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 게시자/배포자를 별도의 컴퓨터에 두는 것이 좋습니다.  
  
 ![단일 서버를 사용한 웹 동기화](media/web-sync02.gif "단일 서버를 사용한 웹 동기화")  
  
## <a name="two-servers"></a>두 대의 서버  
 한 서버에는 IIS를 두고 다른 서버에는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 게시자와 배포자를 구성할 수 있습니다. IIS를 실행하는 서버는 방화벽에 의해 인터넷에서 격리될 수 있습니다. 구독자는 IIS에 연결하여 동기화합니다.  
  
 ![2대의 서버를 사용한 웹 동기화](media/web-sync03.gif "2대의 서버를 사용한 웹 동기화")  
  
## <a name="multiple-iis-systems-and-sql-server-republishing"></a>여러 IIS 시스템 및 SQL Server 재게시  
 동시에 동기화하는 많은 수의 구독자를 지원해야 하는 경우 IIS를 실행하는 여러 개의 컴퓨터에 작업을 분할할 수 있습니다.  
  
 ![여러 대의 IIS 서버를 사용한 웹 동기화](media/web-sync04.gif "여러 대의 IIS 서버를 사용한 웹 동기화")  
  
 
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]를 실행하는 컴퓨터에서 로드 균형 조정이 필요한 경우 여러 컴퓨터에 재게시 계층을 만들 수 있습니다. 최상위 게시자에서 데이터를 구독자에 게시하면 구독자에서는 데이터를 다시 게시하고 최상위 게시자에서는 구독자의 로드 균형 조정 요청을 게시합니다.  
  
> [!NOTE]  
>  구독자는 특정 게시자하고만 동기화될 수 있습니다. 예를 들어 재게시자 A의 구독자는 A를 사용할 수 없는 경우 재게시자 B와도 동기화될 수 없습니다.  
  
 ![다시 게시를 사용한 웹 동기화](media/web-sync05.gif "다시 게시를 사용한 웹 동기화")  
  
## <a name="see-also"></a>참고 항목  
 [웹 동기화 구성](configure-web-synchronization.md)   
 [병합 복제에 대한 웹 동기화](web-synchronization-for-merge-replication.md)  
  
  
