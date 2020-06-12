---
title: 저장 프로시저의 쿼리 컨텍스트 액세스 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- execution context [Analysis Services]
- stored procedures [Analysis Services], query context
- Context object
- query context [Analysis Services]
ms.assetid: bdc7dad8-2f22-4265-aba4-a3a451527840
author: minewiskan
ms.author: owend
ms.openlocfilehash: 9da8ddb223ed03c0208fe524ea5cd7195a039c97
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84545374"
---
# <a name="accessing-query-context-in-stored-procedures"></a>저장 프로시저의 쿼리 컨텍스트 액세스
  저장 프로시저의 실행 컨텍스트는 ADOMD.NET 서버 개체 모델의 `Context` 개체로 저장 프로시저 코드 내에서 사용할 수 있습니다. 이것은 읽기 전용 컨텍스트이며 저장 프로시저로 수정할 수 없습니다. 이 개체에 다음 속성을 사용할 수 있습니다.  
  
|속성|Type|설명|  
|--------------|----------|-----------------|  
|**CurrentCube**|Cube|현재 쿼리 컨텍스트에 대한 큐브입니다.|  
|**CurrentDatabaseName**|String|현재 데이터베이스의 식별자입니다.|  
|**CurrentConnection**|연결|현재 컨텍스트의 연결 개체에 대한 참조입니다.|  
|**통과**|정수|현재 컨텍스트의 패스 번호입니다.|  
  
 저장 프로시저에서 MDX(Multidimensional Expressions) 개체 모델을 사용할 경우 `Context` 개체가 존재하게 됩니다. 그러나 클라이언트에서 MDX 개체 모델을 사용할 경우에는 이 개체를 사용할 수 없습니다. `Context` 개체는 저장 프로시저에 명시적으로 전달되거나 저장 프로시저에서 명시적으로 반환하지 않습니다. 이 개체는 저장 프로시저 실행 중에만 사용할 수 있습니다.  
  
## <a name="see-also"></a>참고 항목  
 [다차원 모델 어셈블리 관리](../multidimensional-models/multidimensional-model-assemblies-management.md)   
 [저장 프로시저 정의](../multidimensional-models-extending-olap-stored-procedures/defining-stored-procedures.md)  
  
  
