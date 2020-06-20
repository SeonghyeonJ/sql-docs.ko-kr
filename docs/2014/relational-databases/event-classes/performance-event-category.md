---
title: Performance 이벤트 범주 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- SQL Server event classes, Performance event category
- Performance event category [SQL Server]
- event classes [SQL Server], Performance event category
ms.assetid: 708f3585-d8be-4980-bbff-672d7c59397e
author: stevestein
ms.author: sstein
ms.openlocfilehash: b0c076a4132298797313ecbf0874d9d2d4e453cd
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/18/2020
ms.locfileid: "85052806"
---
# <a name="performance-event-category"></a>Performance 이벤트 범주
  **Performance** 이벤트 범주를 사용하여 **Showplan** 이벤트 클래스 및 SQL DML(데이터 조작 언어) 연산자 실행으로 생성된 이벤트 클래스를 모니터링할 수 있습니다.  
  
## <a name="in-this-section"></a>섹션 내용  
  
|항목|Description|  
|-----------|-----------------|  
|[Auto Stats 이벤트 클래스](auto-stats-event-class.md)|인덱스 및 열 통계가 자동으로 업데이트되었음을 나타냅니다.|  
|[Degree of Parallelism&#40;7.0 Insert&#41; 이벤트 클래스](degree-of-parallelism-7-0-insert-event-class.md)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서 직렬 또는 병렬 계획을 사용하여 SELECT, INSERT, UPDATE 또는 DELETE 문을 실행했음을 나타냅니다. 또한 작업에 사용된 CPU 수도 보고합니다.|  
|[Performance Statistics 이벤트 클래스](performance-statistics-event-class.md)|실행 중인 쿼리의 성능을 모니터링합니다.|  
|[Showplan All 이벤트 클래스](showplan-all-event-class.md)|SQL 문 내의 **Showplan** 연산자를 식별합니다.|  
|[Showplan All for Query Compile 이벤트 클래스](showplan-all-for-query-compile-event-class.md)|**Showplan** 연산자에 대한 컴파일 시간 데이터를 표시합니다.|  
|[Showplan Statistics Profile 이벤트 클래스](showplan-statistics-profile-event-class.md)|쿼리의 예상 비용을 표시합니다.|  
|[Showplan XML 이벤트 클래스](showplan-xml-event-class.md)|SQL 문 내의 **Showplan** 연산자를 식별합니다. 이 이벤트 클래스는 각 이벤트를 잘 정의된 XML 문서로 저장합니다.|  
|[Showplan XML for Query Compile 이벤트 클래스](showplan-xml-for-query-compile-event-class.md)|**Showplan** 연산자에 대한 컴파일 시간 데이터를 XML 형식으로 표시합니다.|  
|[Showplan XML Statistics Profile 이벤트 클래스](showplan-xml-statistics-profile-event-class.md)|SQL 문에 연결된 **Showplan** 연산자를 식별합니다. 출력은 XML 문서입니다.|  
|[SQL:FullTextQuery 이벤트 클래스](sql-fulltextquery-event-class.md)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서 전체 텍스트 쿼리를 실행했음을 나타냅니다.|  
|[Plan Guide Successful 이벤트 클래스](plan-guide-successful-event-class.md)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서 계획 지침이 포함된 쿼리 또는 일괄 처리에 대한 실행 계획을 성공적으로 만들었음을 나타냅니다.|  
|[Plan Guide Unsuccessful 이벤트 클래스](plan-guide-unsuccessful-event-class.md)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서 계획 지침이 포함된 쿼리 또는 일괄 처리에 대한 실행 계획을 만들지 못했음을 나타냅니다.|  
  
## <a name="see-also"></a>참고 항목  
 [확장 이벤트](../extended-events/extended-events.md)  
  
  
