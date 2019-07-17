---
title: EXPORT (DMX) | Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 2cf3cf85b0efb024d65744f6eea0f5eea47ead83
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68074850"
---
# <a name="export-dmx"></a>EXPORT(DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  서버의 마이닝 모델 또는 마이닝 구조 개체를 Analysis Services 백업 파일(.abf)로 추출합니다.  
  
## <a name="syntax"></a>구문  
  
```  
  
EXPORT <object type> <object name>[, <object name>] [<object type> <object name>[, <object name] ] TO <filename> [WITH DEPENDENCIES]  
```  
  
## <a name="arguments"></a>인수  
 *개체 유형*  
 (마이닝 모델 또는 마이닝 구조)를 내보내려면 개체 형식의 선택 사항입니다.  
  
 *개체 이름*  
 (선택 사항) 내보낼 개체 이름입니다.  
  
 *filename*  
 문자열로 내보낼 파일의 이름과 위치입니다.  
  
## <a name="remarks"></a>설명  
 문에서 마이닝 모델을 지정하는 경우 결과 파일에는 연결된 마이닝 구조도 포함됩니다. 문을 지정 하는 경우 **WITH DEPENDENCIES**, 개체 (예를 들어, 데이터 원본 및 데이터 원본 뷰)를 처리 하는 데 필요한 모든 개체가.abf 파일에 포함 됩니다.  
  
 데이터베이스 이거나 가져오거나 내보내는 데 서버 관리자에서 개체를 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 데이터베이스입니다.  
  
## <a name="export-mining-structure-example"></a>마이닝 구조 내보내기 예  
 다음 예에서는 Targeted Mailing 및 Forecasting 마이닝 구조와 Association 마이닝 모델을 특정 파일 위치로 내보냅니다. Association 모델은 Market Basket 마이닝 구조의 일부이므로 이 예에서는 Market Basket 구조도 내보냅니다. 연결 모델을 사용 하 여 내보낸 부분에서는 Market Basket 마이닝 구조를 내보낼 수는 존재할 수 있는 다른 모든 마이닝 모델 **마이닝 모델**가 아닌 **마이닝 구조**합니다.  
  
```  
EXPORT MINING STRUCTURE [Targeted Mailing], [Forecasting] MINING MODEL Association TO 'C:\TM_NEW.abf'  
```  
  
## <a name="export-mining-model-example"></a>마이닝 모델 내보내기 예  
 다음 예에서는 Association 마이닝 모델을 지정한 파일 위치로 내보냅니다. 문에서 지정 하므로 **WITH DEPENDENCIES**, 데이터 원본 및 데이터 원본 뷰 개체도.abf 파일에 포함 됩니다.  
  
```  
EXPORT MINING MODEL [Association] TO 'C:\Association_NEW.abf' WITH DEPENDENCIES  
```  
  
## <a name="see-also"></a>관련 항목  
 [Data Mining Extensions &#40;DMX&#41; 데이터 정의 문](../dmx/dmx-statements-data-definition.md)   
 [Data Mining Extensions &#40;DMX&#41; 데이터 조작 문](../dmx/dmx-statements-data-manipulation.md)   
 [Data Mining Extensions &#40;DMX&#41; 문 참조](../dmx/data-mining-extensions-dmx-statements.md)   
 [가져오기 &#40;DMX&#41;](../dmx/import-dmx.md)   
 [데이터 마이닝 개체 내보내기 및 가져오기](../analysis-services/data-mining/export-and-import-data-mining-objects.md)  
  
  
