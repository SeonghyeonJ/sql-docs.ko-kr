---
title: 보고서 또는 모델을 공유 데이터 원본에 바인딩(SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- shared data sources [Reporting Services]
- data sources [Reporting Services], shared
ms.assetid: 23cc15f2-2883-48e2-bc6c-fa0ab61a2e21
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: b6d973d4628e9c80b47c4fea0ef3476dbd05131f
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66107447"
---
# <a name="bind-a-report-or-model-to-a-shared-data-source-ssrs"></a>보고서 또는 모델을 공유 데이터 원본에 바인딩(SSRS)
  보고서나 모델을 테스트 서버에서 프로덕션 서버로 이동할 때와 같이 로컬 컴퓨터에 파일을 저장한 다음 이 파일을 다른 보고서 서버로 업로드해야 하는 경우가 있습니다. 보고서나 모델을 새 서버로 업로드하는 경우 새 보고서 서버에 저장된 공유 데이터 원본에 다시 바인딩해야 합니다. 보고서나 모델을 다시 바인딩하지 않으면 새 보고서 서버에서 액세스할 때 제대로 작동하지 않습니다.  
  
> [!IMPORTANT]  
>  보고서나 모델을 공유 데이터 원본에 다시 바인딩하기 전에 보고서 서버나 SharePoint 라이브러리에 이미 데이터 원본이 있어야 합니다. 데이터 원본에 대한 자세한 내용은 [공유 데이터 원본 만들기, 수정 및 삭제&#40;SSRS&#41;](create-modify-and-delete-shared-data-sources-ssrs.md)를 참조하세요.  
  
### <a name="to-bind-a-report-or-model-to-a-shared-data-source-on-a-report-server-running-in-native-mode"></a>보고서나 모델을 기본 모드로 실행되는 보고서 서버의 공유 데이터 원본에 바인딩하려면  
  
1.  **보고서 관리자**에서 서버로 업로드할 보고서나 모델의 이름을 클릭합니다.  
  
     속성 탭이 열립니다.  
  
2.  **데이터 원본**을 클릭합니다.  
  
3.  **찾아보기**를 클릭한 다음 보고서나 모델을 바인딩할 데이터 원본을 탐색합니다.  
  
4.  데이터 원본을 선택한 다음 **확인**을 클릭합니다.  
  
5.  **적용**을 클릭합니다.  
  
     이제 보고서나 모델이 선택한 데이터 원본에 바인딩되었습니다.  
  
### <a name="to-bind-a-report-or-model-to-a-shared-data-source-on-a-report-server-running-in-sharepoint-integrated-mode"></a>보고서나 모델을 SharePoint 통합 모드로 실행되는 보고서 서버의 공유 데이터 원본에 바인딩하려면  
  
1.  라이브러리가 아직 열려 있지 않으면 빠른 실행 표시줄에서 해당 이름을 클릭합니다. 라이브러리 이름이 나타나지 않으면 **모든 사이트 콘텐츠 보기**를 클릭한 다음 라이브러리 이름을 클릭합니다.  
  
2.  보고서나 모델을 가리키고 아래쪽 화살표를 클릭합니다.  
  
3.  **데이터 원본 관리**를 클릭합니다.  
  
4.  **dataSource1**을 클릭합니다.  
  
5.  **연결 형식** 영역에서 **공유 데이터 원본** 이 선택되어 있는지 확인합니다.  
  
6.  **데이터 원본 링크** 영역에서 줄임표(...) 단추를 클릭합니다.  
  
7.  사용할 데이터 원본을 찾습니다.  
  
8.  데이터 원본을 선택하고 **확인**을 클릭합니다.  
  
9. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
10. **닫기**를 클릭합니다.  
  
## <a name="see-also"></a>관련 항목  
 [파일 또는 보고서 업로드&#40;보고서 관리자&#41;](../reports/upload-a-file-or-report-report-manager.md)   
 [SharePoint 라이브러리에 문서 업로드&#40;SharePoint 모드의 Reporting Services&#41;](../upload-documents-to-a-sharepoint-library-reporting-services-in-sharepoint-mode.md)   
 [공유 데이터 원본 만들기 및 관리&#40;SharePoint 통합 모드의 Reporting Services&#41;](../create-manage-shared-data-sources-reporting-services-sharepoint-integrated-mode.md)   
 [공유 데이터 원본 만들기, 삭제 또는 수정&#40;보고서 관리자&#41;](../create-delete-or-modify-a-shared-data-source-report-manager.md)   
 [데이터 연결, 데이터 원본 및 Reporting Services의 연결 문자열](../data-connections-data-sources-and-connection-strings-in-reporting-services.md)   
 [Reporting Services&#40;SSRS&#41;에서 지원하는 데이터 원본](../create-deploy-and-manage-mobile-and-paginated-reports.md)  
  
  
