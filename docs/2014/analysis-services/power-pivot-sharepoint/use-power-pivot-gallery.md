---
title: PowerPivot 갤러리 사용 | Microsoft Docs
ms.custom: ''
ms.date: 09/01/2015
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: c9ff92d1-787a-4f34-990f-6676b61875d7
author: minewiskan
ms.author: owend
ms.openlocfilehash: f634f6c0a435c733af7f223de333cb52d95ce897
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84547715"
---
# <a name="use-powerpivot-gallery"></a>PowerPivot 갤러리 사용
  [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 갤러리는 특수한 용도의 SharePoint 문서 라이브러리로서 PowerPivot 데이터를 포함하는 게시된 Excel 통합 문서 및 Reporting Services 보고서에 대해 풍부한 미리 보기와 문서 관리 기능을 제공합니다.

> [!NOTE]
>  해당 서버를 구성하는 방법에 따라 특정 문서에 대한 미리 보기 영역에서 경고 또는 오류 메시지가 표시될 수 있습니다. Excel 통합 문서를 열 때마다 해당 데이터를 자동으로 새로 고치도록 설정한 경우 메시지가 표시될 수 있습니다. Excel 서비스가 새로 고칠 때 경고 오류 메시지를 표시하도록 구성되어 있으면 데이터 새로 고침 경고 메시지가 미리 보기 이미지로 나타납니다. 팜 또는 서비스 관리자는 구성 설정을 수정하여 실제 워크시트의 미리 보기가 나타나도록 허용할 수 있습니다. 자세한 내용은 [Create a trusted location for PowerPivot sites in Central Administration](create-a-trusted-location-for-power-pivot-sites-in-central-administration.md)을 참조하세요.

##  <a name="in-this-topic"></a><a name="bkmk_top"></a> 항목 내용

-   [PowerPivot 갤러리의 아이콘](#icons)

-   [PowerPivot 갤러리에 Excel 통합 문서 저장](#add)

-   [게시된 PowerPivot 통합 문서를 기반으로 새 보고서나 통합 문서 만들기](#newdocs)

-   [통합 문서 또는 보고서를 전체 페이지 모드로 열기](#view)

-   [PowerPivot 갤러리의 PowerPivot 통합 문서에 대한 데이터 새로 고침 예약](#newdr)

-   [PowerPivot 갤러리에서 통합 문서 또는 보고서 삭제](#delete)

-   [축소판 이미지 새로 고침](#image)

-   [알려진 문제](#bkmk_known_issues)

 [필수 구성 요소](#prereq)

##  <a name="prerequisites"></a><a name="prereq"></a> 전제 조건

> [!NOTE]
>  파워 피벗 갤러리에는 Microsoft Silverlight가 필요합니다.  Microsoft Edge 브라우저는 Silverlight를 지원하지 않습니다. Microsoft Edge에서 라이브러리 콘텐츠를 보려면 파워 피벗 갤러리에서 **라이브러리** 탭을 클릭 한 다음 문서 라이브러리 보기를 **모든 문서**로 변경 합니다.  
> 기본 보기를 변경하려면 **라이브러리** 탭을 클릭한 다음 보기 수정을 클릭합니다. "이 보기를 기본 보기로 만듭니다"를 클릭한 다음 확인을 클릭하여 기본 보기를 저장합니다.
> Microsoft Edge에서 지 원하는 항목에 대 한 자세한 내용은 Windows 블로그, [과거의 중단, 2 부: ActiveX에](https://blogs.windows.com/msedgedev/2015/05/06/a-break-from-the-past-part-2-saying-goodbye-to-activex-vbscript-attachevent/) 대 한 의견을 표시 합니다. VBScript ...

 필수 구성 요소의 전체 목록은 [PowerPivot 갤러리 만들기 및 사용자 지정](create-and-customize-power-pivot-gallery.md)을 참조 하세요.

##  <a name="icons-in-powerpivot-gallery"></a><a name="icons"></a>PowerPivot 갤러리의 아이콘
 아이콘은 콘텐츠 사용 가능 여부와 상태를 시각적으로 표시합니다.

|아이콘|설명|
|----------|-----------------|
|![GMNI_PowerPivotGalleryIcon_Hourglass](../media/gmni-powerpivotgalleryicon-hourglass.gif "GMNI_PowerPivotGalleryIcon_Hourglass")|문서의 각 페이지 축소판 이미지를 생성하는 동안에는 모래 시계 아이콘이 나타납니다. 업데이트된 이미지를 표시하려면 페이지를 새로 고칩니다.|
|![GMNI_PowerPivotGalleryIcon_Truncated](../media/gmni-powerpivotgalleryicon-truncated.gif "GMNI_PowerPivotGalleryIcon_Truncated")|통합 문서 또는 보고서의 페이지 수가 PowerPivot 갤러리에 표시할 수 있는 것보다 많으면 페이지 아이콘이 나타납니다. 모든 페이지를 표시하려면 클라이언트 애플리케이션을 사용해야 합니다.|
|![GMNI_PowerPivotGalleryIcon_Error](../media/gmni-powerpivotgalleryicon-error.gif "GMNI_PowerPivotGalleryIcon_Error")|문서의 축소판 이미지를 렌더링할 수 없으면 오류 아이콘이 나타납니다. 문서는 라이브러리에 게시되기는 하지만 사용자 지정 PowerPivot 갤러리 보기에서 렌더링할 수는 없습니다. PowerPivot for Excel 추가 기능 등의 클라이언트 애플리케이션에서 문서를 볼 수 있습니다.|
|![GMNI_PowerPivotGalleryIcon_badtype](../media/gmni-powerpivotgalleryicon-badtype.gif "GMNI_PowerPivotGalleryIcon_badtype")|업로드한 문서를 PowerPivot 갤러리에서 렌더링할 수 없으면 콘텐츠 사용할 수 없음 아이콘이 나타납니다. 지원되는 문서 유형에는 SQL Server 2008 R2 Reporting Services 보고서 작성기에서 만든 PowerPivot 통합 문서 및 보고서가 포함됩니다.<br /><br /> 휴지통에서 문서를 재활용하는 경우에도 이 아이콘이 표시됩니다.<br /><br /> 이전에는 유효한 미리 보기 이미지를 제공했던 문서에 이 아이콘이 표시되게 하려는 경우 문서 속성을 편집하고 변경 사항을 저장하여 이미지를 새로 고칠 수 있습니다.|
|![GMNI_PowerPivotGalleryIcon_Locked](../media/gmni-powerpivotgalleryicon-locked.gif "GMNI_PowerPivotGalleryIcon_Locked")|이 문서에 대해 축소판 이미지를 의도적으로 사용할 수 없도록 설정한 경우 콘텐츠 잠김 아이콘이 나타납니다. PowerPivot 갤러리는 PowerPivot 데이터가 없는 Excel 통합 문서나 스냅샷 생성 요구 사항을 충족하지 않는 PowerPivot 통합 문서 또는 Reporting Services 보고서에 대한 축소판 이미지를 생성하지 않습니다. 자세한 내용은 이 항목의 사전 요구 사항 섹션을 참조하세요.|

##  <a name="save-an-excel-workbook-to-powerpivot-gallery"></a><a name="add"></a>PowerPivot 갤러리에 Excel 통합 문서 저장
 Excel 2010에서 제공하는 모든 공유 기술을 사용하여 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 통합 문서를 라이브러리에 게시할 수 있습니다. 예를 들어 Excel 2010에서 다른 이름으로 저장을 사용하여 라이브러리에 대한 전체 또는 부분 SharePoint 경로를 지정할 수 있습니다.

1.  파일을 저장합니다.

2.  1.  **Excel 2010:** 파일 메뉴에서 **저장 및 보내기**를 클릭합니다.

    2.  **SharePoint에 저장**을 클릭합니다.

    3.  Excel 서비스 옵션을 사용하여 게시하려는 개별 시트 또는 매개 변수를 선택하려면 **게시 옵션** 을 클릭합니다. 예를 들어 Excel 서비스 옵션의 매개 변수 탭을 사용하면 게시된 통합 문서에 표시할 슬라이서를 선택할 수 있습니다.

    1.  **Excel 2013:**  파일 메뉴에서 **저장**을 클릭하세요.

    2.  Excel 서비스 옵션을 사용하여 게시하려는 개별 시트 또는 매개 변수를 선택하려면 **브라우저 보기 옵션** 을 클릭합니다. 예를 들어 Excel 서비스 옵션의 매개 변수 탭을 사용하면 게시된 통합 문서에 표시할 슬라이서를 선택할 수 있습니다.

3.  다른 이름으로 저장 대화 상자의 파일 이름에 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 갤러리의 전체 또는 부분 URL을 입력합니다. 서버 이름과 같이 URL 주소의 일부를 입력하는 경우 사이트를 탐색하여 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 갤러리를 찾을 수 있습니다. 이렇게 하려면 **저장** 을 클릭하여 지정한 서버에 대한 연결을 엽니다.

     ![GMNI_ExcelSaveAs](../media/gmni-excelsaveas.gif "GMNI_ExcelSaveAs")

1.  다른 이름으로 저장 대화 상자를 사용하여 사이트에서 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 갤러리를 선택합니다.

2.  **열기** 를 클릭하여 라이브러리를 엽니다.

3.  **저장** 을 클릭하여 통합 문서를 라이브러리에 게시합니다.

 브라우저 창에서 해당 문서가 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 갤러리에 나타나는지 확인합니다. 새로 게시된 문서가 목록에 나타납니다. 라이브러리 설정에 따라 문서의 표시 방법이 결정됩니다(예: 날짜별 오름차순 정렬 또는 이름별 사전순 정렬). 가장 최근에 추가된 항목을 보려면 브라우저 창을 새로 고쳐야 할 수도 있습니다.

#### <a name="upload-a-workbook-into-powerpivot-gallery"></a>PowerPivot 갤러리에 통합 문서 업로드
 SharePoint에서 시작하여 컴퓨터에서 게시할 파일을 선택하려는 경우 통합 문서를 업로드할 수도 있습니다.

1.  SharePoint  사이트에서 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 갤러리를 엽니다.

2.  라이브러리 리본에서 **문서**를 클릭합니다.

3.  **문서 업로드**에서 업로드 옵션을 선택한 다음 업로드할 파일의 이름과 위치를 입력합니다. 라이브러리 설정에 따라 문서의 표시 방법이 결정됩니다. 가장 최근에 추가된 항목을 보려면 브라우저 창을 새로 고쳐야 할 수도 있습니다.

##  <a name="create-new-reports-or-workbooks-based-on-a-published-powerpivot-workbook"></a><a name="newdocs"></a>게시 된 PowerPivot 통합 문서를 기반으로 새 보고서 나 통합 문서 만들기
 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 갤러리에 게시하는 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 통합 문서의 경우 게시된 통합 문서를 연결된 데이터 원본으로 사용하는 추가 통합 문서나 Reporting Services 보고서를 만들 수 있습니다.

|||
|-|-|
|![GMNI_btn_NewDocReportGallery](../media/gmni-btn-newdocreportgallery.gif "GMNI_btn_NewDocReportGallery")|보고서 작성기나 Excel 2010을 시작하려면 새 보고서 단추의 아래쪽 화살표 부분을 클릭합니다. 새 보고서 단추를 사용하려면 PowerPivot 갤러리에서 미리 정의된 보기(극장식, 갤러리, 회전식) 중 하나를 사용해야 합니다.|

#### <a name="create-report-builder-report"></a>보고서 작성기 보고서 만들기
 라이브러리에서 기존 PowerPivot 통합 문서를 기반으로 새 보고서를 만들려면 PowerPivot 갤러리를 포함하는 같은 사이트를 위해 Reporting Services를 SharePoint 통합에 맞게 구성해야 합니다. 보고서 작성기 보고서 만들기 옵션을 선택하면 보고서 서버에서 보고서 작성기가 다운로드되어 처음 사용 시 로컬 워크스테이션에 설치됩니다. 그런 다음 새 보고서에 대한 자리 표시자 보고서 파일이 만들어지고 PowerPivot 갤러리에 저장됩니다. 또한, PowerPivot 통합 문서에 대한 연결 정보가 보고서에서 새 데이터 원본으로 자동 생성됩니다. 다음 단계로, 디자인 작업 영역에서 데이터 세트 및 보고서 레이아웃을 만들 수 있습니다. 보고서 작성기를 사용하여 보고서를 조합할 때 변경 사항 및 최종 결과를 갤러리의 보고서 문서에 저장할 수 있습니다. 나중에 데이터 연결이 끊어지지 않도록 같은 라이브러리에 보고서와 통합 문서 파일을 함께 둡니다.

#### <a name="open-new-excel-workbook"></a>새 Excel 통합 문서 열기
 기존 통합 문서에서 새 Excel 통합 문서를 만들려면 로컬 컴퓨터에 Excel 및 [!INCLUDE[ssGeminiClient](../../includes/ssgeminiclient-md.md)] 이 있어야 합니다. 새 Excel 통합 문서 열기를 선택하면 Excel이 시작되고, 빈 통합 문서(.xlsx) 파일이 열리며, 백그라운드로 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 데이터가 연결된 데이터 원본으로 로드됩니다. 원래 통합 문서의 PowerPivot 창의 데이터만 새 통합 문서에서 사용됩니다. 원래 통합 문서의 피벗 테이블 또는 피벗 차트는 제외됩니다. 새 통합 문서는 원래 통합 문서의 데이터에 연결됩니다. 데이터가 새 통합 문서 자체에 복사되지는 않습니다.

##  <a name="open-a-workbook-or-report-in-full-page-mode"></a><a name="view"></a>통합 문서 또는 보고서를 전체 페이지 모드로 열기
 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 갤러리 미리 보기와 관계없이 미리 보기한 문서의 표시된 축소판 이미지를 클릭하여 전체 페이지 모드로 문서를 열 수 있습니다. [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 통합 문서는 브라우저에서 열립니다. Reporting Services 보고서는 SharePoint 서버의 Reporting Services 배포에 포함된 ReportViewer 웹 파트에서 열립니다.

 브라우저에서 통합 문서를 보는 다른 방법은 클라이언트 워크스테이션의 Excel에서 여는 것입니다. 파일을 보려면 Excel 2013 또는 Excel 2010과 [!INCLUDE[ssGeminiClient](../../includes/ssgeminiclient-md.md)] 추가 기능이 있어야 합니다. Excel 2007을 사용하여 파일을 열 수 있지만 이를 사용하여 데이터를 피벗할 수 없습니다. 따라서 PowerPivot 보기와 만들기에는 Excel 2013 또는 Excel 2010을 사용하는 것이 좋습니다. 필요한 애플리케이션이 없는 경우 브라우저를 사용하여 SharePoint에서 통합 문서를 표시해야 합니다.

##  <a name="schedule-data-refresh-for-powerpivot-workbooks-in-powerpivot-gallery"></a><a name="newdr"></a>PowerPivot 갤러리의 PowerPivot 통합 문서에 대 한 데이터 새로 고침 예약
 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 데이터를 예약된 간격으로 새로 고칠 수 있습니다.

|||
|-|-|
|![GMNI_btn_NewDataRefreshReportGallery](../media/gmni-btn-newdatarefreshreportgallery.gif "GMNI_btn_NewDataRefreshReportGallery")|데이터 새로 고침 관리 단추를 클릭하여 연결된 데이터 원본에서 업데이트된 데이터를 검색하는 일정을 만들거나 봅니다. 일정을 만드는 방법에 대 한 지침은 [데이터 새로 고침 예약 &#40;SharePoint용 PowerPivot&#41;](../schedule-a-data-refresh-powerpivot-for-sharepoint.md)를 참조 하세요.|

##  <a name="delete-a-workbook-or-report-in-powerpivot-gallery"></a><a name="delete"></a>PowerPivot 갤러리에서 통합 문서 또는 보고서 삭제
 라이브러리에서 문서를 삭제하려면 먼저 모든 문서 보기로 전환합니다.

1.  SharePoint  사이트에서 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 갤러리를 엽니다.

2.  리본에서 **라이브러리**를 클릭합니다.

3.  보기 관리에 있는 현재 보기 목록에서 아래쪽 화살표를 클릭하고 모든 문서를 선택합니다.

4.  삭제할 통합 문서나 보고서를 선택합니다.

5.  문서(파일)의 관리에서 **문서 삭제** 단추를 클릭합니다.

##  <a name="refresh-a-thumbnail-image"></a><a name="image"></a>축소판 이미지 새로 고침
 다음 단계를 사용하여 PowerPivot 갤러리에 있는 문서에 대한 축소판 이미지를 다시 생성합니다.

1.  PowerPivot 갤러리를 모든 문서 보기로 전환합니다. 이렇게 전환하려면 리본에서 **라이브러리** 를 클릭하고 **현재 보기** 를 **모든 문서**로 변경합니다.

2.  축소판 이미지를 새로 고칠 통합 문서 또는 보고서를 선택합니다.

3.  오른쪽에 있는 아래쪽 화살표를 클릭한 다음 **속성 편집**을 선택합니다.

4.  **저장**을 클릭합니다. 문서를 저장하면 스냅샷 서비스에서 미리 보기 이미지를 다시 생성합니다.

##  <a name="known-issues"></a><a name="bkmk_known_issues"></a> 알려진 문제

### <a name="document-type-is-not-supported"></a>문서 유형이 지원되지 않습니다.
 **PowerPivot 갤러리 문서** 내용 유형은 지원되지 않습니다. 문서 라이브러리에 대해 **PowerPivot 갤러리 문서** 내용 유형을 사용하도록 설정하고 해당 유형의 새 문서를 만들려고 하면 다음 중 하나와 비슷한 오류 메시지가 표시됩니다.

-   ' 새 문서 '를 사용 하려면 Microsoft Sharepoint Foundation 호환 응용 프로그램 및 웹 브라우저가 있어야 합니다. 문서 라이브러리에 문서를 추가 하려면 ' 문서 업로드 ' 단추를 클릭 합니다.

-   "인터넷 주소 ' http://[server name]/testSite/PowerPivot Gallery/ReportGallery/Forms/Template.xlsx '이 (가) 잘못 되었습니다." " Microsoft Excel에서 ' http://[server name]/testSite/PowerPivot 갤러리/ReportGallery/Forms/Template.xlsx ' 파일에 액세스할 수 없습니다. 원인은 다음과 같습니다.

 **PowerPivot 갤러리 문서** 내용 유형이 문서 라이브러리에 자동으로 추가되지 않습니다. 지원되지 않는 내용 유형을 사용하도록 수동으로 설정하지 않으면 이 문제가 발생하지 않습니다.

## <a name="see-also"></a>참고 항목
 [중앙 관리에서 powerpivot 사이트에 대 한 신뢰할 수 있는 위치 만들기](create-a-trusted-location-for-power-pivot-sites-in-central-administration.md) powerpivot [갤러리](delete-power-pivot-gallery.md) [만들기 및 사용자 지정 Powerpivot 갤러리 만들기 및 사용자 지정](create-and-customize-power-pivot-gallery.md) [데이터 새로 고침 &#40;SharePoint용 PowerPivot&#41;](../schedule-a-data-refresh-powerpivot-for-sharepoint.md)

