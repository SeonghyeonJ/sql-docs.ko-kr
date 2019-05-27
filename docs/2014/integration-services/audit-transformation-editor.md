---
title: 감사 변환 편집기 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.audittransformation.f1
helpviewer_keywords:
- Audit Transformation Editor
ms.assetid: 32786a34-5870-4fde-83c7-ec74d62404b8
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 9d31f297b9544c75e416fe798facd6a1c328ff0d
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66061414"
---
# <a name="audit-transformation-editor"></a>감사 변환 편집기
  감사 변환을 사용하면 패키지가 실행되는 환경에 대한 데이터를 패키지의 데이터 흐름에 포함할 수 있습니다. 예를 들어 패키지, 컴퓨터 및 운영자의 이름을 데이터 흐름에 추가할 수 있습니다. [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 에는 이 정보를 제공하는 시스템 변수가 포함되어 있습니다.  
  
 감사 변환에 대한 자세한 내용은 [Audit Transformation](data-flow/transformations/audit-transformation.md)을 참조하십시오.  
  
## <a name="options"></a>변수  
 **출력 열 이름**  
 감사 정보를 포함할 새 출력 열의 이름을 입력합니다.  
  
 **감사 유형**  
 감사 정보를 제공할 사용 가능한 시스템 변수를 선택합니다.  
  
|값|Description|  
|-----------|-----------------|  
|**실행 인스턴스 GUID**|패키지의 실행 인스턴스를 고유하게 식별하는 GUID를 삽입합니다.|  
|**패키지 ID**|패키지를 고유하게 식별하는 GUID를 삽입합니다.|  
|**패키지 이름**|패키지 이름을 삽입합니다.|  
|**버전 ID**|패키지 버전을 고유하게 식별하는 GUID를 삽입합니다.|  
|**실행 시작 시간**|패키지 실행이 시작된 시간을 삽입합니다.|  
|**컴퓨터 이름**|패키지가 시작된 컴퓨터 이름을 삽입합니다.|  
|**사용자 이름**|패키지를 시작한 사용자의 로그인 이름을 삽입합니다.|  
|**태스크 이름**|감사 변환이 연결된 데이터 흐름 태스크의 이름을 삽입합니다.|  
|**태스크 ID**|감사 변환이 연결된 데이터 흐름 태스크를 고유하게 식별하는 GUID를 삽입합니다.|  
  
## <a name="see-also"></a>관련 항목  
 [Integration Services 오류 및 메시지 참조](../../2014/integration-services/integration-services-error-and-message-reference.md)  
  
  
