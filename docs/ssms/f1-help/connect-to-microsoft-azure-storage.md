---
title: Microsoft Azure Storage에 연결 | Microsoft 문서
ms.custom: ''
ms.date: 07/12/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql13.swb.windowsazurestorage.connect.f1
- SQL13.SWB.WINDOWSAZURESTORAGE.CONNECT.F1
ms.assetid: ''
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: cd9af00c06b2e999ec38d201e11fe305f7bb4e71
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/28/2018
ms.locfileid: "52523568"
---
# <a name="connect-to-microsoft-azure-storage"></a>Microsoft Azure Storage에 연결
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
**Windows Azure 저장소 연결** 대화 상자를 사용하여 저장소 계정을 지정하고 Windows Azure 연결의 유효성을 검사할 수 있습니다.  
  
## <a name="options"></a>Options  
Windows Azure 계정에 대해 다음 정보를 지정한 후 **다음** 을 클릭하여 계속합니다.  
  
1.  **저장소 계정** - 저장소 계정 이름을 지정합니다.

   >[!NOTE]
   > [범용 저장소 계정](https://docs.microsoft.com/azure/storage/storage-introduction#introducing-the-azure-storage-services)에만 연결할 수 있습니다. 다른 유형의 스토리지 계정에 연결하면 다음과 유사한 오류 메시지가 발생할 수 있습니다.
   >
   >  HTTP 헤더 중 하나에 대한 값 형식이 올바르지 않습니다. (Microsoft.SqlServer.StorageClient).
   >
   >  원격 서버에서 오류를 반환했습니다. (400) 잘못된 요청. (System)

2.  **계정 키** - 지정한 저장소 계정의 계정 키를 지정합니다.  
  
3.  **보안 엔드포인트 사용(HTTPS)** – 이 옵션은 암호화된 통신 및 네트워크 웹 서버의 보안 ID를 사용합니다.  
  
4.  **계정 키 저장** - 이 옵션은 암호화된 파일에 암호를 저장합니다.  
  
