---
description: MSSQLSERVER_945
title: MSSQLSERVER_945 | Microsoft 문서
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 945 (Database Engine error)
ms.assetid: ee501d13-0bd9-4627-896c-ed5b1bdb88b3
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 2bd18aad57eed6596ff83fc5fddbb50d33cba49a
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88420897"
---
# <a name="mssqlserver_945"></a>MSSQLSERVER_945
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>세부 정보  
  
| attribute | 값 |  
| :-------- | :---- |  
|제품 이름|SQL Server|  
|이벤트 ID|945|  
|이벤트 원본|MSSQLSERVER|  
|구성 요소|SQLEngine|  
|심볼 이름|DB_IS_SHUTDOWN|  
|메시지 텍스트|파일에 액세스할 수 없거나 메모리 또는 디스크 공간이 부족하여 데이터베이스 '%.*ls'을(를) 열 수 없습니다.  자세한 내용은 SQL Server 오류 로그를 참조하십시오.|  
  
## <a name="explanation"></a>설명  
파일 또는 기타 리소스가 없어 데이터베이스에 액세스할 수 없습니다.  
  
## <a name="user-action"></a>사용자 동작  
메모리, 디스크 공간 또는 사용 권한 오류에 대한 자세한 내용은 오류 로그를 확인합니다. 영향을 받는 데이터베이스에 대한 .mdf 및 .ndf 파일의 위치를 확인하고 [!INCLUDE[ssDE](../../includes/ssde-md.md)]에서 사용하는 계정에 해당 .mdf 및 .ndf 파일에 대한 액세스 권한이 있는지 확인합니다. 문제를 수정한 후에는 ALTER DATABASE를 사용하여 데이터베이스를 ONLINE으로 설정하고 데이터베이스를 다시 시작합니다.  
  
