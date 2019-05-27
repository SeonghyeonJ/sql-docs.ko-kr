---
title: 링크된 보고서 만들기 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- linked reports [Reporting Services], creating
ms.assetid: 12be8341-cb57-45e8-a421-2bf66b50234d
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: d0df6a3bdb6f542b02b62ccf4aa6614da290551f
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66102703"
---
# <a name="create-a-linked-report"></a>링크된 보고서 만들기
  링크된 보고서는 기존 보고서에 대한 액세스 지점을 제공하는 보고서 서버 항목입니다. 개념적으로 링크된 보고서는 프로그램을 실행하거나 파일을 열 때 사용하는 프로그램 바로 가기와 비슷합니다.  
  
 링크된 보고서는 기존 보고서에서 파생되며 원본 보고서의 정의를 유지합니다. 또한 항상 원본 보고서의 보고서 레이아웃과 데이터 원본 속성을 상속합니다. 보안, 매개 변수, 위치, 구독 및 일정을 비롯한 다른 모든 속성 및 설정은 원본 보고서와 다를 수 있습니다.  
  
 기존 보고서의 다른 버전을 추가로 만들려는 경우에 링크된 보고서를 만들 수 있습니다. 예를 들어 한 지역의 판매 보고서를 사용하여 모든 판매 지역에 대한 지역별 보고서를 만들 수 있습니다.  
  
 링크된 보고서는 일반적으로 매개 변수가 있는 보고서를 기반으로 하지만 매개 변수가 있는 보고서가 반드시 필요하지는 않습니다. 기존 보고서를 다른 설정으로 배포하고자 할 때마다 링크된 보고서를 만들 수 있습니다.  
  
### <a name="to-create-a-linked-report"></a>링크된 보고서를 만들려면  
  
1.  보고서 관리자에서 링크하려는 보고서가 있는 폴더로 이동한 후 옵션 메뉴를 열고 **링크된 보고서 만들기**를 클릭합니다.  
  
2.  새 링크된 보고서의 이름을 입력합니다. 설명을 입력합니다(옵션).  
  
3.  보고서를 다른 폴더에 만들려면 **위치 변경**을 클릭합니다. 사용할 폴더를 클릭하거나 **위치** 상자에 폴더 이름을 입력합니다. [!INCLUDE[clickOK](../../../includes/clickok-md.md)] 다른 폴더를 선택하지 않으면 현재 폴더(기반이 되는 보고서가 저장되어 있는 폴더)에 링크된 보고서가 만들어집니다.  
  
4.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)] 링크된 보고서가 열립니다.  
  
     링크된 보고서의 아이콘은 보고서 서버가 관리하는 다른 항목의 아이콘과 다릅니다. 다음 아이콘은 링크된 보고서를 나타냅니다.  
  
     ![링크된 보고서 아이콘](../media/hlp-16linked.gif "링크된 보고서 아이콘")  
  
## <a name="see-also"></a>관련 항목  
 [보고서 열기 및 닫기&#40;보고서 관리자&#41;](../reports/open-and-close-a-report-report-manager.md)   
 [새 링크된 보고서 페이지&#40;보고서 관리자&#41;](../new-linked-report-page-report-manager.md)   
 [항목 위치 선택 페이지&#40;보고서 관리자&#41;](../choose-item-location-page-report-manager.md)   
 [일반 속성 페이지, 보고서&#40;보고서 관리자&#41;](../general-properties-page-reports-report-manager.md)   
 [Reporting Services 개념&#40;SSRS&#41;](../reporting-services-concepts-ssrs.md)   
 [보고서 관리자&#40;SSRS 기본 모드&#41;](../report-manager-ssrs-native-mode.md)  
  
  
