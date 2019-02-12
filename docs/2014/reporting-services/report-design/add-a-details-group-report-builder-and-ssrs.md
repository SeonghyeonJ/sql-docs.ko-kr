---
title: 세부 정보 그룹 추가(보고서 작성기 및 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
ms.assetid: 5ef8efba-6d48-4aeb-a3b9-a02ba5a44614
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 9e6b467700d816e4b46dfa7ae38f67be32234c7d
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/11/2019
ms.locfileid: "56041794"
---
# <a name="add-a-details-group-report-builder-and-ssrs"></a>세부 정보 그룹 추가(보고서 작성기 및 SSRS)
  보고서 데이터 세트의 세부 데이터는 그룹 식이 없는 그룹으로 지정됩니다. 행렬에 대한 세부 데이터를 표시하거나, 테이블이나 목록에서 삭제한 세부 데이터를 다시 추가하거나, 추가적인 세부 정보 그룹을 추가하려면 기존 테이블릭스 데이터 영역에 세부 정보 그룹을 추가합니다. 그룹에 대한 자세한 내용은 [그룹 이해&#40;보고서 작성기 및 SSRS&#41;](understanding-groups-report-builder-and-ssrs.md)를 참조하세요.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-a-details-group-to-a-tablix-data-region"></a>테이블릭스 데이터 영역에 세부 정보 그룹을 추가하려면  
  
1.  디자인 화면에서 테이블릭스 데이터 영역의 아무 곳이나 클릭하여 선택합니다. 선택한 데이터 영역에 대한 행 및 열 그룹이 그룹화 창에 표시됩니다.  
  
2.  그룹화 창에서 가장 안쪽 자식 그룹을 마우스 오른쪽 단추로 클릭합니다. **그룹 추가**를 클릭한 다음 **자식 그룹**을 클릭합니다. **테이블릭스 그룹** 대화 상자가 열립니다.  
  
3.  **그룹 식**에서 식을 공백으로 둡니다. 세부 정보 그룹에는 식이 없습니다.  
  
4.  **세부 데이터 표시**를 선택합니다.  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
     새로운 세부 정보 그룹이 그룹화 창에 자식 그룹으로 추가되고 1단계에서 선택한 그룹의 행 핸들에 세부 정보 그룹 아이콘이 표시됩니다. 핸들에 대한 자세한 내용은 [테이블릭스 데이터 영역 셀, 행 및 열&#40;보고서 작성기 및 SSRS&#41;](tablix-data-region-cells-rows-and-columns-report-builder-and-ssrs.md)를 참조하세요.  
  
## <a name="see-also"></a>관련 항목  
 [데이터 영역에서 그룹 추가 또는 삭제&#40;보고서 작성기 및 SSRS&#41;](add-or-delete-a-group-in-a-data-region-report-builder-and-ssrs.md)   
 [그룹 이해&#40;보고서 작성기 및 SSRS&#41;](understanding-groups-report-builder-and-ssrs.md)   
 [테이블릭스 데이터 영역&#40;보고서 작성기 및 SSRS&#41;](../tablix-data-region-report-builder-and-ssrs.md)   
 [테이블&#40;보고서 작성기 및 SSRS&#41;](tables-report-builder-and-ssrs.md)   
 [행렬&#40;보고서 작성기 및 SSRS&#41;](create-a-matrix-report-builder-and-ssrs.md)   
 [목록&#40;보고서 작성기 및 SSRS&#41;](create-invoices-and-forms-with-lists-report-builder-and-ssrs.md)   
 [테이블, 행렬 및 목록&#40;보고서 작성기 및 SSRS&#41;](tables-matrices-and-lists-report-builder-and-ssrs.md)  
  
  
