---
title: 구독자 유형 | Microsoft 문서
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql13.rep.newpubwizard.subscribertypes.f1
ms.assetid: a70656cb-21c9-4489-be77-ccd396747e3b
author: MashaMSFT
ms.author: mathoma
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: c84391d24a25ae8c7fdd8f6d3b6ec38736300255
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68129904"
---
# <a name="subscriber-types"></a>구독자 유형
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  병합 복제를 사용하여 게시가 지원해야 하는 구독자 유형을 지정할 수 있습니다. 구독자 유형을 선택하면 게시에서 사용할 수 있는 기능을 결정하는 *게시 호환성 수준*이 설정됩니다.  
  
 게시 스냅샷을 만든 후 **게시 속성** 대화 상자의 **일반** 페이지에서 게시 호환성 수준을 높여 제한을 강화할 수 있습니다. 호환성 수준은 낮출 수 없습니다.  
  
## <a name="options"></a>옵션  
 이 게시가 지원해야 하는 각 구독자 유형을 선택합니다.  
  
 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
 게시가 모든 기능을 사용할 수 있습니다.  
  
 [!INCLUDE[ssEW](../../includes/ssew-md.md)]  
 게시에서 사용하는 스냅샷 파일이 문자 형식이어야 합니다. 이는 스냅샷 에이전트에서 자동으로 처리됩니다. 또한[!INCLUDE[ssEW](../../includes/ssew-md.md)] 에는 호환성 수준과 관련되지 않은 제한 사항이 많이 있습니다.  
  
 이 옵션을 선택하면 게시에 웹 동기화 옵션을 사용할 수 있습니다. 웹 동기화에 대한 자세한 내용은 [Web Synchronization for Merge Replication](../../relational-databases/replication/web-synchronization-for-merge-replication.md)를 참조하십시오.  
  
## <a name="see-also"></a>참고 항목  
 [데이터 및 데이터베이스 개체 게시](../../relational-databases/replication/publish/publish-data-and-database-objects.md)   
 [Create a Publication](../../relational-databases/replication/publish/create-a-publication.md)   
 [배포자 및 게시자 속성 보기 및 수정](../../relational-databases/replication/view-and-modify-distributor-and-publisher-properties.md)   
  
  
