---
title: IIS에서 가상 서버 구성 | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/09/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- virtual servers in RDS [ADO]
ms.assetid: 2b4786c6-40c4-4ce1-9ad4-03df436e0aff
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c248afac72fac013759ad80f69dea199756a4010
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63214882"
---
# <a name="configuring-virtual-servers-on-iis"></a>IIS에서 가상 서버 구성
인터넷 정보 서비스 4.0의 가상 서버를 만들 때 다음 두 가지 추가 단계를 RDS를 사용 하도록 가상 서버를 구성 하기 위해 필요 합니다.  
  
1.  서버를 설정할 때 확인 "액세스 허용 실행 합니다."  
  
2.  탭 이동 *vroot*\msadc, 여기서 *vroot* 홈 디렉터리 가상 서버입니다.  
  
> [!IMPORTANT]
>  Windows 8 및 Windows Server 2012 부터는 RDS 서버 구성 요소는 더 이상 포함 된 Windows 운영 체제에서 (Windows 8을 참조 하 고 [Windows Server 2012 호환성 설명서](https://www.microsoft.com/download/details.aspx?id=27416) 자세한). RDS 클라이언트 구성 요소는 Windows의 이후 버전에서 제거 됩니다. 새 개발 작업에서는 이 기능을 사용하지 않도록 하고, 현재 이 기능을 사용하는 애플리케이션은 수정하세요. RDS를 사용 하는 응용 프로그램을 마이그레이션해야 [WCF 데이터 서비스](https://go.microsoft.com/fwlink/?LinkId=199565)합니다.  
  
## <a name="see-also"></a>관련 항목  
 [RDS 기본 사항](../../../ado/guide/remote-data-service/rds-fundamentals.md)


