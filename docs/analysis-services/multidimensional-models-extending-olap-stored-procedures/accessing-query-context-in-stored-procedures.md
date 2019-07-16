---
title: 저장 프로시저의 쿼리 컨텍스트 액세스 | Microsoft Docs
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: olap
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 1679b5ddaf2c3abefb6da4e89e97e84193593630
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/15/2019
ms.locfileid: "68209406"
---
# <a name="accessing-query-context-in-stored-procedures"></a>저장 프로시저의 쿼리 컨텍스트 액세스
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  저장된 프로시저의 실행 컨텍스트를 저장된 프로시저 코드 내에서 사용할 수는 **상황에 맞는** 개체는 ADOMD.NET 서버 개체 모델입니다. 이것은 읽기 전용 컨텍스트이며 저장 프로시저로 수정할 수 없습니다. 이 개체에 다음 속성을 사용할 수 있습니다.  
  
|속성|type|설명|  
|--------------|----------|-----------------|  
|**CurrentCube**|Cube|현재 쿼리 컨텍스트에 대한 큐브입니다.|  
|**CurrentDatabaseName**|문자열|현재 데이터베이스의 식별자입니다.|  
|**CurrentConnection**|연결|현재 컨텍스트의 연결 개체에 대한 참조입니다.|  
|**전달**|정수|현재 컨텍스트의 패스 번호입니다.|  
  
 합니다 **상황에 맞는** 개체가 저장된 프로시저에서 MDX (Multidimensional Expressions) 개체 모델에서 사용 되는 경우. 그러나 클라이언트에서 MDX 개체 모델을 사용할 경우에는 이 개체를 사용할 수 없습니다. 합니다 **상황에 맞는** 개체는 명시적으로 전달 되거나 저장된 프로시저에서 반환 합니다. 이 개체는 저장 프로시저 실행 중에만 사용할 수 있습니다.  
  
## <a name="see-also"></a>관련 항목  
 [다차원 모델 어셈블리 관리](../../analysis-services/multidimensional-models/multidimensional-model-assemblies-management.md)   
 [저장된 프로시저 정의](../../analysis-services/multidimensional-models-extending-olap-stored-procedures/defining-stored-procedures.md)  
  
  
