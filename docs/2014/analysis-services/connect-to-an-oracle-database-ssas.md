---
title: Oracle 데이터베이스 (SSAS)에 연결 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.connoracledb.f1
ms.assetid: 9bd177fb-8539-46cd-bf96-189ade52c2a1
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 79808c965828844a467fc232a5432d1207b25c34
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62680194"
---
# <a name="connect-to-an-oracle-database-ssas"></a>Oracle 데이터베이스에 연결(SSAS)
  **테이블 가져오기 마법사** 의 이 페이지에서는 Oracle 데이터베이스에 연결하기 위한 설정을 지정할 수 있습니다. [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]에서 마법사에 액세스하려면 **모델** 메뉴에서 **데이터 원본에서 가져오기**를 클릭합니다.  
  
 데이터 원본에 연결하려면 컴퓨터에 적절한 공급자를 설치해야 합니다.  
  
> [!NOTE]  
>  이 페이지에서 데이터베이스를 선택하는 경우 현재 사용자의 자격 증명이 사용됩니다. 하지만 가장 정보 페이지에 지정된 사용자에게 선택한 데이터베이스를 읽을 수 있는 권한이 없는 경우에는 가져오기 작업이 실패합니다.  
  
## <a name="uielement-list"></a>UIElement 목록  
 **연결 이름**  
 이 데이터 원본 연결의 고유 이름을 입력합니다. 이 이름은 반드시 입력해야 합니다.  
  
 **서버 이름**  
 연결할 서버 인스턴스의 이름을 입력하거나 선택합니다.  
  
 **사용자 이름**  
 데이터베이스 연결의 사용자 이름을 지정합니다.  
  
 이 사용자 이름은 데이터 원본에 대한 연결 문자열을 구성할 때 사용됩니다. 이러한 자격 증명은 테이블 속성 창과 가져오기 마법사에서 데이터를 미리 보거나 필터링할 때도 사용됩니다. 이러한 자격 증명은 데이터를 가져오거나 새로 고칠 때는 사용되지 않습니다. 이 경우에는 가장 정보 페이지에서 지정한 Windows 자격 증명이 사용됩니다.  
  
 **암호**  
 데이터베이스 연결의 암호를 지정합니다.  
  
 **암호 저장**  
 **암호** 상자에 입력한 암호를 저장할지 여부를 지정합니다.  
  
 **고급**  
 **고급 속성 설정** 대화 상자를 사용하여 추가 연결 속성을 설정합니다. 자세한 내용은 [고급 속성 설정&#40;SSAS&#41;](set-advanced-properties-ssas.md)을 참조하세요.  
  
 **연결 테스트**  
 현재 설정을 사용하여 데이터 원본에 대한 연결을 설정해 봅니다. 연결이 성공적인지 여부를 나타내는 메시지가 표시됩니다.  
  
  
