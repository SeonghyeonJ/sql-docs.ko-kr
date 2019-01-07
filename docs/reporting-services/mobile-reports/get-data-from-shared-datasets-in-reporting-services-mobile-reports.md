---
title: Reporting Services 모바일 보고서의 공유 데이터 세트에서 데이터 가져오기 | Microsoft Docs
ms.date: 03/30/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: mobile-reports
ms.topic: conceptual
ms.assetid: 0b846451-c8d0-412c-802d-a42bb1ff8c63
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: cac1a32b49fde5b41c0a8ef21706d873ce037cd3
ms.sourcegitcommit: 9ece10c2970a4f0812647149d3de2c6b75713e14
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51813936"
---
# <a name="get-data-from-shared-datasets-in-reporting-services-mobile-reports"></a>Reporting Services 모바일 보고서에서 공유 데이터 세트의 데이터 가져오기
SQL Server 모바일 보고서 게시자는 [Excel 파일의 데이터 로드](../../reporting-services/mobile-reports/prepare-excel-data-for-reporting-services-mobile-reports.md)할 수 있을 뿐 아니라 거의 모든 원본의 데이터에 액세스할 수 있습니다. 데이터에 액세스하려면 Reporting Services 웹 포털에 구성되어 있는 공유 데이터 원본이 필요합니다. [공유 데이터 원본 만들기](../../reporting-services/report-data/create-modify-and-delete-shared-data-sources-ssrs.md) 및 [공유 데이터 집합 만들기](../../reporting-services/report-data/manage-shared-datasets.md)에 대한 자세한 내용을 확인해 보세요.  
  
Reporting Services 서버에서 공유 데이터 원본과 공유 데이터 세트를 구성한 후에는 [!INCLUDE[PRODUCT_NAME](../../includes/ss-mobilereptpub-short.md)]에서 만든 모바일 보고서에서 해당 데이터 원본과 데이터 세트를 사용할 수 있습니다.   
  
[!INCLUDE[PRODUCT_NAME](../../includes/ssrsnoversion.md)] 에서 [!INCLUDE[PRODUCT_NAME](../../includes/ss-mobilereptpub-short.md)]서버에 연결하고 나면 모바일 보고서를 공유 데이터 집합에 쉽게 연결할 수 있습니다.   
  
1. **데이터** 탭에서 **데이터 추가**를 선택합니다.  
  
2. **보고서 서버**를 선택합니다.   
  
3.  처음으로 서버에 연결하는 경우 서버 이름과 사용자 이름 및 암호를 입력합니다. 서버 주소 상자에 서버 이름을 다음 형식으로 입력합니다.  
  
    \<"servername" > /reports/  
  
    이 예에서는 다음과 같습니다.  
       
    ![SSMRP_ConnectToServer](../../reporting-services/mobile-reports/media/ssmrp-connecttoserver.png)  
      
  
4. [!INCLUDE[PRODUCT_NAME](../../includes/ssrsnoversion.md)] 서버를 선택하면 폴더에서 사용 가능한 데이터 집합을 확인할 수 있습니다. [!INCLUDE[PRODUCT_NAME](../../includes/ss-mobilereptpub-short.md)]로 데이터를 가져올 데이터 집합을 선택합니다.  
  
   ![SS_MRP_ServerData](../../reporting-services/mobile-reports/media/ss-mrp-serverdata.png)  
  
데이터 세트를 가져온 후에는 시뮬레이트된 데이터 또는 Excel 파일의 로컬 데이터를 사용할 때와 같은 방법으로 모바일 보고서를 디자인할 수 있습니다.  
  
기본적으로 공유 데이터 세트는 최신 데이터를 포함하므로 항상 최신 상태로 유지됩니다. 해당 데이터 세트를 기반으로 하는 모바일 보고서를 볼 때마다 SQL Server가 기본 쿼리를 실행하여 최신 데이터를 반환하기 때문입니다. 따라서 많은 사용자가 모바일 보고서를 확인할 때는 이 방식이 적절하지 않을 수도 있으므로 캐싱을 설정해 쿼리를 주기적으로 실행하고 결과 데이터 세트를 캐시할 수 있습니다. 이 블로그 게시물에서는 [웹 포털에서 캐싱 및 데이터 새로 고침이 작동하는 방식](https://christopherfinlan.com/2016/02/10/so-refreshinghow-data-refresh-works-with-mobile-reports-and-kpis-in-reporting-services/)에 대해 설명합니다.  
  
## <a name="add-edit-or-remove-a-report-server"></a>보고서 서버 추가, 편집 또는 제거  
  
보고서 서버에 이미 연결한 경우 데이터 탭에서 **데이터 추가** 를 선택하면 다른 보고서 서버를 추가하는 옵션이 표시되지 않습니다. 대신 다음 단계를 따르세요.  
  
1. 왼쪽 위에서 **연결**을 선택합니다.  
  
   ![SSMRP_AddConnectionIcon](../../reporting-services/mobile-reports/media/ssmrp-addconnectionicon.png)  
     
   서버 연결 창이 오른쪽에 열립니다.  
     
   ![SSMRP_ServerConnectnPane](../../reporting-services/mobile-reports/media/ssmrp-serverconnectnpane.png)  
     
2. 새 서버 연결을 추가하거나 기존 연결을 편집 또는 제거합니다.  
  
### <a name="see-also"></a>관련 항목:  
- [SQL Server 모바일 보고서 게시자를 사용하여 모바일 보고서 만들기 및 게시](../../reporting-services/mobile-reports/create-mobile-reports-with-sql-server-mobile-report-publisher.md)  
-  [웹 포털(SSRS 기본 모드)](../../reporting-services/web-portal-ssrs-native-mode.md)  
-  [iPad 앱에서 SQL Server 모바일 보고서 및 KPI](https://pbiwebprod-docs.azurewebsites.net/documentation/powerbi-mobile-ipad-kpis-mobile-reports)  보기(iOS용 Power BI)  
-  [iPhone 앱에서 SQL Server 모바일 보고서 및 KPI](https://pbiwebprod-docs.azurewebsites.net/documentation/powerbi-mobile-iphone-kpis-mobile-reports) 보기(iOS용 Power BI)  
  
  
  
  

