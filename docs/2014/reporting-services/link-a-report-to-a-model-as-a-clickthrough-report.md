---
title: 보고서를 클릭 광고 보고서로 모델에 연결 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- customizing clickthrough reports
- clickthrough reports, customizing
- clickthrough reports, templates
ms.assetid: 3af42de3-67ef-41c2-bc8a-7045baec6f63
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 45b7695a9cd259d10155036ce1f9367a71e2fe72
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/26/2020
ms.locfileid: "66108366"
---
# <a name="link-a-report-to-a-model-as-a-clickthrough-report"></a>보고서를 클릭 광고 보고서로 모델에 연결
  기본 클릭 광고 보고서 템플릿을 사용하는 대신 보고서 작성기 보고서를 만들고 보고서 모델의 특정 엔터티에 연결할 수 있습니다. 보고서를 보는 사람이 주 보고서에서 대화형 데이터를 클릭하면 이 보고서는 클릭 광고 보고서로 표시됩니다. 엔터티에 보고서를 연결하려면 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 보고서 관리자를 사용합니다.  
  
> [!IMPORTANT]  
>  보고서에서 사용되는 기본 엔터티는 보고서가 연결되는 동일한 엔터티여야 합니다.  
  
### <a name="to-start-report-manager-from-a-browser"></a>브라우저에서 보고서 관리자를 시작하려면  
  
1.  [!INCLUDE[msCoName](../includes/msconame-md.md)] Internet Explorer 6.0 이상을 엽니다.  
  
2.  웹 브라우저의 주소 표시줄에 보고서 관리자 URL을 입력합니다. 기본적으로 URL은 http://\<*ComputerName*>/reports입니다.  
  
### <a name="to-create-a-customized-clickthrough-report"></a>사용자 지정 클릭 광고 보고서를 만들려면  
  
1.  사용자 지정 클릭 광고 보고서를 추가할 보고서 모델로 이동합니다.  
  
2.  보고서 모델을 두 번 클릭합니다.  
  
3.  **클릭 광고**을 클릭합니다.  
  
4.  사용자 지정 클릭 광고 보고서를 연결할 엔터티를 선택합니다.  
  
    > [!NOTE]  
    >  이 엔터티는 사용자 지정 클릭 광고 보고서의 기준 엔터티와 같아야 합니다.  
  
5.  선택한 엔터티의 단일 인스턴스를 클릭할 때 사용자 지정 보고서를 표시하려면 단일 인스턴스 보고서 **찾아보기** 단추를 클릭합니다.  
  
     또는  
  
     선택한 엔터티의 여러 인스턴스를 클릭할 때 사용자 지정 보고서를 표시하려면 여러 인스턴스 보고서 **찾아보기** 단추를 클릭합니다.  
  
6.  보고서를 선택하고 **확인**을 클릭합니다.  
  
7.  **적용**을 클릭합니다.  
  
## <a name="see-also"></a>참고 항목  
 [클릭 광고 보고서 &#40;SSRS&#41;](reports/clickthrough-reports-ssrs.md)  
  
  
