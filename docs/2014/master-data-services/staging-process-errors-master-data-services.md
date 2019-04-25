---
title: 준비 프로세스 오류(Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- staging process [Master Data Services], error messages
ms.assetid: 0d9be0dd-638f-4dd4-92b2-253fda655455
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: d8b32a8e9b6b61c2d108d3a9b8e63242854d0a63
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62763274"
---
# <a name="staging-process-errors-master-data-services"></a>준비 프로세스 오류(Master Data Services)
  준비 프로세스가 완료되면 준비 테이블에 있는 처리된 모든 레코드의 ErrorCode 열에 값이 지정됩니다. 이러한 값에 대해서는 다음 표에서 설명합니다.  
  
|코드|Error|발생하는 경우/세부 정보|적용 테이블|  
|----------|-----------|--------------------------|----------------------|  
|210001|동일한 멤버 코드가 준비 테이블에 여러 번 나옵니다.|준비 배치에 동일한 멤버 코드가 여러 번 나옵니다. 멤버가 생성 또는 업데이트되지 않았습니다.|리프<br /><br /> 통합<br /><br /> 관계|  
|210003|특성 값이 존재하지 않거나 비활성인 멤버를 참조합니다.|도메인 기반 특성을 준비할 때는 이름이 아니라 코드를 사용해야 합니다. **ImportType0**, **1**및 **2**에 적용됩니다.|리프<br /><br /> 통합|  
|210006|멤버 코드가 비활성입니다.|**ImportType** = **1**이며, 존재하지 않는 멤버 코드를 지정했습니다.|리프<br /><br /> 통합<br /><br /> 관계|  
|210032|계층 이름이 없거나 잘못되었습니다.|명시적 계층이 없거나 **HierarchyName** 값이 비어 있습니다.|통합<br /><br /> 관계|  
|210035|코드 생성 비즈니스 규칙이 없기 때문에 **MemberCode** 가 필요합니다.|자동 코드 생성을 사용하지 않는 한 멤버를 만들거나 업데이트할 때 **MemberCode** 가 항상 필요합니다. 자세한 내용은 [코드 자동 생성&#40;Master Data Services&#41;](automatic-code-creation-master-data-services.md)을 참조하세요.|리프<br /><br /> 통합|  
|210036|코드 생성 비즈니스 규칙이 있기 때문에 **MemberCode** 가 필요 없습니다.|자동 코드 생성을 사용하는 경우 멤버를 만들거나 업데이트할 때 **MemberCode** 가 필요하지 않습니다. 그러나 선택하는 경우 코드를 지정할 수 있습니다. 자세한 내용은 [코드 자동 생성&#40;Master Data Services&#41;](automatic-code-creation-master-data-services.md)을 참조하세요.|리프<br /><br /> 통합|  
|210041|"ROOT"는 올바른 멤버 코드가 아닙니다.|**MemberCode** 값에 "ROOT"라는 단어가 포함되어 있습니다.|리프<br /><br /> 통합<br /><br /> 관계|  
|210042|"MDMUNUSED"는 올바른 멤버 코드가 아닙니다.|**MemberCode** 값에 "MDMUNUSED"라는 단어가 포함되어 있습니다.|리프<br /><br /> 통합<br /><br /> 관계|  
|210052|MemberCode는 도메인 기반 특성 값으로 사용되기 때문에 비활성화할 수 없습니다.|**ImportType** = **3** 또는 **4**일 때 멤버가 다른 멤버의 특성 값으로 사용되는 경우 준비할 수 없습니다. **ImportType5** 또는 **6** 을 사용하여 값을 NULL로 설정하거나 준비 프로세스를 실행하기 전에 값을 변경합니다.|리프<br /><br /> 통합|  
|300002|멤버 코드가 잘못되었습니다.|관계: 부모 또는 자식 멤버 코드가 존재 하지 않습니다.<br /><br /> 리프 또는 통합: **ImportType** = **3** 또는 **4**이며 멤버 코드가 존재하지 않습니다.|리프<br /><br /> 통합<br /><br /> 관계|  
|300004|멤버 코드가 이미 있습니다.|**ImportType** = **1** 이며, 이미 엔터티에 존재하는 멤버 코드를 사용했습니다.|리프<br /><br /> 통합|  
|210011|**RelationshipType** 이 **1**인 경우 **ParentCode** 는 리프 멤버일 수 없습니다.|**ParentCode** 값이 통합 멤버 코드인지 확인합니다.|관계|  
|210015|멤버 코드가 계층 및 배치에 대한 준비 테이블에 여러 번 나옵니다.|명시적 계층의 경우 동일한 배치에서 동일한 멤버의 위치를 여러 번 지정했습니다.|관계|  
|210016|이 관계는 순환 참조를 일으키므로 만들 수 없습니다.|자식을 부모 자격으로 할당할 때 발생합니다.|관계|  
|210046|멤버는 루트의 형제일 수 없습니다.|**RelationshipType** = **2** (형제)이고 **ParentCode** 또는 **ChildCode** 가 **루트**인 경우에 발생합니다. 멤버는 루트 노드와 같은 수준일 수 없으며 자식일 수만 있습니다.|관계|  
|210047|멤버는 사용 안 함의 형제일 수 없습니다.|**RelationshipType** = **2** (형제)이고 **ParentCode** 또는 **ChildCode** 가 **사용 안 함**인 경우에 발생합니다. 멤버는 사용 안 함 노드의 자식일 수만 있습니다.|관계|  
|210048|**ParentCode** 와 **ChildCode** 는 같을 수 없습니다.|**ParentCode** 값은 **ChildCode** 값과 동일합니다. 이 값은 달라야 합니다.|관계|  
  
## <a name="see-also"></a>관련 항목  
 [준비 프로세스 동안 발생 하는 오류를 보려면 &#40;Master Data Services&#41;](view-errors-that-occur-during-staging-master-data-services.md)   
 [데이터 가져오기 &#40;Master Data Services&#41;](overview-importing-data-from-tables-master-data-services.md)  
  
  
