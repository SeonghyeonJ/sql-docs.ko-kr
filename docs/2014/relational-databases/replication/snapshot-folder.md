---
title: 스냅숏 폴더 | Microsoft 문서
ms.custom: ''
ms.date: 06/30/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.replicationutilities.specifysnapshotfolder.f1
ms.assetid: 3eb1b73f-ddb3-4d09-be6e-811c414698e9
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 4346b7752c9d4ace22a50cb1b4768c0c7d5df1fc
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/03/2018
ms.locfileid: "52767773"
---
# <a name="snapshot-folder"></a>스냅숏 폴더
  **스냅숏 폴더** 페이지는 배포 구성 마법사 및 새 게시 마법사에 나타납니다. 지정하는 스냅숏 폴더 위치는 이 마법사에서 설정하는 모든 게시자의 기본값으로 사용됩니다. 기본 스냅숏 폴더는 나중에 **배포자 속성** 대화 상자를 사용하여 설정하는 게시자에는 적용되지 않습니다. 배포 구성 마법사 또는 **배포자 속성** 대화 상자의 **게시자** 페이지에서 임의의 게시자에 대해 이 기본값을 무시할 수 있습니다.  
  
 스냅숏 폴더는 공유하도록 지정된 디렉터리일 뿐이며 이 폴더에 읽기/쓰기 작업을 수행하려면 에이전트에게 충분한 액세스 권한이 있어야 합니다. 폴더의 적절한 보안 유지 방법에 대한 자세한 내용은 [스냅숏 폴더 보안 설정](security/secure-the-snapshot-folder.md)을 참조하세요. 복제를 구현하기 전에 복제 에이전트에서 스냅숏 폴더에 연결할 수 있는지 테스트합니다. 각 에이전트에서 사용할 계정으로 로그온한 다음 스냅숏 폴더에 액세스해 봅니다.  
  
## <a name="options"></a>변수  
 **Snapshot folder**  
 스냅숏 파일을 저장할 폴더의 경로를 입력합니다.  
  
> [!NOTE]  
>  [!INCLUDE[msCoName](../../includes/msconame-md.md)] 은(는) 네트워크 공유를 스냅숏 폴더 위치로 사용하는 것을 권장합니다. 다른 컴퓨터의 에이전트는 로컬 경로(C:\\와 같이 드라이브 문자로 시작하는 경로)에 액세스할 수 없습니다.  
  
## <a name="see-also"></a>관련 항목:  
 [대체 스냅숏 폴더 위치](alternate-snapshot-folder-locations.md)   
 [배포 구성](configure-distribution.md)   
 [게시 및 배포 구성](configure-publishing-and-distribution.md)   
 [배포자 및 게시자 속성 보기 및 수정](view-and-modify-distributor-and-publisher-properties.md)   
 [스냅숏으로 구독 초기화](initialize-a-subscription-with-a-snapshot.md)  
  
  
