---
title: Windows에 연결할 Azure Storage (복원) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
f1_keywords:
- sql12.swb.restore.connectstorage.f1
ms.assetid: c0b7d7c8-b878-4b7f-8120-d0c6917b583f
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 506f074a8693e54bdc51882ab08b19e9ea3e1994
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/28/2018
ms.locfileid: "52517867"
---
# <a name="connect-to-windows-azure-storage-restore"></a>Microsoft Azure Storage에 연결(복원)
  대화 상자를 사용하면 Windows Azure 저장소 계정에서 파일 저장소를 검색하기 위해 Windows Azure 저장소 계정 정보에 대한 연결을 지정할 수 있습니다. 필요한 정보를 지정한 후 **연결** 을 클릭하여 Windows Azure Storage에 대한 연결을 설정합니다.  
  
## <a name="windows-azure-storage-account"></a>Windows Azure Storage 계정  
 **저장소 계정**  
 사용할 Windows Azure Storage 계정 이름을 선택, 입력 또는 붙여 넣습니다. 드롭다운 상자에 이전에 사용한 계정이 나열됩니다.  
  
 **계정 키**  
 Windows Azure Storage 계정 액세스 키를 지정합니다.  
  
 **보안 엔드포인트 사용(HTTPS)** 확인란  
 Windows Azure 스토리지에 대한 보안 연결을 설정하려면 이 옵션을 선택합니다(권장 사항).  
  
 **계정 키 저장** 확인란  
 SQL Server에서 이 저장소 계정에 대한 액세스 키를 기억하도록 설정하려면 이 확인란을 선택합니다.  
  
### <a name="sql-credential"></a>SQL 자격 증명  
 **기존 자격 증명 선택**  
 저장소 계정 및 계정 키 정보와 일치하는 기존 SQL 자격 증명을 선택합니다.  
  
 **새 자격 증명 만들기**  
 저장소 계정 및 계정 키 정보를 사용하여 새 자격 증명을 만들려면 이 옵션을 선택합니다. **자격 증명 이름** 필드에서 새 자격 증명 이름을 지정합니다.  
  
  
