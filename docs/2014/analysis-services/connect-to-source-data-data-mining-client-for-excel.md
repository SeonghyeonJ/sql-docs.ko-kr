---
title: 원본 데이터에 연결 (Excel 용 데이터 마이닝 클라이언트) | Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- connections
ms.assetid: 548672ce-e403-4aca-b67a-c2c797f053dd
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 468686314bb2446415a6883c6233708f9cbd1d2b
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/26/2020
ms.locfileid: "66087097"
---
# <a name="connect-to-source-data-data-mining-client-for-excel"></a>원본 데이터에 연결(Excel용 데이터 마이닝 클라이언트)
  이 항목에서는 데이터 마이닝 모델 저장 및 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]에 저장된 외부 데이터 액세스용 연결을 만들고 사용하는 방법에 대해 설명합니다.  
  
 **데이터 마이닝 연결.** 추가 기능을 시작할 때 만드는 초기 연결은 알고리즘 액세스, 데이터 분석, 마이닝 구조 및 모델 저장에 사용됩니다.  
  
 추가 기능에는 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]에서 제공하는 알고리즘 및 데이터 구조가 필요하므로 모델링 및 시각화 도구를 사용하려면 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 인스턴스에 연결해야 합니다.  
  
 **외부 데이터 원본 연결.** 모델을 작성하거나 결과를 저장할 때 외부 데이터에 대한 연결을 만들 수도 있습니다. 예를 들어 한 서버에 데이터 마이닝 모델을 만든 다음 다른 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 인스턴스, Excel 데이터 테이블 또는 [!INCLUDE[msCoName](../includes/msconame-md.md)] Access와 같은 외부 데이터 원본에 저장된 데이터를 사용하여 이 데이터 마이닝 모델에 대한 예측 쿼리를 수행할 수 있습니다. 새 데이터 원본에 액세스할 때마다 대화 상자를 사용하여 연결을 만들라는 메시지가 표시됩니다.  
  
##  <a name="prerequisites"></a><a name="bkmk_prereq2"></a> 필수 조건  
 이 버전의 추가 기능을 사용하려면 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 인스턴스가 SQL Server 2012여야 합니다. 개별 버전의 추가 기능을 사용하여 이전 버전의 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]에 연결할 수도 있습니다. SQL Server 2005, SQL Server 2008 및 SQL Server 2008 R2를 지원하는 추가 기능 버전이 있습니다.  
  
 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 데이터베이스에 연결하려면 해당 데이터베이스 서버에 대한 액세스 권한이 있어야 합니다. 또한 데이터 마이닝 세션이 활성화되어야 하며 서버에 저장된 데이터베이스 개체에 대한 읽기 또는 읽기/쓰기 권한이 있어야 합니다.  
  
##  <a name="creating-data-mining-server-connections"></a><a name="bkmk_connect"></a>데이터 마이닝 서버 연결 만들기  
 Excel 용 데이터 마이닝 클라이언트 및 Excel 용 테이블 분석 도구에 있는 **연결** 그룹에서는 인스턴스에 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]대 한 연결을 관리 하기 위한 도구를 제공 합니다.  
  
-   추가 기능을 설치할 때 연결을 만들거나 나중에 추가할 수 있습니다.  
  
-   모델을 만들거나 쿼리하는 중이 아니면 언제든지 여러 연결을 만들고 연결을 변경할 수 있습니다.  
  
     데이터 마이닝 모델을 처리하는 동안에는 연결을 변경하거나 닫지 마십시오. 데이터 마이닝 모델의 데이터가 손실되거나 모델을 사용할 수 없게 될 수 있습니다.  
  
-   특정 시간에 하나의 연결만 활성화될 수 있습니다.  
  
### <a name="connections-in-the-excel-add-ins"></a>Excel 추가 기능에서 연결  
 Excel 용 데이터 마이닝 클라이언트 및 Excel 용 테이블 분석 도구에 있는 **연결** 그룹에서는 인스턴스에 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]대 한 연결을 관리 합니다.  
  
##### <a name="create-a-new-server-connection-in-the-excel-add-ins"></a>Excel 추가 기능에서 새 서버 연결 만들기  
  
1.  **분석** 또는 **데이터 마이닝** 리본에서 **연결** 단추를 클릭 합니다.  
  
    > [!NOTE]  
    >  단추의 텍스트는 연결이 존재하는지 여부를 나타냅니다. 워크시트에 연결 되지 않은 경우 단추에는 "\<no connection>" 텍스트가 포함 됩니다. 워크시트에 생성된 연결이 있는 경우에는 해당 연결의 이름이 단추에 표시됩니다.  
  
