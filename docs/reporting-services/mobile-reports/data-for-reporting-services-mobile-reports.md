---
title: Reporting Services 모바일 보고서의 데이터 | Microsoft Docs
description: SQL Server 모바일 보고서 게시자로 데이터를 가져온 후 모바일 보고서를 만들고 디자인하는 방법은 데이터 원본이 Excel 파일이든, 공유 데이터 세트든 관계없이 동일합니다.
ms.date: 02/08/2016
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: mobile-reports
ms.topic: conceptual
ms.assetid: 91138ef8-ddb4-4ac5-a1e4-fa4cf1c58dcc
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 3c022631d0f21c4e23756e39e4824fe9f52ef3b5
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/29/2020
ms.locfileid: "79447866"
---
# <a name="data-for-reporting-services-mobile-reports"></a>Data for Reporting Services mobile reports
[!INCLUDE[PRODUCT_NAME](../../includes/ss-mobilereptpub-long.md)] 데이터 모델은 간단 합니다. 데이터는 데이터 세트의 컬렉션으로 [!INCLUDE[PRODUCT_NAME](../../includes/ss-mobilereptpub-short.md)]로 가져옵니다. 데이터 세트 간의 형식 관계는 필요하지 않습니다. 데이터 세트 간의 조회는 키 값이 일치하는 한 작동합니다. 날짜/시간 집계는 모바일 보고서 런타임을 통해 처리되며 데이터 세트 간에 날짜/시간 데이터 세분성이 달라도 데이터 세트 간의 집계 일치 여부를 확인합니다.   
  
다음과 같은 두 가지 유형의 원본에서 데이터를 가져올 수 있습니다.   
  
* **로컬 Excel 파일**: Excel 문서를 선택하고 가져올 워크시트를 선택합니다. 가져온 데이터는 모바일 보고서 정의 내에 저장됩니다. 원본 Excel 파일에서 데이터를 새로 고치려면 [!INCLUDE[PRODUCT_NAME](../../includes/ss-mobilereptpub-short.md)] **데이터** 탭 오른쪽 위에 있는 **데이터 새로 고침** 명령을 사용합니다. [SSRS 모바일 보고서용으로 Excel 데이터 준비](../../reporting-services/mobile-reports/prepare-excel-data-for-reporting-services-mobile-reports.md)에 대해 자세히 확인해 보세요.  
  
* **SQL Server 모바일 보고서 게시자 공유 데이터 세트**: 서버에 게시된 데이터 세트 목록을 검색하여 모바일 보고서에 추가할 데이터 세트를 선택합니다. 서버 데이터를 기반으로 하는 모바일 보고서는 항상 원본 서버 데이터 세트에 연결된 상태로 유지되며 서버 데이터의 최신 상태를 반영합니다. [지원되는 데이터 원본 목록](../report-data/data-sources-supported-by-reporting-services-ssrs.md)을 참조하세요.   
  
  자세한 내용은 [모바일 보고서 게시자의 공유 데이터 세트에서 데이터 가져오기](../../reporting-services/mobile-reports/get-data-from-shared-datasets-in-reporting-services-mobile-reports.md)를 참조하세요.  
  
[!INCLUDE[PRODUCT_NAME](../../includes/ss-mobilereptpub-short.md)]로 데이터를 가져온 후의 나머지 모바일 보고서 만들기 및 디자인 환경은 데이터를 가져온 위치에 관계없이 동일합니다.   
  
## <a name="connect-mobile-report-elements-to-data"></a>데이터에 모바일 보고서 요소 연결 ##  
  
각 SQL Server 모바일 보고서 게시자 요소에는 하나 이상의 데이터 설정을 포함합니다. 예를 들어 방사형 계기 요소에는 주 값과 비교 값의 두 데이터 설정이 포함되어 있습니다. 이러한 각 설정은 특정 데이터 세트에서 정확히 하나의 필드(열)를 가리킵니다.   
  
모바일 보고서 런타임은 사용자의 선택 항목에 따라 계기에 대해 집계된 값을 제공합니다. 같은 방사형 계기 인스턴스의 비교 값을 다른 데이터 세트의 필드에 바인딩할 수 있습니다.   
  
### <a name="see-also"></a>참고 항목  
-  [Reporting Services 모바일 보고서에 대한 데이터 준비](../../reporting-services/mobile-reports/prepare-data-for-reporting-services-mobile-reports.md)
- [SQL Server 모바일 보고서 게시자를 사용하여 모바일 보고서 만들기 및 게시](../../reporting-services/mobile-reports/create-mobile-reports-with-sql-server-mobile-report-publisher.md)  
- [공유 데이터 세트에서 데이터 가져오기](../../reporting-services/mobile-reports/get-data-from-shared-datasets-in-reporting-services-mobile-reports.md)
- [모바일 보고서에서 Analysis Services 데이터에 대한 날짜 형식 지정 유지](../../reporting-services/mobile-reports/retain-date-formatting-for-analysis-services-in-mobile-reports.md) 
  
  

