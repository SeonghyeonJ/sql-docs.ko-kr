---
description: 구독 다시 초기화 - 모든 구독
title: 구독 다시 초기화 - 모든 구독 | Microsoft 문서
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql13.rep.reinit.all.f1
helpviewer_keywords:
- Reinitialize Subscription(s) dialog box
ms.assetid: e1122018-9f74-43e3-8489-7eae33ff23d9
author: MashaMSFT
ms.author: mathoma
monikerRange: =azuresqldb-mi-current||>=sql-server-2016||=sqlallproducts-allversions
ms.openlocfilehash: cee027fbc0e614e7aa6bbc14292b79141a9b4df1
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88405539"
---
# <a name="reinitialize-subscriptions---all-subscriptions"></a>구독 다시 초기화 - 모든 구독
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]
  **구독 다시 초기화** 대화 상자를 사용하여 게시에 대한 모든 구독을 다시 초기화로 표시할 수 있습니다. 다시 초기화를 수행하려면 각 구독자에 스냅샷을 적용해야 하며 이 작업은 트랜잭션 게시에 대한 구독을 위한 배포 에이전트 및 병합 게시에 대한 구독을 위한 병합 에이전트에서 수행합니다.  
  
## <a name="options"></a>옵션  
 **현재 스냅샷 사용**  
 다음에 배포 에이전트 또는 병합 에이전트가 구독에 대해 실행될 때 현재 스냅샷을 각 구독자에 적용하려면 선택합니다. 유효한 스냅샷이 없으면 이 옵션을 선택할 수 없습니다.  
  
 **새 스냅샷 사용**  
 새 스냅샷으로 모든 구독을 다시 초기화하려면 선택합니다. 스냅샷 에이전트에 의해 스냅샷이 생성된 후에만 스냅샷을 각 구독자에 적용할 수 있습니다. 스냅샷 에이전트가 예약 실행되도록 설정한 경우에는 일정에 따라 다음에 스냅샷 에이전트가 실행될 때까지 구독이 다시 초기화되지 않습니다.  
  
 스냅샷 에이전트를 바로 시작하려면 **지금 새 스냅샷 생성** 을 선택합니다.  
  
 **다시 초기화하기 전에 동기화되지 않은 변경 내용 업로드**  
 병합 복제에 대해서만 사용할 수 있습니다. 구독자의 데이터를 스냅샷으로 덮어쓰기 전에 보류 중인 구독 데이터베이스의 변경 내용을 업로드하려면 선택합니다.  
  
 매개 변수가 있는 필터를 추가, 삭제 또는 변경할 경우 다시 초기화를 진행하는 동안에는 보류 중인 구독자의 변경 내용을 게시자로 업로드할 수 없습니다. 보류 중인 변경 내용을 업로드하려면 필터를 변경하기 전에 모든 구독을 동기화하세요.  
  
 **다시 초기화 표시**  
 각 구독을 다시 초기화로 표시하려면 클릭합니다. 유효한 스냅샷을 사용할 수 있으면 다음에 배포 에이전트 또는 병합 에이전트가 해당 구독에 대해 실행될 때 이 스냅샷이 구독자에 적용됩니다.  
  
## <a name="see-also"></a>참고 항목  
 [구독 다시 초기화](../../relational-databases/replication/reinitialize-subscriptions.md)  
  
  