2.  **Analysis Services 연결** 대화 상자에서 **새로 만들기**를 클릭 합니다.  
  
3.  **새 Analysis Services 연결** 대화 상자에서 서버 이름을 입력 합니다.  
  
4.  인증 방법을 지정합니다.  
  
5.  **카탈로그 이름** 드롭다운 목록에서 데이터베이스를 선택 합니다. 인스턴스에 데이터베이스가 없는 경우 **(기본값)** 을 선택 합니다.  
  
6.  연결에 대한 이름을 입력합니다.  
  
7.  **연결 테스트** 를 클릭 하 여 서버 및 데이터베이스를 사용할 수 있는지 확인 합니다.  
  
8.  **확인**을 클릭한 다음 **닫기**를 클릭합니다.  
  
### <a name="connections-using-a-web-service"></a>웹 서비스를 사용하여 연결  
 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 큐브 및 데이터에 대한 찾아보기 기능을 활성화하는 씬 클라이언트 아키텍처를 사용할 경우에는 웹 서비스를 통해 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 서버에 대한 연결을 구성할 수도 있습니다. 웹 기반 클라이언트를 정의하는 방법은 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 온라인 설명서를 참조하십시오.  
  
 웹 서비스용으로 구성된 서버에 대한 액세스 권한이 있다면 처음 연결을 만들 때 연결 유형을 지정할 수 있습니다.  
  
##### <a name="create-an-http-connection-to-analysis-services"></a>Analysis Services에 대한 HTTP 연결 만들기  
  
1.  **새 Analysis Services 연결** 대화 상자를 엽니다.  
  
2.  서버 이름에는 http:// 다음 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 서버에 할당된 URL을 입력합니다.  
  
3.  웹 서비스에 액세스하는 데 필요한 사용자 이름과 암호를 입력합니다.  
  
### <a name="connections-in-the-visio-add-in"></a>Visio 추가 기능에서 연결  
 Visio는 Excel과는 달리 도구 리본을 제공하지 않으며 연결 설정 또는 모니터링을 위한 단추가 없습니다. 대신 처음으로 데이터 마이닝 셰이프를 선택하여 Visio 페이지로 끌어 놓을 때 데이터 연결을 만듭니다. 셰이프 모델을 선택하고 기타 옵션을 설정하라는 메시지가 나타납니다.  
  
 Excel에서 이전에 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 데이터 원본에 대한 연결을 사용한 경우 해당 연결이 선택 가능한 데이터 원본으로 표시됩니다.  
  
##### <a name="create-a-connection-for-a-visio-shape"></a>Visio 셰이프에 대한 연결 만들기  
  
1.  데이터 마이닝 템플릿을 열고 데이터 마이닝 셰이프 중 하나를 선택합니다.  
  
2.  셰이프를 빈 페이지로 끌어서 놓습니다.  
  
3.  **데이터 원본 선택** 대화 상자의 목록에서 데이터 원본을 선택 하거나 **새로 만들기**를 클릭 합니다.  
  
4.  **새로 만들기**를 선택 하는 경우 앞에서 설명한 절차에 따라 서버 및 카탈로그 이름을 지정 하거나 웹 서비스를 통해 연결 합니다.  
  
##  <a name="changing-connections"></a><a name="bkmk_change"></a>연결 변경  
 동일한 워크시트 내에 여러 개의 연결을 만들 수 있지만 한 번에 한 연결만 활성화할 수 있습니다. 현재 연결의 이름이 **연결** 단추에 표시 됩니다.  
  
 Excel 용 데이터 마이닝 클라이언트에서 **추적** 을 클릭 한 다음 **현재 연결**을 클릭 하 여 현재 연결에 대 한 연결 문자열 및 상태를 확인할 수도 있습니다.  
  
#### <a name="use-a-different-server-connection"></a>다른 서버 연결 사용  
  
1.  **연결**을 클릭 합니다.  
  
2.  **Analysis Services 연결** 창의 **다른 연결** 목록에서 연결을 선택 하 고 **현재 만들기**를 클릭 합니다.  
  
3.  **연결 테스트** 를 클릭 하 여 연결을 사용할 수 있는지 확인 합니다.  
  
 마이닝 모델 처리를 완료하면 결과는 로컬로 저장되며 한 서버에 대한 연결을 닫고 다른 서버에 연결하면 데이터에는 영향이 없습니다. 그러나 데이터가 손상될 수 있으므로 데이터 마이닝 모델이 처리되고 있는 동안에는 연결을 변경 또는 해제하지 않는 것이 좋습니다.  
  
