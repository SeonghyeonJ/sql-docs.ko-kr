---
title: Analysis Services 테이블 형식 모델에 테이블 추가 | Microsoft Docs
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 224df75c15acf560c7eadc70fe91fbbc2b0396d9
ms.sourcegitcommit: 8a64c59c5d84150659a015e54f8937673cab87a0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/08/2018
ms.locfileid: "53072290"
---
# <a name="add-a-table"></a>테이블 추가
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  이 문서는 이전에 가져온 데이터 모델에 데이터 원본에서 테이블을 추가 하는 방법을 설명 합니다. 같은 데이터 원본의 테이블을 추가하려면 기존 데이터 원본 연결을 사용합니다. 단일 데이터 원본에서 임의 개수의 테이블을 가져올 때는 항상 단일 연결을 사용하는 것이 좋습니다.  
  
### <a name="to-add-a-table-from-an-existing-data-source"></a>기존 데이터 원본의 테이블을 추가하려면  
  
1.  [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]에서 **모델** 메뉴를 클릭한 다음 **기존 연결**을 클릭합니다.  
  
2.  **기존 연결** 페이지에서 추가할 테이블이 있는 데이터 원본에 대한 연결을 선택한 다음 **열기**를 클릭합니다.  
  
3.  **테이블 및 뷰 선택** 페이지에서 모델에 추가할 데이터 원본의 테이블을 선택합니다.  
  
    > [!NOTE]  
    >  **테이블 및 뷰 선택** 페이지에서는 이전에 가져온 테이블이 선택된 것으로 표시되지 않습니다.  이 연결을 사용하여 이전에 가져온 테이블을 선택했는데 해당 테이블에 다른 이름을 지정하지 않은 경우 이름에 1이 추가됩니다. 이 연결을 사용하여 이전에 가져온 테이블을 다시 선택할 필요는 없습니다.  
  
4.  필요한 경우 **미리 보기 및 필터**를 사용하여 특정 열만 선택하거나 가져올 데이터에 필터를 적용합니다.  
  
5.  **마침** 을 클릭하여 새 테이블을 가져옵니다.  
  
> [!NOTE]  
>  단일 데이터 원본에서 여러 테이블을 동시에 가져올 때는 원본에 있는 해당 테이블 간의 관계가 모델에서 자동으로 생성됩니다. 그러나 나중에 테이블을 추가할 때는 새로 추가한 테이블과 이전에 가져온 테이블 간에 모델에서 관계를 수동으로 만들어야 할 수 있습니다.  
  
## <a name="see-also"></a>참고자료  
 [데이터 가져오기](http://msdn.microsoft.com/library/6617b2a2-9f69-433e-89e0-4c5dc92982cf)   
 [테이블 삭제](../../analysis-services/tabular-models/delete-a-table-ssas-tabular.md)  
  
  
