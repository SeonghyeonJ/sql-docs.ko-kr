---
title: 배포자 속성, 게시자 | Microsoft 문서
ms.custom: ''
ms.date: 06/30/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.configdistwizard.distproperties.publishers.f1
helpviewer_keywords:
- Distributor Properties dialog box
ms.assetid: 31c81898-11ca-4d2f-afea-2fbc71e19ce4
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 9ee329a923bf0b3c3c08b23fb6071a773dc16400
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/03/2018
ms.locfileid: "52816445"
---
# <a name="distributor-properties-publishers"></a>배포자 속성, 게시자
  **배포자 속성** 대화 상자의 **게시자** 페이지를 사용하여 게시자가 이 배포자를 사용하도록 허용할 수 있습니다. 해당 게시자와 연결된 속성을 설정할 수도 있습니다. 현재 서버를 원격 배포자로 사용하도록 게시자를 설정해도 해당 서버가 게시자가 되지는 않습니다. 게시자에 연결하여 이를 게시자로 구성하고, 이 서버를 배포자로 선택해야 합니다. 새 게시 마법사를 통해 게시자를 구성하고 배포자를 선택할 수 있습니다.  
  
## <a name="options"></a>변수  
 **게시자**  
 이 배포자를 사용하도록 허용할 서버를 선택합니다. 게시자 옆의 속성 단추 ( **...** )를 클릭하여 추가 속성을 보고 설정할 수 있습니다.  
  
 **추가**  
 허용할 서버가 나열되지 않으면 **추가** 를 클릭하여 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 게시자 또는 Oracle 게시자를 사용 가능한 게시자 목록에 추가합니다. 추가한 서버가 이 배포자를 원격 배포자로 사용하는 첫 번째 서버이면 관리 연결 암호를 입력하라는 메시지가 표시됩니다.  
  
 **관리 연결 암호**  
 복제에서 **distributor_admin** 로그인을 사용하여 게시자와 원격 배포자 간에 구성하는 연결의 암호를 지정하거나 업데이트하려면 사용합니다.  
  
-   배포자가 로컬 배포자로만 사용되는 경우 이 암호는 임의로 생성되고 자동으로 구성됩니다.  
  
-   배포자에 원격 게시자가 있으면 이 페이지 또는 배포 구성 마법사의 **배포자 암호** 페이지에서 암호를 이미 입력한 것입니다.  
  
-   이 배포자에 대해 원격 게시자를 처음으로 설정하는 경우 암호를 입력하라는 메시지가 표시됩니다.  
  
 배포자 보안에 자세한 내용은 [배포자 보안 설정](security/secure-the-distributor.md)을 참조하세요.  
  
## <a name="see-also"></a>관련 항목:  
 [배포 구성](configure-distribution.md)   
 [게시 및 배포 구성](configure-publishing-and-distribution.md)   
 [Create a Publication](publish/create-a-publication.md)   
 [배포자 및 게시자 속성 보기 및 수정](view-and-modify-distributor-and-publisher-properties.md)  
  
  
