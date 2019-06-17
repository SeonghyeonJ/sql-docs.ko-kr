---
title: MSSQLSERVER_9790 | Microsoft 문서
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 9790 (Database Engine error)
ms.assetid: 83fd379f-5deb-4f97-8cb4-282e3d3fed94
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: dd965940d43fdcc1e2420e8c5a43e512b45298e2
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63014973"
---
# <a name="mssqlserver9790"></a>MSSQLSERVER_9790
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>세부 정보  
  
|||  
|-|-|  
|제품 이름|SQL Server|  
|이벤트 ID|9790|  
|이벤트 원본|MSSQLSERVER|  
|구성 요소|SQLEngine|  
|심볼 이름|SB3_XMIT_ERROR_ENTRANCE_BROKER_SINGLE_USER|  
|메시지 텍스트|들어오는 메시지를 라우팅할 수 없습니다. 라우팅 정보를 포함하는 시스템 데이터베이스 MSDB가 단일 사용자 모드입니다.|  
  
## <a name="explanation"></a>설명  
MSDB 데이터베이스가 단일 사용자 모드에 있었기 때문에 네트워크를 통해 수신한 메시지를 분류하려고 하는 동안 오류가 발생했습니다.  
  
## <a name="user-action"></a>사용자 동작  
ALTER DATABASE 명령을 사용하여 MSDB를 다중 사용자 모드로 변경합니다.  
  
