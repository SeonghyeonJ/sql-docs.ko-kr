---
title: 보고서 기록에서 스냅샷 만들기, 수정 및 삭제 | Microsoft Docs
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-server
ms.topic: conceptual
helpviewer_keywords:
- snapshots [Reporting Services]
- report snapshots [Reporting Services]
ms.assetid: 5aebbbfa-a8db-462d-8ab9-746fad9525f0
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 72486193f4171be9fdce9400328bd1c2a199f2c5
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/29/2020
ms.locfileid: "65580474"
---
# <a name="create-modify-and-delete-snapshots-in-report-history"></a>보고서 기록에서 스냅샷 만들기, 수정 및 삭제
  보고서 기록은 보고서 스냅샷의 모음입니다. 스냅샷을 추가하고 삭제하거나 보고서 기록 스토리지에 영향을 주는 속성을 수정하여 보고서 기록을 유지 관리할 수 있습니다. 수동으로 또는 예약된 일정을 통해 보고서 기록을 만들 수 있습니다.  
  
 보고서 기록을 만들려면 역할 할당에 "보고서 기록 관리" 태스크가 포함되어 있어야 합니다. 보고서 기록을 보려면 역할 할당에 "보고서 보기" 태스크가 포함되어 있어야 합니다. 보고서에 액세스할 수 있는 모든 사용자가 보고서 기록을 사용할 수 있습니다. 특정 사용자 그룹에 대해서만 보고서 기록을 설정하거나 해제할 수는 없습니다.  
  
 보고서 기록의 스냅샷은 작성 날짜와 시간으로 식별됩니다. 날짜와 시간은 쿼리 실행 시점을 기준으로 합니다.  
  
## <a name="creating-snapshots-in-report-history"></a>보고서 기록에서 스냅샷 만들기  
 무인 모드에서 실행할 수 있는 모든 보고서에 대해 수동으로 또는 예약된 간격으로 스냅샷을 만들 수 있습니다. 무인 모드에서 실행하려면 보고서에서 저장된 자격 증명을 사용하거나 아무 자격 증명도 사용하지 않아야 합니다. 또한 보고서가 매개 변수를 사용하는 경우 보고서를 실행할 때 사용할 기본값을 지정해야 합니다. 보고서의 속성 페이지에서 저장된 자격 증명과 매개 변수 값을 지정할 수 있습니다. 자세한 내용은 [매개 변수 속성 페이지&#40;보고서 관리자&#41;](https://msdn.microsoft.com/library/ebb53598-2378-46ae-8935-d5192f8ea49a)를 참조하세요.  
  
 보고서 스냅샷을 만들면 다음 요소가 보고서 서버 데이터베이스의 보고서 스냅샷과 함께 저장됩니다.  
  
-   결과 집합(즉, 보고서의 데이터 원본 속성 페이지에서 지정된 자격 증명을 통해 검색된 보고서의 데이터)  
  
-   기본 보고서 정의(스냅샷 작성 시 존재하는 보고서 정의). 스냅샷 생성 후 보고서 정의가 수정되는 경우 해당 변경 내용은 스냅샷에 반영되지 않습니다.  
  
-   결과 집합을 구하거나 필터링하는 데 사용되는 매개 변수 값  
  
-   이미지 등의 포함 리소스. 보고서에 링크된 외부 리소스는 보고서 스냅샷에 저장되지 않습니다.  
  
 보고서 기록을 만들 수 있는 방법과 저장할 수 있는 보고서 스냅샷 수는 설정에 따라 결정됩니다.  
  
 보고서에서 오류가 발생하면 스냅샷이 생성되지 않습니다. 보고서에서 경고가 발생하지만 계속 실행되는 경우에는 스냅샷을 생성할 수 있습니다.  
  
## <a name="modifying-properties-and-deleting-report-history"></a>속성 수정 및 보고서 기록 삭제  
 한번 생성된 보고서 스냅샷은 수정할 수 없습니다. 그러나 보고서 기록을 삭제하는 방식으로 속성을 수정할 수 있습니다.  
  
 보고서 기록은 다음과 같은 방법으로 삭제할 수 있습니다.  
  
-   스냅샷을 단독으로 또는 그룹으로 직접 삭제합니다.  
  
     보고서 관리자의 기록 페이지에서 스냅샷을 삭제할 수 있습니다. 보고서로 이동하고 기록을 클릭한 다음 삭제할 스냅샷 옆의 확인란을 선택한 후 **삭제**를 클릭합니다.  
  
-   보고서 기록 제한을 낮춰 저장되는 스냅샷 수를 줄입니다. 보고서 기록 제한은 보고서 서버나 특정 보고서에 대해 설정할 수 있습니다. 제한을 낮추면 기록에서 가장 오래된 스냅샷부터 삭제됩니다.  
  
 보고서 서버에 저장된 보고서 기록을 대량 작업으로 모두 삭제할 수는 없습니다.  
  
 보고서를 삭제하면 보고서 기록도 삭제됩니다. 예를 들어 월별 판매 보고서를 새 버전으로 바꾸기 위해 삭제하면 이 보고서와 연결된 보고서 기록도 모두 삭제됩니다. 그러나 보고서를 이동하면 모든 보고서 기록도 함께 이동합니다.  
  
## <a name="see-also"></a>참고 항목  
 [보고서 기록 만들기&#40;SharePoint 통합 모드의 Reporting Services&#41;](../../reporting-services/report-server/create-report-history-reporting-services-in-sharepoint-integrated-mode.md)   
 [보고서 관리자&#40;SSRS 기본 모드&#41;](https://msdn.microsoft.com/library/80949f9d-58f5-48e3-9342-9e9bf4e57896)   
 [보고서 서버 콘텐츠 관리&#40;SSRS 기본 모드&#41;](../../reporting-services/report-server/report-server-content-management-ssrs-native-mode.md)   
 [보고서 기록에 스냅샷 추가&#40;보고서 관리자&#41;](../../reporting-services/report-server/add-a-snapshot-to-report-history-report-manager.md)   
 [보고서 기록 제한&#40;보고서 관리자&#41;](../../reporting-services/reports/limit-report-history-report-manager.md)  
  
  
