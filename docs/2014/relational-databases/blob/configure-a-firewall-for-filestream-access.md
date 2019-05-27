---
title: FILESTREAM 액세스를 위한 방화벽 구성 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: filestream
ms.topic: conceptual
helpviewer_keywords:
- Windows Firewall [Database Engine], FILESTREAM
- FILESTREAM [SQL Server], Windows Firewall
ms.assetid: fc52007f-c26f-4f8e-b9d8-55a7978f4d56
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: fff59c773e4c96b8d14cf604c1a9a3e2b31869f4
ms.sourcegitcommit: 45a9d7ffc99502c73f08cb937cbe9e89d9412397
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/22/2019
ms.locfileid: "66010306"
---
# <a name="configure-a-firewall-for-filestream-access"></a>FILESTREAM 액세스를 위한 방화벽 구성
  방화벽으로 보호되는 환경에서 FILESTREAM을 사용하려면 클라이언트와 서버에서 DNS 이름을 FILESTREAM 파일이 포함된 서버로 확인할 수 있어야 합니다. FILESTREAM을 사용하려면 Windows 파일 공유 포트 139 및 445가 열려 있어야 합니다.  
  
### <a name="to-open-the-windows-file-sharing-ports-on-a-computer-that-is-running-windows-7"></a>Windows 7을 실행하는 컴퓨터에서 Windows 파일 공유 포트를 열려면  
  
1.  제어판에서 **Windows 방화벽**을 엽니다.  
  
2.  왼쪽 창에서 **고급 설정**을 클릭합니다. 관리자 암호를 묻거나 암호를 확인하는 메시지가 표시되면 암호를 입력하거나 확인합니다.  
  
3.  **고급 보안이 포함된 Windows 방화벽** 대화 상자의 왼쪽 창에서 **인바운드 규칙**을 클릭한 다음 오른쪽 창에서 **새 규칙**을 클릭합니다.  
  
4.  새 인바운드 규칙 마법사의 지시에 따라 TCP 포트 139를 추가합니다.  
  
5.  이전 단계를 반복하여 TCP 포트 445를 추가합니다.  
  
6.  **고급 보안이 포함된 Windows 방화벽** 대화 상자를 닫습니다.  
  
  