#### <a name="modify-an-existing-server-connection"></a>기존 서버 연결 수정  
  
1.  다른 데이터베이스나 서버에 연결하려는 경우 기존 연결을 변경할 수 없으며 새 연결을 만들어야 합니다.  
  
2.  연결 문자열을 수정하여 쿼리 제한 시간을 늘리거나 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 인스턴스와 관련된 다른 매개 변수를 추가해야 하는 경우 한 가지 옵션은 연결 문자열이 저장되는 .dmc 파일을 편집하는 것입니다.  
  
     \<drive: > \Users\\<myusername\>\AppData\Local\Microsoft\Data 마이닝 추가 기능  
  
##  <a name="connecting-to-external-data-sources"></a><a name="bkmk_extconnections"></a>외부 데이터 원본에 연결  
 **분석** 리본의 도구는 Excel의 데이터로만 작동 하지만 **데이터 마이닝** 리본의 도구를 사용 하면 외부 데이터 원본에 직접 연결 하 여 모델에 대 한 입력으로 사용 하거나 샘플링을 수행할 수 있습니다.  
  
 이러한 추가 기능의 다음과 같은 도구가 데이터 마이닝에 외부 데이터를 사용할 수 있도록 지원합니다.  
  
-   [데이터 마이닝 추가 기능을 SQL Server &#40;샘플 데이터&#41;](sample-data-sql-server-data-mining-add-ins.md)  
  
-   [분류 마법사 &#40;Excel 용 데이터 마이닝 추가 기능&#41;](classify-wizard-data-mining-add-ins-for-excel.md)  
  
-   [Excel 용 데이터 마이닝 추가 기능에 대 한 예측 마법사 &#40;&#41;](estimate-wizard-data-mining-add-ins-for-excel.md)  
  
-   [클러스터 마법사는 Excel 용 데이터 마이닝 추가 기능을 &#40;&#41;](cluster-wizard-data-mining-add-ins-for-excel.md)  
  
-   [Excel 용 데이터 마이닝 추가 기능에 대 한 예측 마법사 &#40;&#41;](forecast-wizard-data-mining-add-ins-for-excel.md)  
  
-   [데이터 마이닝 추가 기능을 SQL Server &#40;마이닝 구조를 만듭니다&#41;](create-mining-structure-sql-server-data-mining-add-ins.md)  
  
-   [정확도 차트 &#40;SQL Server 데이터 마이닝 추가 기능&#41;](accuracy-chart-sql-server-data-mining-add-ins.md)  
  
-   [수익 차트 &#40;SQL Server 데이터 마이닝 추가 기능&#41;](profit-chart-sql-server-data-mining-add-ins.md)  
  
-   [분류표는 데이터 마이닝 추가 기능을 SQL Server &#40;&#41;](classification-matrix-sql-server-data-mining-add-ins.md)  
  
### <a name="using-analysis-services-as-a-data-source"></a>Analysis Services를 데이터 원본으로 사용  
 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 큐브나 테이블 형식 모델에 저장된 데이터에는 직접 액세스할 수 없습니다. 대신 Excel에서 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 서버에 대한 연결을 만들고 데이터를 사용하여 모델을 만듭니다.  
  
### <a name="relational-data-sources"></a>관계형 데이터 원본  
 관계형 원본의 데이터를 모델에 대한 입력으로 사용하려는 경우 다음 버전의 SQL Server에 연결합니다.  
  
-   SQL Server 2008  
  
-   SQL Server 2008 R2  
  
-   SQL Server 2012  
  
 또한 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]에서 데이터 원본으로 지원하는 다른 관계형 데이터 원본에서 데이터를 가져올 수도 있습니다. 지원 되는 데이터 원본에 대 한 자세한 내용은 [다차원 모델의 데이터 원본](multidimensional-models/data-sources-in-multidimensional-models.md) 을 참조 하세요.  
  
 다음 데이터 형식은 데이터 마이닝에 사용할 수 없으며 모델 작성 시 포함될 경우 오류가 발생할 수 있습니다.  
  
-   ntext  
  
-   binary  
  
## <a name="see-also"></a>참고 항목  
 [Excel 용 데이터 마이닝 클라이언트&#41;추적 &#40;](trace-data-mining-client-for-excel.md)  
  
  
