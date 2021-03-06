---
title: 링크된 보고서 만들기 | Microsoft Docs
description: 기존 보고서의 다른 버전을 추가로 만들 수 있도록 링크된 보고서를 만드는 방법을 알아봅니다.
ms.date: 05/30/2019
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: reports
ms.topic: conceptual
helpviewer_keywords:
- linked reports [Reporting Services], creating
ms.assetid: 12be8341-cb57-45e8-a421-2bf66b50234d
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: cb362f699e8bf87e0f386c3ec726869f67aec934
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/29/2020
ms.locfileid: "79510164"
---
# <a name="create-a-linked-report"></a>링크된 보고서 만들기
  링크된 보고서는 기존 보고서에 대한 액세스 지점을 제공하는 보고서 서버 항목입니다. 개념적으로 링크된 보고서는 프로그램을 실행하거나 파일을 열 때 사용하는 프로그램 바로 가기와 비슷합니다.  
  
 링크된 보고서는 기존 보고서에서 파생되며 원본 보고서의 정의를 유지합니다. 또한 항상 원본 보고서의 보고서 레이아웃과 데이터 원본 속성을 상속합니다. 보안, 매개 변수, 위치, 구독 및 일정을 비롯한 다른 모든 속성 및 설정은 원본 보고서와 다를 수 있습니다.  
  
 기존 보고서의 다른 버전을 추가로 만들려는 경우에 링크된 보고서를 만들 수 있습니다. 예를 들어 한 지역의 판매 보고서를 사용하여 모든 판매 지역에 대한 지역별 보고서를 만들 수 있습니다.  
  
 링크된 보고서는 일반적으로 매개 변수가 있는 보고서를 기반으로 하지만 매개 변수가 있는 보고서가 반드시 필요하지는 않습니다. 기존 보고서를 다른 설정으로 배포하고자 할 때마다 링크된 보고서를 만들 수 있습니다.  
  
## <a name="to-create-a-linked-report"></a>링크된 보고서를 만들려면  
  
1. 웹 포털에서 원하는 보고서로 이동하여 마우스 오른쪽 단추로 클릭하고 드롭다운 메뉴에서 **관리**를 선택합니다.

2. **관리 <reportname>** 페이지에서 **링크된 보고서 만들기**를 선택합니다.  
  
3. 새 링크된 보고서의 이름을 입력합니다. 선택적으로 설명을 입력합니다.  
  
4. 보고서에 다른 폴더를 선택하려면 ***위치*** 오른쪽에 있는 줄임표 단추(...)를 선택합니다.  보고서의 새 폴더로 이동한 다음 **선택**을 선택합니다. 다른 폴더를 선택하지 않으면 링크된 보고서가 현재 폴더에 만들어집니다.  
  
5. **만들기**를 선택합니다. 링크된 보고서가 만들어집니다.  

6. **고급**에서 원할 경우 다른 **보고서 시간 제한** 값을 선택하고 **적용**을 선택하여 변경 사항을 저장합니다.
  
     링크된 보고서의 아이콘은 보고서 서버가 관리하는 다른 항목의 아이콘과 다릅니다. 다음 아이콘은 링크된 보고서를 나타냅니다.  
  
     ![링크된 보고서 아이콘](../../reporting-services/report-server/media/hlp-16linked.gif "링크된 보고서 아이콘")  
  
## <a name="see-also"></a>참고 항목  

 [Reporting Services 개념&#40;SSRS&#41;](../../reporting-services/reporting-services-concepts-ssrs.md)  
 [보고서 서버의 웹 포털(SSRS 기본 모드)](../../reporting-services/web-portal-ssrs-native-mode.md)
  
