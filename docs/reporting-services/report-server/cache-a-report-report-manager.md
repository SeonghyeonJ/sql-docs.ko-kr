---
title: 보고서 캐시(보고서 관리자) | Microsoft Docs
description: 보고서 관리자에서 캐시된 보고서의 만료를 예약하는 방법을 알아봅니다. 보고서를 캐시하면 캐시된 상태로 유지되는 동안 보기 속도가 빨라집니다.
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-server
ms.topic: conceptual
helpviewer_keywords:
- report execution properties [Reporting Services]
- cache [Reporting Services]
- cached reports [Reporting Services]
- schedules [Reporting Services], report expiration
- expiration [Reporting Services]
ms.assetid: 723d1cb0-c2e7-4763-8690-a6a7a8bbbb90
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 36bc03b94c42d8cf660039eb04c73ce88cf18223
ms.sourcegitcommit: fe59f8dc27fd633f5dfce54519d6f5dcea577f56
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/09/2020
ms.locfileid: "91934947"
---
# <a name="cache-a-report-report-manager"></a>보고서 캐시(보고서 관리자)
  성능을 향상시키는 한 가지 방법은 보고서의 캐싱 속성을 구성하는 것입니다. 보고서가 캐시되면 렌더링된 보고서의 복사본이 짧은 시간 동안 저장됩니다. 보고서를 요청하는 첫 번째 사용자는 모든 처리가 완료될 때까지 기다려야 보고서를 볼 수 있습니다. 캐싱 기간 내에 보고서를 요청하는 이후 사용자는 처리가 이미 발생했기 때문에 보고서를 바로 볼 수 있습니다.  
  
 캐시할 수 있는 보고서 유형은 제한되어 있습니다. 예를 들어 사용자 ID에 따라 보고서 출력이 달라지는 경우 또는 보고서를 요청하는 사용자의 보안 토큰을 사용하여 데이터가 검색되는 경우 보고서를 캐시할 수 없습니다. 자세한 내용은 [보고서 캐시&#40;SSRS&#41;](../../reporting-services/report-server/caching-reports-ssrs.md)버전에서 캐시를 미리 로드할 수 있는 유일한 방법이었습니다.  
  
### <a name="to-schedule-the-expiration-of-a-cached-report"></a>캐시된 보고서의 만료를 예약하려면  
  
1.  [보고서 관리자&#40;SSRS 기본 모드&#41;](../web-portal-ssrs-native-mode.md)를 시작합니다.  
  
2.  보고서 관리자에서 **내용** 페이지로 이동합니다. 캐싱 속성을 설정할 보고서로 이동하고 항목 위로 마우스를 이동한 다음 드롭다운 화살표를 클릭합니다.  
  
3.  드롭다운 메뉴에서 **관리**를 클릭합니다.  
  
4.  왼쪽 프레임에서 **처리 옵션**을 클릭합니다.  
  
5.  해당 페이지에서 **항상 최신 데이터로 이 보고서 실행**을 선택합니다.  
  
6.  다음 두 캐시 옵션 중에서 하나를 선택하고 만료 시간을 구성합니다.  
  
    -   캐시된 복사본이 특정 시간 후에 만료되도록 구성하려면 **보고서의 임시 복사본을 캐시합니다. 보고서 복사본은 다음 분 후에 만료됩니다.** 를 클릭합니다. 보고서 만료 시간(분)을 입력합니다.  
  
    -   일정에 따라 캐시된 복사본이 만료되도록 구성하려면 **보고서의 임시 복사본을 캐시합니다. 보고서 복사본은 다음 일정으로 만료됩니다.** 를 클릭합니다. **구성**을 클릭하거나 공유 일정을 선택하여 보고서 만료를 제어합니다.  
  
7.  **적용**을 클릭합니다.  
  
## <a name="see-also"></a>참고 항목  
 [보고서 처리 속성 설정](../../reporting-services/report-server/set-report-processing-properties.md)   
 [보고서 캐시&#40;SSRS&#41;](../../reporting-services/report-server/caching-reports-ssrs.md)  
  
