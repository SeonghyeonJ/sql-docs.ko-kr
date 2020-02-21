---
title: 보고서 처리 속성 설정 | Microsoft Docs
ms.date: 06/10/2019
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-server
ms.topic: conceptual
helpviewer_keywords:
- on-demand reports
- report processing [Reporting Services], execution properties
- snapshots [Reporting Services], running reports from
- cached reports [Reporting Services]
- report snapshots [Reporting Services], running reports from
- report execution snapshots [Reporting Services]
ms.assetid: b5cbc453-5986-423e-af44-1f243ef3edb1
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 4a7729e8880e811494e6e1016b827831674cd812
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/31/2020
ms.locfileid: "67140395"
---
# <a name="set-report-processing-properties"></a>보고서 처리 속성 설정
  보고서 실행 속성은 보고서의 처리 방식을 제어합니다. 실행 속성은 각 보고서별로 설정해야 합니다.  
  
 보고서 실행 속성을 설정하려면 웹 포털에서 보고서로 이동하고, 보고서를 마우스 오른쪽 단추로 클릭하고, 드롭다운 메뉴에서 **관리**를 선택합니다.
  
## <a name="report-execution-modes"></a>보고서 실행 모드  
 필요에 따라 또는 스냅샷으로 보고서를 실행할 수 있습니다. 다음 섹션에서는 각 방법에 대해 설명합니다.  
  
### <a name="running-reports-on-demand"></a>필요에 따라 보고서 실행 
 사용자가 보고서를 실행할 때마다 보고서가 데이터 원본을 쿼리하도록 지정하여 최신 데이터가 포함된 요청 시 실행 보고서를 실행할 수 있습니다. 보고서를 열거나 요청하는 모든 사용자에 대해 보고서의 새 인스턴스가 만들어집니다. 각각의 새 인스턴스에는 새 쿼리 결과가 포함됩니다. 이 방법을 사용하면 10명의 사용자가 동시에 보고서를 여는 경우 10개의 쿼리가 처리되도록 데이터 원본에 보내집니다.  
  
### <a name="running-reports-on-demand-from-cache"></a>필요에 따라 캐시에서 보고서 실행 
 성능 향상을 위해 사용자가 보고서를 실행할 때 보고서 및 데이터가 일시적으로 캐시되도록 지정할 수 있습니다. 캐시된 복사본은 이후에 같은 보고서를 액세스하는 다른 사용자도 사용할 수 있습니다. 이 방법을 사용하는 경우 10명의 사용자가 보고서를 열면 첫 번째로 요청된 보고서만 처리됩니다. 보고서는 나중에 캐시되며 나머지 9명의 사용자는 캐시된 보고서를 볼 수 있습니다.  
  
 캐시된 보고서는 정의한 간격에 따라 캐시에서 제거됩니다. 분 단위로 간격을 지정하거나 특정 날짜 및 시간에 캐시가 비워지도록 예약할 수 있습니다. 자세한 내용은 [보고서 캐시&#40;SSRS&#41;](../../reporting-services/report-server/caching-reports-ssrs.md)버전에서 캐시를 미리 로드할 수 있는 유일한 방법이었습니다.  
  
### <a name="running-reports-from-snapshots"></a>스냅샷에서 보고서 실행  
 보고서 스냅샷은 레이아웃 정보 및 특정 시점에 검색된 데이터가 들어 있는 보고서입니다. 보고서를 보고서 스냅샷으로 실행하면 임의의 시간에(예: 예약된 백업 시간 동안) 보고서가 실행되지 않도록 할 수 있습니다. 보고서 스냅샷은 일반적으로 일정에 따라 생성되고 이후에 새로 고쳐지므로 보고서 및 데이터 처리 시간을 정확하게 예약할 수 있습니다. 실행하는 데 시간이 오래 걸리는 쿼리 또는 특정 시간 동안 누구도 액세스할 수 없는 데이터 원본의 데이터를 사용하는 쿼리를 기반으로 하는 보고서의 경우 보고서를 스냅샷으로 실행해야 합니다.  
  
 보고서 스냅샷은 보고서 서버 데이터베이스에 저장되며, 이후에 사용자나 구독과 같은 처리에서 보고서를 요청할 때 이 데이터베이스에서 검색됩니다. 보고서 스냅샷이 업데이트되면 새 인스턴스로 덮어쓰여집니다. 보고서 서버는 이전 버전의 보고서 스냅샷을 보고서 기록에 추가하기 위한 옵션을 구체적으로 설정하지 않는 한 이러한 보고서 스냅샷을 저장하지 않습니다. 자세한 내용은 [보고서 기록에서 스냅샷 만들기, 수정 및 삭제](../../reporting-services/report-server/create-modify-and-delete-snapshots-in-report-history.md)를 참조하세요.  
  
 모든 보고서를 스냅샷으로 실행되도록 구성할 수는 없습니다. 사용자에게 자격 증명을 요청하거나 Windows 통합 보안을 사용하여 보고서 데이터를 가져오는 보고서에 대해서는 스냅샷을 만들 수 없습니다. 매개 변수가 있는 보고서를 스냅샷으로 실행하려면 스냅샷을 만들 때 사용할 기본 매개 변수를 지정해야 합니다. 요청 시 실행되는 보고서와 달리 매개 변수가 있는 보고서를 열면 보고서 스냅샷에 대해 다른 매개 변수 값을 지정할 수 없습니다. 다른 매개 변수 값을 선택하면 새 보고서 처리 요청이 발생하며 이는 허용되지 않습니다.  
  
 일부 경우에 요청 시 실행 보고서를 스냅샷으로 실행되도록 구성하면 구독이 비활성화될 수 있습니다. 다음 조건이 발생하면 보고서 서버는 보고서가 요청 시 실행되도록 구성되었을 때 정의된 기존 구독을 비활성화합니다.  
  
-   보고서에 쿼리 매개 변수를 사용하며, 해당 보고서를 스냅샷으로 실행하기 위한 요구 사항에 맞도록 특정 값을 기본 매개 변수로 선택한 경우  
  
-   기존 구독이 스냅샷에 대해 지정한 기본 매개 변수 값과는 다른 매개 변수 값을 사용하도록 구성되어 있는 경우  
  
 이러한 조건이 발생할 경우 보고서 서버는 구독이 실행되도록 예약된 다음 번에 구독을 해제합니다. 구독을 다시 활성화하려면 구독을 열어서 저장합니다. 구독을 열면 보고서 서버에서 구독 매개 변수 값을 스냅샷에 대해 지정한 값으로 업데이트합니다. 구독에 대한 자세한 내용은 [구독 및 배달&#40;Reporting Services&#41;](../../reporting-services/subscriptions/subscriptions-and-delivery-reporting-services.md)을 참조하세요.  
  
## <a name="see-also"></a>참고 항목  
 [처리 옵션 설정&#40;SharePoint 통합 모드의 Reporting Services&#41;](../../reporting-services/report-server-sharepoint/set-processing-options-reporting-services-in-sharepoint-integrated-mode.md)   
 [Reporting Services 개념&#40;SSRS&#41;](../../reporting-services/reporting-services-concepts-ssrs.md)   
 [보고서 기록에서 스냅샷 만들기, 수정 및 삭제](create-modify-and-delete-snapshots-in-report-history.md)   
 [보고서 데이터 원본에 대한 자격 증명 및 연결 정보 지정](../../reporting-services/report-data/specify-credential-and-connection-information-for-report-data-sources.md)  
  