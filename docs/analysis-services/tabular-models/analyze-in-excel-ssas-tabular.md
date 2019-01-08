---
title: Excel에서 Analysis Services 테이블 형식 모델 분석 | Microsoft Docs
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: abd910573f512e32ee58c6c3afabac17664f4b24
ms.sourcegitcommit: 38076f423663bdbb42f325e3d0624264e05beda1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/06/2018
ms.locfileid: "52983874"
---
# <a name="analyze-in-excel"></a>도구 모음
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  Excel에서에서 분석 기능, SSDT에서 테이블 형식 모델 작성자를 신속 하 게 개발 하는 동안 모델 프로젝트를 분석 하는 방법을 제공 합니다. Excel에서 분석 기능은 Microsoft Excel을 열고 모델 작업 영역 데이터베이스에 데이터 원본을 연결한 후 자동으로 워크시트에 피벗 테이블을 추가합니다. 피벗 테이블 필드 목록에 작업 영역 데이터베이스 개체(테이블, 열 및 측정값)가 필드로 포함됩니다. 그런 다음 유효 사용자 또는 역할 및 큐브 뷰의 컨텍스트 내에서 개체 및 데이터를 조회할 수 있습니다.  
  
 이 문서에서는 Microsoft Excel, 피벗 테이블 및 피벗 차트를 사용 하 여 이미 익숙한 가정 합니다. Excel 사용법에 대한 자세한 내용은 Excel 도움말을 참조하십시오.  
  
##  <a name="bkmk_benefits"></a> 이점  
 모델 작성자는 Excel에서 분석 기능을 사용하여 일반적인 데이터 분석 애플리케이션인 Microsoft Excel으로 모델 프로젝트의 효율성을 테스트할 수 있습니다. 분석에서에서 Excel 기능을 사용 하려면 Microsoft Office 2003 있어야 합니다. 또는 나중에 SSDT와 동일한 컴퓨터에 설치 합니다.  
  
 Excel에서 분석 기능은 Excel을 실행하여 새 Excel 통합 문서(.xls)를 만듭니다. 통합 문서에 모델 작업 영역 데이터베이스에 대한 데이터 연결이 생성됩니다. 워크시트에 빈 피벗 테이블이 추가되고 피벗 테이블 필드 목록에 모델 개체 메타데이터가 채워집니다. 그런 다음 피벗 테이블에 보기 가능한 데이터 및 슬라이서를 추가할 수 있습니다.  
  
 Excel에서 분석 기능을 사용할 때는 기본적으로 현재 로그온한 사용자 계정이 유효 사용자가 됩니다. 이 계정은 주로 모델 개체 또는 데이터를 보는 데 제한이 없는 관리자이지만, 다른 유효 사용자 이름 또는 역할을 지정할 수도 있습니다. 이를 통해 Excel에서 특정 사용자 또는 역할 컨텍스트에 따라 모델 프로젝트를 검색할 수 있습니다. 유효 사용자 지정 시 다음과 같은 옵션이 있습니다.  
  
 **현재 Windows 사용자**  
 현재 로그온한 사용자 계정을 사용합니다.  
  
 **기타 Windows 사용자**  
 현재 로그온한 사용자가 아닌 다른 Windows 사용자 이름을 지정합니다. 다른 Windows 사용자를 사용할 때 암호는 필요 없습니다. Excel에서 유효 사용자 이름의 컨텍스트 내에서 개체 및 데이터에 대한 조회만 가능하며, 모델 개체 또는 데이터를 변경할 수 없습니다.  
  
 **역할**  
 역할은 개체 메타데이터 및 데이터에 대한 사용자 권한을 정의하는 데 사용됩니다. 역할은 일반적으로 특정 Windows 사용자 또는 Windows 사용자 그룹에 대해 정의됩니다. 일부 역할은 DAX 수식에서 정의하는 추가 행 수준 필터를 포함할 수 있습니다. Excel에서 분석 기능을 사용할 때 선택 사항으로 사용할 역할을 지정할 수 있습니다. 역할에 정의된 권한 및 필터에 따라 조회할 수 있는 개체 메타데이터 및 데이터가 제한됩니다. 자세한 내용은 [만들기 및 관리 역할](../../analysis-services/tabular-models/create-and-manage-roles-ssas-tabular.md)입니다.  
  
 유효 사용자 또는 역할 외에 큐브 뷰를 지정할 수 있습니다. 큐브 뷰를 사용하는 모델의 작성자는 모델 개체 및 데이터의 특정 비즈니스 시나리오 보기를 정의할 수 있습니다. 기본 설정은 큐브 뷰를 사용하지 않는 것입니다. Excel에서 분석을 사용 하 여 큐브 뷰를 사용 하려면 이미 SSDT의 큐브 뷰 대화 상자를 사용 하 여 대 큐브 뷰 정의 되어야 합니다. 큐브 뷰가 지정되면 피벗 테이블 필드 목록에 큐브 뷰에서 선택된 개체만 포함됩니다. 자세한 내용은 [만들기 및 관리 하는 큐브 뷰](../../analysis-services/tabular-models/create-and-manage-perspectives-ssas-tabular.md)합니다.  
  
##  <a name="bkmk_rt"></a> Related tasks  
  
|**항목**|**설명**|  
|---------------|---------------------|  
|[Excel에서 테이블 형식 모델 분석](../../analysis-services/tabular-models/analyze-a-tabular-model-in-excel-ssas-tabular.md)|이 문서에서는 Excel을 열고 모델 작업 영역 데이터베이스에 데이터 원본 연결 만들기, 워크시트에 피벗 테이블을 추가 하려면 모델 디자이너에서 Excel 기능에서 분석을 사용 하는 방법을 설명 합니다.|  
  
## <a name="see-also"></a>참고 항목  
 [Excel에서 테이블 형식 모델 분석](../../analysis-services/tabular-models/analyze-a-tabular-model-in-excel-ssas-tabular.md)   
 [역할](../../analysis-services/tabular-models/roles-ssas-tabular.md)   
 [큐브 뷰](../../analysis-services/tabular-models/perspectives-ssas-tabular.md)  
  
  
